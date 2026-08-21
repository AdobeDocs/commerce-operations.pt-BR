---
title: 'MDVA-38666: O usuário administrador não pode alterar as opções de produto configuráveis'
description: O patch MDVA-38666 resolve o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-38666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Products
role: Admin
exl-id: 8e72f6a4-b36f-4fe4-bc01-2254984dd512
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# MDVA-38666: O usuário administrador não pode alterar as opções de produto configuráveis

O patch MDVA-38666 resolve o problema em que o usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-38666. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.4-p2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode alterar as opções de produto configuráveis no carrinho do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Definir escopo da conta do cliente como Global.
1. Crie dois sites com lojas.
1. Crie dois produtos configuráveis e atribua-os a cada site.
1. Crie uma conta do cliente no front-end e faça logon.
1. Adicione um produto ao carrinho e faça uma finalização (isso é feito para tornar as IDs de cotação diferentes em cada site).
1. Adicione um produto ao carrinho e deixe-o.
1. Alterne para o segundo site e adicione o produto ao carrinho (o mesmo logon deve funcionar, pois o escopo da conta do cliente está definido como Global).
1. Abra o cliente no admin e navegue até a guia do carrinho.
1. Alterne o armazenamento do menu suspenso e tente alterar a configuração.

<u>Resultados esperados</u>:

O usuário recebe um pop-up com opções configuráveis.

<u>Resultados reais</u>:

Nenhum formulário pop-up é exibido. O usuário não pode alterar a configuração.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
