---
title: Verificação final
description: Verifique se a configuração de verniz está definida corretamente para funcionar com o aplicativo do Adobe Commerce.
feature: Configuration, Cache
exl-id: 01f28c93-75cd-4969-9142-b8dac0aa2adb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Verificação final da configuração do verniz

Agora que você está usando o `default.vcl` gerado para você pelo Commerce, é possível executar algumas verificações finais para verificar se o Verniz está funcionando.

## Verificar cabeçalhos de resposta HTTP

Use o `curl` ou outro utilitário para exibir cabeçalhos HTTP de resposta quando você visitar qualquer página do Commerce em um navegador da Web.

Primeiro, verifique se você está usando o [modo de desenvolvedor](../cli/set-mode.md#change-to-developer-mode); caso contrário, você não verá os cabeçalhos.

Por exemplo,

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Cabeçalhos importantes:

```
X-Magento-Cache-Control: max-age=86400, public, s-maxage=86400
Age: 0
X-Magento-Cache-Debug: MISS
```

>[!INFO]
>
>Este valor também é aceitável: `X-Magento-Cache-Debug: HIT`.

## Verificar tempos de carregamento da página

Se o Verniz estiver funcionando, qualquer página do Commerce com blocos que podem ser armazenados em cache deverá ser carregada em menos de 150 ms. Exemplos dessas páginas são as páginas de categoria da porta frontal e da loja.

Use um inspetor de navegador para medir os tempos de carregamento da página.

Por exemplo, para usar o Inspetor de Chrome:

1. Acesse qualquer página do Commerce que possa ser armazenada em cache no Chrome.
1. Clique com o botão direito do mouse em qualquer lugar da página.
1. No menu pop-up, clique em **[!UICONTROL Inspect Element]**
1. No painel do inspetor, clique na guia **[!UICONTROL Network]**.
1. Atualize a página.
1. Role até a parte superior do painel do inspetor para que você possa ver o URL da página que está visualizando.

   A figura a seguir mostra um exemplo de carregamento da página de índice `magento2`.

   ![Clique na página que você está visualizando](../../assets/configuration/varnish-inspector.png)

   O tempo de carregamento da página é exibido ao lado do URL da página. Nesse caso, o tempo de carga é de 5 ms. Isso ajuda a confirmar se o Varnish armazenou a página em cache.

1. Para exibir cabeçalhos HTTP de resposta, clique no URL da página (na coluna Name ).

   Você pode exibir cabeçalhos HTTP discutidos com mais detalhes na seção Verificar cabeçalhos de resposta HTTP.

## Verificar o cache do Commerce

Verifique se o diretório `<magento_root>/var/page_cache` está vazio:

1. Faça logon no servidor do Commerce ou alterne para o proprietário do sistema de arquivos.
1. Digite o seguinte comando:

   ```bash
   rm -rf <magento_root>/var/page_cache/*
   ```

1. Acesse uma ou mais páginas do Commerce que podem ser armazenadas em cache.
1. Verifique o diretório `var/page_cache/`.

   Se o diretório estiver vazio, parabéns! Você configurou com sucesso o Varnish e o Commerce para trabalharem juntos!

1. Se você limpou o diretório `var/page_cache/`, reinicie o Verniz.

>[!TIP]
>
>Se você encontrar erros 503 (Falha na busca de backend), consulte [Solução de problemas 503 (Serviço indisponível) erros](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshooting-503-errors.html) na _Central de Ajuda da Adobe Commerce_.
