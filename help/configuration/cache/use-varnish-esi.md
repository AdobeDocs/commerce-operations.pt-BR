---
title: Bloco ESI Varno
description: Saiba mais sobre os Edge Side Includes e como você pode usá-los para incorporar páginas da Web.
contributor_name: Goivvy LLC
contributor_link: https://www.goivvy.com/magento-optimization-service
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---


# Bloco ESI Varno

Edge Side Includes (ESI) são diretivas especiais que podem ser usadas para incluir páginas da Web em outras páginas da Web.

Um exemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

O Varnish busca conteúdo de `http://domain.com/index.php/page_cache/block/esi/blocks` e substitua o `<esi>` com ele.

## Comércio e ESI Varna

A estrutura Commerce cria uma tag ESI quando as seguintes condições são atendidas:

- O aplicativo de armazenamento em cache está definido como `Varnish Cache`
- Um layout XML `block` é adicionado com um `ttl` atributo

### Exemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

No exemplo acima, a variável `block` elemento adiciona conteúdo do `esi.phtml` modelo para uma página inicial e a Varnish a atualiza automaticamente a cada 30 segundos.

## Limitações

Atualmente, a Varnish não oferece suporte a ESI por HTTPS, portanto, ela muda automaticamente para HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
