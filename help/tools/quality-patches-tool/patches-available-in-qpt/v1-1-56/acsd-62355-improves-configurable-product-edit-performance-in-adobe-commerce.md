---
title: 'ACSD-62355: melhora o desempenho de edição do produto configurável no Adobe Commerce'
description: Aplique o patch ACSD-62355 para corrigir o problema do Adobe Commerce em que a página de edição do produto configurável apresenta carregamento lento quando o produto se baseia em vários atributos com muitos valores.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: e8694744c8a2411a8e966148860f43fb56b48772
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: melhora o desempenho de edição do produto configurável no Adobe Commerce

O patch ACSD-62355 corrige o problema de tempos lentos de carregamento e alto consumo de memória na página de edição do produto configurável quando o produto tem muitos atributos com vários valores. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62355. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página de edição do produto configurável leva muito tempo para ser carregada quando o produto configurável se baseia em vários atributos com muitos valores, causando atrasos e possíveis problemas de tempo limite ou de memória.

<u>Etapas a serem reproduzidas</u>:

1. Crie 9 novos atributos no conjunto de atributos padrão, cada um é [!UICONTROL Filterable] e tem [!UICONTROL Scope]: [!UICONTROL Global].
   * Atributo 1: 50 opções
   * Atributo 2: 20 opções
   * Atributo 3: 10 opções
   * Atributo 4: 5 opções
   * Atributo 5: 5 opções
   * Opções do Atributo 6: 5
   * Atributo 7: 5 opções
   * Atributo 8: 3 opções
   * Opções do Atributo 9: 2

1. Crie 9 produtos simples com combinações de opções dos atributos recém-criados.
   * Produto 1: Primeira opção de cada atributo
   * Produto 2: Segunda opção de cada atributo
   * Produto 3: Terceira opção de cada atributo
   * Produto 4: Quarta opção de cada atributo
   * Se um atributo tiver menos opções do que o número de produtos, atribua os produtos restantes às opções aleatórias dentro desse atributo.

1. Crie um produto configurável que use os atributos recém-criados:
   * Adicione um produto secundário com a seguinte configuração:
      * Use a última opção do Atributo 1 e a primeira opção dos Atributos 2 a 9.
      * Isso resulta em 1 produto configurável e 1 produto secundário.
1. Vá para a guia **[!UICONTROL Configurations]** do produto configurável.
1. Clique em **[!UICONTROL Add Products]** manualmente e comece a adicionar os produtos simples criados anteriormente, um por um.
1. Salve as alterações após cada adição.
1. À medida que você adiciona produtos, observe o tempo de carregamento da página editar produto configurável.
1. Depois de adicionar 7 produtos, você deve notar um aumento significativo no consumo de RAM e no tempo de carregamento da página

<u>Resultados esperados</u>:

O formulário de edição do produto deve ser carregado de forma rápida e eficiente sem consumo excessivo de memória.

<u>Resultados reais</u>:

A edição do produto configurável leva muito tempo para carregar e pode atingir limites de memória ou erros de tempo limite.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
