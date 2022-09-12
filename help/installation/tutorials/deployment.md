---
title: Criar ou atualizar a configuração de implantação
description: Siga estas etapas para gerenciar a configuração de implantação do Adobe Commerce ou Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# Criar ou atualizar a configuração de implantação

Não há pré-requisitos para usar esse comando.

## Criar ou atualizar a configuração de implantação

[Configuração de implantação](../../configuration/reference/deployment-files.md) O fornece as informações necessárias para inicializar e inicializar o aplicativo.

Você pode usar esse comando se:

* Você instalou o aplicativo anteriormente e deseja modificar a configuração da implantação
* Você deseja criar somente a configuração de implantação e continuar a instalação de alguma outra maneira
* Para atualizar a configuração de implantação sem afetar mais nada

Opções de comando:

```bash
bin/magento setup:config:set [--<parameter>=<value>, ...]
```

A tabela a seguir discute os significados dos parâmetros e valores de instalação.

| Parâmetro | Valor | Obrigatório? |
|--- |--- |--- |
| `--backend-frontname` | Identificador de recurso uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) para acessar o Administrador.<br><br>Para evitar explorações, recomendamos que você não use uma palavra comum como administrador, back-end. O URI de administrador pode conter valores alfanuméricos e o caractere sublinhado (`_`) apenas. | Não |
| `--db-host` | Use qualquer um dos seguintes:<br><br>- O nome de host ou endereço IP totalmente qualificado do servidor de banco de dados.<br><br>- `localhost` (padrão) ou `127.0.0.1` se o servidor de banco de dados estiver no mesmo host que o servidor da Web. localhost significa que a biblioteca do cliente MySQL usa soquetes UNIX para se conectar ao banco de dados. `127.0.0.1` faz com que a biblioteca do cliente use o protocolo TCP. Para obter mais informações sobre soquetes, consulte o [Documentação do PHP DOP_MYSQL](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Observação:** Opcionalmente, você pode especificar a porta do servidor de banco de dados em seu nome de host como `www.example.com:9000` | Não |
| `--db-name` | Nome da instância do banco de dados na qual deseja instalar as tabelas do banco de dados.<br><br>O padrão é `magento2`. | Não |
| `--db-user` | Nome de usuário do proprietário da instância do banco de dados.<br><br>O padrão é `root`. | Não |
| `--db-password` | Senha do proprietário da instância do banco de dados. | Não |
| `--db-prefix` | Use somente se estiver instalando as tabelas do banco de dados em uma instância de banco de dados que já tenha tabelas Adobe Commerce e Magento Open Source.<br><br>Nesse caso, use um prefixo para identificar as tabelas para esta instalação. Alguns clientes têm mais de uma instância Adobe Commerce ou Magento Open Source em execução em um servidor com todas as tabelas no mesmo banco de dados.<br><br>O prefixo pode ter no máximo cinco caracteres. Deve começar com uma letra e pode incluir somente letras, números e caracteres sublinhados.<br><br>Essa opção permite que esses clientes compartilhem o servidor de banco de dados com mais de uma instalação do Adobe Commerce ou Magento Open Source. | Não |
| `--session-save` | Use qualquer um dos seguintes:<br><br>- `db` para armazenar dados da sessão no [banco de dados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/). Escolha o armazenamento do banco de dados se tiver um banco de dados em cluster; caso contrário, pode não haver muito benefício com o armazenamento baseado em arquivos.<br><br>- `files` para armazenar dados de sessão no sistema de arquivos. O armazenamento de sessão baseado em arquivo é apropriado, a menos que o acesso ao sistema de arquivos esteja lento, você tenha um banco de dados em cluster ou queira armazenar os dados da sessão em Redis.<br><br>- `redis` para armazenar os dados da sessão no [Use Redis para armazenamento de sessão](../../configuration/cache/config-redis.md). Se você estiver usando o Redis para armazenamento em cache padrão ou de página, o Redis já deve estar instalado. | Não |
| `--key` | Se você tiver uma, especifique uma chave para criptografar [dados confidenciais](#sensitive-data) no banco de dados. Se você não tiver um, o aplicativo gera um para você. | Não |
| `--db-init-statements` | Parâmetro de configuração do MySQL avançado. Usa instruções de inicialização de banco de dados a serem executadas ao se conectar ao banco de dados MySQL.<br><br>O padrão é `SET NAMES utf8;`.<br><br>Consulte uma referência semelhante a [this one](https://dev.mysql.com/doc/refman/5.6/en/server-options.html) antes de definir qualquer valor. | Não |
| `--http-cache-hosts` | Lista separada por vírgulas de hosts de gateway de cache HTTP para os quais enviar solicitações de limpeza. (Por exemplo, servidores Varnish.) Use esse parâmetro para especificar o host ou hosts a serem limpos na mesma solicitação. (Não importa se você tem apenas um host ou muitos hosts.)<br><br>O formato deve ser `<hostname or ip>:<listen port>`, onde é possível omitir `<listen port>` se for a porta 80. Por exemplo, `--http-cache-hosts=192.0.2.100,192.0.2.155:6081`. Não separe hosts com um caractere de espaço. | Não |

## Importar dados de configuração

Ao configurar um sistema de produção, é recomendável importar as configurações de `config.php` e `env.php` no banco de dados.
Essas configurações incluem caminhos e valores de configuração, sites, lojas, visualizações de loja e temas.

Após importar sites, lojas, visualizações de loja e temas, é possível criar atributos de produto e aplicá-los a sites, lojas e visualizações de loja no sistema de produção.

No sistema de produção, execute o seguinte comando para importar dados dos arquivos de configuração (`config.php` e `env.php`) ao banco de dados:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

O `[-n, --no-interaction]` O sinalizador permite que o comando seja executado sem confirmações adicionais.

Para obter mais informações, verifique a [Importar dados de arquivos de configuração](../../configuration/cli/import-configuration.md)

### Dados sensíveis

{{$include /help/_includes/sensitive-data.md}}
