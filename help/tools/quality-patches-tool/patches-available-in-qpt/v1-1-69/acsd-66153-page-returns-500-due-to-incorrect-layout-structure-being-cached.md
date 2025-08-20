---
title: 'ACSD-66153: a página retorna o erro 500 devido à estrutura de layout incorreta em cache'
description: Aplique o patch ACSD-66153 para corrigir o problema do Adobe Commerce em que uma página retorna um código de erro 500 devido a uma estrutura de layout incorreta em cache.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153: a página retorna o erro 500 devido à estrutura de layout incorreta em cache

O patch ACSD-66153 corrige o problema em que uma página retorna um código de erro 500 devido a uma estrutura de layout incorreta em cache. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACSD-66153. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.5-p10

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Uma página retorna um erro 500 devido a uma estrutura de layout incorreta em cache.

<u>Etapas a serem reproduzidas</u>:

1. Instalar `2.4-develop`.
1. Criar e instalar módulo personalizado:
1.1 Adicione um bloco personalizado ao layout `catalog_category_view`.
1.1 Insira `Magento\Framework\View\Result\Layout` no bloco personalizado por meio de seu construtor.
1. Criar a categoria **[!UICONTROL shop]**.
1. Abrir **[!UICONTROL two terminal windows]**:
   1. **Terminal 1**: limpar continuamente o cache de layout:

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2**: simular solicitações simultâneas à página de categoria:

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Algumas solicitações falham aleatoriamente com um código de status 500, e `var/log/support_report.log` mostra o seguinte erro:

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Resultados esperados</u>:

Todas as solicitações retornam 200 OK.

<u>Resultados reais</u>:

Algumas solicitações retornam intermitentemente o Erro interno 500 do servidor.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
