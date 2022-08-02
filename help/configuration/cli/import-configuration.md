---
title: Importar dados de arquivos de configuração
description: Importe as configurações do Adobe Commerce dos arquivos de configuração.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# Importar configurações

{{file-system-owner}}

Ao configurar um sistema de produção usando o Commerce 2.2 [modelo de implantação de pipeline](../deployment/technical-details.md), você deve _importar_ configurações de `config.php` e `env.php` no banco de dados.
Essas configurações incluem caminhos e valores de configuração, sites, lojas, visualizações de loja e temas.

Após importar sites, lojas, visualizações de loja e temas, é possível criar atributos de produto e aplicá-los a sites, lojas e visualizações de loja no sistema de produção.

>[!INFO]
>
>O `bin/magento app:config:import` O comando não processa a configuração armazenada nas variáveis de ambiente.

## comando Importar

No sistema de produção, execute o seguinte comando para importar dados dos arquivos de configuração (`config.php` e `env.php`) ao banco de dados:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Use o `[-n, --no-interaction]` sinalizador para importar dados sem qualquer interação.

Se você inserir `bin/magento app:config:import` sem o sinalizador opcional, é necessário confirmar as alterações.

Por exemplo, se o arquivo de configuração contiver um novo site e uma nova loja, a seguinte mensagem será exibida:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar a importação, insira `yes`.

Se os arquivos de configuração de implantação contiverem alguns dados para importar, uma mensagem semelhante à seguinte será exibida:

```terminal
Start import:
Some information about importing
```

Se os arquivos de configuração de implantação não contiverem dados para importar, uma mensagem semelhante à seguinte será exibida:

```terminal
Start import:
Nothing to import
```

## O que importamos

As seções a seguir discutem detalhadamente quais dados importamos.

### Configuração do sistema

O Commerce usa diretamente os valores na `system` no `config.php` ou `env.php` arquivos em vez de importá-los para o banco de dados, pois exigem algumas ações de pré e pós-processamento.

Por exemplo, o valor do caminho de configuração `web/secure/base_url` deve ser validado com [backend](https://glossary.magento.com/backend) modelos.

#### Modelos de backend

Modelos de backend são o mecanismo de processamento de alterações na configuração do sistema.
Você define módulos de backend em `<module_name>/adminhtml/system.xml`.

Todos os modelos de back-end devem estender o [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) classe .

Quando importamos modelos de backend, não salvamos os valores de configuração.

### Configuração de sites, lojas e grupos de loja

Importamos os seguintes tipos de configurações.
(Essas configurações estão na seção `scopes` array em `config.php`.)

- `websites`: configuração relacionada a sites
- `groups`: armazena configuração relacionada
- `stores`: configuração relacionada às visualizações de loja

As configurações anteriores podem ser importadas nos seguintes modos:

- `create`: `config.php` contém novas entidades (`websites`, `groups`, `stores`) que estão ausentes no ambiente de produção
- `update`: `config.php` contém entidades (`websites`, `groups`, `stores`) que são diferentes do ambiente de produção
- `delete`: `config.php` does _not_ contêm entidades (`websites`, `groups`, `stores`) que estão presentes no ambiente de produção

>[!INFO]
>
>Não importamos a raiz [categoria](https://glossary.magento.com/category) associado a lojas. Você deve associar uma categoria raiz a uma loja usando o Commerce [Administrador](https://glossary.magento.com/admin).

### Configuração do tema

A configuração de tema inclui todos os temas registrados em seu sistema de Comércio; os dados vêm diretamente do `theme` tabela de banco de dados. (A configuração de tema está no `themes` array em `config.php`.)

#### Estrutura dos dados temáticos

A chave do array é o caminho completo do tema: `area` + `theme path`

Por exemplo, `frontend/Magento/luma`.
`frontend` é área e `Magento/luma` é [tema](https://glossary.magento.com/theme) caminho.

O valor da matriz são dados sobre tema: código, título, caminho, id principal

Exemplo completo:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Registro do tema_. Se os dados de tema forem definidos em `config.php` mas o código-fonte do tema não está presente no sistema de arquivos, o tema é ignorado (ou seja, não registrado).
>- _Remoção de tema_. Se um tema não estiver presente em `config.php` mas o código-fonte está presente no sistema de arquivos, o tema não é removido.

