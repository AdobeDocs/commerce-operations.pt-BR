---
title: Práticas recomendadas do Update Services
description: Saiba como manter sua Adobe Commerce atualizada na pilha de tecnologia de infraestrutura em nuvem.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Práticas recomendadas do Update Services

Este artigo fornece recomendações para manter sua pilha de tecnologia do Adobe Commerce na infraestrutura em nuvem atualizada e fornece links para recursos úteis.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.x e posterior

## Serviços de atualização

Atualize os serviços e componentes usados pelo Adobe Commerce antes de atingirem ou estarem próximos da data de término da vida útil. Isso ajuda a manter a conformidade com o PCI e a diminuir as vulnerabilidades de segurança.

Os clientes com planos iniciais podem realizar ações de autoatendimento em atualizações de serviços. Consulte [Alterar versão do serviço](https://devdocs.magento.com/cloud/project/services.html#change-service-version) para obter detalhes sobre como fazer isso.

Os clientes com planos Pro só podem realizar autoatendimento em atualizações de serviços em seus [Ambiente de integração](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Para atualizações de serviços na produção, é necessário [enviar um tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando a atualização.

>[!WARNING]
>
>As atualizações de serviço não podem ser enviadas para o ambiente de produção sem aviso prévio de 48 horas úteis para nossa equipe de infraestrutura. Isso é necessário, pois precisamos garantir que tenhamos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um prazo desejado com tempo de inatividade mínimo para seu ambiente de produção.

Você pode exibir a lista de versões de serviço e datas de fim da vida útil no seguinte arquivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este arquivo não pode ser considerado uma única fonte da verdade. Se tiver dúvidas, consulte os sites oficiais dos fornecedores dessas tecnologias.

## Informações adicionais

[Requisitos do sistema](../../../installation/system-requirements.md)
