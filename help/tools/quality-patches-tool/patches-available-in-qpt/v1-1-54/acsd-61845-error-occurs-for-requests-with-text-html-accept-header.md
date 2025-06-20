---
title: 'ACSD-61845: Ocorre um erro para solicitações com text/html accept header'
description: Aplique o patch ACSD-61845 para corrigir o problema do Adobe Commerce em que o envio de uma solicitação HTTP com apenas um cabeçalho de aceitação *text/html* causa um erro 500, com módulos B2B instalados.
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: Ocorre um erro para solicitações com *text/html* para aceitar o cabeçalho

O patch ACSD-61845 corrige o problema em que uma solicitação HTTP com apenas um cabeçalho de aceitação *text/html* causa um erro 500 devido a incompatibilidades de tipo de mídia no tratamento de resposta. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-61845. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Ao enviar uma solicitação HTTP com apenas *text/html* no cabeçalho de aceitação, ocorre um erro 500 devido a uma incompatibilidade na configuração do tipo de mídia.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Envie uma solicitação somente com *text/html* no cabeçalho de aceitação, da seguinte maneira:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Resultados esperados</u>:

A página é retornada com um *código de status 200*.

<u>Resultados reais</u>:

Um erro 500 é retornado, com a seguinte mensagem de erro no `exception.log`:

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
