---
title: Estratégias de implantação para arquivos de visualização estáticos
description: Saiba mais sobre as estratégias de implantação para arquivos de exibição estáticos em aplicativos do Adobe Commerce. Descubra os melhores métodos de implantação para diferentes casos de uso.
feature: Configuration, Deploy, Extensions
exl-id: 12ebbd36-f813-494f-9515-54ce697ca2e4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Estratégias de implantação para arquivos de visualização estáticos

Ao implantar arquivos de visualização estáticos, você pode escolher uma das três estratégias disponíveis. Cada uma delas fornece resultados ideais de implantação para diferentes casos de uso:

- [Standard](#standard-strategy): o processo de implantação normal.
- [Rápido](#quick-strategy) (_padrão_): minimiza o tempo necessário para implantação quando os arquivos de mais de uma localidade são implantados.
- [Compacto](#compact-strategy): minimiza o espaço ocupado pelos arquivos de exibição publicados.

As seções a seguir descrevem os detalhes e os recursos de implementação de cada estratégia.

## Estratégia padrão

Quando a estratégia Padrão é usada, todos os arquivos de exibição estáticos de todos os pacotes são implantados, ou seja, processados por [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Para obter mais informações, consulte [Implantar arquivos de exibição estáticos](../cli/static-view-file-deployment.md).

## Estratégia rápida

A estratégia rápida executa as seguintes ações:

1. Para cada tema, um local arbitrário é escolhido e todos os arquivos para esse local são implantados, como na estratégia padrão.
1. Para todas as outras localidades do tema:

   1. Os arquivos que substituem o local implantado são definidos e implantados.
   1. Todos os outros arquivos são considerados semelhantes para todas as localidades e são copiados da localidade implantada.

>[!INFO]
>
>Por _semelhante_, queremos dizer arquivos que são independentes da localidade, tema ou área. Esses arquivos podem incluir CSS, imagens e fontes.

Essa abordagem minimiza o tempo de implantação necessário para várias localidades, embora muitos arquivos sejam duplicados.

## Estratégia compacta

A estratégia compacta evita a duplicação de arquivos armazenando arquivos semelhantes em subdiretórios `base`.

Para o resultado mais otimizado, três escopos para possível similaridade são alocados: área, tema e localidade. Os subdiretórios `base` são criados para todas as combinações desses escopos.

Os arquivos são implantados nesses subdiretórios de acordo com os padrões a seguir.

| Padrão | Descrição |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Arquivos específicos para uma determinada área, tema e localidade |
| `<area>/<theme>/default` | Arquivos semelhantes para todas as localidades de um tema específico de uma área específica. |
| `<area>/Magento/base/<locale>` | Arquivos específicos para uma área e localidade específicas, mas semelhantes para todos os temas. |
| `<area>/Magento/base/default` | Arquivos específicos para uma área específica, mas semelhantes para todos os temas e localidades. |
| `base/Magento/base/<locale>` | Arquivos semelhantes para todas as áreas e temas, mas específicos para uma localidade específica. |
| `base/Magento/base/default` | Semelhante para todas as áreas, temas e localidades. |

### Mapeamento de arquivos implantados

A abordagem de implantação usada na estratégia compacta significa que os arquivos são herdados de temas básicos e localidades. Essas relações de herança são armazenadas nos arquivos de mapa para cada combinação de área, tema e localidade. Existem arquivos de mapa separados para PHP e JS:

- `map.php`
- `requirejs-map.js`

O arquivo `map.php` é usado por [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) para criar URLs corretas.

O `requirejs-map.js` é usado pelo plug-in `baseUrlResolver` para RequireJS.

Exemplo de `map.php`:

```php?start_inline=1
return [
    'Magento_Checkout::cvv.png' => [
        'area' => 'frontend',
        'theme' => 'Magento/luma',
        'locale' => 'en_US',
    ],
    '...' => [
        'area' => '...',
        'theme' => '...',
        'locale' => '...'
    ]
];
```

Exemplo de `requirejs-map.js`:

```js
require.config({
    "config": {
       "baseUrlInterceptor": {
            "jquery.js": "../../../../base/Magento/base/en_US/"
        }
    }
});
```

## Dicas para desenvolvedores de extensão

Para criar URLs para arquivos de exibição estáticos, use [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Não use concatenações de URL para evitar problemas com arquivos estáticos que não são encontrados e exibidos durante a renderização da página.
