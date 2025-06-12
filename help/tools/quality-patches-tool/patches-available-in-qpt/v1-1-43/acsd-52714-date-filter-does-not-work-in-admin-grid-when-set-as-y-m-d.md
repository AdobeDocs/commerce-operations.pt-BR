---
title: 'ACSD-52714: o filtro de data não funciona na grade de administração quando definido como y-m-d'
description: Aplique o patch ACSD-52714 para corrigir o problema do Adobe Commerce em que o filtro de data não funciona na grade de administração quando o formato de data é definido como y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714: o filtro de data não funciona na grade de administração quando definido como y-m-d

O patch ACSD-52714 corrige o problema em que o filtro de data não funciona na grade do administrador quando o formato de data é definido como y-m-d. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-52714. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O filtro de datas não funciona na grade de administração quando o formato de data é definido como y-m-d.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce limpo.
1. Editar
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
arquivo e adicionar
   `<dateFormat>Y-MM-dd</dateFormat>`
para
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
na tag
   `<dataType>date</dataType>`

1. Liberar o cache `bin/magento c:f`.
1. Faça logon como Administrador e crie um novo cliente em **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * de: data atual menos 1 dia
   * para: data atual

1. Clique em **[!UICONTROL Apply Filters]**.

<u>Resultados esperados</u>:

O filtro de data da grade funciona corretamente, independentemente do conjunto de localidades.

<u>Resultados reais</u>:

A seguinte mensagem é exibida: *Não foi possível localizar nenhum registro*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
