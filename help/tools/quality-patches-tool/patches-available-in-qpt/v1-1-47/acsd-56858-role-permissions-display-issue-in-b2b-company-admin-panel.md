---
title: 'ACSD-56858: discrepância de permissões de função no administrador da empresa B2B'
description: Aplique o patch ACSD-56858 para corrigir o problema do Adobe Commerce em que as permissões de função são exibidas incorretamente para um administrador de empresa restrita no ambiente B2B.
feature: Companies, B2B, Roles/Permissions
role: Admin, Developer
exl-id: 28f90c8b-5d8b-4444-99ef-c91cfb5d6081
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '462'
ht-degree: 0%
---
# ACSD-56858: discrepância de permissões de função no administrador da empresa B2B

O patch ACSD-56858 corrige o problema em que as permissões de função são exibidas incorretamente para um administrador de empresa restrita no ambiente B2B. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.47 está instalado. A ID do patch é ACSD-56858. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.7.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.2 - 2.4.6-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

As permissões de função para um administrador de empresa restrito no ambiente B2B são exibidas incorretamente.

<u>Etapas a serem reproduzidas</u>:

1. Comece criando uma empresa, adicionando um administrador de empresa e usuários de empresa.
1. Faça logon como o administrador da empresa na loja e crie várias funções para usuários diferentes.
1. Atribua essas funções conforme necessário, como limitar o acesso a algumas tarefas enquanto permite o acesso total a outras.
1. Atribua essas funções com acesso total a um usuário diferente do administrador da empresa.
1. Faça logon em um usuário administrador que não seja da empresa, por exemplo, company_manager.
1. Navegue até **[!UICONTROL Roles and permission]** e edite a função.
1. Observe que as permissões exibidas não correspondem às permissões definidas no banco de dados da empresa para essa ID de função.

<u>Resultados esperados</u>:

As funções e permissões são exibidas corretamente para o usuário administrador não pertencente à empresa.

<u>Resultados reais</u>:

As funções não aparecem corretamente para o usuário administrador não-empresa conforme os registros do banco de dados na tabela de permissões.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool]
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem

## Leitura relacionada

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) na base de dados de conhecimento de suporte
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool]
* [Práticas recomendadas para modificar tabelas de banco de dados](/help/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables.md#why-adobe-recommends-avoiding-modifications) no Manual de implementação do Commerce

Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) no guia [!DNL Quality Patches Tool].
