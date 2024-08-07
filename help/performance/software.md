---
title: Recommendations de software
description: Revise uma lista de softwares recomendados relacionados ao desempenho ideal das implantações do Adobe Commerce.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Recomendações de software

São necessários os seguintes softwares para as instâncias de produção do [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx e [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] ou OpenSearch](../installation/prerequisites/search-engine/overview.md)

Para implantações de vários servidores ou para comerciantes que planejam expandir seus negócios, recomendamos o seguinte:

* [Cache de [!DNL Varnish]](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) para sessões (de 2.0.6+)
* Uma instância Redis separada como seu [cache padrão](../configuration/cache/redis-pg-cache.md) (não use esta instância para cache de página)

Consulte [requisitos do sistema](../installation/system-requirements.md) para obter informações sobre versões com suporte de cada tipo de software.

## Sistema operacional

As configurações e otimizações do sistema operacional são semelhantes para o [!DNL Commerce] em comparação a outros aplicativos web de carga alta. À medida que o número de conexões simultâneas manipuladas pelo servidor aumenta, o número de soquetes disponíveis pode se tornar totalmente alocado. O kernel do Linux suporta um mecanismo para &quot;reutilizar&quot; conexões TCP. Para habilitar este mecanismo, defina o seguinte valor em `/etc/sysctl.conf`:

>[!INFO]
>
>A habilitação de net.ipv4.tcp_tw_reuse não afeta as conexões de entrada.

```text
net.ipv4.tcp_tw_reuse = 1
```

