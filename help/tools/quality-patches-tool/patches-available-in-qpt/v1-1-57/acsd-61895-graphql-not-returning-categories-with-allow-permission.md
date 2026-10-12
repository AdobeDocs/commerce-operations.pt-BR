---
title: 'ACSD-61895: [!DNL GraphQL] falha na consulta de categorias para catálogo compartilhado privado com exibição restrita'
description: Aplique o patch ACSD-61895 para corrigir o problema do Adobe Commerce em que as respostas do [!DNL GraphQL] para clientes convidados (usando um catálogo compartilhado público com todas as categorias permitidas) não retornavam nenhuma categoria quando um catálogo compartilhado privado com restrições era criado para as mesmas categorias.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e439352c-5b67-587d-b34e-d2a0aa5a0242
    internal-label: Roles/Permissions
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
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
source-wordcount: '564'
ht-degree: 0%
---
# ACSD-61895: [!DNL GraphQL] `categories` falha na consulta para catálogo compartilhado privado com exibição restrita

O patch ACSD-61895 corrige o problema em que as respostas do [!DNL GraphQL] para clientes convidados (usando um catálogo compartilhado público com todas as categorias permitidas) não retornavam nenhuma categoria quando um catálogo compartilhado privado com restrições era criado para as mesmas categorias.

Após a correção, ele retorna todas as categorias com permissões (catálogo compartilhado público) para usuários convidados, mesmo que a categoria raiz não tenha permissão de permissão no escopo de um catálogo compartilhado privado.

Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-61895. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL GraphQL] respostas para clientes convidados (usando um catálogo compartilhado público com todas as categorias permitidas) não retornam nenhuma categoria quando um catálogo compartilhado privado com restrições é criado para as mesmas categorias.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com B2B e dados de amostra.
1. Certifique-se de que os recursos B2B estejam ativados.
1. Crie dois catálogos compartilhados: um público e um privado.

   * Catálogo público compartilhado:

     * Atribuir todas as categorias ao catálogo público.

   * Catálogo privado compartilhado:

     * Atribua somente a categoria `Gear` e suas categorias filho ao catálogo privado.
     * Atribuir o catálogo privado a uma empresa de teste.

1. Criar um usuário da empresa:

   * Crie um usuário associado à empresa de teste vinculada ao catálogo compartilhado privado.
   * Certifique-se de que o usuário só possa acessar a categoria `Gear` e suas categorias filho no front-end quando conectado.

1. Categorias de consulta por meio da API:

   * Use o cliente da API para executar a seguinte consulta [!DNL GraphQL] sem um token de cliente:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Observe a resposta e verifique se a categoria `Gear` e outras categorias foram retornadas.
1. Agora, consulte categorias com um token de cliente:

   * Efetue logon como o usuário da empresa de teste.
   * Execute a mesma consulta de categoria [!DNL GraphQL], mas inclua o token do cliente para o usuário conectado.
   * Observe a resposta e verifique se apenas a categoria `Gear` e suas categorias secundárias são retornadas.


<u>Resultados esperados</u>:

Ao consultar como usuário convidado da empresa, todas as categorias devem ser retornadas (conforme esperado).

<u>Resultados reais</u>:

A resposta da consulta `categories` não mostra nenhuma categoria.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
