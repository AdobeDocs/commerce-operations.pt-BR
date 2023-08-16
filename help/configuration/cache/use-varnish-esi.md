---
title: Bloco ESI de verniz
description: Saiba mais sobre as Inclusões do Edge Side e como você pode usá-las para incorporar páginas da Web.
badge: label="Contribuição de Constantino G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G"
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Bloco ESI de verniz

ESI (Edge Side Includes) são diretivas especiais que você pode usar para incluir páginas da Web em outras páginas da Web.

Um exemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Verniz busca conteúdo de `http://domain.com/index.php/page_cache/block/esi/blocks` e substitua o `<esi>` com ele.

## ESI do Commerce e do Vernish

A estrutura de comércio cria uma tag ESI quando as seguintes condições são atendidas:

- O aplicativo de armazenamento em cache está definido como `Varnish Cache`
- Um layout XML `block` elemento é adicionado com um `ttl` atributo

### Exemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

No exemplo acima, a variável `block` elemento adiciona conteúdo do `esi.phtml` O modelo de para uma página inicial e o Vernish o atualiza automaticamente a cada 30 segundos.

## Limitação

Atualmente, o Verniz não é compatível com ESI em HTTPS, portanto, ele muda automaticamente para HTTP.

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
