---
title: Otimização de desempenho Recommendations
description: Otimize o desempenho da sua implementação do Adobe Commerce seguindo estas recomendações.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Análise da otimização de desempenho

Embora a otimização de desempenho possa vir de muitos aspectos, há algumas recomendações gerais que devem ser consideradas para a maioria dos cenários. Isso inclui otimização de configuração para elementos de infraestrutura, configuração de back-end do Adobe Commerce e planejamento de escalabilidade da arquitetura.

## Infraestrutura

As seções a seguir descrevem as recomendações para a otimização da infraestrutura.

### Pesquisas de DNS

A pesquisa de DNS é o processo de descobrir a qual endereço IP o nome de domínio pertence. O navegador deve aguardar até que a pesquisa de DNS seja concluída para poder baixar qualquer item para cada solicitação. A redução de pesquisas de DNS é importante para melhorar o tempo geral de carregamento da página.

### Rede de entrega de conteúdo (CDN)

Use uma CDN para otimizar o desempenho do download de ativos. O Adobe Commerce usa o Fastly. Se tiver uma implementação local do Adobe Commerce, você também deve considerar adicionar uma camada de CDN.

### Latência da Web

A localização do data center afeta a latência da Web para usuários de front-end.

### Largura de banda de rede

Largura de banda de rede suficiente é um dos principais requisitos para a troca de dados entre nós da Web, bancos de dados, servidores de cache/sessão e outros serviços.

Como o Adobe Commerce aproveita efetivamente o cache para obter alto desempenho, seu sistema pode trocar dados ativamente com servidores de cache como o Redis. Se o Redis estiver localizado em um servidor remoto, você deverá fornecer um canal de rede suficiente entre os nós da Web e o servidor de cache para evitar gargalos nas operações de leitura/gravação.

### Sistema operacional (SO)

As configurações e otimizações do sistema operacional são semelhantes para o Adobe Commerce quando comparadas a outros aplicativos web de carga alta. À medida que o número de conexões simultâneas manipuladas pelo servidor aumenta, o número de soquetes disponíveis pode se tornar totalmente alocado.

### CPU de nós da Web

Um núcleo de CPU pode atender a cerca de 2 a 4 solicitações Adobe Commerce sem cache de forma eficiente. Para determinar quantos nós/núcleos da Web são necessários para processar todas as solicitações recebidas sem colocá-las em fila, use a equação:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Configurações de PHP-FPM

A otimização dessas configurações depende dos resultados do teste de desempenho para projetos diferentes.

- **ByteCode**—Para obter a velocidade máxima do Adobe Commerce no PHP 7, você deve ativar o `opcache` módulo e o configure adequadamente.

- **APCU**—Recomendamos ativar a extensão PHP APCu e configurar o Composer para otimizar o desempenho máximo. Essa extensão armazena em cache locais de arquivos abertos, o que aumenta o desempenho de chamadas de servidor do Adobe Commerce, incluindo páginas, chamadas de Ajax e pontos de extremidade.

- **Realpath_cacheconfiguration**—Otimização `realpath_cache` permite que processos PHP armazenem em cache caminhos para arquivos em vez de pesquisá-los sempre que uma página é carregada.

### Servidor da Web

Somente uma pequena reconfiguração é necessária para usar o nginx como servidor da Web. O servidor Web nginx fornece melhor desempenho e é fácil de configurar usando o arquivo de configuração de exemplo do Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurar o PHP-FPM com TCP corretamente

- Ativar HTTP/2 e Gzip

- Otimizar conexões de trabalho

### Banco de dados

Este documento não fornece instruções detalhadas de ajuste do MySQL porque cada armazenamento e ambiente é diferente, mas podemos fazer algumas recomendações gerais.

O banco de dados do Adobe Commerce (bem como qualquer outro banco de dados) é sensível à quantidade de memória disponível para armazenar dados e índices. Para aproveitar efetivamente a indexação de dados MySQL, a quantidade de memória disponível deve ser, no mínimo, cerca de metade do tamanho dos dados armazenados no banco de dados.

