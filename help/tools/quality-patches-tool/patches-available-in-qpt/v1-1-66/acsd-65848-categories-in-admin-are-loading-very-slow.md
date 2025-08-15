---
title: 'ACSD-65848: as categorias no administrador estão carregando muito lentamente'
description: Aplique o patch ACSD-65848 para corrigir o problema do Adobe Commerce em que a contagem total de produtos em uma categoria foi calculada usando uma subseleção, o que atrasou o tempo de carregamento da categoria.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848: as categorias no administrador estão carregando muito lentamente

O patch ACSD-65848 corrige o problema em que a contagem total de produtos em uma categoria era calculada usando uma subseleção, o que atrasava o tempo de carregamento da categoria. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 está instalado. A ID do patch é ACSD-65848. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A página de edição/exibição de categoria do Administrador apresenta atrasos significativos ao carregar. O atraso é causado pelo método usado para calcular a contagem total de produtos em uma categoria, que depende de uma consulta de subseleção. Refatorar essa lógica para usar uma junção melhora o desempenho e reduz o tempo de carregamento.

<u>Etapas a serem reproduzidas</u>:

1. Crie uma nova instância da Adobe Commerce Cloud usando a versão 2.4.8.
1. Crie 2.500 categorias e pelo menos 10.000 produtos:
   1. Copie o diretório `setup/performance-toolkit` para `./var` para poder editar os perfis.
   1. Abra o perfil `small.xml` e atualize-o para incluir 2.500 categorias e 250.000 produtos (para corresponder à configuração do comerciante).
   1. Execute o seguinte comando para gerar as correções:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Após a criação dos produtos e categorias, verifique se todas as categorias estão definidas como âncoras. Executar esta consulta SQL:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. No painel Administração, crie uma estrutura de categoria mais profunda:
   * Mova a Categoria 2 na Categoria 1 para aninhá-la mais profundamente na árvore.
1. Tente abrir uma página de categoria no painel Admin usando um URL como:
   ```/admin/catalog/category/edit/id/xx/```

<u>Resultados esperados</u>:

Cada página de categoria é aberta na primeira tentativa em alguns segundos.

<u>Resultados reais</u>:

As páginas de categoria levam mais de um minuto para serem abertas.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
