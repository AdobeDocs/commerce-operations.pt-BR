---
title: Atualizar práticas recomendadas dos serviços
description: Saiba como manter atualizada a pilha de tecnologia de infraestrutura em nuvem do Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Atualizar práticas recomendadas dos serviços

Este artigo fornece recomendações para manter a pilha de tecnologia de infraestrutura em nuvem do Adobe Commerce atualizada e fornece links para recursos úteis.

## Produtos e versões afetados

Adobe Commerce na infraestrutura de nuvem 2.4.x e posterior

## Serviços de atualização

Atualize os serviços e componentes usados pela Adobe Commerce antes que atinjam ou estejam próximos da data de término da vida útil. Isso ajuda a acompanhar a conformidade com o PCI e diminuir as vulnerabilidades de segurança.

Os clientes nos planos iniciais podem se autoatender em atualizações de serviços. Consulte [Alterar versão do serviço](https://devdocs.magento.com/cloud/project/services.html#change-service-version) para obter detalhes sobre como fazer isso.

Os clientes com planos Pro só podem se autoservir em atualizações de serviços em seus [Ambiente de integração](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Para atualizações de serviços na Produção, você deve [enviar um tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando a atualização.

>[!WARNING]
>
>As atualizações de serviço não podem ser enviadas para o ambiente de produção sem um aviso de 48 horas úteis para a equipe de infraestrutura. Isso é necessário, pois precisamos garantir que temos um engenheiro de suporte de infraestrutura disponível para atualizar sua configuração dentro de um período desejado com o mínimo de tempo de inatividade para seu ambiente de produção.

Você pode exibir a lista de versões de serviço e datas de fim de vida no seguinte arquivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este arquivo não pode ser considerado uma única fonte de verdade. Em caso de dúvida, consulte os sites oficiais de fornecedores para obter essas tecnologias.

## Informações adicionais

[Requisitos do sistema](../../../installation/system-requirements.md)
