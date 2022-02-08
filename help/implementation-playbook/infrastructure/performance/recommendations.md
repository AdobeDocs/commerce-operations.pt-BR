---
title: Recommendations de otimização de desempenho
description: Otimize o desempenho de sua implementação do Adobe Commerce seguindo essas recomendações.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 0%

---

# Análise de otimização de desempenho

Mesmo que a otimização de desempenho possa vir de vários aspectos, há algumas recomendações gerais que devem ser consideradas para a maioria dos cenários. Isso inclui otimização de configuração para elementos de infraestrutura, configuração de back-end do Adobe Commerce e planejamento de escalabilidade de arquitetura.

## Infraestrutura

As seções a seguir descrevem as recomendações para otimizações de infraestrutura.

### Pesquisas de DNS

A pesquisa de DNS é o processo de descobrir a qual endereço IP o nome de domínio pertence. O navegador deve aguardar até que a pesquisa de DNS seja concluída antes de poder baixar qualquer coisa para cada solicitação. A redução de pesquisas de DNS é importante para melhorar o tempo geral de carregamento de página.

### Rede de entrega de conteúdo (CDN)

Use uma CDN para otimizar o desempenho do download de ativos. O Adobe Commerce usa o Fastly. Se tiver uma implementação local do Adobe Commerce, você também deve considerar adicionar uma camada de CDN.

### Latência da Web

A localização do data center afeta a latência da Web para usuários de primeiro plano.

### Largura de banda de rede

A largura de banda de rede suficiente é um dos principais requisitos para o intercâmbio de dados entre nós da Web, bancos de dados, servidores de armazenamento em cache/sessão e outros serviços.

Como a Adobe Commerce utiliza o armazenamento em cache de modo eficaz para proporcionar alto desempenho, seu sistema pode trocar dados ativamente com servidores de armazenamento em cache, como o Redis. Se Redis estiver localizado em um servidor remoto, você deve fornecer um canal de rede suficiente entre os nós da Web e o servidor de cache para evitar gargalos nas operações de leitura/gravação.

### Sistema operacional (SO)

As configurações e otimizações do sistema operacional são semelhantes para o Adobe Commerce quando comparadas a outros aplicativos Web de alto carregamento. À medida que o número de conexões simultâneas manipuladas pelo servidor aumenta, o número de soquetes disponíveis pode se tornar totalmente alocado.

### CPU de nós da Web

Um núcleo da CPU pode atender cerca de 2 a 4 solicitações do Adobe Commerce sem cache eficaz. Para determinar quantos nós/núcleos da Web são necessários para processar todas as solicitações recebidas sem colocá-las em fila, use a equação:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### configurações PHP-FPM

A otimização dessas configurações depende dos resultados do teste de desempenho para diferentes projetos.

- **ByteCode**—Para obter a velocidade máxima do Adobe Commerce no PHP 7, você deve ativar o `opcache` e configure-o corretamente.

- **APCU**—Recomendamos habilitar a extensão APCu PHP e configurar o Composer para otimizar o desempenho máximo. Essa extensão armazena em cache locais de arquivos abertos, o que aumenta o desempenho para chamadas de servidor do Adobe Commerce, incluindo páginas, chamadas Ajax e endpoints.

- **Realpath_cacheconfiguration**—Otimização `realpath_cache` permite que os processos PHP armazenem caminhos em cache em arquivos em vez de pesquisá-los sempre que uma página é carregada.

### Servidor da Web

Somente uma pequena reconfiguração é necessária para usar o nginx como servidor da Web. O novo servidor da Web fornece melhor desempenho e é fácil de configurar usando o arquivo de configuração de amostra do Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurar PHP-FPM com TCP corretamente

- Habilitar HTTP/2 e Gzip

- Otimizar conexões de trabalho

### Banco de dados

Este documento não fornece instruções detalhadas de ajuste do MySQL, pois cada loja e ambiente são diferentes, mas podemos fazer algumas recomendações gerais.

O banco de dados do Adobe Commerce (bem como qualquer outro banco de dados) é sensível à quantidade de memória disponível para armazenar dados e índices. Para utilizar efetivamente a indexação de dados do MySQL, a quantidade de memória disponível deve ser, no mínimo, próxima da metade do tamanho dos dados armazenados no banco de dados.

