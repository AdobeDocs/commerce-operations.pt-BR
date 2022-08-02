---
title: Estratégias de implantação para arquivos de visualização estática
description: Leia sobre as estratégias de implantação do aplicativo Commerce.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Estratégias de implantação para arquivos de visualização estática

Ao implantar arquivos de visualização estáticos, você pode escolher uma das três estratégias disponíveis. Cada um deles fornece os melhores resultados de implantação para diferentes casos de uso:

- [Padrão](#standard-strategy): o processo de implantação regular.
- [Rápido](#quick-strategy) (_default_): minimiza o tempo necessário para a implantação quando os arquivos de mais de uma localidade forem implantados.
- [Compacto](#compact-strategy): minimiza o espaço ocupado pelos arquivos de visualização publicados.

As seções a seguir descrevem os detalhes e os recursos de implementação de cada estratégia.

## Estratégia-padrão

Quando a Estratégia padrão é usada, todos os arquivos de visualização estática para todos os pacotes são implantados, ou seja, processados por [`\Magento\Framework\App\View\Asset\Publisher`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/View/Asset/Publisher.php).

Para obter mais informações, consulte [Implantar arquivos de visualização estáticos](../cli/static-view-file-deployment.md).

## Estratégia rápida

A estratégia rápida executa as seguintes ações:

1. Para cada tema, uma localidade arbitrária é escolhida e todos os arquivos dessa localidade são implantados, como na estratégia padrão.
1. Para todas as outras localidades do tema:

   1. Os arquivos que substituem o local implantado são definidos e implantados.
   1. Todos os outros arquivos são considerados semelhantes para todas as localidades e são copiados do local implantado.

>[!INFO]
>
>Por _semelhante_, queremos dizer arquivos que são independentes da localidade, tema ou área. Esses arquivos podem incluir CSS, imagens e fontes.

Essa abordagem minimiza o tempo de implantação necessário para várias localidades, embora muitos arquivos estejam duplicados.

## Estratégia compacta

A estratégia compacta evita a duplicação de arquivos armazenando arquivos semelhantes em `base` subdiretórios.

Para o resultado mais otimizado, três escopos para possível similaridade são alocados: área, tema e localidade. O `base` subdiretórios são criados para todas as combinações desses escopos.

Os arquivos são implantados nesses subdiretórios de acordo com os seguintes padrões.

| Padrão | Descrição |
| ------- | ----------- |
| `<area>/<theme>/<locale>` | Arquivos específicos para uma área, tema e localidade específicos |
| `<area>/<theme>/default` | Arquivos semelhantes para todas as localidades de um tema específico de uma área específica. |
| `<area>/Magento/base/<locale>` | Arquivos específicos para uma área específica e local, mas semelhantes para todos os temas. |
| `<area>/Magento/base/default` | Arquivos específicos para uma área específica, mas semelhantes para todos os temas e localidades. |
| `base/Magento/base/<locale>` | Arquivos semelhantes para todas as áreas e temas, mas específicos a uma localidade específica. |
| `base/Magento/base/default` | Semelhante para todas as áreas, temas e localidades. |

### Mapeamento de arquivos implantados

A abordagem à implantação usada na estratégia compacta significa que os arquivos são herdados de temas e localidades de base. Essas relações de herança são armazenadas nos arquivos de mapa para cada combinação de área, tema e localidade. Há arquivos de mapa separados para PHP e JS:

- `map.php`
- `requirejs-map.js`

O `map.php` arquivo é usado por [`Magento\Framework\View\Asset\Repository`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php) para criar URLs corretos.

O `requirejs-map.js` é usada pelo `baseUrlResolver` plug-in para RequireJS.

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

Para criar URLs para arquivos de visualização estáticos, use [`\Magento\Framework\View\Asset\Repository::createAsset()`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Asset/Repository.php#L211-L244).

Não use concatenações de URL para evitar problemas com arquivos estáticos que não são encontrados e não são exibidos durante a renderização da página.
