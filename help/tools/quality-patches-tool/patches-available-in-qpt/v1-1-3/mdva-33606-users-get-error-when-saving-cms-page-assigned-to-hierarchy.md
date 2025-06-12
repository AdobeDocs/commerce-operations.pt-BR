---
title: 'MDVA-33606: Os usuários recebem um erro ao salvar a página do CMS atribuída à hierarquia'
description: O patch MDVA-33606 resolve o problema em que os usuários obtêm o erro *Violação de restrição exclusiva encontrada* ao salvar uma página do CMS atribuída à árvore de hierarquia. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 está instalada. A ID do patch é MDVA-33606. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.
feature: CMS
role: Admin
exl-id: 19aaa13f-7ee6-49bc-b1d9-c288dc93b951
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# MDVA-33606: Os usuários recebem um erro ao salvar a página do CMS atribuída à hierarquia

O patch MDVA-33606 resolve o problema em que os usuários obtêm o erro *Violação de restrição exclusiva encontrada* ao salvar uma página do CMS atribuída à árvore de hierarquia. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3 está instalada. A ID do patch é MDVA-33606. Observe que o problema foi corrigido no Adobe Commerce 2.4.3.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1-2.4.2-p2

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao tentar salvar uma página do CMS atribuída à árvore hierárquica, os usuários recebem a seguinte mensagem de erro: *Violação de restrição exclusiva encontrada*.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova página do CMS. Defina o escopo como Todos os modos de exibição de armazenamento. Esta é a sua página 1 do CMS.
1. Criar uma nova exibição de loja. Esta é a Visualização 2 da Loja.
1. Vá para **Conteúdo** > **Hierarquia** > Adicionar a Página 1 do CMS à árvore hierárquica.
1. Altere o escopo para Exibição de armazenamento 2.
   * Desmarque &quot;Usar a hierarquia do nó principal&quot;.
   * Adicione a Página 1 do CMS a este escopo e salve-o.
1. Agora altere o escopo para Exibição de armazenamento padrão.
   * Desmarque &quot;Usar a hierarquia do nó principal&quot;.
   * Adicione a Página 1 do CMS a este escopo e salve-o.
1. Ir para **Conteúdo** > **Páginas** > **Adicionar nova página**.
   * Coloque o título da página como Page 2.
   * Na seção Página nos Sites, atribua a Todas as Exibições da Loja e a ambas as exibições da loja (Exibição da Loja Padrão e Exibição da Loja 2) e clique em **Salvar Página**.
1. Na página de edição do CMS, abra a guia Hierarquia.
   * Atribua a Página 2 ao nó Exibição de armazenamento 2, nó Padrão e nó Todos os sites.

<u>Resultados esperados</u>:

Você pode atribuir a página CMS a todos os três nós sem qualquer erro.

<u>Resultados reais</u>:

Você recebe o seguinte erro: *Violação de restrição exclusiva encontrada*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches).
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
