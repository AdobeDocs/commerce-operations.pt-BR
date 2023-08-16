---
title: Configuração do sistema de produção
description: Saiba como configurar um sistema de produção para o aplicativo Commerce.
exl-id: e678e97e-d9f2-4f24-bb6b-1994a2a1167c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Configuração do sistema de produção

Você pode ter um sistema de produção. Todos os itens a seguir devem ser verdadeiros:

- Todo o código do Commerce está no controle de origem no mesmo repositório dos sistemas de desenvolvimento e criação
- Verifique se todos os itens a seguir estão _incluído_ no controle de origem:

   - `app/etc/config.php`
   - `generated` diretório (e subdiretórios)
   - `pub/media` diretório
   - `pub/media/wysiwyg` diretório (e subdiretórios)
   - `pub/static` diretório (e subdiretórios)

- O Commerce 2.2 ou posterior deve estar instalado e configurado para [modo de produção](../bootstrap/application-modes.md#production-mode)
- Ele tem a propriedade e as permissões do sistema de arquivos definidas conforme discutido em [Pré-requisito para seus sistemas de desenvolvimento, compilação e produção](../deployment/prerequisites.md).

## Configurar uma máquina de produção

Para configurar uma máquina de produção:

1. Depois de instalar o Commerce ou obtê-lo do controle do código-fonte, faça logon no servidor de produção como proprietário do sistema de arquivos ou alterne para ele.
1. Criar `~/.ssh/.composer/auth.json` caso ainda não o tenha feito.

   Crie o diretório:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Criar `auth.json` nesse diretório.

   `auth.json` deve conter seu [chaves de autenticação](../../installation/prerequisites/authentication-keys.md).

   A seguir, há uma amostra:

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

1. Salvar as alterações em `auth.json`.
1. Copiar `<Commerce root dir>/app/etc/env.php` do sistema de desenvolvimento para o sistema de produção.
1. Abertura `env.php` em um editor de texto e altere quaisquer valores necessários (por exemplo, informações de conexão de banco de dados).
1. Execute o [`magento config:set`](../cli/set-configuration-values.md) ou [`magento config:set-sensitive`](../cli/set-configuration-values.md) comando para definir os valores de quaisquer valores de configuração sensíveis ou específicos do sistema, respectivamente.

   A seção a seguir mostra um exemplo.

## Defina os valores de configuração no seu sistema de produção

Esta seção discute como definir valores confidenciais no sistema de produção usando o `magento config:sensitive:set` comando.

Para definir valores confidenciais:

1. Encontre um valor para definir usando o [referência de valor sensível](../reference/config-reference-sens.md).
1. Anote o caminho de configuração para a configuração.
1. Faça logon no sistema de produção como proprietário do sistema de arquivos ou alterne para ele.
1. Altere para o diretório de instalação do Commerce.
1. Digite o seguinte comando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Por exemplo, para definir o valor da chave de API do YouTube como `1234`, insira

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Também é possível definir um ou mais valores interativamente da seguinte maneira:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Quando solicitado, insira um valor para cada configuração sensível ou pressione Enter para ignorar um valor e passar para o próximo.

1. Para verificar se o valor foi definido, faça logon no Admin.
1. Localize a configuração em Admin.

   Por exemplo, a configuração da chave de API do YouTube está localizada em **Lojas** > Configurações > **Configuração** > **Catálogo** > **Catálogo** > **Vídeo do produto**.

   A configuração é exibida no Admin e não pode ser editada. A figura a seguir mostra um exemplo.

   ![Configuração sensível no Admin](../../assets/configuration/sensitive-set.png)
