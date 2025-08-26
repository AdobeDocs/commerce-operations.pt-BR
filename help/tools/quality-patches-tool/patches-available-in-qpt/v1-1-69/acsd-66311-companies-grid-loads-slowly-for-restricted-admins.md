---
title: 'ACSD-66311: a grade das empresas é carregada lentamente para usuários administradores restritos'
description: Aplique o patch ACSD-66311 para corrigir o problema do Adobe Commerce em que as empresas carregam lentamente a grade para usuários administradores com acesso restrito a sites.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311: a grade das empresas é carregada lentamente para usuários administradores restritos

O patch ACSD-66311 corrige o problema em que a grade das empresas é carregada lentamente para usuários administradores com acesso restrito ao site. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66311. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A grade das empresas é carregada lentamente para usuários administradores com acesso restrito ao site.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com **[!UICONTROL B2B features]**.
1. Crie 2 sites extras (além do site principal) com lojas/visualizações:
   * Site principal (criado durante a instalação)
   * Site 2 → Loja 2 → StoreView 2
   * Site 3 → Loja 3 → StoreView 3
1. Criar a função de usuário **[!UICONTROL Admins in Scope]**:
   * Escopo: apenas dois armazenamentos: *Site Principal* + *Site 3/Loja 3*.
   * Recursos: somente *Painel* + *Empresas*.
1. Crie um usuário administrador com função **[!UICONTROL Admins in Scope]**, por exemplo, **adminscope**.
1. Gerar dados específicos distribuídos do cliente e da empresa:
   1. **Clientes atribuídos a sites**

      | ID do site | Número de clientes |
      |------------|---------------------|
      | 1 | 600.000 |
      | 2 | 1.500 |
      | 3 | 500 |


   1. Execute a seguinte consulta para verificar a distribuição:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Clientes atribuídos a empresas**

      | Número de clientes | Número de empresas |
      |---------------------|---------------------|
      | 1 | 4.500 |
      | 2 | ~1.000 |
      | ~595 k | 1 |

   1. Execute a seguinte consulta para verificar a distribuição:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            SELECIONE company_id, COUNT(customer_id) AS customer_count
            FROM company_advanced_customer_entity
            AGRUPAR POR company_id
) subconsulta AS
AGRUPAR POR customer_count
ORDER BY customer_count;
&quot;

1. Reindexe todos os dados para gerar entradas na **customer_grid_flat**.
1. Faça logon como **adminscope**.
1. Vá para **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Resultados esperados</u>:

A página é carregada em menos de 1 segundo.

<u>Resultados reais</u>:

A página demora mais de 14 minutos para carregar.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
