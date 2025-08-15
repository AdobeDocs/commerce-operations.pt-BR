---
title: Configuração avançada de verniz
description: Configurar recursos avançados de verniz, incluindo verificação de integridade, graça e modos santo.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Configuração avançada de verniz

O verniz fornece vários recursos que impedem que os clientes enfrentem longos atrasos e tempos limite quando o servidor do Commerce não está funcionando corretamente. Esses recursos podem ser configurados no arquivo `default.vcl`. Este tópico descreve as adições que o Commerce fornece no arquivo VCL (Linguagem de configuração de verniz) que você baixa do Administrador.

Consulte o [Manual de referência de verniz](https://varnish-cache.org/docs/index.html) para obter detalhes sobre o uso da Linguagem de configuração de verniz.

## Verificação de integridade

O recurso de verificação de integridade do Vernish consulta o servidor do Commerce para determinar se ele está respondendo em tempo hábil. Se estiver respondendo normalmente, o conteúdo novo é gerado novamente após a expiração do TTL (Time to Live). Caso contrário, o verniz sempre serve conteúdo obsoleto.

O Commerce define a seguinte verificação de integridade padrão:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

A cada 5 segundos, essa verificação de integridade chama o script `pub/health_check.php`. Este script verifica a disponibilidade do servidor, de cada banco de dados e do Redis (se instalado). O script deve retornar uma resposta em 2 segundos. Se o script determinar que qualquer um desses recursos está inativo, retornará um código de erro 500 HTTP. Se esse código de erro for recebido em seis de dez tentativas, o back-end será considerado não íntegro.

O script `health_check.php` está localizado no diretório `pub`. Se o diretório raiz do Commerce for `pub`, altere o caminho no parâmetro `url` de `/pub/health_check.php` para `health_check.php`.

Para obter mais informações, consulte a documentação das [Verificações de integridade do verniz](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks).

## Modo de carência

O modo de carência permite que o Vernish mantenha um objeto no cache além de seu valor TTL. O verniz pode então fornecer o conteúdo expirado (obsoleto) enquanto busca uma nova versão. Isso melhora o fluxo de tráfego e diminui os tempos de carregamento. Ele é usado nas seguintes situações:

- Quando o back-end do Commerce está íntegro, mas uma solicitação está demorando mais do que o normal
- Quando o back-end do Commerce não está íntegro.

A sub-rotina `vcl_hit` define como o Verniz responde a uma solicitação para objetos que foram armazenados em cache.

### Quando o back-end do Commerce está íntegro

Quando as verificações de integridade determinam que o back-end do Commerce está íntegro, o Vernish verifica se o tempo permanece no período de carência. O período de carência padrão é de 300 segundos, mas um comerciante pode definir o valor do Administrador conforme descrito em [Configurar o Commerce para usar o Verniz](configure-varnish-commerce.md). Se o período de carência não tiver expirado, o Varnish fornecerá o conteúdo obsoleto e atualizará de forma assíncrona o objeto do servidor do Commerce. Se o período de carência tiver expirado, o Varnish fornecerá o conteúdo obsoleto e atualizará de forma síncrona o objeto do back-end do Commerce.

O tempo máximo que o Verniz fornece a um objeto obsoleto é a soma do período de carência (300 segundos por padrão) e do valor TTL (86.400 segundos por padrão).

Para alterar o período de carência padrão no arquivo `default.vcl`, edite a seguinte linha na subrotina `vcl_hit`:

```conf
if (obj.ttl + 300s > 0s) {
```

### Quando o back-end do Commerce não está íntegro

Se o back-end do Commerce não for responsivo, o Varnish fornecerá conteúdo obsoleto do cache por três dias (ou conforme definido em `beresp.grace`) mais o TTL restante (que por padrão é um dia), a menos que o conteúdo em cache seja limpo manualmente.

## Modo Saint

O modo Saint exclui back-end não íntegros por um período de tempo configurável. Como resultado, back-end não íntegros não podem fornecer tráfego ao usar o Varnish como balanceador de carga. O modo Saint pode ser usado com o modo de carência para permitir o manuseio complexo de servidores de back-end não íntegros. Por exemplo, se um servidor de back-end não estiver íntegro, as tentativas poderão ser roteadas para outro servidor. Se todos os outros servidores estiverem inativos, forneça objetos em cache obsoletos. Os hosts de back-end do modo saint e os períodos de blecaute são definidos no arquivo `default.vcl`.

O modo Saint também pode ser usado quando as instâncias do Commerce são colocadas offline individualmente para executar tarefas de manutenção e atualização sem afetar a disponibilidade do site do Commerce.

### Pré-requisitos do modo Saint

Designar uma máquina como a instalação principal. Nesta máquina, instale a instância principal do Commerce, do banco de dados mySQL e do Varnish.

Em todas as outras máquinas, a instância do Commerce deve ter acesso ao banco de dados mySQL da máquina primária. As máquinas secundárias também devem ter acesso aos arquivos da instância primária do Commerce.

Como alternativa, o controle de versão de arquivos estáticos pode ser desativado em todas as máquinas. Isto pode ser acessado pelo Administrador em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de Arquivos Estáticos** > **Assinar Arquivos Estáticos** = **Não**.

Por fim, todas as instâncias do Commerce devem estar no modo de produção. Antes de o Verniz ser iniciado, limpe o cache em cada instância. No Administrador, vá para **Sistema** > Ferramentas > **Gerenciamento de Cache** e clique em **Limpar Cache do Magento**. Você também pode executar o seguinte comando para limpar o cache:

```bash
bin/magento cache:flush
```

### Instalação

O modo Saint não faz parte do pacote principal de vernizes. É um `vmod` com versão separada que deve ser baixado e instalado. Como resultado, você deve recompilar o Varnish a partir da origem, conforme descrito nas [instruções de instalação](https://varnish-cache.org/docs/index.html) para a sua versão do Varnish.

Depois de recompilar, você pode instalar o módulo Saint mode. Em geral, siga estas etapas:

1. Obter o código-fonte de [módulos de verniz](https://github.com/varnish/varnish-modules). Clonar a versão do Git (versão mestre) desde que as versões 0.9.x contenham um erro de código-fonte.
1. Crie o código-fonte com as ferramentas automáticas:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Consulte [Coleção de módulos vernish](https://github.com/varnish/varnish-modules) para obter informações sobre a instalação do módulo Saint mode.

### Arquivo VCL de exemplo

O código a seguir mostra o código que deve ser adicionado ao arquivo VCL para ativar o modo santo. Coloque as instruções `import` e as definições `backend` na parte superior do arquivo.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
