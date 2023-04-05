---
title: Configurar e usar o Varnish
description: Entenda como a Varnish armazena arquivos e melhora o tráfego HTTP.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---


# Configurar Varnês

[Cache Varna] é um acelerador de aplicações web de código aberto (também conhecido como _Acelerador HTTP_ ou _armazenamento em cache do proxy reverso HTTP_). A varnish armazena (ou armazena em cache) arquivos ou fragmentos de arquivos na memória, o que permite que a Varnish reduza o tempo de resposta e o consumo de largura de banda da rede em solicitações futuras equivalentes. Ao contrário dos servidores da Web como o Apache e o Nginx, a Varnish foi projetada para uso exclusivo com o protocolo HTTP.

O Commerce 2.4.2 é testado com o Varnish 6.4. O Commerce 2.4.x é compatível com o Varnish 6.x

>[!WARNING]
>
>We _altamente recomendável_ você usa a língua Varnish na produção. O armazenamento em cache de página inteira integrado — para o sistema de arquivos ou [banco de dados]—é muito mais lento do que o Varnish, e o Varnish foi projetado para acelerar o tráfego HTTP.

Para obter mais informações sobre o Varnish, consulte:

- [A imagem grande e verniz]
- [Opções de inicialização de Varnish]
- [Desempenho da Varnish e do site]

## Diagrama de topologia Varna

A figura a seguir mostra uma exibição básica de Varnish em sua topologia de Comércio.

![Diagrama básico do Varno](../../assets/configuration/varnish-basic.png)

Na figura anterior, as solicitações HTTP dos usuários pela Internet resultam em várias solicitações de CSS, HTML, JavaScript e imagens (chamadas coletivamente de _ativos_). A Varnish fica na frente do servidor da Web e envia essas solicitações para o servidor da Web.

Conforme o servidor da Web retorna ativos, os ativos em cache são armazenados em Varnish. Quaisquer solicitações subsequentes para esses ativos são atendidas pela Varnish (ou seja, as solicitações não chegam ao servidor da Web). A língua inglesa retorna o conteúdo em cache extremamente rapidamente. Os resultados são tempos de resposta mais rápidos para retornar o conteúdo aos usuários e um número reduzido de solicitações que devem ser atendidas pelo Commerce.

Os ativos em cache pela Varnish expiram em um intervalo configurável ou são substituídos por versões mais recentes dos mesmos ativos. Você também pode limpar o cache manualmente usando o Administrador ou a [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) comando.

## Visão geral do processo

Este tópico discute como instalar inicialmente o Varnish com um conjunto mínimo de parâmetros e testar se ele funciona. Em seguida, exporte uma configuração Varnish do Administrador de comércio e teste-a novamente.

O processo pode ser resumido da seguinte maneira:

1. Instale o Varnish e teste-o acessando qualquer página de Comércio para ver se você está recebendo cabeçalhos de resposta HTTP que indicam que o Varnish está funcionando.
1. Instale o software Commerce e use o Admin para criar um arquivo de configuração Varnish.
1. Substitua seu arquivo de configuração Varnish existente pelo arquivo gerado pelo Administrador.
1. Teste tudo novamente.

   Se não houver nada em seu `<magento_root>/var/page_cache` , você configurou o Varnish com o Commerce!

>[!NOTE]
- Exceto quando indicado, você deve inserir todos os comandos discutidos neste tópico como um usuário com `root` privilégios.
- Este tópico foi escrito para Varnish no CentOS e no Apache 2.4. Se você estiver configurando o Varnish em um ambiente diferente, alguns comandos poderão ser diferentes. Consulte a documentação da Varnish para obter mais informações.


## Problemas conhecidos

Temos conhecimento dos seguintes problemas com a língua Varnish:

- [Varnish não suporta SSL]

   Como alternativa, use a terminação SSL ou um proxy de terminação SSL.

- Se você excluir manualmente o conteúdo da variável `<magento_root>/var/cache` , você deve reiniciar o Varnish.

- Possível erro ao instalar o Commerce:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   Se você tiver esse erro, edite `default.vcl` e adicione um tempo limite à `backend` stanza:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Visão geral do armazenamento em cache da Varnish

