---
title: Verificação final
description: Verifique se a configuração Varnish está configurada corretamente para funcionar com o aplicativo Adobe Commerce.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# Verificação final da configuração da Varnish

Agora que você está usando a variável `default.vcl` gerado para você pelo Commerce, você pode realizar algumas verificações finais para garantir que o Varnish esteja funcionando.

## Verificar cabeçalhos de resposta HTTP

Use `curl` ou outro utilitário para exibir cabeçalhos de resposta HTTP quando você visita qualquer página do Commerce em um navegador da Web.

Primeiro, verifique se você está usando [modo desenvolvedor](../cli/set-mode.md#change-to-developer-mode); caso contrário, você não verá os cabeçalhos.

Por exemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Cabeçalhos importantes:

```terminal
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Este valor também é aceitável: `X-Magento-Cache-Debug: HIT`.

## Verificar tempos de carregamento de página

Se a Varnish estiver funcionando, qualquer página do Commerce com blocos armazenáveis em cache deverá carregar em menos de 150 ms. Exemplos dessas páginas são a porta da frente e [vitrine](https://glossary.magento.com/storefront) [categoria](https://glossary.magento.com/category) páginas.

Use um inspetor de navegador para medir o tempo de carregamento da página.

Por exemplo, para usar o Inspetor do Chrome:

1. Acesse qualquer página de Comércio em cache no Chrome.
1. Clique com o botão direito do mouse em qualquer lugar da página.
1. No menu pop-up, clique em **[!UICONTROL Inspect Element]**
1. No painel do inspetor, clique no **[!UICONTROL Network]** guia .
1. Atualize a página.
1. Role até a parte superior do painel do inspetor, para que você possa ver o URL da página que está visualizando.

   A figura a seguir mostra um exemplo de carregamento da variável `magento2` página de índice.

   ![Clique na página que você está visualizando](../../assets/configuration/varnish-inspector.png)

   O tempo de carregamento da página é exibido ao lado do URL da página. Nesse caso, o tempo de carregamento é de 5 ms. Isso ajuda a confirmar que a Varnish armazenou a página em cache.

1. Para exibir cabeçalhos de resposta HTTP, clique no URL da página (na coluna Nome ).

   Você pode exibir cabeçalhos HTTP que são discutidos com mais detalhes na seção Verificar cabeçalhos de resposta HTTP .

## Verificar o cache do Commerce

Certifique-se de que o `<magento_root>/var/page_cache` o diretório está vazio:

1. Faça logon no seu servidor do Commerce ou alterne para o [proprietário do sistema de arquivos](https://glossary.magento.com/magento-file-system-owner).
1. Digite o seguinte comando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Acesse uma ou mais páginas do Commerce que podem ser armazenadas em cache.
1. Verifique a `var/page_cache/` diretório.

   Se o diretório estiver vazio, parabéns! Você configurou o Varnish e o Commerce com êxito para trabalharem juntos!

1. Se você limpou o `var/page_cache/` diretório, reinicie o Varnish.

>[!TIP]
>
>Se encontrar erros 503 (Falha na Busca de Backend), consulte [Solução de problemas de erros 503 (serviço indisponível)](https://support.magento.com/hc/en-us/articles/360034631211) no _Central de ajuda da Adobe Commerce_.
