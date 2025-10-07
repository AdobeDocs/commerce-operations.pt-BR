---
title: Bloco ESI de verniz
description: Saiba mais sobre as ESI (Varnish Edge Side Includes) e como incorporar páginas da Web para o Adobe Commerce. Descubra a implementação e otimização de blocos ESI.
badge: label="Contribuição de Constantino G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G"
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Bloco ESI de verniz

As ESI (Edge Side Includes) são diretivas especiais que podem ser usadas para incluir páginas da Web em outras páginas da Web.

Um exemplo:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

O verniz busca conteúdo de `http://domain.com/index.php/page_cache/block/esi/blocks` e substitui a marca `<esi>` por ela.

## ESI do Commerce e do verniz

A estrutura do Commerce cria uma tag ESI quando as seguintes condições são atendidas:

- O aplicativo de cache está definido como `Varnish Cache`
- Um elemento `block` do layout XML é adicionado com um atributo `ttl`

### Exemplo

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

No exemplo acima, o elemento `block` adiciona conteúdo do modelo `esi.phtml` a uma página inicial e o Verniz o atualiza automaticamente a cada 30 segundos.

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