O parâmetro de kernel `net.core.somaxconn` controla o número máximo de soquetes abertos que aguardam conexões. Esse valor pode ser aumentado com segurança para 1024, mas deve ser correlacionado com a capacidade do servidor de lidar com essa quantidade. Para habilitar este parâmetro de kernel, defina o seguinte valor em `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

O Magento suporta totalmente o PHP 7.3 e 7.4. Há vários fatores a serem considerados ao configurar o PHP para obter o máximo de velocidade e eficiência no processamento de requisições.

### Extensões PHP

Recomendamos limitar a lista de extensões ativas do PHP àquelas que são necessárias para a funcionalidade [!DNL Commerce].

Magento Open Source e Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext- libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sódio
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Além disso, o Adobe Commerce exige:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* ext-gd
* ext-hash
* ext-iconv
* ext-intl
* ext-json
* ext- libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* ext-sockets
* ext-sódio
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Adicionar mais extensões aumenta os tempos de carregamento da biblioteca.

>[!INFO]
>
>`php-mcrypt` foi removido do PHP 7.2 e substituído pela biblioteca [`sodium` ](https://www.php.net/manual/en/book.sodium.php). Verifique se [sódio](https://www.php.net/manual/en/sodium.installation.php) está habilitado corretamente ao atualizar o PHP.

>[!INFO]
>
>A presença de qualquer extensão de criação de perfil e depuração pode afetar negativamente o tempo de resposta de suas páginas. Como exemplo, um módulo xDebug ativo sem qualquer sessão de depuração pode aumentar o tempo de resposta da página em até 30%.

### Configurações do PHP

Para garantir a execução bem-sucedida de todas as instâncias [!DNL Commerce] sem despejar dados ou código em disco, defina o limite de memória da seguinte maneira:

```text
memory_limit=1G
```

Para depuração, aumente esse valor para 2G.

#### Configuração do Realpath_cache

Para melhorar o desempenho do [!DNL Commerce], adicione ou atualize as seguintes configurações recomendadas do `realpath_cache` no arquivo `php.ini`. Essa configuração permite que processos PHP armazenem em cache caminhos para arquivos em vez de pesquisá-los sempre que uma página é carregada. Consulte [Ajuste de desempenho](https://www.php.net/manual/en/ini.core.php) na documentação do PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Para obter a velocidade máxima de [!DNL Commerce] no PHP 7, você deve ativar o módulo OpCache e configurá-lo corretamente. Estas configurações são recomendadas para o módulo:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Ao ajustar a alocação de memória para o opcache, considere o tamanho da base de código do Magento e todas as suas extensões. A equipe de desempenho do Magento usa os valores do exemplo anterior para testes, pois fornece espaço suficiente no opcache para o número médio de extensões instaladas.

Se você tiver um computador com pouca memória e não tiver muitas extensões ou personalizações instaladas, use as seguintes configurações para obter um resultado semelhante:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Recomendamos ativar a [extensão PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) e [configurar o `composer` para ter suporte](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) para otimizar o desempenho máximo. Essa extensão armazena em cache locais de arquivos abertos, o que aumenta o desempenho de chamadas do servidor [!DNL Commerce], incluindo páginas, chamadas de Ajax e pontos de extremidade.

Edite seu arquivo `apcu.ini` para incluir o seguinte:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Servidor da Web

O Magento é totalmente compatível com os servidores Web Nginx e Apache. O [!DNL Commerce] fornece arquivos de configuração recomendados de exemplo nos arquivos `<magento_home>/nginx.conf.sample` (Nginx) e `<magento_home>.htaccess.sample` (Apache).  A amostra do Nginx contém configurações para melhor desempenho e é projetada para que seja necessária pouca reconfiguração. Algumas das principais práticas recomendadas de configuração definidas no arquivo de amostra incluem:

* Configurações para armazenamento em cache de conteúdo estático em um navegador
* Configurações de memória e tempo de execução para PHP
* Configurações de compactação de conteúdo

Você também deve configurar o número de threads para processamento de solicitação de entrada, conforme listado abaixo:

| Servidor da Web | Nome do atributo | Localização | Informações relacionadas |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ajustando o NGINX para Desempenho](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ajuste de desempenho do Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Diretivas Comuns do Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Este documento não fornece instruções detalhadas de ajuste do [!DNL MySQL] porque cada armazenamento e ambiente são diferentes, mas podemos fazer algumas recomendações gerais.

Houve muitas melhorias no [!DNL MySQL] 5.7.9. Estamos confiantes de que o [!DNL MySQL] é distribuído com boas configurações padrão. As configurações mais críticas são:

| Parâmetro | Padrão | Descrição |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | O valor padrão é definido como 8 para evitar problemas com várias threads tentando acessar a mesma instância. |
| `innodb_buffer_pool_size` | 128 MB | Combinado com as várias instâncias de pool descritas acima, isso significa uma alocação de memória padrão de 1024 MB. O tamanho total é dividido entre todos os pools de buffer. Para maior eficiência, especifique uma combinação de `innodb_buffer_pool_instances` e `innodb_buffer_pool_size` para que cada instância do pool de buffers tenha pelo menos 1 GB. |
| `max_connections` | 150 | O valor do parâmetro `max_connections` deve correlacionar-se com o número total de threads do PHP configurados no servidor de aplicativos. Uma recomendação geral seria de 300 para um ambiente pequeno e de 1.000 para um ambiente médio. |
| `innodb_thread_concurrency` | 0 | O melhor valor para esta configuração deve ser calculado pela fórmula: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

A Magento recomenda usar o [!DNL Varnish] como o servidor de cache de página inteira da sua loja. O módulo PageCache ainda está presente na base de código, mas deve ser usado somente para fins de desenvolvimento. Ela não deve ser usada junto com ou em vez de [!DNL Varnish].

Instale o [!DNL Varnish] em um servidor separado, em frente à camada da Web. Ele deve aceitar todas as solicitações recebidas e fornecer cópias de página em cache. Para permitir que [!DNL Varnish] funcione efetivamente com páginas seguras, um proxy de encerramento SSL pode ser colocado na frente de [!DNL Varnish]. O Nginx pode ser usado para essa finalidade.

O [!DNL Commerce] distribui um arquivo de configuração de exemplo para [!DNL Varnish] (versões 4 e 5) que contém todas as configurações recomendadas para desempenho. Entre eles, os mais críticos em termos de desempenho são:

* **A verificação de integridade do back-end** sonda o servidor [!DNL Commerce] para determinar se ele está respondendo em tempo hábil.
* O **modo de carência** permite que você instrua o [!DNL Varnish] a manter um objeto no cache além do período TTL (Time to Live) e fornecer esse conteúdo obsoleto se [!DNL Commerce] não estiver íntegro ou se o conteúdo novo ainda não tiver sido obtido.
* **Modo Saint** coloca na lista negra os servidores [!DNL Commerce] não íntegros por um período de tempo configurável. Como resultado, back-end não íntegros não podem fornecer tráfego ao usar [!DNL Varnish] como balanceador de carga.

Consulte [Avançado [!DNL Varnish] configuração](../configuration/cache/config-varnish-advanced.md) para obter mais informações sobre como implementar esses recursos.

### Otimizar o desempenho dos ativos

Em geral, recomendamos armazenar seus ativos (imagens, JS, CSS etc.) em um CDN para obter o melhor desempenho.

Se seu site não exigir a implantação de um grande número de localidades e seus servidores estiverem na mesma região que a maioria de seus clientes, você poderá encontrar ganhos de desempenho significativos a um custo menor armazenando seus ativos no [!DNL Varnish] em vez de usar uma CDN.

Para armazenar seus ativos no [!DNL Varnish], adicione as seguintes entradas de VCL no arquivo `default.vcl` gerado por [!DNL Commerce] para [!DNL Varnish] 5.

No final da instrução `if` para solicitações PURGE na sub-rotina `vcl_recv`, adicione:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Na sub-rotina `vcl_backend_response`, procure a instrução `if` que desmarca o cookie para solicitações `GET` ou `HEAD`.
O bloco `if` atualizado deve ser semelhante ao seguinte:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Reinicie o servidor [!DNL Varnish] para liberar ativos em cache sempre que atualizar o site ou implantar/atualizar ativos.

## Armazenamento em cache e servidores de sessão

O Magento fornece várias opções para armazenar o cache e os dados da sessão, incluindo Redis, Memcache, sistema de arquivos e banco de dados. Algumas dessas opções são discutidas abaixo.

### Configuração de nó único da Web

Se você planeja atender todo o seu tráfego com apenas um nó da Web, não faz sentido colocar seu cache em um servidor Redis remoto. Em vez disso, use o sistema de arquivos ou um servidor Redis local. Se quiser usar o sistema de arquivos, coloque as pastas de cache em um volume montado em um sistema de arquivos RAM. Se você quiser usar um servidor Redis local, é altamente recomendável configurar o Redis para que ele use soquetes para conexões diretas, em vez de trocar dados por meio de HTTP.

### Configuração de vários nós da Web

Para uma configuração de vários nós da Web, Redis é a melhor opção. Como o [!DNL Commerce] armazena ativamente muitos dados em cache para melhorar o desempenho, preste atenção ao canal da rede entre os nós da Web e o servidor Redis. Você não deseja que o canal se torne um afunilamento para o processamento de solicitações.

>[!INFO]
>
>Se você precisar atender centenas e milhares de solicitações simultâneas, pode precisar de um canal de até 1 Gbit (ou até mesmo maior) para seu servidor Redis.
