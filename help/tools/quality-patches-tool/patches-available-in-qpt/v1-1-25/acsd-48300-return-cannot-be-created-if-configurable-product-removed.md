---
title: "ACSD-48300: a devolução não pode ser criada se o produto configurável for removido"
description: Aplique o patch ACSD-48300 para corrigir o problema do Adobe Commerce em que o retorno não pode ser criado se o produto configurável for removido.
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-48300: a devolução não pode ser criada se o produto configurável for removido

O patch ACSD-48300 corrige o problema em que um retorno não pode ser criado se o produto configurável for removido. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 está instalado. A ID do patch é ACSD-48300. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A devolução não pode ser criada se o produto configurável for removido.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar RMA na loja em **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Crie um produto configurável.
1. Na loja, crie uma conta (e/ou faça logon).
1. Adicione um produto configurável ao carrinho como o primeiro item.
1. Adicione qualquer produto simples depois.
1. Coloque o pedido.
1. Enviar a ordem.
1. Agora, exclua somente o produto configurável (não exclua os produtos derivados).
1. Na vitrine, vá para **[!UICONTROL My Orders]** e veja o pedido.
1. Clique em **[!UICONTROL Return]**.

<u>Resultados esperados</u>:

O administrador pode retornar itens mesmo que o produto configurável seja excluído.

<u>Resultados reais</u>:

Ocorre um erro ao retornar itens.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
