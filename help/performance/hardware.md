---
title: Recommendations de hardware
description: Revise uma lista de hardware recomendado relacionado ao desempenho ideal das implantações de Adobe Commerce e Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Recomendações de hardware

## CPUs

[!DNL Commerce] os nós da Web atendem a todas as solicitações que não estão em cache ou que não podem ser armazenadas em cache por meio do aplicativo. Um núcleo da CPU pode servir cerca de dois (às vezes até quatro) [!DNL Commerce] solicitações de maneira eficaz. Use a seguinte equação para determinar quantos nós/núcleos da Web você precisa processar todas as solicitações recebidas sem colocá-las em fila:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Se você espera que a carga de um armazenamento mude, é possível aumentar manualmente o número de nós/núcleos da Web para um período de vendas ativo. Como alternativa, um modelo de dimensionamento automático pode ser usado para estender automaticamente camadas da Web.

## Memória

### PHP

O Magento tem diferentes requisitos de memória PHP, com base em como seu sistema é implantado.  Em geral, se você estiver configurando um único armazenamento de servidor, recomendamos configurar a memória PHP para 2G.  Se você estiver configurando um site usando a implantação de pipeline, recomendamos 2 GB em seu servidor de build e 1 GB em seus nós da Web.

Cenários e requisitos de memória PHP esperados:

* Webnode que serve apenas páginas de vitrine: 256 MB
* Webnode que serve páginas de administrador com um catálogo grande: 1 GB
* [!DNL Commerce] cron indexando um site com um catálogo grande: >256 MB (Consulte [configuração avançada](../performance/advanced-setup.md) para otimizar o desempenho.)
* [!DNL Commerce] compilar e implantar ativos estáticos: 756 MB
* [!DNL Commerce] geração de perfil do kit de ferramentas de desempenho: >1 GB de RAM PHP, >16 MB [!DNL MySQL] Configurações TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

O [!DNL Commerce] o banco de dados (bem como qualquer outro banco de dados) é sensível à quantidade de memória disponível para armazenar dados e índices. Para aproveitar com eficácia [!DNL MySQL] indexação de dados, a quantidade de memória disponível deve ser, no mínimo, próxima da metade do tamanho dos dados armazenados no banco de dados.

### Caches

Se estiver implantando vários [!DNL Commerce] e utilizando Redis ou [!DNL Varnish] para seus caches, lembre-se dos seguintes princípios:

* [!DNL Varnish] a invalidação completa da memória do cache de página é eficaz, recomende memória suficiente alocada para [!DNL Varnish] para manter suas páginas mais populares na memória
* O cache de sessão é um bom candidato a ser configurado para uma instância separada de Redis.  A configuração de memória desse tipo de cache deve considerar a estratégia de abandono do carrinho do site e por quanto tempo uma sessão deve esperar permanecer no cache
* Redis deve ter memória suficiente alocada para manter todos os outros caches na memória para obter o melhor desempenho.  O cache de bloco será o fator chave para determinar a quantidade de memória a ser configurada.  O cache de bloco cresce em relação ao número de páginas em um site (número de SKU x número de visualizações de loja)

## Largura de banda de rede

A largura de banda de rede suficiente é um dos principais requisitos para a troca de dados entre nós da Web, banco(s) de dados, servidores de armazenamento em cache/sessão e outros serviços. Porque [!DNL Commerce] utiliza o armazenamento em cache de modo eficiente para proporcionar alto desempenho, seu sistema pode trocar dados ativamente com servidores de armazenamento em cache, como o Redis. Se Redis estiver localizado em um servidor remoto, você deve fornecer um canal de rede suficiente entre os nós da Web e o servidor de cache para evitar gargalos nas operações de leitura/gravação.
