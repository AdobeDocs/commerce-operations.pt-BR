---
title: 'ACSD-57337: O usuário administrador com restrições de acesso pode visualizar todas as empresas na grade *Empresas*'
description: Aplique o patch ACSD-57337 para corrigir o problema do Adobe Commerce em que um usuário administrador com restrições de acesso a sites específicos pode visualizar empresas de todos os sites na grade *Empresas*.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: 7a05d335-5ed8-460e-80c4-dbc51d06c5bd
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-57337: O usuário administrador com restrições de acesso pode exibir todas as empresas na grade *Empresas*

O patch ACSD-57337 corrige o problema em que um usuário administrador com restrições de acesso a sites específicos podia exibir empresas de todos os sites na grade *Empresas*. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 está instalado. A ID do patch é ACSD-57337. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um usuário administrador com restrições de acesso a sites específicos pode exibir empresas de todos os sites na grade *Empresas*.

<u>Etapas a serem reproduzidas</u>:

1. Crie um site, uma loja e uma loja adicionais.
1. Crie algumas empresas atribuídas a sites diferentes.
1. Crie uma função de usuário administrador e defina o escopo da função para o site criado.
1. Crie um administrador e atribua-o à função criada.
1. Faça logon com um novo administrador.
1. Abra **[!UICONTROL Customers]** > **[!UICONTROL Companies]** e observe a lista de empresas.

<u>Resultados esperados</u>:

As empresas atribuídas ao site adicional estão visíveis na grade *Empresas*.

<u>Resultados reais</u>:

Todas as empresas estão visíveis na grade *Empresas*.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
