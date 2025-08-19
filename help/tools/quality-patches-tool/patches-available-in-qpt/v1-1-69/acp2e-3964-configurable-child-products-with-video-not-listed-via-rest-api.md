---
title: 'ACP2E-3964: Produtos filho configuráveis com vídeo não listados pela API REST'
description: Aplique o patch ACP2E-3964 para corrigir o problema do Adobe Commerce em que produtos derivados de produtos configuráveis com um vídeo no [!UICONTROL Media Gallery] não são listados por meio da API REST.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964: Produtos filho configuráveis com vídeo não listados pela API REST

O patch ACP2E-3964 corrige o problema em que produtos derivados de produtos configuráveis com um vídeo no **[!UICONTROL Media Gallery]** não são listados por meio da API REST. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 está instalado. A ID do patch é ACP2E-3964. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.9.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os produtos derivados de produtos configuráveis com um vídeo no **[!UICONTROL Media Gallery]** não podem ser listados por meio da API REST, resultando em uma resposta de erro.

<u>Etapas a serem reproduzidas</u>:

1. Crie um novo produto configurável e adicione um único produto secundário.
1. Edite o produto derivado e adicione um vídeo em **[!UICONTROL Images and Videos]** (por exemplo, [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Salve o produto derivado.
1. Envie uma solicitação GET para o ponto de extremidade da API REST: `rest/v1/configurable-products/%sku%/children` usando um token de portador de administrador.

<u>Resultados esperados</u>:

A API REST deve retornar os dados do produto filho sem erros, incluindo as informações de vídeo no **[!UICONTROL Media Gallery]**.

<u>Resultados reais</u>:

A API REST retorna um erro:

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
