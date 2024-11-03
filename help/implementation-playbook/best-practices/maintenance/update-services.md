---
title: Práticas recomendadas do Update Services
description: Saiba como manter sua Adobe Commerce atualizada na pilha de tecnologia de infraestrutura em nuvem.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Práticas recomendadas do Update Services

Este artigo fornece recomendações para manter sua pilha de tecnologia do Adobe Commerce na infraestrutura em nuvem atualizada e fornece links para recursos úteis.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.x e posterior

## Serviços de atualização

Atualize os serviços e componentes usados pelo Adobe Commerce antes de atingirem ou estarem próximos da data de término da vida útil. Isso ajuda a manter a conformidade com o PCI e a diminuir as vulnerabilidades de segurança.

Os clientes com planos iniciais podem realizar ações de autoatendimento em atualizações de serviços. Consulte [Alterar versão do serviço](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) para obter detalhes sobre como fazer isso.

Os clientes com planos Pro só podem realizar autoatendimento em atualizações de serviços em seu [ambiente de integração](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Para atualizações de serviços em Produção, você deve [enviar um tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando a atualização.

>[!WARNING]
>
>As atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção.

Você pode exibir a lista de versões de serviço e datas de fim de vida útil no seguinte arquivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este arquivo não pode ser considerado uma única fonte da verdade. Se tiver dúvidas, consulte os sites oficiais dos fornecedores dessas tecnologias.

## Informações adicionais

[Requisitos do sistema](../../../installation/system-requirements.md)
