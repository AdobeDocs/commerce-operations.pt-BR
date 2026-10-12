---
title: 'ACSD-59366: excluir equipes com usuários desativados não visíveis na lista de equipes'
description: Aplique o patch ACSD-59366 para corrigir o problema do Adobe Commerce em que ocorre um erro ao tentar excluir uma equipe que contém usuários desativados que não estão visíveis na lista de equipes.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '395'
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
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

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

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
