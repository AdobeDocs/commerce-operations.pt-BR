---
title: 'ACSD-58131: a galeria de mídia antiga falha ao carregar imagens devido ao arquivo de imagem de 0 byte'
description: Aplique o patch ACSD-58131 para corrigir o problema do Adobe Commerce em que a galeria de mídia antiga falha ao renderizar imagens quando uma imagem de 0 byte está presente no diretório.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: a galeria de mídia antiga falha ao carregar imagens devido ao arquivo de imagem de 0 byte

O patch ACSD-58131 corrige o problema em que a galeria de mídia antiga falha ao renderizar imagens quando uma imagem de 0 byte está presente no diretório. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 está instalado. A ID do patch é ACSD-58131. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Quando uma imagem de 0 byte é colocada no diretório da galeria de mídia, a galeria de mídia antiga não renderiza imagens. O sistema atualizado agora ignora arquivos de 0 bytes inválidos, exibe imagens válidas conforme esperado e registra um aviso para cada arquivo inválido.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Defina **[!UICONTROL Enable Old Media Gallery]** como *Sim*.
1. Coloque algumas imagens no diretório `pub/media/wysiwyg`.
1. Crie uma imagem de 0 bytes no mesmo diretório usando `touch pub/media/wysiwyg/empty_image.png`.
1. Adicione uma imagem do diretório `wysiwyg` por meio do Page Builder em qualquer conteúdo (por exemplo, um Bloco CMS):
   1. Crie um novo bloco. Vá para **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** e clique em **[!UICONTROL Add New Block]**.
   1. Edite a seção de conteúdo usando o Page Builder.
   1. Em **[!UICONTROL Layout]**, arraste uma nova **[!UICONTROL Row]** para o estágio.
   1. Expanda **[!UICONTROL Media]** e arraste um espaço reservado **[!UICONTROL Image]** para a linha.
   1. Clique em **[!UICONTROL Select from Gallery]**.
   1. Selecione o diretório `wysiwyg` se ele não estiver selecionado por padrão.

<u>Resultados esperados</u>:

A galeria de mídia permanece funcional mesmo se uma imagem de 0 byte (ou qualquer outro arquivo) existir.

<u>Resultados reais</u>:

Falha da galeria de mídia ao carregar imagens do diretório `wysiwyg` devido a um erro crítico registrado em `var/log/system.log`:

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