Otimize o `innodb_buffer_pool_instances` configuração para evitar problemas com várias threads tentando acessar a mesma instância. O valor de `max_connections` deve estar correlacionado com o número total de threads do PHP configurados no servidor de aplicativo. Use a seguinte fórmula para calcular o melhor valor para `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Armazenamento em cache da sessão

O armazenamento em cache de sessão é um bom candidato para configurar para uma instância separada do Redis. A configuração de memória para esse tipo de cache deve considerar a estratégia de abandono do carrinho do site e por quanto tempo uma sessão deve permanecer no cache.

Os Redis devem ter memória suficiente alocada para armazenar todos os outros caches na memória para obter um desempenho ideal. O cache de bloco será o principal fator na determinação da quantidade de memória a ser configurada. O cache de blocos cresce em relação ao número de páginas em um site (número de SKUs x número de visualizações de loja).

### Armazenamento em cache de páginas

Recomendamos usar o Varnish para o cache de página completa na loja da Adobe Commerce. A variável `PageCache` O módulo ainda está presente na base de código, mas deve ser usado somente para fins de desenvolvimento.

Instale o Varnish em um servidor separado na frente da camada da Web. Ele deve aceitar todas as solicitações recebidas e fornecer cópias de página em cache. Para permitir que o Verniz funcione de maneira eficaz com páginas seguras, um proxy de terminação SSL pode ser colocado na frente do Verniz. O Nginx pode ser usado para essa finalidade.

Embora a invalidação da memória cache de página inteira do Vernish seja eficaz, recomendamos alocar memória suficiente para o Vernish armazenar suas páginas mais populares na memória.

### Filas de mensagens

O Message Queue Framework (MQF) é um sistema que permite que um módulo publique mensagens em filas. Também define os consumidores que recebem as mensagens de forma assíncrona. O Adobe Commerce oferece suporte [!DNL RabbitMQ] como o agente de mensagens, que fornece uma plataforma escalável para enviar e receber mensagens.

### Teste e monitoramento de desempenho

O teste de desempenho antes de cada versão de produção é sempre recomendado para obter uma estimativa da capacidade da sua plataforma de comércio eletrônico. Mantenha o monitoramento após o lançamento e tenha um plano de escalabilidade e backup para lidar com picos.

>[!NOTE]
>
> O Adobe Commerce na infraestrutura em nuvem já aplica todas as otimizações de infraestrutura e arquitetura acima, exceto a pesquisa de DNS porque está fora do escopo.

### Pesquisar {#search-heading}

O Elasticsearch (ou OpenSearch) é necessário a partir do Adobe Commerce versão 2.4, mas também é uma prática recomendada ativá-lo para versões anteriores à 2.4.

## Modelos operacionais

Além das recomendações comuns de otimização de infraestrutura mencionadas anteriormente, também há abordagens para aprimorar o desempenho de modos e escalas de negócios específicos. Este documento não fornece instruções de ajuste detalhado para todos eles porque cada cenário é diferente, mas podemos fornecer algumas opções de alto nível para sua referência.

### Arquitetura headless

Temos uma seção separada dedicada a detalhar o [headless](../../architecture/headless/adobe-commerce.md) é e opções diferentes. Em resumo, ela separa a camada da loja da própria plataforma. Ainda é o mesmo back-end, mas o Adobe Commerce não processa mais solicitações diretamente e, em vez disso, oferece suporte somente a vitrines personalizadas por meio da API do GraphQL.

### Manter o Adobe Commerce atualizado

O Adobe Commerce sempre tem melhor desempenho ao executar a versão mais recente. Mesmo que não seja possível manter o Adobe Commerce atualizado após cada lançamento de uma nova versão, ainda é recomendável [atualização](../../../upgrade/overview.md) quando a Adobe Commerce apresenta otimizações significativas de desempenho.

Por exemplo, em 2020, o Adobe lançou uma otimização para a camada Redis, corrigindo muitas ineficiências, problemas de conexão e transferência de dados desnecessários entre o Redis e o Adobe Commerce. O desempenho geral entre as versões 2.3 e 2.4 é noturno e diurno, e vimos melhorias significativas no carrinho, checkout, usuários simultâneos, apenas por causa da otimização do Redis.

### Otimizar modelo de dados

Muitos problemas se originam de dados, incluindo modelos de dados inválidos, dados que não estão estruturados corretamente e dados que não têm um índice.

Parece bom se você estiver testando algumas conexões, mas é visto na produção quando o tráfego real chega e é aqui que entra a lentidão. É muito importante que os integradores de sistemas saibam como projetar um modelo de dados (especialmente para atributos de produtos), evitar a adição de atributos desnecessários e manter atributos obrigatórios que afetam a lógica de negócios (como preços, disponibilidade de estoque e pesquisa).

Para os atributos que não afetam a lógica de negócios, mas ainda precisam estar presentes na loja, combine-os em alguns atributos (por exemplo, formato JSON).

Para otimizar o desempenho da plataforma, se a lógica comercial não for exigida na loja a partir de dados ou atributos obtidos de um PIM ou ERP, não há necessidade de adicionar esse atributo ao Adobe Commerce.

### Design para escalabilidade

Isso é importante para empresas que realizam campanhas e enfrentam horários de pico com frequência. Para que o design da arquitetura e do aplicativo seja fácil de dimensionar, isso pode aumentar os recursos durante os períodos de pico e reduzi-los posteriormente.
