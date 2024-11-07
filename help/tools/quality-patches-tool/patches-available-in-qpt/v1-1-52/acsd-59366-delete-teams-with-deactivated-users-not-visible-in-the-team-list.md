---
title: "ACSD-59366: excluir equipes com usuários desativados não visíveis na lista de equipes"
description: Aplique o patch ACSD-59366 para corrigir o problema do Adobe Commerce em que ocorre um erro ao tentar excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes.
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: excluir equipes com usuários desativados não visíveis na lista de equipes

O patch ACSD-59366 corrige o problema em que ocorre um erro ao tentar excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 está instalado. A ID do patch é ACSD-59366. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ocorre um erro ao excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes.

<u>Pré-requisitos</u>:

Os módulos B2B do Adobe Commerce são instalados e as empresas são ativadas.

<u>Etapas a serem reproduzidas</u>:

1. Crie e faça logon com um usuário da empresa.
1. Em estrutura da empresa, crie uma nova equipe.
1. Na nova equipe do, crie um novo usuário.
1. Editar o novo usuário e desativar.
1. Selecione a equipe e exclua.

<u>Resultados esperados</u>:

A equipe tem um ou mais usuários inativos. A exclusão da equipe cancelará a atribuição desses usuários. Você pode encontrar usuários inativos na seção [!UICONTROL Company Users].

<u>Resultados reais</u>:

Ocorre um erro ao tentar excluir uma equipe com um usuário desativado.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.


