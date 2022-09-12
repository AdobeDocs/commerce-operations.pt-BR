---
title: Gerenciar o cache
description: Gerencie os tipos de cache e exiba o status do cache.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Gerenciar o cache

{{file-system-owner}}

## Tipos de cache

O Commerce 2 tem os seguintes tipos de cache:

| Nome &quot;amigável&quot; do tipo de cache | Nome do código do tipo de cache | Descrição |
|--- |--- |--- |
| Configuração | configuração | O Commerce coleta a configuração de todos os módulos, a mescla e salva o resultado mesclado no cache. Esse cache também contém configurações específicas do armazenamento armazenadas no sistema de arquivos e no banco de dados. Limpe ou libere esse tipo de cache após modificar os arquivos de configuração. |
| Layout | layout | Layouts de página compilados (ou seja, os componentes de layout de todos os componentes). Limpe ou libere esse tipo de cache após modificar os arquivos de layout. |
| Bloquear saída HTML | block_html | Fragmentos de HTML page por bloco. Limpe ou libere esse tipo de cache após modificar a camada de exibição. |
| Dados de coleções | coleções | Resultados de consultas de banco de dados. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou libere esse tipo de cache se o seu módulo personalizado usar uma lógica que resulte em entradas de cache que o Commerce não pode limpar. |
| DDL | db_ddl | Schema do banco de dados. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou libere esse tipo de cache depois de fazer alterações personalizadas no esquema do banco de dados. (Em outras palavras, atualizações que o Commerce não faz a si mesmo.) Uma maneira de atualizar o schema do banco de dados automaticamente é usando o `magento setup:db-schema:upgrade` comando. |
| Configuração compilada | collected_config | Configuração de compilação |
| Valor do atributo da entidade (EAV) | eav | Metadados relacionados a atributos EAV (por exemplo, rótulos de armazenamento, links para o código PHP relacionado, renderização de atributo, configurações de pesquisa e assim por diante). Geralmente, não é necessário limpar ou liberar esse tipo de cache. |
| Cache de página | full_page | Páginas HTML geradas. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou libere esse tipo de cache após modificar o nível de código que afeta a saída do HTML. É recomendável manter esse cache ativado, pois o HTML de armazenamento em cache melhora significativamente o desempenho. |
| Reflexo | reflexão | Remove uma dependência entre o módulo Webapi e o módulo Cliente. |
| Traduções | tradução | Após mesclar traduções de todos os módulos, o cache de mesclagem será limpo. |
| Configuração da integração | config_integration | Integrações compiladas. Limpe ou libere esse cache após alterar ou adicionar integrações. |
| Configuração da API de integração | config_integration_api | Configuração das APIs de integração compiladas das Integrações da loja. |
| Configuração de serviços da Web | config_webservice | Armazenamento em cache da estrutura da API da Web. |
| Notificação do cliente | customer_notification | Notificações temporárias que aparecem na interface do usuário. |

## Visualizar o status do cache

Para exibir o status do cache, insira

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

Uma amostra:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## Ativar ou desativar tipos de cache

Este comando permite habilitar ou desabilitar todos os tipos de cache ou somente aqueles especificados. Desativar os tipos de cache é útil durante o desenvolvimento porque você vê os resultados de suas alterações sem precisar liberar o cache; no entanto, a desativação dos tipos de cache tem um efeito adverso no desempenho.

>[!INFO]
>
>A partir da versão 2.2, você só poderá ativar ou desativar os tipos de cache usando a linha de comando ao executar o Commerce no modo de produção. Se o Commerce estiver sendo executado no modo desenvolvedor, é possível ativar ou desativar os tipos de cache usando a linha de comando ou manualmente. Antes de fazer isso, você deve fazer manualmente `<magento_root>/app/etc/env.php` gravável pelo [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

Você pode limpar (também conhecido como _liberação_ ou _atualizar_) tipos de cache usando a linha de comando ou o Administrador.

Opções de comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Em que omissão `[type]` ativa ou desativa todos os tipos de cache ao mesmo tempo. O `type` é uma lista separada por espaços de tipos de cache.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Para listar os tipos de cache e seus status:

```bash
bin/magento cache:status
```

Por exemplo, para desativar o cache de página completo e o cache DDL:

```bash
bin/magento cache:disable db_ddl full_page
```

Exemplo de resultado:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Habilitar um tipo de cache limpa automaticamente esse tipo de cache.

>[!INFO]
>
>A partir da versão 2.3.4, o Commerce armazena em cache todos os atributos EAV do sistema conforme são recuperados. O armazenamento em cache de atributos EAV dessa maneira melhora o desempenho, pois diminui a quantidade de solicitações de inserção/seleção no banco de dados. No entanto, também aumenta o tamanho da rede de cache. Os desenvolvedores podem armazenar em cache atributos EAV personalizados executando o `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Isso também pode ser feito pelo Administrador enquanto em [Modo de desenvolvedor](../bootstrap/application-modes.md) ao configurar **Lojas** > Configurações **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de armazenamento em cache** > **Atributos Definidos pelo Usuário do Cache** para **Sim**.

## Limpar e liberar tipos de cache

Para limpar itens desatualizados do cache, você pode _limpar_ ou _liberação_ tipos de cache:

- A limpeza de um tipo de cache exclui todos os itens somente dos tipos de cache ativados do Commerce. Em outras palavras, essa opção não afeta outros processos ou aplicativos porque limpa somente o cache que o Commerce usa.

   Os tipos de cache desativados não são limpos.

   >[!TIP]
   >
   >Sempre limpe o cache após atualizar as versões do Magento Open Source ou Adobe Commerce, atualizar do Magento Open Source para o Adobe Commerce ou instalar o B2B para Adobe Commerce ou qualquer módulo.

- A liberação de um tipo de cache limpa o armazenamento de cache, o que pode afetar outros processos que estão usando o mesmo armazenamento.

Limpe os tipos de cache se já tiver tentado limpar o cache e ainda houver problemas que não possam ser isolados.

Uso do comando:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Onde `[type]` é uma lista separada por espaços de tipos de cache. Omissão `[type]` limpa ou libera todos os tipos de cache ao mesmo tempo. Por exemplo, para liberar todos os tipos de cache, insira

```bash
   bin/magento cache:flush
```

Exemplo de resultado:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>Você também pode limpar e liberar tipos de cache no Administrador. Ir para **Sistema** > **Ferramentas** > **Gerenciamento de cache**. **Armazenamento do Cache de Liberação** é equivalente a `bin/magento cache:flush`. **Liberar cache Magento** é equivalente a `bin/magento cache:clean`.
