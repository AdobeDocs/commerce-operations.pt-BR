---
title: Práticas recomendadas para processamento e armazenamento de pagamentos
description: Saiba como processar e armazenar com segurança os detalhes de pagamento
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Práticas recomendadas para processamento e armazenamento de pagamentos

Um dos princípios-chave para manter a [conformidade com o PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html?lang=pt-BR) é ter uma estratégia para processar e armazenar corretamente os pagamentos com cartão de crédito.

O armazenamento de dados de titulares de cartão no Adobe Commerce é **estritamente proibido**, e isso pode ser uma violação de suas obrigações como comerciante, de acordo com o PCI-DSS (Payment Card Industry Data Security Standard, padrão de segurança de dados do setor de cartões de pagamento). Mais informações sobre o modelo de responsabilidade compartilhada e as diretrizes para obrigações do comerciante estão disponíveis no [Guia de Modelo de Responsabilidade Compartilhada da Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) na Central de Confiabilidade da Adobe.

Siga as práticas recomendadas abaixo para garantir o processamento correto das informações de pagamento no seu site de comércio eletrônico. Para obter orientações adicionais sobre práticas recomendadas de segurança, consulte [Proteger o site e a infraestrutura](../launch/security-best-practices.md).

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

* Adobe Commerce na infraestrutura em nuvem
* Adobe Commerce no local

## Protegendo dados de titulares de cartão

Se o armazenamento dos dados de titulares de cartão for necessário, os dados devem ser armazenados fora da Adobe Commerce com proteções de armazenamento. Ter salvaguardas de armazenamento em vigor para detalhes de pagamento, como dados de titulares de cartão de crédito, ajuda a evitar fraudes e outros possíveis problemas de segurança. De acordo com outros padrões PCI, ter proteções é a primeira linha de defesa. Alguns métodos preferidos para melhorar a proteção dos dados armazenados incluem criptografia, truncamento, geração de tokens, hash unidirecional e mascaramento.

As proteções para chaves criptográficas são vitais para as estratégias de proteção de dados. É essencial ter custodiantes qualificados e confiáveis supervisionando essas chaves.

Finalmente, um número de conta principal (PAN) deve ser ilegível durante o armazenamento, por exemplo, mascarado com `XXX`. Isso inclui mídias portáteis de armazenamento e backup, como unidades flash, USB e discos rígidos externos, e até mesmo registros de auditoria.

## Criptografar a transmissão de dados de titulares de cartão

A proteção dos dados durante a transmissão é fundamental para proteger as informações de pagamento, como os dados de titulares de cartão. Quando essas informações são transmitidas por redes abertas, elas podem se tornar mais vulneráveis a problemas de segurança.

### Usar protocolos de transmissão seguros

Transmitir dados de titulares de cartão usando protocolos e práticas de transmissão seguros, incluindo:

* Chaves e certificados confiáveis
* Protocolos de transmissão seguros, como TLS, SSH ou VPN
* Algoritmos assimétricos na criptografia
* Testes de tokenização, mascaramento e penetração com transmissão e exibição de PANs
* Restringir o acesso aos dados de titulares de cartão
* O acesso a informações sensíveis deve ser limitado com base no princípio da &quot;necessidade de conhecer&quot; e concedido apenas a pessoal autorizado com necessidades comerciais

O método recomendado para lidar com dados de titulares de cartão é criar um token dos dados, em vez de armazená-los. Crie um token do cartão com um provedor de processamento de pagamento específico e armazene o token, o tipo de cartão e a data de expiração criptografada. Você pode usar o token como uma credencial no arquivo para uso futuro, pois ele é exclusivo somente para cada comerciante. Como o token é exclusivo, se houver um problema de segurança, o token será invalidado, o que ajuda a evitar atividades fraudulentas.

## Informações adicionais

Se você estiver procurando soluções de pagamento recomendadas pela Adobe, considere os [Serviços de Pagamento da Adobe](https://experienceleague.adobe.com/docs/commerce/payment-services/overview.html?lang=pt-BR).
