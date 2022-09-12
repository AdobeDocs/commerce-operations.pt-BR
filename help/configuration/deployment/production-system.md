---
title: Configuração do sistema de produção
description: Saiba como configurar um sistema de produção para o aplicativo Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Configuração do sistema de produção

Você pode ter um sistema de produção. Todos os itens a seguir devem ser verdadeiros:

- Todo o código do Commerce está no controle de origem no mesmo repositório que os sistemas de desenvolvimento e criação
- Certifique-se de que todos os itens a seguir sejam _included_ no controlo-fonte:

   - `app/etc/config.php`
   - `generated` diretório (e subdiretórios)
   - `pub/media` diretory
   - `pub/media/wysiwyg` diretório (e subdiretórios)
   - `pub/static` diretório (e subdiretórios)

- O Commerce 2.2 ou posterior deve ser instalado e definido para [modo de produção](../bootstrap/application-modes.md#production-mode)
- Ele tem a propriedade do sistema de arquivos e as permissões definidas como discutido em [Pré-requisito para seus sistemas de desenvolvimento, criação e produção](../deployment/prerequisites.md).

## Configurar uma máquina de produção

Para configurar uma máquina de produção:

1. Depois de instalar o Commerce ou retirá-lo do controle de origem, faça logon no servidor de produção como, ou alterne para, o [proprietário do sistema de arquivos](https://glossary.magento.com/magento-file-system-owner).
1. Criar `~/.ssh/.composer/auth.json` se ainda não o fez.

   Crie o diretório:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Criar `auth.json` nesse diretório.

   `auth.json` deve conter a [chaves de autenticação](../../installation/prerequisites/authentication-keys.md).

   Uma amostra:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Salve as alterações em `auth.json`.
1. Copiar `<Commerce root dir>/app/etc/env.php` do sistema de desenvolvimento ao sistema de produção.
1. Abrir `env.php` em um editor de texto e altere quaisquer valores necessários (por exemplo, informações de conexão de banco de dados).
1. Execute o [`magento config:set`](../cli/set-configuration-values.md) ou [`magento config:set-sensitive`](../cli/set-configuration-values.md) para definir os valores de qualquer valor de configuração sensível ou específico do sistema, respectivamente.

   A seção a seguir mostra um exemplo.

## Definir valores de configuração no sistema de produção

Esta seção discute como definir valores confidenciais em seu sistema de produção usando o `magento config:sensitive:set` comando.

Para definir valores confidenciais:

1. Encontre um valor a ser definido usando a variável [referência de valor sensível](../reference/config-reference-sens.md).
1. Observe o caminho de configuração da configuração.
1. Faça logon no sistema de produção como ou alterne para o proprietário do sistema de arquivos.
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Por exemplo, para definir o valor da chave de API do YouTube como `1234`, insira

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Você também pode definir um ou mais valores interativamente como segue:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Quando solicitado, insira um valor para cada configuração sensível ou pressione Enter para ignorar um valor e ir para o próximo.

1. Para verificar se o valor foi definido, faça logon no Admin.
1. Localize a configuração em Admin.

   Por exemplo, a configuração da chave de API do YouTube está localizada em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo** > **Vídeo do produto**.

   A configuração é exibida em Admin e não pode ser editada. A figura a seguir mostra um exemplo.

   ![Configuração sensível no Administrador](../../assets/configuration/sensitive-set.png)
