---
title: Configurar o profiler do banco de dados
description: Consulte um exemplo de como configurar a saída para o profiler do banco de dados.
feature: Configuration, Storage
badge: label="Contribuição de Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%
---
# Configurar o profiler do banco de dados

O profiler do banco de dados do Commerce exibe todas as consultas implementadas em uma página, incluindo o tempo para cada consulta e quais parâmetros foram aplicados.

## Etapa 1: Modificar a configuração de implantação

Modifique `<magento_root>/app/etc/env.php` para adicionar a seguinte referência à [classe do criador de perfil do banco de dados](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Um exemplo é o seguinte:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Etapa 2: configurar a saída

Configure a saída no arquivo de inicialização do aplicativo Commerce; pode ser `<magento_root>/pub/index.php` ou pode estar localizado em uma configuração de host virtual de servidor Web.

O exemplo a seguir exibe resultados em uma tabela de três colunas:

- Tempo total (exibe o tempo total para executar todas as consultas na página)
- SQL (exibe todas as consultas SQL; o cabeçalho da linha exibe a contagem de consultas)
- Parâmetros de consulta (exibe os parâmetros de cada consulta SQL)

Para configurar a saída, adicione o seguinte após a linha `$bootstrap->run($app);` no arquivo de inicialização:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Etapa 3: exibir os resultados

Vá para qualquer página na loja ou no Administrador para visualizar os resultados. A seguir, há uma amostra:

![Resultados do criador de perfil do banco de dados de exemplo](../../assets/configuration/db-profiler-results.png)
