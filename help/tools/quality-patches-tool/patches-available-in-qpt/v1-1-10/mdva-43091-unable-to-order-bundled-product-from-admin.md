---
title: "MDVA-43091: não é possível solicitar produto fornecido do administrador"
description: O patch MDVA-43091 resolve o problema em que os usuários não podem solicitar o produto agrupado do administrador do Commerce. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-43091. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# MDVA-43091: Não é possível solicitar produto fornecido do Administrador

O patch MDVA-43091 resolve o problema em que os usuários não podem solicitar o produto agrupado do administrador do Commerce. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 está instalada. A ID do patch é MDVA-43091. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.4.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao tentar solicitar o produto agrupado do Administrador, ocorre o seguinte erro: *Você não pode usar a quantidade decimal para este produto.*

<u>Etapas a serem reproduzidas</u>:

1. Instale um Adobe Commerce limpo.
1. Crie dois produtos simples.
1. Crie um produto incluído com duas opções.
1. Crie uma conta de cliente no front-end.
1. Vá para **Admin** > **Vendas** > **Pedidos** > **Criar Novo Pedido**.
   * Selecione a conta de cliente criada agora mesmo.
   * Tente adicionar o produto incluído ao carrinho.

<u>Resultados esperados</u>:

O usuário administrador pode adicionar o produto com uma quantidade ao carrinho.

<u>Resultados reais</u>:

O usuário administrador recebe o seguinte erro: *Você não pode usar a quantidade decimal para este produto.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