Otimize o `innodb_buffer_pool_instances` configuração para evitar problemas com vários threads tentando acessar a mesma instância. O valor da variável `max_connections` deve correlacionar-se com o número total de threads PHP configurados no servidor de aplicativos. Use a seguinte fórmula para calcular o melhor valor para `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Armazenamento em cache de sessão

O armazenamento em cache de sessão é um bom candidato a configurar para uma instância separada de Redis. A configuração de memória desse tipo de cache deve considerar a estratégia de abandono do carrinho do site e por quanto tempo uma sessão deve esperar permanecer no cache.

Redis deve ter memória suficiente alocada para manter todos os outros caches na memória para obter o melhor desempenho. O cache de bloco será o fator chave para determinar a quantidade de memória a ser configurada. O cache de bloco cresce em relação ao número de páginas em um site (número de SKU x número de visualizações de loja).

### Armazenamento de páginas em cache

Recomendamos o uso do Varnish para o cache de página completo na sua loja da Adobe Commerce. O `PageCache` O módulo ainda está presente na base de código, mas deve ser usado somente para fins de desenvolvimento.

Instale o Varnish em um servidor separado, na frente da camada da Web. Ele deve aceitar todas as solicitações recebidas e fornecer cópias de página em cache. Para permitir que a Varnish funcione efetivamente com páginas seguras, um proxy de terminação SSL pode ser colocado na frente da Varnish. O Nginx pode ser usado para essa finalidade.

Embora a invalidação de memória de cache de página inteira Varnish seja eficaz, recomendamos alocar memória suficiente para a Varnish para manter suas páginas mais populares na memória.

### Filas de mensagens

O MQF (Message Queue Framework, Estrutura da Fila de Mensagens) é um sistema que permite que um módulo publique mensagens em filas. Também define os consumidores que recebem as mensagens de forma assíncrona. A Adobe Commerce suporta o RabbitMQ como o corretor de mensagens, que fornece uma plataforma escalável para enviar e receber mensagens.

### Teste e monitoramento de desempenho

Os testes de desempenho antes de cada versão de produção são sempre recomendados para obter uma estimativa da capacidade da plataforma de comércio eletrônico. Continue monitorando após o lançamento e tenha um plano de dimensionamento e backup para lidar com os tempos de pico.

>[!NOTE]
>
> O Adobe Commerce na infraestrutura de nuvem já aplica todas as otimizações de infraestrutura e arquitetura acima, exceto pela pesquisa de DNS, pois está fora do escopo.

### Pesquisar

O Elasticsearch é necessário a partir do Adobe Commerce versão 2.4, mas também é uma prática recomendada habilitá-lo para versões anteriores à 2.4.

## Modelos operacionais

Além das recomendações de otimização de infraestrutura comum anteriormente mencionadas, também existem abordagens para melhorar o desempenho de modos e escalas de negócios específicos. Este documento não fornece instruções de ajuste detalhadas para todas elas, pois cada cenário é diferente, mas podemos fornecer algumas opções de alto nível para sua referência.

### Arquitetura headless

Temos uma seção separada dedicada a detalhar o que [impiedoso](../../architecture/headless/adobe-commerce.md) é e opções diferentes. Em resumo, ele separa a camada da loja da própria plataforma. Ainda é o mesmo back-end, mas a Adobe Commerce não processa mais solicitações diretamente e, em vez disso, suporta apenas vitrines personalizadas por meio da API GraphQL.

### Manter o Adobe Commerce atualizado

O Adobe Commerce sempre tem melhor desempenho ao executar a versão mais recente. Mesmo que não seja possível manter o Adobe Commerce atualizado após o lançamento de cada nova versão, ainda é recomendável [atualizar](../../../upgrade/overview.md) quando a Adobe Commerce apresenta otimizações significativas de desempenho.

Por exemplo, em 2020, o Adobe lançou uma otimização para a camada Redis, corrigindo muitas ineficiências, problemas de conexão e transferência desnecessária de dados entre Redis e Adobe Commerce. O desempenho geral entre 2.3 e 2.4 é noite e dia e vimos melhorias significativas no carrinho, check-out, usuários simultâneos, só por causa da otimização de Redis.

### Otimizar modelo de dados

Muitos problemas são originados de dados, incluindo modelos de dados incorretos, dados que não estão estruturados corretamente e dados que não têm índice.

Parece bom se você está testando algumas conexões, mas vistas na produção quando o tráfego real chega e é aqui que a lentidão entra. É muito importante que os integradores de sistemas saibam projetar um modelo de dados (especialmente para atributos de produtos), evitar adicionar atributos desnecessários e manter atributos obrigatórios que afetam a lógica comercial (como preços, disponibilidade de estoque e pesquisa).

Para aqueles atributos que não afetam a lógica de negócios, mas ainda precisam estar presentes na loja, combine-os em alguns atributos (por exemplo, formato JSON).

Para otimizar o desempenho da plataforma, se a lógica comercial não for necessária na loja a partir de dados ou atributos obtidos de um PIM ou ERP, não há necessidade de adicionar esse atributo ao Adobe Commerce.

### Design para escalabilidade

Isso é importante para as empresas que executam campanhas e enfrentam horários de pico com frequência. Para que a arquitetura e o design de aplicativos sejam fáceis de dimensionar, isso pode aumentar os recursos durante os horários de pico e reduzi-los depois.
