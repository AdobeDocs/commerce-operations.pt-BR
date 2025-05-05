---
title: 'ACSD-64137: a pesquisa de locais de coleta por código postal não funciona corretamente na localização holandesa'
description: Aplique o patch ACSD-64137 para corrigir o problema em que a pesquisa de locais de coleta por código postal não funciona corretamente para a localização holandesa.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 4947133daaffb919aeba986c8a6b88ecb2e1b943
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# ACSD-64137: Pesquisar locais de coleta por código postal não funciona corretamente para localização holandesa

O patch ACSD-64137 corrige o problema em que a pesquisa de locais de coleta por código postal não funciona corretamente para a localização holandesa. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 está instalado. A ID do patch é ACSD-64137. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A pesquisa por código postal da Holanda não mostra resultados na página de check-out de front-end. No entanto, funciona por cidade e exibe o endereço correspondente sem pesquisa.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma instância limpa com módulos de inventário.
1. Criar um estoque personalizado.
1. Crie duas fontes com endereços dos Países Baixos e atribua-as ao estoque (códigos postais 7311ER e 7311AE).
1. Crie um produto simples e adicione inventário.
1. Habilite **[!UICONTROL In-Store Delivery]** navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. Defina **[!UICONTROL Provider]** como *Cálculo offline*.
1. Execute o seguinte comando para importar nomes geográficos para o país NL.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Adicione o produto ao carrinho e vá para a etapa de envio.
1. Selecione **[!UICONTROL Pick In Store]**. Em seguida, clique em **[!UICONTROL Select Other]** para selecionar outros armazenamentos.
1. Digite *7311* ou *7311AE* no formulário de pesquisa **[!UICONTROL Select Store]**.


**Resultados esperados**:

* Os armazenamentos correspondentes devem ser preenchidos.

**Resultados reais**:

* Nenhum resultado encontrado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
