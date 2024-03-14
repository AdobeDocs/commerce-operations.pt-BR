---
title: Gerenciar o cache
description: Gerenciar tipos de cache e exibir status do cache.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 6e0e7f209b265e5b924e0092fec020e0cefc165d
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# Gerenciar o cache

{{file-system-owner}}

## Tipos de cache

O Commerce tem os seguintes tipos de cache:

| Nome &quot;amigável&quot; do tipo de cache | Nome do código do tipo de cache | Descrição |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Configuração | config | O Commerce coleta a configuração de todos os módulos, mescla-a e salva o resultado mesclado no cache. Esse cache também contém configurações específicas do armazenamento armazenadas no sistema de arquivos e no banco de dados. Limpar ou liberar esse tipo de cache após modificar os arquivos de configuração. |
| Layout | layout | Layouts de página compilados (ou seja, os componentes de layout de todos os componentes). Limpar ou liberar este tipo de cache após modificar arquivos de layout. |
| Bloquear saída de HTML | block_html | HTML fragmentos de página por bloco. Limpe ou limpe esse tipo de cache após modificar a camada de exibição. |
| Dados das coleções | coleções | Resultados de consultas ao banco de dados. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou limpe esse tipo de cache se o módulo personalizado usar uma lógica que resulte em entradas de cache que o Commerce não pode limpar. |
| DDL | db_ddl | Esquema de banco de dados. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou limpe esse tipo de cache depois de fazer alterações personalizadas no esquema do banco de dados. (Em outras palavras, atualizações que o Commerce não cria.) Uma maneira de atualizar o esquema do banco de dados automaticamente é usando o `magento setup:db-schema:upgrade` comando. |
| Configuração compilada | compilation_config | Configuração de compilação |
| Valor do atributo de entidade (EAV) | eav | Metadados relacionados a atributos EAV (por exemplo, rótulos de armazenamento, links para código PHP relacionado, renderização de atributo, configurações de pesquisa e assim por diante). Normalmente, não é necessário limpar ou liberar esse tipo de cache. |
| Cache de página | full_page | Páginas de HTML geradas. Se necessário, o Commerce limpa esse cache automaticamente, mas desenvolvedores de terceiros podem colocar quaisquer dados em qualquer segmento do cache. Limpe ou limpe esse tipo de cache após modificar o nível de código que afeta a saída de HTML. É recomendável manter esse cache habilitado, pois o HTML de cache melhora significativamente o desempenho. |
| Reflexo | reflexão | Remove uma dependência entre o módulo Webapi e o módulo Cliente. |
| Traduções | traduzir | Depois de mesclar as traduções de todos os módulos, o cache de fusão será limpo. |
| Configuração de integração | config_integration | Integrações compiladas. Limpe ou limpe esse cache após alterar ou adicionar integrações. |
| Configuração da API de integração | config_integration_api | Configuração das APIs de integração compiladas das integrações da loja. |
| Resultados do GraphQL Query Resolver [!BADGE 2.4.7-beta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Disponível somente na versão 2.4.7-beta"} | graphql_query_resolver_result | Armazena em cache os resultados dos resolvedores de consultas do GraphQL para entidades de galeria de mídia de clientes, páginas do CMS, blocos do CMS e produtos. Mantenha esse cache ativado para melhorar o desempenho do GraphQL. |
| Configuração de serviços da Web | config_webservice | Armazenamento em cache da estrutura da API da Web. |
| Notificação de Cliente | customer_notification | Notificações temporárias exibidas na interface do usuário. |

## Exibir o status do cache

Para exibir o status do cache, informe

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

A seguir, há uma amostra:

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
 graphql_query_resolver_result: 1
             config_webservice: 1
                     translate: 1
```

## Habilitar ou desabilitar tipos de cache

Esse comando permite habilitar ou desabilitar todos os tipos de cache ou apenas os que você especificar. A desativação dos tipos de cache é útil durante o desenvolvimento, pois você vê os resultados de suas alterações sem ter que liberar o cache; no entanto, a desativação dos tipos de cache tem um efeito adverso no desempenho.

>[!INFO]
>
>A partir da versão 2.2, você só poderá ativar ou desativar os tipos de cache usando a linha de comando ao executar o Commerce no modo de produção. Se estiver executando o Commerce no modo de desenvolvedor, você poderá habilitar ou desabilitar tipos de cache usando a linha de comando ou manualmente. Antes de fazer isso, você deve fazer `<magento_root>/app/etc/env.php` gravável pelo [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).

Você pode limpar (também conhecido como _liberar_ ou _atualizar_) tipos de cache usando a linha de comando ou o Administrador.

Opções de comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Quando a omissão `[type]` ativa ou desativa todos os tipos de cache ao mesmo tempo. A variável `type` é uma lista separada por espaços de tipos de cache.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Para listar os tipos de cache e seus status:

```bash
bin/magento cache:status
```

Por exemplo, para desativar o cache de página inteira e o cache DDL:

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
>A partir da versão 2.3.4, o Commerce armazena em cache todos os atributos de EAV do sistema conforme são recuperados. O armazenamento em cache de atributos de EAV dessa maneira melhora o desempenho, pois diminui a quantidade de solicitações de inserção/seleção para o BD. No entanto, também aumenta o tamanho da rede de cache. Os desenvolvedores podem armazenar em cache atributos personalizados de EAV executando o `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Isso também pode ser feito pelo Administrador enquanto no [Modo de desenvolvedor](../bootstrap/application-modes.md) por configuração **Lojas** > Configurações **Configuração** > **Avançado** > **Desenvolvedor** > **Configurações de armazenamento em cache** > **Armazenar Atributos Definidos pelo Usuário em Cache** para **Sim**.

## Limpar e liberar tipos de cache

>[!NOTE]
>
>O cache de várias páginas pode ser invalidado simultânea e automaticamente **_sem_** edição dessas entidades. Por exemplo, quando qualquer produto no catálogo é atribuído a qualquer categoria ou quando qualquer [!UICONTROL related product rule] foi modificado.

Para limpar itens desatualizados do cache, você pode _limpar_ ou _liberar_ tipos de cache:

- A limpeza de um tipo de cache exclui todos os itens somente dos tipos de cache do Commerce ativados. Em outras palavras, essa opção não afeta outros processos ou aplicativos porque ela limpa somente o cache que o Commerce usa.

  Os tipos de cache desativados não são limpos.

  >[!TIP]
  >
  >Sempre limpe o cache após atualizar as versões do Magento Open Source ou do Adobe Commerce, atualizar do Magento Open Source para o Adobe Commerce ou instalar B2B para o Adobe Commerce ou qualquer módulo.

- A limpeza de um tipo de cache limpa o armazenamento em cache, o que pode afetar outros aplicativos de processos que estejam usando o mesmo armazenamento.

Limpe os tipos de cache se você já tiver tentado limpar o cache e ainda tiver problemas que não podem ser isolados.

Uso do comando:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Onde `[type]` é uma lista separada por espaços de tipos de cache. Omitindo `[type]` limpa ou libera todos os tipos de cache ao mesmo tempo. Por exemplo, para liberar todos os tipos de cache, informe

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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>Também é possível limpar e liberar tipos de cache no Administrador. Ir para **Sistema** > **Ferramentas** > **Gerenciamento de cache**. **Liberar armazenamento de cache** equivale a `bin/magento cache:flush`. **Liberar cache de Magento** equivale a `bin/magento cache:clean`.
