---
title: Aplicar patches
description: Saiba mais sobre os métodos para aplicar patches a um projeto Adobe Commerce ou Magento Open Source.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Aplicar patches

Você pode aplicar patches usando qualquer um dos métodos a seguir:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Linha de comando](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)

## Compositor

>[!IMPORTANT]
>
>Para aplicar patches de qualidade oficiais, use o [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Sempre realize testes abrangentes antes de implantar qualquer patch personalizado.

Para aplicar um patch personalizado usando o Composer:

1. Abra o aplicativo de linha de comando e navegue até o diretório do projeto.
1. Adicione o `cweagans/composer-patches` plug-in para a `composer.json` arquivo.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite o `composer.json` e adicione a seguinte seção para especificar:
   - **Módulo:** *\&quot;magento/module-payment\&quot;*
   - **Título:** *\&quot;MAGETWO-56934: a página de check-out congela ao fazer pedidos com Authorize.net com cartão de crédito inválido\&quot;*
   - **Caminho para correção:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

   Se um patch afetar vários módulos, você deverá criar vários arquivos de patch direcionados a vários módulos.

1. Aplique o patch. Use o `-v` opção somente se desejar ver informações de depuração.

   ```bash
   composer -v install
   ```

1. Atualize o `composer.lock` arquivo. O arquivo de bloqueio rastreia quais patches foram aplicados a cada pacote do Composer em um objeto.

   ```bash
   composer update --lock
   ```

## Linha de comando

Para aplicar patches a partir da linha de comando:

1. Faça upload do arquivo local no `<Magento_root>` no servidor usando FTP, SFTP, SSH ou o método de transporte normal.
1. Efetue logon no servidor como o [usuário administrador](../../configuration/cli/config-cli.md#prerequisites) e verifique se o arquivo está no diretório correto.
1. Na interface de linha de comando, execute os seguintes comandos de acordo com a extensão de patch:

   ```bash
   patch < patch_file_name.patch
   ```

   O comando presume que o arquivo a ser corrigido está localizado em relação ao arquivo de correção.

   >[!NOTE]
   >
   >Se a linha de comando mostrar: `File to patch:`, significa que não é possível localizar o arquivo pretendido, mesmo que o caminho pareça correto. Na caixa exibida no terminal de linha de comando, a primeira linha mostra o arquivo a ser corrigido. Copie o caminho do arquivo e cole-o na `File to patch:` e pressione `Enter` e o patch deve ser concluído.

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > Ferramentas > **Gerenciamento de cache**.

   Como alternativa, o patch pode ser aplicado localmente com o mesmo comando, depois confirmado e enviado normalmente.
