---
title: 'ACSD-55305: Congelamento de pop-ups durante a edição de usuários da empresa em [!UICONTROL My Account]'
description: Aplique a correção ACSD-55305 para corrigir o problema do Adobe Commerce em que o pop-up [!UICONTROL Edit Company User] no &gt; [!UICONTROL My Account] da página congela com um carregador na tela.[!UICONTROL Company Structure]
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305: Congelamento de pop-ups durante a edição de usuários da empresa em [!UICONTROL My Account]

O patch ACSD-55305 corrige o problema em que o pop-up [!UICONTROL Edit Company User] da página [!UICONTROL My Account]> [!UICONTROL Company Structure] congela com um carregador na tela. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 está instalado. A ID do patch é ACSD-55305. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erro ao tentar usar o pop-up *[!UICONTROL Edit Company User]* na página *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]*, pois ele congela com um carregador exibido na tela.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma empresa B2B.
1. Crie um atributo de seleção múltipla para clientes.
1. Atribua um valor ao atributo recém-criado para o administrador da empresa.
1. Faça logon como Administrador da empresa.
1. Vá para [!UICONTROL account dashboard] e navegue até **[!UICONTROL Company Structure]**.
1. Selecione o usuário.
1. Clique em **[!UICONTROL Edit Selected]**.

<u>Resultados esperados</u>:

O pop-up do formulário é exibido com precisão, fornecendo a opção para editar as informações da empresa.

<u>Resultados reais</u>:

O pop-up do formulário é exibido sem qualquer possibilidade de edição.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
