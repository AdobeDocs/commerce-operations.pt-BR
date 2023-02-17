---
title: Configurar o criador de perfis do banco de dados
description: Veja um exemplo de como configurar a saída para o criador de perfis do banco de dados.
badge: label="Contribuído por Goswami em Abritânico" type="Informative" url="https://github.com/atishgoswami" tooltip="Goswami em Atiche"
source-git-commit: bcb995ea417423b0cbc59c035ba5fdedbce3310e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configurar o criador de perfis do banco de dados

O criador de perfil do banco de dados do Commerce exibe todas as consultas implementadas em uma página, incluindo o tempo de cada query e quais parâmetros foram aplicados.

## Etapa 1: Modificar a configuração da implantação

Modificar `<magento_root>/app/etc/env.php` para adicionar a seguinte referência ao [classe profiler do banco de dados](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php):

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Um exemplo:

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

## Etapa 2: Configurar a saída

Configure a saída no arquivo de inicialização do aplicativo Commerce; isso pode ser `<magento_root>/pub/index.php` ou pode estar localizado em uma configuração de host virtual do servidor da Web.

O exemplo a seguir exibe resultados em uma tabela de três colunas:

- Tempo total (exibe a quantidade total de tempo para executar todas as consultas na página)
- SQL (exibe todas as consultas SQL; o cabeçalho da linha exibe a contagem de queries)
- Params de Consulta (exibe os parâmetros de cada consulta SQL)

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

## Etapa 3: Visualizar os resultados

Acesse qualquer página da loja ou do Administrador para visualizar os resultados. Uma amostra:

![Resultados do perfil do banco de dados de exemplo](../../assets/configuration/db-profiler-results.png)
