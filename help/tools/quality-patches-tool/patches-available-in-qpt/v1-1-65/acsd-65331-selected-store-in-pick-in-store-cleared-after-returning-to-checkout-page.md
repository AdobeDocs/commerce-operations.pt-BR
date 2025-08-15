---
title: 'ACSD-65331: O armazenamento selecionado em [!UICONTROL Pick in Store] foi limpo após retornar ao check-out'
description: Aplique o patch ACSD-65331 para corrigir o problema do Adobe Commerce em que o armazenamento selecionado na opção [!UICONTROL Pick In Store] é limpo quando os usuários retornam repetidamente à página de check-out.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331: O armazenamento selecionado em **[!UICONTROL Pick in Store]** foi limpo após retornar ao check-out

O patch ACSD-65331 corrige o problema em que o armazenamento selecionado na opção **[!UICONTROL Pick In Store]** é limpo quando os usuários retornam repetidamente à página de check-out. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 está instalado. A ID do patch é ACSD-65331. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O armazenamento selecionado na opção **[!UICONTROL Pick In Store]** é limpo quando os usuários retornam repetidamente à página de check-out.

<u>Etapas a serem reproduzidas</u>:

1. Habilite **[!UICONTROL In-Store Delivery]** navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Configure uma chave de API [!DNL Google] válida para [!UICONTROL Google Distance Provider] navegando até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** para adicionar uma nova fonte com os seguintes detalhes:

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sim*
   * **[!UICONTROL Country]**: *Estados Unidos*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Fluxo de Carol*
   * **[!UICONTROL Street]**: *565 E. Avenida Fullerton.*
   * **[!UICONTROL Postcode]**: *60188*

1. Vá para **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** para criar um novo estoque.

   Atribua a origem recém-criada e o site principal a esse estoque.
1. Edite qualquer produto e:

   1. Atribua-a à origem recém-criada.
   1. Defina o status como *[!UICONTROL In Stock]* e a quantidade como maior que 0.

1. Execute seus reindexadores.
1. Na loja, crie um novo cliente e defina um endereço da Califórnia como o endereço de entrega e cobrança padrão.
1. Adicione um endereço Illinois adicional ao mesmo cliente (não padrão).
1. Adicione o produto configurado ao carrinho e prossiga para **[!UICONTROL Checkout]**.
1. Selecione o endereço de Illinois, escolha **[!UICONTROL Pick In Store]** como método de envio e clique em **[!UICONTROL Next]**.
1. Aguarde o carregamento da origem e clique em **[!UICONTROL Next]**.
1. Navegue de volta para a página inicial.
1. Visite novamente a página **[!UICONTROL Checkout]**.

<u>Resultados esperados</u>:

O armazenamento selecionado deve permanecer disponível em **[!UICONTROL Pick In Store]**.

<u>Resultados reais</u>:

A etapa de envio começa a carregar e redireciona para **[!UICONTROL Pick In Store]**, mas nenhum armazenamento está visível.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
