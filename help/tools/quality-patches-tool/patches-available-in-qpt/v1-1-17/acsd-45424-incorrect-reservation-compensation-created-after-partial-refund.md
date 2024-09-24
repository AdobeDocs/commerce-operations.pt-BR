---
title: "ACSD-45424: compensação de reserva incorreta criada após reembolso parcial"
description: O patch ACSD-45424 corrige o problema em que uma compensação de reserva incorreta é criada após um reembolso parcial. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45424. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Compensação de reserva incorreta criada após reembolso parcial

O patch ACSD-45424 corrige o problema em que uma compensação de reserva incorreta é criada após um reembolso parcial. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 está instalada. A ID do patch é ACSD-45424. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A compensação de reserva incorreta é criada após um reembolso parcial.

<u>Etapas a serem reproduzidas</u>:

1. Habilitar método de envio de entrega na loja.
1. Crie três origens de inventário e certifique-se de que o local de retirada esteja ativo em cada uma (origem1, origem2, origem3).
1. Crie um novo estoque e atribua as três fontes a ele.
   * Esse estoque deve ser atribuído ao site principal.
1. Crie um produto simples, P3, e atribua todas as fontes a ele.
1. Adicione as seguintes quantidades para as origens do produto simples e ative backorders:
   * Origem padrão - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Adicione o produto simples ao carrinho do front-end e prossiga para o formulário de envio.
1. Selecione &quot;source1&quot; como o local de entrega.
1. Conclua a ordem e execute a seguinte consulta no banco de dados:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Você obterá o registro de pedido feito na tabela `inventory_reservation`. A quantidade é 10, o que é correto.
1. Faturar esta ordem no back-end.
1. Agora crie um memorando de crédito para apenas um produto. NÃO marque a caixa de seleção *Retornar ao Estoque*.
1. Execute a mesma query da Etapa 8.

<u>Resultados esperados</u>:

Se você não tiver selecionado *Retornar ao Estoque* durante a criação do memorando de crédito, a tabela `inventory_reservation` não terá um registro correspondente ao memorando de crédito.

<u>Resultados reais</u>:

Mesmo que você não tenha selecionado o *Retornar ao Estoque* durante a criação do memorando de crédito, ele adiciona um registro à tabela `inventory_reservation` com o tipo de evento `creditmemo_created`. Além disso, o registro de memorando de crédito adicionado à tabela `inventory_reservation` tem uma quantidade de 10, mesmo que você tenha criado o memorando de crédito para apenas uma quantidade.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
