---
title: Aplicar patches
description: Saiba mais sobre os métodos para aplicar patches a um projeto do Adobe Commerce.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Aplicar patches

Você pode aplicar patches usando qualquer um dos métodos a seguir:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR){target="_blank"}
- [Linha de comando](../patches/apply.md#command-line)
- [Compositor](../patches/apply.md#composer)


>[!TIP]
>
>Consulte [práticas recomendadas](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) para obter informações sobre patches centralizados para o Adobe Commerce em escala corporativa.

## Compositor

{{custom-patches-disclaimer}}

Para aplicar um patch personalizado usando o Composer:

1. Abra o aplicativo de linha de comando e navegue até o diretório do projeto.
1. Adicionar o plug-in `cweagans/composer-patches` ao arquivo `composer.json`.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Edite o arquivo `composer.json` e adicione a seguinte seção para especificar:
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

1. Aplique o patch. Use a opção `-v` somente se desejar ver informações de depuração.

   ```bash
   composer -v install
   ```

1. Atualize o arquivo `composer.lock`. O arquivo de bloqueio rastreia quais patches foram aplicados a cada pacote do Composer em um objeto.

   ```bash
   composer update --lock
   ```

## Linha de comando

Para aplicar patches a partir da linha de comando:

1. Carregue o arquivo local no diretório `<Magento_root>` no servidor usando FTP, SFTP, SSH ou seu método de transporte normal.
1. Faça logon no servidor como o [usuário administrador](../../configuration/cli/config-cli.md#prerequisites) e verifique se o arquivo está no diretório correto.
1. Na interface de linha de comando, execute os seguintes comandos de acordo com a extensão de patch:

   ```bash
   patch < patch_file_name.patch
   ```

   O comando presume que o arquivo a ser corrigido está localizado em relação ao arquivo de correção.

   >[!NOTE]
   >
   >Se a linha de comando mostrar: `File to patch:`, significa que não é possível localizar o arquivo pretendido, mesmo que o caminho pareça correto. Na caixa exibida no terminal de linha de comando, a primeira linha mostra o arquivo a ser corrigido. Copie o caminho do arquivo e cole-o no prompt `File to patch:` e pressione `Enter` para que o patch seja concluído.

1. Para que as alterações sejam refletidas, atualize o cache no Administrador em **Sistema** > Ferramentas > **Gerenciamento de Cache**.

   Como alternativa, o patch pode ser aplicado localmente com o mesmo comando, depois confirmado e enviado normalmente.
