---
title: 'MDVA-43451: Erro ao definir Preço e Estrutura para catálogo compartilhado'
description: O patch MDVA-43451 resolve o problema em que o usuário não consegue definir a Precificação e a Estrutura de um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43451. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
exl-id: 2cddfca2-ee32-4e73-9ef6-78125fbaa13d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-43451: Erro ao definir Preço e Estrutura para catálogo compartilhado

O patch MDVA-43451 resolve o problema em que o usuário não consegue definir a Precificação e a Estrutura de um catálogo compartilhado. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 está instalada. A ID do patch é MDVA-43451. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário não pode definir preços e estrutura para um catálogo compartilhado. A seguinte mensagem é exibida: *O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.*

<u>Etapas a serem reproduzidas</u>:

1. Crie um site personalizado. As ids dos sites devem ser 0, 1, 2.
1. Crie uma loja no site acima. As ids dos armazenamentos devem ser 0,1,2.
1. Crie três exibições de loja para a loja acima. As IDs das exibições de loja devem ser 0,1, 2, 3, 4.
1. Exclua a exibição de loja com a id 2. Agora, a tabela de lojas deve ser semelhante à tabela abaixo.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Crie um novo catálogo compartilhado.
1. Ao configurar Preço e Estrutura, selecione o armazenamento criado na Etapa 2.
1. Salve o catálogo compartilhado.

<u>Resultados esperados</u>:

O catálogo compartilhado é salvo sem nenhum problema.

<u>Resultados reais</u>:

Não é possível salvar o catálogo compartilhado. O seguinte erro é exibido:
*O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente.*

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
