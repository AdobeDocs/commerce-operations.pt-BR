---
title: 'MDVA-37984: Merchandiser visual não está funcionando corretamente quando atualizações de preparo são aplicadas'
description: O patch MDVA-37984 resolve o problema em que a funcionalidade "Corresponder produto por regra" do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-37984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%
---
# MDVA-37984: Merchandiser visual não está funcionando corretamente quando atualizações de preparo são aplicadas

O patch MDVA-37984 resolve o problema em que a funcionalidade &quot;Corresponder produto por regra&quot; do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.9 está instalada. A ID do patch é MDVA-37984. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A funcionalidade &quot;Corresponder produto por regra&quot; do Visual Merchandiser não filtra produtos corretamente quando atualizações de preparo são aplicadas.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma atualização de agendamento para qualquer produto existente.
   * Defina valores diferentes para `entity_id` e `row_id`.
1. Crie um novo produto configurável e, em seguida, um produto simples (para que os novos produtos `entity_id` e `row_ids` também sejam diferentes).
   * Para facilitar a replicação do problema, defina um valor de quantidade diferenciável para o produto simples - por exemplo, 5000.
1. Ir para uma categoria > **Produtos na categoria** e habilitar **Corresponder produtos por regra**.
1. Agora selecione &quot;Quantidade&quot; como o atributo, &quot;Maior&quot; como o operador e &quot;4500&quot; como o valor.
1. Clique em **salvar**.

<u>Resultados esperados</u>:

O produto configurável recém-criado é listado.

<u>Resultados reais</u>:

O produto configurável recém-criado não está listado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
