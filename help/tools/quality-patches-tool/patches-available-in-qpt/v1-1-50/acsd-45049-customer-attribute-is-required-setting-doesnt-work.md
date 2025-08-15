---
title: 'ACSD-45049: a configuração de atributo "É necessário" do cliente não funciona de acordo com o escopo do site no Administrador'
description: Aplique o patch ACSD-45049 para corrigir o problema do Adobe Commerce em que o atributo do cliente "[!UICONTROL Is required]" não é substituído corretamente de acordo com o escopo do site em Administração.
feature: Attributes, Customers
role: Admin, Developer
exl-id: 368af877-a3ec-431f-8f41-5d51354be571
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049: A configuração de atributo do cliente *[!UICONTROL Is required]* não funciona de acordo com o escopo do site no Administrador

O patch ACSD-45049 corrige o problema em que a configuração do atributo *[!UICONTROL Is required]* do cliente não funciona corretamente de acordo com o escopo do site em Administração. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50 está instalado. A ID do patch é ACSD-45049. Observe que o problema foi corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p7 e 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A configuração de atributo do cliente *[!UICONTROL Is required]* não funciona corretamente de acordo com o escopo do site em Administração.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois sites.
1. Abrir **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]**.
1. Crie um novo atributo, defina **[!UICONTROL Is value required]** = *Não*.
1. Alterne para o site padrão e altere **[!UICONTROL Is value required]** = *Sim*. O outro site tem o valor padrão.
1. Crie um novo cliente a partir do Administrador para o site não padrão.

<u>Resultados esperados</u>:

O atributo não é necessário para o site não padrão.

<u>Resultados reais</u>:

* O atributo é necessário para o site não padrão ao criar um cliente no Admin.
* O atributo não é necessário para o site não padrão ao registrar um cliente na loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
