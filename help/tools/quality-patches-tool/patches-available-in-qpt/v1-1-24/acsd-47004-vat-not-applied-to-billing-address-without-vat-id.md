---
title: 'ACSD-47004: IVA não aplicado ao endereço de faturamento sem ID de IVA'
description: Aplique o patch ACSD-47004 para corrigir o problema do Adobe Commerce em que o IVA não é aplicado a um endereço de faturamento sem uma ID de IVA.
feature: Customer Service, Shipping/Delivery, Orders
role: Admin
exl-id: 72a64937-1c04-4fc2-bc61-fd2056e24419
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 1%

---

# ACSD-47004: IVA não aplicado ao endereço de faturamento sem ID de IVA

O patch ACSD-47004 corrige o problema em que o IVA não é aplicado a um endereço de faturamento sem uma ID de IVA. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 está instalado. A ID do patch é ACSD-47004. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O IVA não é aplicado a um endereço de faturamento sem uma ID de IVA.

<u>Etapas a serem reproduzidas</u>:

1. Abra o [!UICONTROL Commerce Admin] > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Create New Account Options]** e defina o **[!UICONTROL Enable Automatic Assignment to Customer Group]** como *[!UICONTROL Yes]*.
1. Defina grupos diferentes para validações de ID de IVA. Por exemplo:

   ![Validações de ID de IVA](/help/assets/tools/vat-id-validations.png)

1. Registre um novo cliente.
1. Adicione um novo endereço padrão sem IVA. Por exemplo:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

1. Verifique se o grupo do cliente permanece [!UICONTROL General].
1. Edite este endereço e adicione um número de IVA válido:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   VAT: DE329376919
   ```

1. Verifique se o grupo do cliente foi alterado para [!UICONTROL Retailer].
1. Edite o endereço e remova o número de IVA:

   ```
   123 N University Dr
   Edmond, 73034
   Germany
   T: 0900000000
   ```

<u>Resultados esperados</u>:

O grupo de clientes foi alterado automaticamente para o grupo [!UICONTROL General] padrão.

<u>Resultados reais</u>:

O grupo de clientes não é alterado automaticamente para o grupo [!UICONTROL General] padrão.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
