---
title: Recommendations de hardware
description: Revise uma lista de hardware recomendado relacionado ao desempenho ideal das implantações de Adobe Commerce e Magento Open Source.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# Recomendações de hardware

## CPUs

[!DNL Commerce] os nós da web atendem a todas as solicitações que não estão armazenadas em cache ou que não podem ser armazenadas em cache por meio do aplicativo. Um núcleo de CPU pode servir em torno de dois (às vezes até quatro) [!DNL Commerce] pedidos de asilo. Use a seguinte equação para determinar quantos nós/núcleos da Web você precisa processar todas as solicitações recebidas sem colocá-las em fila:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Se você espera que a carga de uma loja mude, é possível aumentar manualmente o número de nós/núcleos da web para um período de vendas ativo. Como alternativa, um modelo de dimensionamento automático pode ser usado para estender camadas da Web automaticamente.

## Memória

### PHP

O Magento tem diferentes requisitos de memória PHP, baseado em como seu sistema é implantado.  Em geral, se você está configurando uma única loja de servidor, recomendamos configurar a memória PHP para 2G.  Se você estiver configurando um site usando implantação de pipeline, recomendamos 2 GB no servidor de build e 1 GB nos nós da Web.

Cenários e requisitos de memória do PHP esperados:

* Nó da Web que atende somente páginas da loja: 256 MB
* Páginas de administrador do servidor de nós da Web com um catálogo grande: 1 GB
* [!DNL Commerce] cron indexando um site com um catálogo grande: >256 MB (Consulte [advanced-setup](../performance/advanced-setup.md) para otimizar o desempenho.)
* [!DNL Commerce] compilação e implantação de ativos estáticos: 756 MB
* [!DNL Commerce] geração de perfil do kit de ferramentas de desempenho: >1 GB de RAM PHP, >16 MB [!DNL MySQL] Configurações de TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

A variável [!DNL Commerce] O banco de dados (bem como qualquer outro banco de dados) é sensível à quantidade de memória disponível para armazenar dados e índices. Para utilizar efetivamente [!DNL MySQL] indexação de dados, a quantidade de memória disponível deve ser, no mínimo, cerca de metade do tamanho dos dados armazenados no banco de dados.

### Caches

Se estiver implantando várias [!DNL Commerce] e usando Redis ou [!DNL Varnish] para seus caches, lembre-se dos seguintes princípios:

* [!DNL Varnish] a invalidação da memória cache de página inteira é eficaz, recomende memória suficiente alocada para [!DNL Varnish] para guardar na memória suas páginas mais populares
* O cache de sessão é um bom candidato para configurar para uma instância separada do Redis.  A configuração de memória para esse tipo de cache deve considerar a estratégia de abandono do carrinho do site e por quanto tempo uma sessão deve permanecer no cache
* Os Redis devem ter memória suficiente alocada para armazenar todos os outros caches na memória para obter um desempenho ideal.  O cache de bloco será o principal fator na determinação da quantidade de memória a ser configurada.  O cache de blocos cresce em relação ao número de páginas em um site (número de skus x número de visualizações de loja)

## Largura de banda de rede

Largura de banda de rede suficiente é um dos principais requisitos para a troca de dados entre nós da Web, bancos de dados, servidores de cache/sessão e outros serviços. Porque [!DNL Commerce] utiliza efetivamente o cache para obter alto desempenho, seu sistema pode trocar dados ativamente com servidores de cache como o Redis. Se o Redis estiver localizado em um servidor remoto, você deverá fornecer um canal de rede suficiente entre os nós da Web e o servidor de cache para evitar gargalos nas operações de leitura/gravação.
