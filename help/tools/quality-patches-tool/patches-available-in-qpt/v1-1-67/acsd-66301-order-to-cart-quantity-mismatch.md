---
title: 'ACSD-66301: mover produtos de um pedido para o carrinho no Commerce Admin resulta em uma incompatibilidade de quantidade'
description: Aplique o patch ACSD-66301 para corrigir o problema do Adobe Commerce em que, ao criar um pedido no painel de Administração, os produtos no carrinho do cliente não são removidos após serem adicionados ao pedido.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
exl-id: 61e0e491-b2dc-4ae0-807e-2ae80d17f9c2
source-git-commit: 1e56c38713344b117ca3882861ced35e602b3239
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-66301: mover os produtos de um pedido de volta para o carrinho no Commerce Admin resulta em incompatibilidade de quantidade

O patch ACSD-66301 corrige o problema em que mover produtos de um pedido de volta para o carrinho no Admin resulta em incompatibilidade de quantidade. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 está instalado. A ID do patch é ACSD-66301. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p10, 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Mover os produtos de um pedido de volta para o carrinho no Commerce Admin resulta em incompatibilidade de quantidade.

<u>Etapas a serem reproduzidas</u>:

1. Crie um usuário por meio da loja.
2. Adicionar um produto ao carrinho com quantidade = *5*.
3. Vá para o painel Admin e abra a conta de usuário em que o produto foi adicionado.
4. Clique em **[!UICONTROL Create Order]**.
5. No painel esquerdo, é possível exibir as atividades do cliente, incluindo o produto e a quantidade adicionada.
6. Adicione o produto ao pedido.
7. Atualize a quantidade = *4* na seção principal da ordem.
8. Clique no botão **[!UICONTROL Update Items and Quantities]**.
9. Transfira os itens selecionados do pedido de volta para o carrinho de compras do cliente.

<u>Resultados esperados</u>:

Produto adicionado ao carrinho com a nova quantidade = *4*.

<u>Resultados reais</u>:

Produto adicionado ao carrinho com a quantidade antiga = *5*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
