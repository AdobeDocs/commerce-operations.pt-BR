---
title: 'ACSD-45781: O campo de pesquisa frontal da loja não é exibido no celular'
description: O patch MDVA-45781 resolve o problema em que o campo de pesquisa frontal da loja não é exibido em dispositivos móveis. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19 está instalada. A ID do patch é MDVA-45781. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
feature: Cache, Native Luma Frontend Development, Search
role: Admin
exl-id: f761461b-2dd0-45d2-b80d-57793f6f0924
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-45781: O campo de pesquisa frontal da loja não é exibido no celular

O patch MDVA-45781 resolve o problema em que o campo de pesquisa frontal da loja não é exibido em dispositivos móveis. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.19 está instalada. A ID do patch é MDVA-45781. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O campo de pesquisa frontal da loja não é exibido em dispositivos móveis

<u>Etapas a serem reproduzidas</u>:

1. Acesse Administrador do Commerce > **Lojas** > **Configuração** > **Catálogo** > **Pesquisa de Catálogo** e defina:
   * Habilitar recomendações de pesquisa para *Não*
   * Habilitar Sugestões de Pesquisa para *Não*
1. Clique no botão **Salvar configuração**.
1. Limpar cache.
1. Usando o tema Luma padrão, navegue com dispositivos móveis.
1. Clique no botão **Pesquisar**.

<u>Resultados esperados</u>:

Formulário de pesquisa de entrada é exibido.

<u>Resultados reais</u>:

Nada acontece.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
