---
title: Como funcionam os patches
description: Saiba mais sobre os diferentes tipos de patches para Adobe Commerce e Magento Open Source e como eles funcionam.
source-git-commit: 38b054bbae8ba116557ce367c8397c646c837558
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# Como funcionam os patches

>[!WARNING]
>
>Recomendamos testar todos os patches em um ambiente de preparo ou desenvolvimento antes de implantá-los na produção. Também recomendamos fazer backup de seus dados antes de aplicar um patch. Consulte [Faça backup e reverta o sistema de arquivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Arquivos de patch (ou diff) são arquivos de texto que observam:

- Os arquivos a serem alterados.
- O número da linha para iniciar a alteração e o número de linhas a serem alteradas.
- O novo código para troca.

Quando a variável [correção](https://en.wikipedia.org/wiki/Patch_(Unix)) for executado, este arquivo será lido e as alterações especificadas serão feitas no(s) arquivo(s).

Existem três tipos de patches:

- **Hotfixes**—Correções que o Adobe publica no [Central de segurança](https://magento.com/security/patches).
- **Correções individuais**—Patches que o Suporte Adobe Commerce cria e distribui individualmente.
- **Correções personalizadas**—Patches não oficiais que você pode criar a partir de um commit de git.

## Hotfixes

Hotfixes são patches que contêm correções de alta segurança ou qualidade que afetam muitos comerciantes. Essas correções são aplicadas à próxima versão de patch para a versão secundária aplicável. O Adobe lança hotfixes conforme necessário.

Você pode encontrar hotfixes no [Central de segurança](https://magento.com/security/patches). Siga as instruções na página para baixar o arquivo de patch, dependendo da versão e do tipo de instalação. Use o [linha de comando](../patches/apply.md#) ou [Composer](../patches/apply.md) para aplicar patches de hot fix.

>[!NOTE]
>
>Os hotfixes podem conter alterações incompatíveis com o passado.

## Correções individuais

Os patches individuais contêm correções de qualidade de baixo impacto para um problema específico. Essas correções são aplicadas à versão secundária compatível mais recentemente (por exemplo, 2.4.x), mas podem estar ausentes da versão secundária compatível anterior (por exemplo, 2.3.x). O Adobe libera patches individuais conforme necessário.

Use o [Ferramenta Correções de Qualidade](https://devdocs.magento.com/quality-patches/tool.html) para aplicar patches individuais.

>[!NOTE]
>
>Os patches individuais não contêm alterações incompatíveis com o passado.

## Correções personalizadas

Às vezes, leva um tempo para a equipe de engenharia do Adobe incluir uma correção de erro feita no GitHub em uma versão do Adobe Commerce ou do Magento Open Source Composer. Enquanto isso, você pode criar um patch no GitHub e usar o [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) para aplicá-lo à sua instalação baseada no Composer.

Use o [linha de comando] ou [Composer] para aplicar patches personalizados.

Há muitas maneiras de criar arquivos de patch personalizados. O exemplo a seguir foca na criação de um patch a partir de uma confirmação de git conhecida.

Para criar um patch personalizado:

1. Crie um `patches/composer` no seu projeto local.
1. Identifique a confirmação ou a solicitação de pull do GitHub a ser usada para o patch. Esse exemplo usa a variável [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) commit, vinculado ao problema do GitHub [#6474](https://github.com/magento/magento2/issues/6474).
1. Anexar o `.patch` ou `.diff` extensões para o URL de confirmação. Use `.diff` para um tamanho de arquivo menor. Por exemplo: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Salve a página como um arquivo na `patches/composer` diretório. Por exemplo, `github-issue-6474.diff`.
1. Edite o arquivo e remova `app/code/<VENDOR>/<PACKAGE>` de todos os caminhos para que sejam relativos a `vendor/<VENDOR>/<PACKAGE>` diretório.

   >[!NOTE]
   >
   >Editores de texto que removem automaticamente o espaço em branco à direita ou adicionam novas linhas podem quebrar o patch. Use um editor de texto simples para fazer essas alterações.

O exemplo a seguir mostra o arquivo DIFF mencionado anteriormente após remover todas as instâncias de `app/code/Magento/Payment`:

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

Você pode aplicar patches usando qualquer um dos seguintes métodos:

- [Ferramenta Correções de Qualidade](https://devdocs.magento.com/quality-patches/tool.html)
- [Linha de comando](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)

>[!NOTE]
>
>Para aplicar um patch a um projeto de infraestrutura em nuvem do Adobe Commerce, consulte [Aplicar patches](https://devdocs.magento.com/cloud/project/project-patch.html) no _Guia da nuvem_.
