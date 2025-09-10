---
title: Como funcionam os patches
description: Saiba mais sobre os diferentes tipos de patches para o Adobe Commerce e como eles funcionam.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Como funcionam os patches

>[!WARNING]
>
>Recomendamos testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantar na produção. Também recomendamos que você faça o backup dos seus dados antes de aplicar um patch. Consulte [Fazer backup e reverter o sistema de arquivos](../../installation/tutorials/backup.md).

Arquivos de patch (ou diff) são arquivos de texto que observam:

- Os arquivos a serem alterados.
- O número da linha que iniciará a alteração e o número de linhas a serem alteradas.
- O novo código a ser trocado.

Quando o programa de patch é executado, esse arquivo é lido e as alterações especificadas são feitas no(s) arquivo(s).

Há três tipos de patches:

- **Hotfixes** — Patches publicados pela Adobe na [Central de Segurança](https://magento.com/security/patches).
- **Patches individuais** — Patches criados e distribuídos individualmente pelo Suporte da Adobe Commerce.
- **Patches personalizados** — Patches não oficiais que você pode criar a partir de uma confirmação do Git.

## Hotfixes

Hotfixes são patches que contêm correções de segurança ou qualidade de alto impacto que afetam muitos comerciantes. Essas correções são aplicadas à próxima versão de patch da versão secundária aplicável. O Adobe lança hotfixes conforme necessário.

Você pode encontrar hotfixes na [Central de Segurança](https://magento.com/security/patches). Siga as instruções na página para baixar o arquivo de patch, dependendo da sua versão e do tipo de instalação. Use a [linha de comando](../patches/apply.md#) ou o [Composer](../patches/apply.md) para aplicar patches de hot fix.

>[!NOTE]
>
>Hot fixes podem conter alterações incompatíveis com versões anteriores.

## Patches individuais

Patches individuais contêm correções de qualidade de baixo impacto para um problema específico. Essas correções são aplicadas à versão secundária com suporte mais recente (por exemplo, 2.4.x), mas podem estar ausentes da versão secundária com suporte anterior (por exemplo, 2.3.x). O Adobe lança patches individuais conforme necessário.

Use o [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR){target="_blank"} para aplicar patches individuais.

>[!NOTE]
>
>Os patches individuais não contêm alterações incompatíveis com versões anteriores.

## Patches personalizados

Às vezes demora um pouco para a Equipe de engenharia da Adobe incluir uma correção de erro feita no GitHub em uma versão oficial do Adobe Commerce. Enquanto isso, você pode criar uma correção do GitHub e usar o plug-in [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) para aplicá-la à instalação baseada no Composer.

{{custom-patches-disclaimer}}

Use a [linha de comando](apply.md#command-line) ou o [Composer](apply.md#composer) para aplicar patches personalizados.

Há muitas maneiras de criar arquivos de patch personalizados. O exemplo a seguir se concentra na criação de um patch a partir de uma Git Commit conhecida.

Para criar um patch personalizado:

1. Crie um diretório `patches/composer` em seu projeto local.
1. Identifique a solicitação de confirmação ou extração do GitHub a ser usada para o patch. Este exemplo usa a confirmação [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede), vinculada ao problema do GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Anexe as extensões `.patch` ou `.diff` à URL de confirmação. Use `.diff` para um arquivo menor. Por exemplo: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Salve a página como um arquivo no diretório `patches/composer`. Por exemplo, `github-issue-6474.diff`.
1. Edite o arquivo e remova `app/code/<VENDOR>/<PACKAGE>` de todos os caminhos para que eles sejam relativos ao diretório `vendor/<VENDOR>/<PACKAGE>`.

   >[!NOTE]
   >
   >Os editores de texto que removem automaticamente os espaços em branco à direita ou adicionam novas linhas podem quebrar a correção. Use um editor de texto simples para fazer essas alterações.

O exemplo a seguir mostra o arquivo DIFF mencionado anteriormente após a remoção de todas as instâncias de `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();

                 return this;
             },
```

## Aplicação de patches

Você pode aplicar patches usando qualquer um dos métodos a seguir:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR){target="_blank"}
- [Linha de comando](/help/upgrade/patches/apply.md#command-line)
- [Compositor](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Para aplicar um patch a um projeto do Adobe Commerce na infraestrutura em nuvem, consulte [Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no _guia do Commerce na nuvem_.
