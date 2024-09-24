---
title: "MDVA-42657: Não é possível selecionar categorias nas condições do segmento do cliente"
description: O patch MDVA-42657 resolve o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-42657. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: Não é possível selecionar categorias nas condições do segmento do cliente

O patch MDVA-42657 resolve o problema em que o usuário administrador não consegue selecionar categorias nas condições do segmento do cliente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 está instalada. A ID do patch é MDVA-42657. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O usuário administrador não pode selecionar categorias nas condições do segmento do cliente.

<u>Etapas a serem reproduzidas</u>:

1. Vá para **Clientes** > **Segmentos**.
1. Crie um novo segmento.
1. Vá para o segmento recém-criado e clique em **Condições** no lado esquerdo da navegação.
1. Clique no sinal de mais verde.
1. Selecione Histórico de produtos em Produtos.
1. Altere &quot;visualizado&quot; para &quot;ordenado&quot;.
1. Altere &quot;ALL&quot; para &quot;ANY&quot;.
1. Clique no sinal de mais verde aninhado e selecione Categoria.
1. Clique no sinal **...** e no ícone do seletor (à esquerda da marca de seleção).
1. Abra o console de desenvolvimento do navegador.
1. Marque as caixas de seleção para qualquer/várias categorias e observe o erro de javascript lançado no console.
1. Clique no botão **Salvar**.
1. Volte para a condição e verifique se as categorias selecionadas foram salvas.

<u>Resultados esperados</u>:

As categorias selecionadas são salvas e selecionadas ao visualizar/editar as condições do segmento.

<u>Resultados reais</u>:

As categorias selecionadas estão ausentes e não foram salvas corretamente. Você recebe o seguinte erro no console:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
