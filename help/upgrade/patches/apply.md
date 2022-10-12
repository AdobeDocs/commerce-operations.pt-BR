---
title: Aplicar Correções
description: Saiba mais sobre os métodos para aplicar patches a um projeto do Adobe Commerce ou Magento Open Source.
source-git-commit: e2ddb30da8dd86236e1dcf33a3f911b67384a6d7
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# Aplicar patches

Você pode aplicar patches usando qualquer um dos seguintes métodos:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}
- [Linha de comando](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)

## Composer

>[!IMPORTANT]
>
>Para aplicar os sistemas oficiais de qualidade, utilize o [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;}. Sempre execute testes abrangentes antes de implantar qualquer patch personalizado.

Para aplicar um patch personalizado usando o Composer:

1. Abra o aplicativo de linha de comando e navegue até o diretório do projeto.
1. Adicione o `cweagans/composer-patches` para `composer.json` arquivo.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite o `composer.json` e adicione a seguinte seção para especificar:
   - **Módulo:** *\&quot;magento/module-payment\&quot;*
   - **Título:** *\&quot;MAGETWO-56934: A página de check-out congela ao solicitar com Authorize.net com cartão de crédito inválido\&quot;*
   - **Caminho para o patch:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Por exemplo:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Se um patch afeta vários módulos, você deve criar vários arquivos de patch direcionados a vários módulos.

1. Aplique o patch. Use o `-v` somente se desejar visualizar as informações de depuração.

   ```bash
   composer -v install
   ```

1. Atualize o `composer.lock` arquivo. O arquivo de bloqueio rastreia quais patches foram aplicados a cada pacote do Composer em um objeto.

   ```bash
   composer update --lock
   ```

## Linha de comando

Para aplicar patches a partir da linha de comando:

1. Faça upload do arquivo local no `<Magento_root>` no servidor usando FTP, SFTP, SSH ou seu método de transporte normal.
1. Faça logon no servidor como o [usuário administrador](../../configuration/cli/config-cli.md#prerequisites) e verifique se o arquivo está no diretório correto.
1. Na interface da linha de comando, execute os seguintes comandos de acordo com a extensão de patch:

   ```bash
   patch < patch_file_name.patch
   ```

   O comando supõe que o arquivo a ser corrigido está localizado em relação ao arquivo de patch.

   >[!NOTE]
   >
   >Se a linha de comando mostrar: `File to patch:`, significa que não pode localizar o arquivo pretendido, mesmo que o caminho pareça estar correto. Na caixa exibida no terminal da linha de comando, a primeira linha mostra o arquivo a ser corrigido. Copie o caminho do arquivo e cole-o no `File to patch:` prompt e pressione `Enter` e o sistema transdérmico deve ser concluído.

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > Ferramentas > **Gerenciamento de cache**.

   Como alternativa, o patch pode ser aplicado localmente com o mesmo comando e, em seguida, confirmado e enviado normalmente.
