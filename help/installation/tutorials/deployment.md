---
title: Criar ou atualizar a configuração de implantação
description: Siga estas etapas para gerenciar a configuração de implantação do Adobe Commerce ou Magento Open Source.
feature: Install, Deploy, Configuration
exl-id: 2cdde735-0c70-44e8-b2ee-ffb874c1c443
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Criar ou atualizar a configuração de implantação

Não há pré-requisitos para usar este comando.

## Criar ou atualizar a configuração de implantação

[Configuração de implantação](../../configuration/reference/deployment-files.md) O fornece as informações que o aplicativo precisa para inicializar e inicializar.

Você pode usar esse comando se:

* Você instalou o aplicativo anteriormente e deseja modificar a configuração de implantação
* Você deseja criar somente a configuração de implantação e continuar a instalação de alguma outra maneira
* Para atualizar a configuração de implantação sem afetar mais nada

Opções de comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

A tabela a seguir discute os significados dos parâmetros e valores da instalação.

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `--backend-frontname` | Identificador uniforme de recurso ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) para acessar o Admin.<br><br>Para evitar explorações, recomendamos que você não use uma palavra comum como admin, backend. O URI do Administrador pode conter valores alfanuméricos e o caractere de sublinhado (`_`) somente. | Não |
| `--db-host` | Use qualquer um dos seguintes:<br><br>- O nome de host ou endereço IP totalmente qualificado do servidor de banco de dados.<br><br>- `localhost` (padrão) ou `127.0.0.1` se o servidor de banco de dados estiver no mesmo host que o servidor Web. localhost significa que a biblioteca do cliente MySQL usa soquetes UNIX para se conectar ao banco de dados. `127.0.0.1` faz com que a biblioteca do cliente use o protocolo TCP. Para obter mais informações sobre soquetes, consulte [Documentação do PHP PDO_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Nota:** Opcionalmente, você pode especificar a porta do servidor de banco de dados em seu nome de host como `www.example.com:9000` | Não |
| `--db-name` | Nome da instância do banco de dados em que você deseja instalar as tabelas do banco de dados.<br><br>O padrão é `magento2`. | Não |
| `--db-user` | Nome de usuário do proprietário da instância do banco de dados.<br><br>O padrão é `root`. | Não |
| `--db-password` | Senha do proprietário da instância do banco de dados. | Não |
| `--db-prefix` | Use apenas se estiver instalando as tabelas do banco de dados em uma instância do banco de dados que já tenha tabelas do Adobe Commerce.<br><br>Nesse caso, use um prefixo para identificar as tabelas dessa instalação. Alguns clientes têm mais de uma instância Adobe Commerce ou Magento Open Source em execução em um servidor com todas as tabelas no mesmo banco de dados.<br><br>O prefixo pode ter no máximo cinco caracteres. Ela deve começar com uma letra e pode incluir apenas letras, números e caracteres sublinhados.<br><br>Essa opção permite que esses clientes compartilhem o servidor de banco de dados com mais de uma instalação Adobe Commerce ou Magento Open Source. | Não |
| `--session-save` | Use qualquer um dos seguintes:<br><br>- `db` para armazenar dados de sessão na [banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Escolha armazenamento de banco de dados se você tiver um banco de dados clusterizado; caso contrário, pode não haver muito benefício sobre o armazenamento baseado em arquivo.<br><br>- `files` para armazenar dados de sessão no sistema de arquivos. O armazenamento de sessão baseado em arquivo é apropriado, a menos que o acesso ao sistema de arquivos seja lento, você tenha um banco de dados clusterizado ou deseje armazenar dados de sessão em Redis.<br><br>- `redis` para armazenar dados da sessão em [Usar Redis para armazenamento de sessão](../../configuration/cache/config-redis.md). Se você estiver usando Redis para cache padrão ou de página, Redis já deve estar instalado. | Não |
| `--key` | Se você tiver uma, especifique uma chave para criptografar [dados confidenciais](#sensitive-data) no banco de dados. Se você não tiver um, o aplicativo gera um para você. | Não |
| `--db-init-statements` | Parâmetro de configuração avançado do MySQL. Usa instruções de inicialização de banco de dados a serem executadas ao conectar-se ao banco de dados MySQL.<br><br>O padrão é `SET NAMES utf8;`.<br><br>Consulte uma referência semelhante a [este](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) antes de definir quaisquer valores. | Não |
| `--http-cache-hosts` | Lista separada por vírgulas de hosts de gateway do cache HTTP para os quais enviar solicitações de limpeza. (Por exemplo, servidores Vernish.) Use esse parâmetro para especificar o(s) host(s) a serem expurgados na mesma solicitação. (Não importa se você tem apenas um host ou muitos hosts.)<br><br>O formato deve ser `<hostname or ip>:<listen port>`, em que é possível omitir `<listen port>` se for a porta 80. Por exemplo, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Não separe hosts com um caractere de espaço. | Não |

## Importar dados de configuração

Ao configurar um sistema de produção, é uma boa prática importar as definições de configuração do `config.php` e `env.php` no banco de dados.
Essas configurações incluem caminhos e valores de configuração, sites, lojas, visualizações de loja e temas.

Após importar sites, lojas, visualizações de loja e temas, você pode criar atributos de produto e aplicá-los a sites, lojas e visualizações de loja no sistema de produção.

No sistema de produção, execute o seguinte comando para importar dados dos arquivos de configuração (`config.php` e `env.php`) ao banco de dados:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

O modelo opcional `[-n, --no-interaction]` O sinalizador permite que o comando seja executado sem confirmações adicionais.

Para obter informações adicionais, consulte a [Importar dados de arquivos de configuração](../../configuration/cli/import-configuration.md)

### Dados sensíveis

{{$include /help/_includes/sensitive-data.md}}
