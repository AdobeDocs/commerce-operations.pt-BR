---
title: Configurar o profiler do banco de dados
description: Consulte um exemplo de como configurar a saída para o profiler do banco de dados.
badge: label="Contribuição de Atish Goswami" type="Informativo" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Configurar o profiler do banco de dados

O criador de perfil do banco de dados do Commerce exibe todas as consultas implementadas em uma página, incluindo o tempo para cada consulta e quais parâmetros foram aplicados.

## Etapa 1: Modificar a configuração de implantação

Modificar `<magento_root>/app/etc/env.php` para adicionar a seguinte referência à [classe profiler do banco de dados](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

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

Configure a saída no arquivo de inicialização do aplicativo do Commerce. Pode ser `<magento_root>/pub/index.php` ou ele pode estar localizado em uma configuração de host virtual do servidor da web.

O exemplo a seguir exibe resultados em uma tabela de três colunas:

- Tempo total (exibe o tempo total para executar todas as consultas na página)
- SQL (exibe todas as consultas SQL; o cabeçalho da linha exibe a contagem de consultas)
- Parâmetros de consulta (exibe os parâmetros de cada consulta SQL)

Para configurar a saída, adicione o seguinte após a variável `$bootstrap->run($app);` no arquivo de inicialização:

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

![Resultados do criador de perfil de banco de dados de exemplo](../../assets/configuration/db-profiler-results.png)
