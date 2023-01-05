---
title: Práticas recomendadas para processamento e armazenamento de pagamentos
description: Saiba como processar e armazenar com segurança detalhes de pagamento
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Práticas recomendadas para processamento e armazenamento de pagamentos

Um dos princípios fundamentais para a manutenção [Conformidade com a PCI](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) A tem uma estratégia para processar e armazenar adequadamente os pagamentos com cartão de crédito.

O armazenamento de dados de titulares de cartão no Adobe Commerce é **estritamente proibido** e fazer isso pode ser uma violação de suas obrigações como comerciante sob o padrão PCI-DSS (Payment Card Industry Data Security Standard, padrão de segurança de dados do setor de cartões de pagamento). Mais informações sobre nosso modelo de responsabilidade compartilhada e diretrizes para obrigações de comerciantes podem ser encontradas em nosso [guia de responsabilidade compartilhada do Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) no Adobe Trust Center.

Recomendamos seguir as práticas recomendadas abaixo para ajudar a garantir que você esteja processando corretamente as informações de pagamento no site de comércio eletrônico. Orientações adicionais sobre as práticas recomendadas gerais de segurança podem ser encontradas em nosso [guia de práticas recomendadas de segurança para o Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) sobre o Centro de Confiança do Adobe

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

* Adobe Commerce na infraestrutura de nuvem
* Adobe Commerce no local

## Proteção de dados do titular do cartão

Se o armazenamento de dados do titular do cartão for necessário, os dados do titular do cartão deverão ser armazenados fora da Adobe Commerce com proteções de armazenamento. A existência de salvaguardas de armazenamento para os detalhes do pagamento, como os dados do titular do cartão de crédito, ajuda a evitar fraudes e outras potenciais questões de segurança. De acordo com outros padrões PCI, ter proteções em vigor é a primeira linha de defesa. Alguns métodos preferidos para aprimorar as proteções dos dados armazenados incluem criptografia, truncamento, tokenização, hash unidirecional e mascaramento.

As proteções das chaves criptográficas são vitais para as estratégias de proteção de dados. É importante ter custodiantes qualificados e confiáveis que supervisionem essas chaves.

Por fim, um número de conta principal (PAN) deve estar ilegível durante o armazenamento (por exemplo, mascarado como XXX). Isso inclui armazenamento portátil e mídia de backup, como unidades flash, USB e discos rígidos externos, e até registros de auditoria.

## Criptografar transmissão de dados do titular do cartão

A proteção dos dados durante a transmissão é fundamental para a proteção das informações sobre pagamentos, como os dados do titular do cartão. Quando esta informação é transmitida através de redes abertas, pode tornar-se mais vulnerável a questões de segurança.

### Usar protocolos de transmissão seguros

Transmitir dados do titular do cartão usando protocolos e práticas de transmissão seguras, incluindo:

* Chaves e certificados confiáveis
* Protocolos de transmissão segura, como TLS, SSH ou VPN
* Algoritmos assimétricos na criptografia
* Tokenização, mascaramento e teste de penetração com a transmissão e exibição de PANs
* Restringir o acesso aos dados do titular do cartão
* O acesso a informações sensíveis deve ser limitado em função da necessidade de saber e concedido apenas ao pessoal autorizado com necessidades comerciais

O método recomendado para lidar com dados do titular do cartão é não armazenar o número da conta primária (PAN), mas sim tokenizar o cartão com um provedor de processamento de pagamento específico e armazenar o token, o tipo de cartão e a data de expiração criptografada. Você pode usar o token como uma credencial no arquivo para uso futuro, pois ele é exclusivo para cada comerciante somente. Como o token é exclusivo, se houver um problema de segurança, o token em será invalidado, o que ajuda a impedir a atividade fraudulenta

## Informações adicionais

Se você estiver procurando soluções de pagamento recomendadas pelo Adobe, considere [Serviços de pagamento Adobe](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
