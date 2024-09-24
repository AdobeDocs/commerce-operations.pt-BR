---
title: "ACSD-46520: status de pedido incorreto quando reembolsado usando créditos da loja"
description: Este artigo fornece uma solução para o problema em que os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja.
feature: Orders, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-46520: status de pedido incorreto quando reembolsado usando créditos de loja

O patch ACSD-46520 resolve o problema em que os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 está instalado. A ID do patch é ACSD-46520. Observe que o problema foi corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 e 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.5

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários obtêm um status de pedido incorreto quando reembolsados usando créditos da loja.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma conta de cliente na loja e faça logon.
1. Atribua créditos da loja ao cliente do Administrador. Os créditos da loja devem cobrir toda a ordem.
1. Fazer um pedido usando os créditos da loja.
1. Faturar a ordem.
1. Crie um aviso de crédito para reembolsar o valor total da ordem.
Marque a caixa de seleção **[!UICONTROL Refund to store credit]**.
1. Verifique o status do pedido.

<u>Resultados esperados</u>:

O status do pedido é *Fechado*.

<u>Resultados reais</u>:

O status do pedido é *Concluído*, que não é o status correto.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou [!DNL Magento Open Source] no local: [Ferramentas de Patches de Qualidade > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) no guia da Ferramenta de Patches de Qualidade.
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando o [!DNL Quality Patches Tool]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) em nossa base de dados de conhecimento de suporte.

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia Ferramenta de patches de qualidade.
