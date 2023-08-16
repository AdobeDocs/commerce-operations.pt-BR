---
title: Importar dados de arquivos de configuração
description: Importe as definições de configuração do Adobe Commerce dos arquivos de configuração.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Importar definições de configuração

{{file-system-owner}}

Ao configurar um sistema de produção usando o Commerce 2.2 [modelo de implantação de pipeline](../deployment/technical-details.md), você deve _importar_ definições de configuração de `config.php` e `env.php` no banco de dados.
Essas configurações incluem caminhos e valores de configuração, sites, lojas, visualizações de loja e temas.

Após importar sites, lojas, visualizações de loja e temas, você pode criar atributos de produto e aplicá-los a sites, lojas e visualizações de loja no sistema de produção.

>[!INFO]
>
>A variável `bin/magento app:config:import` O comando não processa a configuração armazenada em variáveis de ambiente.

## Importar comando

No sistema de produção, execute o seguinte comando para importar dados dos arquivos de configuração (`config.php` e `env.php`) ao banco de dados:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Use o opcional `[-n, --no-interaction]` sinalizador para importar dados sem qualquer interação.

Se você inserir `bin/magento app:config:import` sem o sinalizador opcional, é necessário confirmar as alterações.

Por exemplo, se o arquivo de configuração contiver um novo site e um novo armazenamento, a seguinte mensagem será exibida:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar a importação, insira `yes`.

Se os arquivos de configuração de implantação contiverem alguns dados a serem importados, uma mensagem semelhante à seguinte será exibida:

```terminal
Start import:
Some information about importing
```

Se os arquivos de configuração de implantação não contiverem dados a serem importados, uma mensagem semelhante à seguinte será exibida:

```terminal
Start import:
Nothing to import
```

## O que importamos

As seções a seguir discutem detalhadamente quais dados são importados.

### Configuração do sistema

O Commerce usa valores diretamente na variável `system` matriz no `config.php` ou `env.php` arquivos, em vez de importá-los para o banco de dados, porque exigem algumas ações pré e pós-processamento.

Por exemplo, o valor do caminho de configuração `web/secure/base_url` deve ser validado com modelos de back-end.

#### Modelos de back-end

Os modelos de back-end são o mecanismo para processar alterações na configuração do sistema.
Os módulos de back-end são definidos em `<module_name>/adminhtml/system.xml`.

Todos os modelos de back-end devem estender a variável [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) classe.

Quando importamos modelos de back-end, não salvamos os valores de configuração.

### Configuração de sites, lojas e grupos de lojas

Importamos os seguintes tipos de configurações.
(Essas configurações estão sob o `scopes` matriz em `config.php`.)

- `websites`: configuração relacionada a sites
- `groups`: armazena configurações relacionadas
- `stores`: configuração relacionada às exibições de loja

As configurações anteriores podem ser importadas nos seguintes modos:

- `create`: `config.php` contém novas entidades (`websites`, `groups`, `stores`) que estão ausentes no ambiente de produção
- `update`: `config.php` contém entidades (`websites`, `groups`, `stores`) que são diferentes do ambiente de produção
- `delete`: `config.php` faz _não_ contém entidades (`websites`, `groups`, `stores`) presentes no ambiente de produção

>[!INFO]
>
>Não importamos a categoria raiz associada aos armazenamentos. Você deve associar uma categoria raiz a uma loja usando o Administrador do Commerce.

### Configuração do tema

A configuração de tema inclui todos os temas registrados no sistema do Commerce; os dados vêm diretamente do `theme` tabela de banco de dados. (A configuração de tema está no `themes` matriz em `config.php`.)

#### Estrutura dos dados do tema

A chave da matriz é o caminho completo do tema: `area` + `theme path`

Por exemplo, `frontend/Magento/luma`.
`frontend` é a área e `Magento/luma` é o caminho do tema.

O valor da matriz são os dados sobre o tema: código, título, caminho, id principal

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
>- _Registro de tema_. Se os dados de um tema forem definidos em `config.php` mas o código-fonte do tema não estiver presente no sistema de arquivos, o tema será ignorado (ou seja, não será registrado).
>- _Remoção do tema_. Se um tema não estiver presente no `config.php` mas o código-fonte estiver presente no sistema de arquivos, o tema não será removido.
