---
title: Importar dados de arquivos de configuração
description: Importe as definições de configuração do Adobe Commerce dos arquivos de configuração.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Importar definições de configuração

{{file-system-owner}}

Ao configurar um sistema de produção usando o [modelo de implantação de pipeline](../deployment/technical-details.md) do Commerce 2.2, você deve _importar_ as configurações de `config.php` e `env.php` para o banco de dados.
Essas configurações incluem caminhos e valores de configuração, sites, lojas, visualizações de loja e temas.

Após importar sites, lojas, visualizações de loja e temas, você pode criar atributos de produto e aplicá-los a sites, lojas e visualizações de loja no sistema de produção.

>[!INFO]
>
>O comando `bin/magento app:config:import` não processa a configuração armazenada em variáveis de ambiente.

## Importar comando

No sistema de produção, execute o seguinte comando para importar dados dos arquivos de configuração (`config.php` e `env.php`) para o banco de dados:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Use o sinalizador `[-n, --no-interaction]` opcional para importar dados sem nenhuma interação.

Se você inserir `bin/magento app:config:import` sem o sinalizador opcional, será necessário confirmar as alterações.

Por exemplo, se o arquivo de configuração contiver um novo site e um novo armazenamento, a seguinte mensagem será exibida:

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Para continuar a importação, insira `yes`.

Se os arquivos de configuração de implantação contiverem alguns dados a serem importados, uma mensagem semelhante à seguinte será exibida:

```
Start import:
Some information about importing
```

Se os arquivos de configuração de implantação não contiverem dados a serem importados, uma mensagem semelhante à seguinte será exibida:

```
Start import:
Nothing to import
```

## O que importamos

As seções a seguir discutem detalhadamente quais dados são importados.

### Configuração do sistema

O Commerce usa valores diretamente na matriz `system` nos arquivos `config.php` ou `env.php`, em vez de importá-los para o banco de dados, pois eles exigem algumas ações pré e pós-processamento.

Por exemplo, o valor do caminho de configuração `web/secure/base_url` deve ser validado com modelos de back-end.

#### Modelos de back-end

Os modelos de back-end são o mecanismo para processar alterações na configuração do sistema.
Você define módulos de back-end em `<module_name>/adminhtml/system.xml`.

Todos os modelos de back-end devem estender a classe [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php).

Quando importamos modelos de back-end, não salvamos os valores de configuração.

### Configuração de sites, lojas e grupos de lojas

Importamos os seguintes tipos de configurações.
(Essas configurações estão na matriz `scopes` em `config.php`.)

- `websites`: configuração relacionada a sites
- `groups`: armazena configuração relacionada
- `stores`: configurações relacionadas às exibições de armazenamento

As configurações anteriores podem ser importadas nos seguintes modos:

- `create`: `config.php` contém novas entidades (`websites`, `groups`, `stores`) que estão ausentes no ambiente de produção
- `update`: `config.php` contém entidades (`websites`, `groups`, `stores`) diferentes do ambiente de produção
- `delete`: `config.php` _não_ contém entidades (`websites`, `groups`, `stores`) presentes no ambiente de produção

>[!INFO]
>
>Não importamos a categoria raiz associada aos armazenamentos. Você deve associar uma categoria raiz a um armazenamento usando o Administrador do Commerce.

### Configuração do tema

A configuração de tema inclui todos os temas registrados em seu sistema Commerce; os dados vêm diretamente da tabela de banco de dados `theme`. (A configuração do tema está na matriz `themes` em `config.php`.)

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
>- _Registro de tema_. Se dados de um tema forem definidos em `config.php`, mas o código-fonte do tema não estiver presente no sistema de arquivos, o tema será ignorado (ou seja, não será registrado).
>- _Remoção do tema_. Se um tema não estiver presente em `config.php`, mas o código-fonte estiver presente no sistema de arquivos, o tema não será removido.
