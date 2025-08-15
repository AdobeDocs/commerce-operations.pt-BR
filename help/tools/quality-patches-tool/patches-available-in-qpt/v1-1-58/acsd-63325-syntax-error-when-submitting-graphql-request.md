---
title: 'ACSD-63325: Erro de sintaxe: &lt;EOF&gt; inesperado ao enviar solicitação  [!DNL GraphQL]  vazia'
description: Aplique o patch ACSD-63325 para corrigir o problema do Adobe Commerce em que ocorre um erro de sintaxe ao enviar uma solicitação  [!DNL GraphQL]  vazia.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: erro &quot;Erro de sintaxe: inesperado &lt; EOF >&quot; ao enviar solicitação [!DNL GraphQL] vazia

O patch ACSD-63325 corrige o problema em que um erro &quot;Erro de sintaxe: inesperado &lt; EOF >&quot; e um código de resposta não 200 são retornados ao enviar uma solicitação [!DNL GraphQL] vazia. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 está instalado. A ID do patch é ACSD-63325. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao enviar uma solicitação [!DNL GraphQL] vazia, há um erro interno do servidor HTTP em vez de um código de resposta 200.

<u>Etapas a serem reproduzidas</u>:

1. Enviar uma solicitação GraphQL vazia

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u>Resultados esperados</u>:

O código de resposta da solicitação é 200.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u>Resultados reais</u>:

Ocorre um erro interno de servidor 500, como mostrado:

```
HTTP/1.1 500 Internal Server Error
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na Infraestrutura em Nuvem: [Atualizações e Patches > Aplicar Patches](https://experienceleague.adobe.com/pt-br/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) no guia do Commerce na Infraestrutura em Nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
