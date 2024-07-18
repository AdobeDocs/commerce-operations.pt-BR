---
title: Usar memcached para armazenamento de sessão
description: Saiba mais sobre como usar o memcached para o armazenamento de sessão do Commerce.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Usar memcached para armazenamento de sessão

O Memcached é um sistema de cache de memória distribuída de uso geral. Geralmente é usado para acelerar sites dinâmicos orientados por bancos de dados, armazenando dados em cache e objetos na RAM para reduzir o número de vezes que uma fonte de dados externa (como um banco de dados ou uma API) deve ser lida.

Memcached fornece uma grande tabela de hash que pode ser distribuída entre várias máquinas. Quando a tabela está cheia, as inserções subsequentes fazem com que os dados mais antigos sejam removidos na ordem de LRU (Least Recently Used, menos usados recentemente). O tamanho dessa tabela de hash geralmente é muito grande. (Source: [memcached.org](https://www.memcached.org/))

O Commerce usa o memcached para armazenamento de sessão, mas não para armazenamento em cache de página. Para armazenamento em cache de páginas, recomendamos [Redis](../cache/redis-pg-cache.md) ou [Varnish](../cache/config-varnish.md).

**Para configurar o Commerce para usar o memcached**:

1. Abra `<your install dir>/app/etc/env.php` em um editor de texto.
1. Localize:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Altere da seguinte maneira:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   o memcached tem parâmetros de inicialização opcionais que estão além do escopo deste guia. Você pode encontrar mais informações sobre eles na documentação [memcached](https://www.php.net/manual/en/memcached.sessions.php), no código-fonte e nos logs de alterações.

1. Prossiga para a próxima seção.

**Para verificar se o memcached funciona com Commerce**:

1. Exclua o conteúdo dos seguintes diretórios no diretório de instalação do Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vá para qualquer página da loja.

1. Faça logon no Admin e navegue até várias páginas.

   Se nenhum erro for exibido, parabéns. o memcached está funcionando! Como opção, você pode examinar o armazenamento em cache memorizado conforme discutido na próxima etapa.

   Se forem exibidos erros (como HTTP 500 (Erro interno do servidor)), ative o modo de desenvolvedor e diagnostique o problema. Verifique se o memcached está em execução, configurado corretamente e se `env.php` não tem erros de sintaxe.

1. (Opcional.) Use o Telnet para examinar o armazenamento de dados em cache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Os resultados são exibidos de forma semelhante ao seguinte:

   ```
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
