---
title: 'ACSD-63326: corrija o problema de redirecionamento do administrador após colocar um pedido do back-end'
description: Aplique o patch ACSD-63326 para corrigir o problema do Adobe Commerce em que o administrador é redirecionado para uma página corrompida após fazer um pedido no back-end.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: corrija o problema de redirecionamento do administrador após colocar um pedido do back-end

O patch ACSD-63326 corrige o problema em que o administrador é redirecionado para uma página interrompida após fazer um pedido no back-end. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-63326. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os administradores são redirecionados para uma página com um layout corrompido depois de fazer um pedido para um cliente no back-end.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até a seção **[!UICONTROL Customers]** no painel Administrador.
1. Selecione qualquer cliente e clique em **[!UICONTROL Edit]**.
1. Na página de detalhes do cliente, clique em **[!UICONTROL Create Order]** no menu superior.
1. Selecione a loja [!UICONTROL FR French] e adicione qualquer produto disponível ao pedido.
1. Preencha os detalhes necessários no check-out e clique em **[!UICONTROL Get shipping methods and rates]**.
1. Clique em **[Enviar Pedido]** para fazer o pedido.

<u>Resultados esperados</u>:

O administrador é redirecionado para a página de confirmação do pedido ou de agradecimento com o layout correto.

<u>Resultados reais</u>:

O administrador é redirecionado para uma página com um layout corrompido. O layout é corrigido somente após a atualização da página.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
