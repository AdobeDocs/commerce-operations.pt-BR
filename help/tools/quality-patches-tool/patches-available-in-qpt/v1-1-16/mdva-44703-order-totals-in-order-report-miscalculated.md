---
title: "MDVA-44703: os totais de pedidos no relatório Pedidos são calculados incorretamente"
description: O patch MDVA-44703 corrige o problema em que os totais de pedidos no relatório Pedidos são calculados incorretamente para o usuário administrador restrito. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44703. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703: os totais de pedidos no relatório Pedidos são calculados incorretamente

O patch MDVA-44703 corrige o problema em que os totais de pedidos no relatório Pedidos são calculados incorretamente para o usuário administrador restrito. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 está instalada. A ID do patch é MDVA-44703. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.6.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os totais de pedidos no relatório Pedidos são calculados incorretamente para o usuário administrador restrito.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site adicional com duas lojas.
1. Crie um usuário administrador restrito com acesso somente ao novo site.
1. Faça logon como o usuário administrador restrito.
1. Crie duas ordens com totais diferentes, uma para cada nova loja.
1. Criar faturas para as ordens.
1. Vá para **Relatórios** > **Vendas** e abra o **Relatório de pedidos**.
1. Atualizar estatísticas.
1. Ver o relatório de cada loja.

<u>Resultados esperados</u>:

Os totais de vendas correspondem ao valor da ordem de cada loja.

<u>Resultados reais</u>:

O total de vendas agregado para todo o site é exibido para cada loja.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