O armazenamento em cache Varnish funciona com o Commerce usando:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) do repositório GitHub Magento 2
- `.htaccess` arquivo de configuração distribuído para o Apache fornecido com o Commerce
- `default.vcl` configuração para Varnish gerada usando o [Administrador](../cache/configure-varnish-commerce.md)

>[!INFO]
Este tópico aborda apenas as opções padrão na lista anterior. Há muitas outras maneiras de configurar o armazenamento em cache em cenários complexos (por exemplo, usando uma Rede de entrega de conteúdo); esses métodos estão além do escopo deste guia.

Na primeira solicitação do navegador, os ativos em cache são entregues ao navegador do cliente da Varnish e armazenados em cache no navegador.

Além disso, a Varnish usa uma tag de entidade (ETag) para ativos estáticos. O ETag fornece uma maneira de determinar quando os arquivos estáticos são alterados no servidor. Como resultado, os ativos estáticos são enviados ao cliente quando são alterados no servidor, seja em uma nova solicitação de um navegador ou quando o cliente atualiza o cache do navegador, normalmente pressionando F5 ou Control+F5.

Mais detalhes são fornecidos nas seções a seguir.

## Armazenamento em cache por solicitação do navegador

Esta seção usa um inspetor de navegador para mostrar como os ativos são entregues ao navegador na primeira solicitação e depois carregados do cache do navegador local.

### Primeira solicitação do navegador

`nginx.conf.sample` e `.htaccess` forneça opções para armazenamento em cache do cliente. Quando a primeira solicitação é feita de um navegador para um objeto armazenável em cache, a Varnish a entrega ao cliente.

A figura a seguir mostra um exemplo usando um inspetor de navegador:

![Na primeira vez que uma solicitação é feita para um objeto armazenável em cache, a Varnish a entrega para o navegador](../../assets/configuration/varnish-apache-first-visit.png)

O exemplo anterior mostra uma solicitação para a página principal da loja (`m2_ce_my`). Os ativos CSS e JavaScript são armazenados em cache no navegador do cliente.

>[!NOTE]
A maioria dos ativos estáticos tem um código de status HTTP 200 (OK), indicando que o ativo foi recuperado do servidor.

### Segunda solicitação do navegador

Se o mesmo navegador solicitar a mesma página novamente, esses ativos serão entregues a partir do cache do navegador local, como mostra a figura a seguir.

![Na próxima vez que o mesmo objeto for solicitado, os ativos serão carregados do cache do navegador local](../../assets/configuration/varnish-apache-second-visit.png)

Observe a diferença no tempo de resposta entre a primeira e a segunda solicitação. Novamente, os ativos estáticos têm um código de resposta 200 (OK), pois são fornecidos do cache local pela primeira vez.

## Como o Commerce usa o Etag

O exemplo a seguir mostra cabeçalhos de resposta para um ativo estático específico.

![O ETag facilita determinar se um ativo estático foi alterado ou não](../../assets/configuration/varnish-etag.png)

`calendar.css` tem um cabeçalho de resposta ETag, o que significa que o arquivo CSS no navegador do cliente pode ser comparado ao arquivo no servidor.

Além disso, os ativos estáticos são retornados com um código de status HTTP 304 (Não modificado), como mostra a figura a seguir.

![O código de resposta HTTP 304 (Not Modified) indica que o ativo estático no cache local é o mesmo que no servidor](../../assets/configuration/varnish-304.png)

O código de status 304 ocorre porque o usuário invalidou o cache local e o conteúdo no servidor não foi alterado. Devido ao código de status 304, o ativo estático _conteúdo_ não é transferido; somente cabeçalhos HTTP são baixados no navegador.

Se o conteúdo mudar no servidor, o cliente baixará o ativo estático com um código de status HTTP 200 (OK) e um novo ETag.

<!-- Link Definitions -->

[banco de dados]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[A imagem grande e verniz]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Cache Varna]: https://varnish-cache.org
[Opções de inicialização de Varnish]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Desempenho da Varnish e do site]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish não suporta SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
