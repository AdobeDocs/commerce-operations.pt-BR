---
title: Opções de back-end de cache e referência de armazenamento
description: Saiba mais sobre as opções de back-end do cache no Adobe Commerce, incluindo sistema de arquivos, Redis, Valkey e armazenamento de banco de dados. Descubra as opções baseadas em Zend (RemoteSynchronizedCache) e Symfony Cache.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="No local" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos locais do Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 23f63c896760992da9b0d30b756a37de2117f6b8
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%
---
# Opções de back-end de cache e referência de armazenamento

>[!NOTE]
>
>Esta página documenta a configuração `app/etc/env.php` local.
>
>Para projetos [!DNL Adobe Commerce on Cloud], o pacote `ece-tools` gera a configuração `app/etc/env.php` resultante durante a implantação com base na configuração da variável de implantação em `.magento.env.yaml`. Você não edita o arquivo `env.php`.  Consulte [Práticas recomendadas para a configuração do serviço Valkey e Redis](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/redis-valkey-service-configuration) e [Implantar variáveis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy).

O aplicativo Commerce usa um front-end e back-end de cache de baixo nível para fornecer acesso ao armazenamento em cache. O Commerce oferece suporte a vários back-end e estratégias de armazenamento em cache, cada um adequado a casos de uso diferentes. Esta página descreve as infraestruturas disponíveis e a sua diferença.

>[!NOTE]
>
>[Verniz](config-varnish-install.md) lida com o armazenamento em cache de página inteira no nível HTTP para implantações locais. O [Fastly service](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly) o manipula para implantações na Nuvem. Nenhuma das soluções usa o back-end do cache de baixo nível.

## Opções de cache de back-end

A tabela a seguir resume os caches de backend disponíveis:

| Infraestrutura | Descrição | Guia de configuração |
| ------- | ----------- | ------------------- |
| Sistema de arquivos | Padrão. Armazena dados do cache em arquivos em `var/cache/`. Nenhuma configuração é necessária. | N/D |
| Redis | Armazenamento de dados na memória para cache de alto desempenho. | [Usar Redis para cache padrão](redis-pg-cache.md) |
| Valkey | Alternativa de código aberto e compatível com Redis. | [Usar Valkey para cache padrão](valkey-pg-cache.md) |
| Banco de dados | Mecanismo de cache personalizado apoiado por um banco de dados | [Criar mecanismos de cache personalizados](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching){target="_blank"} (documentação do Adobe Developer) |

>[!IMPORTANT]
>
>O cache Redis não é suportado para o Adobe Commerce 2.4.9 ou versões de patch posteriores a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 e 2.4.8-p4. Se você estiver atualizando para uma dessas versões, configure Valkey e atualize a configuração do cache para usá-la. Para [!DNL Adobe Commerce on-premises], consulte [configurar Valkey](config-valkey.md).

## Implementações de back-end de cache e L2 {#implementation-approaches}

O Commerce oferece suporte a back-end de cache direto e cache L2. Um back-end direto seleciona o armazenamento em cache. O cache L2 adiciona uma camada de cache local na frente do armazenamento remoto.

### Infraestruturas de cache diretas

A tabela a seguir resume os valores de configuração de back-end do cache para `<Commerce-install-dir>/app/etc/env.php`. Ele não ativa o cache L2.

| Versão do Commerce | Infraestrutura | Valor de configuração |
| ---------------- | ------- | -------------------- |
| 2.4.8 e anterior, quando suportado | arquivo | Padrão. Nenhuma configuração é necessária |
| 2.4.8 e anterior, quando suportado | Redis | `Magento\Framework\Cache\Backend\Redis` |
| 2.4.8 e anterior, quando suportado | Valkey | `Magento\Framework\Cache\Backend\Valkey` |
| 2.4.9 e posteriores, além de portas de apoio compatíveis | arquivo | `file` |
| 2.4.9 e posteriores, além de portas de apoio compatíveis | Valkey | `valkey` |

Para obter suporte exato em nível de patch, consulte os [Requisitos do sistema](../../installation/system-requirements.md).

>[!TAB Cache baseado no Zend (2.4.8 e anterior)]

#### Exemplos de backend

Para implantações locais, os exemplos a seguir configuram back-ends de cache direto em `<Commerce-install-dir>/app/etc/env.php`. Eles não ativam o cache L2. Não use estes exemplos para [!DNL Adobe Commerce on Cloud] implantações, que usam o pacote `ece-tools` para gerar a configuração `app/etc/env.php` resultante durante a implantação.

>[!BEGINTABS]

>[!TAB Redis]

Use o nome completo da classe Redis apenas em versões em que o Redis é compatível:

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!TAB Chave de valor]

```php?start_inline=1
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379',
            ],
        ],
    ],
],
```

>[!ENDTABS]

## Cache L2

O cache L2 (de dois níveis) adiciona uma camada de cache local em cada nó da Web em frente ao armazenamento de cache remoto compartilhado, reduzindo o tráfego de rede entre o Commerce e o cache remoto. Para opções de implementação, suporte de versão e etapas de configuração, consulte [configuração do cache L2](level-two-cache.md).

Para projetos na nuvem, configure o cache L2 por meio das variáveis de implantação descritas em [Implantar variáveis](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy){target="_blank"}.

- [Usar Redis para cache padrão](redis-pg-cache.md)
- [Usar Valkey para cache padrão](valkey-pg-cache.md)
- [Configuração do cache L2](level-two-cache.md)
