---
title: 'ACSD-65913: [!DNL OpenSearch] lança um argumento_exceção_ilegal para categorias com produtos com o mesmo preço'
description: Aplique o patch ACSD-65913 para corrigir o problema do Adobe Commerce em que [!DNL Opensearch]  está gerando um argumento_ilegal_exceção ("[do] parâmetro não pode ser negativo") nas categorias que contêm todos os produtos com o mesmo preço.
feature: Search
role: Admin, Developer
type: Troubleshooting
exl-id: 984db32e-1a0d-4e0a-a83b-7fe909226ed3
source-git-commit: e24b62305ef97c5fff13582b4bb68f622dffb6d3
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-65913: [!DNL OpenSearch] lança um `illegal_argument_exception` para categorias com produtos com o mesmo preço

O patch ACSD-65913 corrige o problema em que [!DNL OpenSearch] exibia um `illegal_argument_exception` para categorias com produtos com o mesmo preço. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-65913. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL OpenSearch] aciona um `illegal_argument_exception` (*[de] parâmetro não pode ser negativo*) ao carregar categorias em que todos os produtos compartilharam o mesmo preço.

<u>Etapas a serem reproduzidas</u>:

1. Instale a versão 2.19.1 do [!DNL OpenSearch] e defina-a como mecanismo de pesquisa padrão.
1. Configure o atributo de produto **[!UICONTROL Price]** para ficar visível na Navegação em Camadas:
   1. **[!UICONTROL Visible in Advanced Search]**: *Sim*
   1. **[!UICONTROL Comparable on Storefront]**: *Sim*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filtrável (com resultados)*
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]**. Defina **[!UICONTROL Price Navigation Step Calculation]** como *Automático (equalizar contagens de produtos)*.
1. Crie uma categoria com seis produtos com o mesmo preço:
   1. SKU: product_super_0-1-1-1, Preço: US$ 150
   1. SKU: product_super_0-1-1, Preço: US$ 48
   1. SKU: product_super_0-1, Preço: US$ 48
   1. SKU: product_super_0, Preço: US$ 48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Preço: US$ 48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1, Preço: US$ 48
1. Execute o seguinte comando:
   `bin/magento indexer:reindex`
1. Abra a página de categoria. Você verá um erro:
   O parâmetro *[from] não pode ser negativo, encontrado [-1]*

<u>Resultados esperados</u>:

[!DNL OpenSearch] não deve lançar um `illegal_argument_exception` quando todos os produtos em uma categoria têm o mesmo preço.

<u>Resultados reais</u>:

* [!DNL OpenSearch] lança um `illegal_argument_exception` com a mensagem:
  O parâmetro *[from] não pode ser negativo, encontrado [-1]*

* O arquivo `var/log/exception.log` contém:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
