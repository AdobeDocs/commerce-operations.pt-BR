---
title: 'ACSD-67264: layouts de pacote e de página de produto baixáveis inconsistentes entre dispositivos'
description: Aplique o patch ACSD-67264 para corrigir o pacote do Adobe Commerce e as páginas baixáveis enfrentaram problemas de layout devido a uma reorganização do bloco de mídia de informações do produto.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: layouts de pacote e de página de produto baixáveis inconsistentes entre dispositivos

O patch ACSD-67264 corrige o problema em que os layouts de pacote e de página de produto baixáveis são inconsistentes entre os dispositivos. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-67264. Observe que esse problema foi corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Problemas de layout no pacote e nas páginas de produto baixáveis devido a uma reorganização do bloco de mídia de informações do produto.

<u>Etapas a serem reproduzidas</u>:

1. Instale os dados de amostra.
1. Abra a página de produto do pacote e verifique o layout no desktop.
1. Adicione a página de produto do pacote à lista de desejos, navegue até a lista de desejos, clique no ícone de edição e verifique o layout.
1. Repita as etapas 2 e 3 para um produto baixável.

<u>Resultados esperados</u>:

O PDP do produto do pacote é renderizado sem problemas.

<u>Resultados reais</u>:

A PDP do produto do pacote é renderizada com espaços aleatórios.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas
