---
title: Software Recommendations
description: Revise uma lista de softwares recomendados relacionados ao desempenho ideal das implantações de Adobe Commerce e Magento Open Source.
source-git-commit: 8572cc8702d6f7e9c40b64110a9ba18aa5784f44
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---


# Recomendações de software

Exigimos o seguinte software para instâncias de produção de [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx e [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] ou OpenSearch](../installation/prerequisites/search-engine/overview.md)

Para implantações de vários servidores ou para comerciantes que planejam dimensionar seus negócios, recomendamos o seguinte:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) para sessões (a partir de 2.0.6+)
* Uma instância separada do Redis como [cache padrão](../configuration/cache/redis-pg-cache.md) (não use essa instância para cache de página)

Consulte [requisitos do sistema](../installation/system-requirements.md) para obter informações sobre versões compatíveis de cada tipo de software.

## Sistema operacional

As configurações e otimizações do sistema operacional são semelhantes para [!DNL Commerce] em comparação com outros aplicativos Web de alta carga. À medida que o número de conexões simultâneas manipuladas pelo servidor aumenta, o número de soquetes disponíveis pode se tornar totalmente alocado. O kernel Linux suporta um mecanismo para &quot;reutilizar&quot; conexões TCP. Para ativar esse mecanismo, defina o seguinte valor em `/etc/sysctl.conf`:

>[!INFO]
>
>Habilitar net.ipv4.tcp_tw_reuse não tem efeito nas conexões de entrada.

```text
net.ipv4.tcp_tw_reuse = 1
```

O parâmetro kernel `net.core.somaxconn` controla o número máximo de soquetes abertos aguardando conexões. Esse valor pode ser aumentado com segurança para 1024, mas deve ser correlacionado à capacidade do servidor de lidar com essa quantia. Para ativar esse parâmetro de kernel, defina o seguinte valor em `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

O Magento oferece suporte total ao PHP 7.3 e 7.4. Há vários fatores a serem considerados ao configurar o PHP para obter velocidade e eficiência máximas no processamento de solicitações.

### extensões PHP

Recomendamos limitar a lista de extensões PHP ativas àquelas que são necessárias para [!DNL Commerce] funcionalidade.

Magento Open Source e Adobe Commerce:

* ext-bcmath
* ext-ctype
* curl de texto
* ext-dom
* ext-fileinfo
* ext-gd
* hash de texto
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* saída de soquetes
* extrato-sódico
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Além disso, o Adobe Commerce exige:

* ext-bcmath
* ext-ctype
* curl de texto
* ext-dom
* ext-fileinfo
* ext-gd
* hash de texto
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* saída de soquetes
* extrato-sódico
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Adicionar mais extensões aumenta o tempo de carregamento da biblioteca.

>[!INFO]
>
>`php-mcrypt` foi removido do PHP 7.2 e substituído pelo [`sodium` biblioteca](https://www.php.net/manual/en/book.sodium.php). Certifique-se de que [sódio](https://www.php.net/manual/en/sodium.installation.php) está corretamente ativado ao atualizar o PHP.

>[!INFO]
>
>A presença de qualquer criação de perfil e extensão de depuração pode afetar negativamente o tempo de resposta de suas páginas. Como exemplo, um módulo xDebug ativo sem qualquer sessão de depuração pode aumentar o tempo de resposta da página em até 30%.

### Configurações PHP

Para garantir a execução bem-sucedida de todos [!DNL Commerce] instâncias sem descarregar dados ou códigos em disco, defina o limite de memória da seguinte maneira:

```text
memory_limit=1G
```

Para depuração, aumente esse valor para 2G.

#### Configuração do Realpath_cache

Para melhorar [!DNL Commerce] , adicione ou atualize o seguinte `realpath_cache` nas `php.ini` arquivo. Essa configuração permite que processos PHP armazenem em cache caminhos em arquivos em vez de pesquisá-los sempre que uma página é carregada. Consulte [Ajuste de desempenho](https://www.php.net/manual/en/ini.core.php) na documentação do PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Para obter a velocidade máxima fora de [!DNL Commerce] no PHP 7, você deve ativar o módulo OpCache e configurá-lo corretamente. Essas configurações são recomendadas para o módulo :

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Ao ajustar a alocação de memória para opcache, considere o tamanho do código base do Magento e todas as suas extensões. A equipe anterior do Magento usa os valores no exemplo de teste, pois fornece espaço suficiente no opcache.

Se você tiver uma máquina de baixa memória e não tiver muitas extensões ou personalizações instaladas, use as seguintes configurações para obter um resultado semelhante:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Recomendamos habilitar o [Extensão PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) e [configuração `composer` para a apoiar](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) para otimizar o desempenho máximo. Essa extensão armazena em cache locais de arquivos abertos, o que aumenta o desempenho para [!DNL Commerce] chamadas do servidor, incluindo páginas, chamadas do Ajax e endpoints.

Edite as `apcu.ini` para incluir o seguinte:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Servidor da Web

O Magento oferece suporte total aos servidores da Web Nginx e Apache. [!DNL Commerce] O fornece arquivos de configuração recomendados de amostra no  `<magento_home>/nginx.conf.sample` (Nginx) e  `<magento_home>.htaccess.sample` Arquivos (Apache).  A amostra Nginx contém configurações para melhor desempenho e é projetada para que pouca reconfiguração seja necessária. Algumas das principais práticas recomendadas de configuração definidas no arquivo de amostra incluem:

* Configurações para armazenar conteúdo estático em cache em um navegador
* Configurações de memória e tempo de execução para PHP
* Configurações de compactação de conteúdo

Você também deve configurar o número de threads para o processamento de solicitação de entrada, conforme listado abaixo:

| Servidor da Web | Nome do atributo | Localização | Informações relacionadas |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ajustando a NGINX para desempenho](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ajuste de desempenho do Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Diretivas comuns do Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Este documento não fornece detalhes [!DNL MySQL] instruções de ajuste porque cada loja e ambiente são diferentes, mas podemos fazer algumas recomendações gerais.

Houve muitas melhorias para [!DNL MySQL] 5.7.9 Estamos confiantes de que [!DNL MySQL] O é distribuído com boas configurações padrão. As configurações mais críticas são:

| Parâmetro | Padrão | Descrição |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | O valor padrão é definido como 8 para evitar problemas com vários threads que tentam acessar a mesma instância. |
| `innodb_buffer_pool_size` | 128 MB | Combinado com as várias instâncias de pool descritas acima, isso significa uma alocação de memória padrão de 1024MB. O tamanho total é dividido entre todos os pools de buffer. Para ter mais eficiência, especifique uma combinação de `innodb_buffer_pool_instances` e `innodb_buffer_pool_size` para que cada instância do pool de buffer seja de pelo menos 1 GB. |
| `max_connections` | 150 | O valor da variável `max_connections` deve correlacionar-se com o número total de threads PHP configurados no servidor de aplicativos. Uma recomendação geral seria 300 para um pequeno e 1.000 para um ambiente médio. |
| `innodb_thread_concurrency` | 0 | O melhor valor para essa configuração deve ser calculado pela fórmula: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

A Magento recomenda usar [!DNL Varnish] como o servidor de cache de página completo da sua loja. O módulo PageCache ainda está presente na base de código, mas deve ser usado somente para fins de desenvolvimento. Não deve ser utilizado juntamente com, ou em vez de, [!DNL Varnish].

Instalar [!DNL Varnish] em um servidor separado na frente da camada da Web. Ele deve aceitar todas as solicitações recebidas e fornecer cópias de página em cache. Para permitir [!DNL Varnish] para trabalhar com páginas seguras, um proxy de terminação de SSL pode ser colocado na frente de [!DNL Varnish]. O Nginx pode ser usado para essa finalidade.

[!DNL Commerce] O distribui um arquivo de configuração de amostra para [!DNL Varnish] (versões 4 e 5) que contém todas as configurações recomendadas para desempenho. Entre elas, as mais críticas em termos de desempenho são:

* **Verificação de integridade de backend** pesquisa a [!DNL Commerce] para determinar se está respondendo em tempo hábil.
* **Modo de carência** permite instruir [!DNL Varnish] para manter um objeto em cache além do período Time to Live (TTL) e veicular esse conteúdo obsoleto se [!DNL Commerce] não estiver íntegro ou se o conteúdo novo ainda não tiver sido buscado.
* **Modo Saint** listas negras não são saudáveis [!DNL Commerce] servidores por um período de tempo configurável. Como resultado, back-end não íntegro não podem fornecer tráfego ao usar [!DNL Varnish] como balanceador de carga.

Consulte [Avançado [!DNL Varnish] configuração](../configuration/cache/config-varnish-advanced.md) para obter mais informações sobre como implementar esses recursos.

### Otimizar o desempenho dos ativos

Em geral, recomendamos armazenar seus ativos (imagens, JS, CSS etc.) em uma CDN para obter o desempenho ideal.

Se o site não exigir a implantação de um grande número de localidades e os servidores estiverem na mesma região que a maioria dos clientes, você poderá encontrar ganhos significativos de desempenho a um custo menor armazenando seus ativos em [!DNL Varnish] em vez de usar um CDN.

Para armazenar seus ativos em [!DNL Varnish], adicione as seguintes entradas de VCL em seu `default.vcl` arquivo gerado por [!DNL Commerce] para [!DNL Varnish] 5.

No final do `if` instrução para solicitações PURGE na `vcl_recv` sub-rotina, adicione:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

No `vcl_backend_response` sub-rotina, procure a variável `if` declaração que desdefine o cookie para `GET` ou `HEAD` solicitações.
O arquivo `if` O bloco deve ser semelhante ao seguinte:

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

Reinicie o [!DNL Varnish] para liberar ativos em cache sempre que atualizar seu site ou implantar/atualizar ativos.

## Armazenamento em cache e servidores de sessão

O Magento fornece várias opções para armazenar o cache e os dados da sessão, incluindo Redis, Memcache, sistema de arquivos e banco de dados. Algumas dessas opções são discutidas abaixo.

### Configuração única do nó da Web

Se você planeja veicular todo o seu tráfego com apenas um nó da Web, não faz sentido colocar seu cache em um servidor Redis remoto. Em vez disso, use o sistema de arquivos ou um servidor Redis local. Se quiser usar o sistema de arquivos, coloque suas pastas de cache em um volume montado em um sistema de arquivos RAM. Se você quiser usar um servidor Redis local, recomendamos configurar o Redis para que ele use soquetes para conexões diretas, em vez de trocar dados por HTTP.

### Configuração de vários nós da Web

Para uma configuração de vários nós da Web, Redis é a melhor opção. Porque [!DNL Commerce] O armazena em cache muitos dados para melhorar o desempenho, presta atenção ao canal de rede entre os nós da Web e o servidor Redis. Você não deseja que o canal se torne um gargalo para o processamento de solicitações.

>[!INFO]
>
>Se precisar atender centenas e milhares de solicitações simultâneas, pode ser necessário um canal de até 1 Gbit (ou até mais amplo) para o servidor Redis.
