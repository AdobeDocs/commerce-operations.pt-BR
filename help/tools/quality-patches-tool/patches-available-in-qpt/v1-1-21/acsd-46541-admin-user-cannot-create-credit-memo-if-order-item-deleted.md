---
title: 'ACSD-46541: Um usuário administrador não pode criar um aviso de crédito se um item de pedido for excluído'
description: Aplique o patch ACSD-46541 para corrigir o problema do Adobe Commerce em que, uma vez excluído o produto, não é possível criar um memorando de crédito no Administrador do Adobe Commerce.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541: Um usuário administrador não pode criar um aviso de crédito se um item de pedido for excluído

O patch ACSD-46541 corrige o problema em que um usuário administrador não pode criar um aviso de crédito se um item de pedido for excluído. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.21 está instalado. A ID do patch é ACSD-46541. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Depois que um produto é excluído, não é possível criar um aviso de crédito no Administrador do Commerce.

<u>Etapas a serem reproduzidas</u>:

1. Faça logon no Administrador do Commerce.
1. Criar um pedido.
1. Faturar a ordem.
1. Excluir o produto do pedido.
1. Clique no link **[!UICONTROL Credit Memo]** na página de edição do pedido.
1. Clique em **[!UICONTROL Refund Offline]** para criar um memorando de crédito.

<u>Resultados esperados</u>:

Um memorando de crédito foi criado com sucesso.

<u>Resultados reais</u>:

Os _seguintes produtos com SKUs solicitadas não foram encontrados: SKU001_ erros são exibidos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
