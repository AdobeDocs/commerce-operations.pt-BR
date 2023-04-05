---
title: Configuração Varnish avançada
description: Configure recursos avançados do Varnish, incluindo os modos de verificação de integridade, carência e saint.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 0%

---


# Configuração Varnish avançada

A Varnish oferece vários recursos que impedem os clientes de experimentar longos atrasos e tempos limite quando o servidor do Commerce não está funcionando corretamente. Esses recursos podem ser configurados no `default.vcl` arquivo. Este tópico descreve as adições que o Commerce fornece no arquivo VCL (Linguagem de configuração Varnish) que você baixa do Administrador.

Consulte a [Manual de referência da Varnish](https://varnish-cache.org/docs/6.3/reference/index.html) para obter detalhes sobre o uso do idioma Varnish Configuration.

## Verificação de integridade

O recurso Varnish health check pesquisa o servidor Commerce para determinar se ele está respondendo em tempo hábil. Se estiver respondendo normalmente, o conteúdo novo é gerado novamente após o período de Tempo de vida (TTL) expirar. Caso contrário, o verniz sempre exibirá conteúdo obsoleto.

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

A cada 5 segundos, essa verificação de integridade chama a função `pub/health_check.php` script. Esse script verifica a disponibilidade do servidor, cada banco de dados e Redis (se instalado). O script deve retornar uma resposta em 2 segundos. Se o script determinar que qualquer um desses recursos está inativo, retornará um código de erro HTTP 500. Se esse código de erro for recebido em seis de dez tentativas, o back-end será considerado incorreto.

O `health_check.php` O script está localizado na variável `pub` diretório. Se o diretório raiz do Commerce estiver `pub`, certifique-se de alterar o caminho no `url` parâmetro de `/pub/health_check.php` para `health_check.php`.

Para obter mais informações, consulte o [Controlos de saúde da Varna](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) documentação.

## Modo de carência

O modo de carência permite que a Varnish mantenha um objeto em cache além do valor TTL. A Varnish pode servir o conteúdo expirado (obsoleto) enquanto busca uma nova versão. Isso melhora o fluxo do tráfego e diminui o tempo de carga. Ele é usado nas seguintes situações:

- Quando o back-end do Commerce está íntegro, mas uma solicitação está demorando mais do que o normal
- Quando o back-end do Commerce não estiver funcionando.

O `vcl_hit` subrotina define como o Varnish responde a uma solicitação para objetos que foram armazenados em cache.

### Quando o back-end do Commerce estiver íntegro

Quando as verificações de integridade determinam que o backend do Commerce está íntegro, a Varnish verifica se o tempo permanece no período de carência. O período de carência padrão é de 300 segundos, mas um comerciante pode definir o valor em Administração, conforme descrito em [Configurar comércio para usar o Varnish](configure-varnish-commerce.md). Se o período de carência não tiver expirado, a Varnish fornecerá o conteúdo obsoleto e atualizará de forma assíncrona o objeto do servidor do Commerce. Se o período de carência tiver expirado, a Varnish exibirá o conteúdo obsoleto e atualizará de forma síncrona o objeto do back-end do Commerce.

A quantidade máxima de tempo que a Varnish serve um objeto obsoleto é a soma do período de carência (300 segundos por padrão) e do valor TTL (86400 segundos por padrão).

Para alterar o período de carência padrão de dentro do `default.vcl` edite a seguinte linha no arquivo `vcl_hit` subrotina:

```conf
if (obj.ttl + 300s > 0s) {
```

### Quando o back-end do Commerce não estiver funcionando

Se o back-end do Commerce não for responsivo, a Varnish fornecerá conteúdo obsoleto do cache por três dias (ou conforme definido em `beresp.grace`) mais o TTL restante (que por padrão é um dia), a menos que o conteúdo em cache seja removido manualmente.

## Modo Saint

O modo Saint exclui backends não íntegros por um período configurável. Como resultado, backends não íntegros não podem fornecer tráfego ao usar Varnish como balanceador de carga. O modo Saint pode ser usado com o modo de carência para permitir o manuseio complexo de servidores de back-end não íntegros. Por exemplo, se um servidor de back-end não estiver funcionando, as tentativas poderão ser roteadas para outro servidor. Se todos os outros servidores estiverem inativos, eles fornecerão objetos obsoletos em cache. Os hosts de backend do modo saint e os períodos de blecaute são definidos no `default.vcl` arquivo.

O modo Saint também pode ser usado quando instâncias de Comércio são individualmente offline para executar tarefas de manutenção e atualização sem afetar a disponibilidade do site de Comércio.

### Pré-requisitos do modo Saint

Designar uma máquina como a instalação primária. Nesta máquina, instale a instância principal do Commerce, mySQL database e Varnish.

Em todas as outras máquinas, a instância do Commerce deve ter acesso ao banco de dados mySQL da máquina primária. As máquinas secundárias também devem ter acesso aos arquivos da instância principal do Commerce.

Como alternativa, o controle de versão de arquivos estáticos pode ser desativado em todas as máquinas. Isso pode ser acessado em Admin em **Lojas** > Configurações > **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de arquivos estáticos** > **Assinar arquivos estáticos** = **Não**.

Finalmente, todas as instâncias de Comércio devem estar no modo de produção. Antes de Varnish ser iniciado, limpe o cache em cada instância. Em Admin, acesse **Sistema** > Ferramentas > **Gerenciamento de cache** e clique em **Liberar cache Magento**. Você também pode executar o seguinte comando para limpar o cache:

```bash
bin/magento cache:flush
```

### Instalação

O modo Saint não faz parte do pacote Varnish principal. É um controle de versão separado `vmod` que deve ser baixada e instalada. Como resultado, você deve recompilar o Varnish da origem, conforme descrito nos seguintes artigos:

- [Instalação do Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Instalação do Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Depois de recompilar, você pode instalar o módulo do modo Saint. Em geral, siga estas etapas:

1. Obter o código-fonte de [Módulos variados](https://github.com/varnish/varnish-modules). Clonar a versão Git (versão principal), pois as versões 0.9.x contêm um erro de código-fonte.
1. Crie o código-fonte com ferramentas automáticas:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Consulte [Coleção de módulo Varna](https://github.com/varnish/varnish-modules) para obter informações sobre a instalação do módulo do modo Saint.

### Arquivo VCL de exemplo

O exemplo de código a seguir mostra o código que deve ser adicionado ao arquivo VCL para ativar o modo saint. Coloque o `import` declarações e `backend` na parte superior do arquivo.

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
