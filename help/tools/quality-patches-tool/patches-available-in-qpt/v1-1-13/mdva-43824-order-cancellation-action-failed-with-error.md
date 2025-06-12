---
title: 'MDVA-43824: Falha na ação de cancelamento do pedido com o erro "Você não cancelou o item"'
description: 'O patch MDVA-43824 resolve o problema em que a ação de cancelamento do pedido falhou com o erro: *Você não cancelou o item*. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43824. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.'
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824: Falha na ação de cancelamento do pedido com o erro &quot;Você não cancelou o item&quot;

O patch MDVA-43824 resolve o problema em que a ação de cancelamento do pedido falhou com o erro: *Você não cancelou o item*. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43824. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O pedido feito por um cliente conectado não pode ser cancelado. A ação de cancelamento do pedido falhou com o seguinte erro:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Etapas a serem reproduzidas</u>:

1. Crie uma regra de vendas (o tipo de cupom é &quot;Cupom específico&quot; ou &quot;Sem cupom&quot;).
1. Acesse a loja, faça logon como cliente e adicione um produto ao carrinho.
1. Vá para o carrinho e aplique a regra de preço do carrinho se a regra de preço do carrinho tiver um cupom como &quot;Cupom específico&quot;. A regra de preço do carrinho deve ser aplicada com sucesso.
1. Ir para checkout e fazer o pedido com qualquer forma de pagamento.
1. Acesse Administrador do Commerce > **Vendas** > **Pedidos**.
1. Abra o pedido feito na Etapa 4.
1. Clique no botão **Cancelar**.

<u>Resultados esperados</u>:

O pedido foi cancelado com êxito sem nenhum erro.

<u>Resultados reais</u>:

Falha na ação de cancelamento do pedido com o seguinte erro: *Você não cancelou o item.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
