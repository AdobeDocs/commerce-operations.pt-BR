---
title: 'ACSD-62979: ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro de memória fatal'
description: Aplique o patch ACSD-62979 para corrigir o problema do Adobe Commerce em que o uso da ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro fatal de memória
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-62979: ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro de memória fatal

O patch ACSD-62979 corrige o problema em que o uso da ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro de memória fatal. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 está instalado. A ID do patch é ACSD-62979. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6, 2.4.6-p7, 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Corrige o problema em que o uso da ID de armazenamento incorreta no cabeçalho do GraphQL causa um erro de memória fatal.

<u>Etapas a serem reproduzidas</u>:

1. Navegue até **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]**). Habilitar **[!UICONTROL Add Store Code to Urls]**.
1. Execute a consulta GraphQL abaixo com o valor incorreto para o cabeçalho da loja.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

Mensagem de erro: &quot;O armazenamento solicitado não foi encontrado. Verifique o armazenamento e tente novamente&quot;

<u>Resultados reais</u>:

Erro fatal como:

```Allowed memory size of 792723456 bytes exhausted```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
