---
title: Usar memcache para armazenamento de sessão
description: Saiba mais sobre como usar memorizado para armazenamento de sessão do Commerce.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Usar memcache para armazenamento de sessão

Memcached é um sistema de armazenamento em cache de memória distribuída de uso geral. Geralmente é usado para acelerar sites orientados por bancos de dados dinâmicos armazenando em cache dados e objetos na RAM para reduzir o número de vezes que uma fonte de dados externa (como um banco de dados ou uma API) deve ser lida.

Memcached fornece uma grande tabela de hash que pode ser distribuída por várias máquinas. Quando a tabela está cheia, as inserções subsequentes fazem com que os dados mais antigos sejam limpos na ordem de LRUs (LRU) usada menos recentemente. O tamanho dessa tabela de hash geralmente é muito grande. (Fonte: [memcached.org](https://www.memcached.org/))

O Commerce usa memorizado para armazenamento de sessão, mas não para armazenamento em cache de página. Para armazenamento em cache de páginas, recomendamos [Redis](../cache/redis-pg-cache.md) ou [Verniz](../cache/config-varnish.md).

**Para configurar o Commerce para usar memcache**:

1. Abrir `<your install dir>/app/etc/env.php` em um editor de texto.
1. Localize o seguinte:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Altere-o da seguinte maneira:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   memcached tem parâmetros de inicialização opcionais que estão além do escopo deste guia. Você pode encontrar mais informações sobre eles na [em cache](https://www.php.net/manual/en/memcached.sessions.php) documentação, código-fonte e alterações.

1. Continue com a próxima seção.

**Para verificar se os trabalhos em cache foram armazenados em cache com o Commerce**:

1. Exclua o conteúdo dos seguintes diretórios no diretório de instalação do Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vá para qualquer página na loja.

1. Faça logon no Administrador e navegue até várias páginas.

   Se nenhum erro for exibido, parabéns! memcached está funcionando! Opcionalmente, você pode consultar o armazenamento em cache, conforme discutido na próxima etapa.

   Se os erros forem exibidos (como um HTTP 500 (Internal Server Error), ative o modo de desenvolvedor e diagnostice o problema. Certifique-se de que o cache está em execução, configurado corretamente e que `env.php` não tem erros de sintaxe.

1. (Opcional.) Use Telnet para examinar o armazenamento em cache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   Os resultados são exibidos de forma semelhante ao seguinte:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
