---
title: Práticas recomendadas do Update Services
description: Saiba como manter sua Adobe Commerce atualizada na pilha de tecnologia de infraestrutura em nuvem.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
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
>As atualizações de serviço não podem ser enviadas para um ambiente de produção sem aviso prévio de 48 horas úteis para a equipe de infraestrutura do Adobe. Isso é necessário para que o Adobe possa garantir que um engenheiro de suporte de infraestrutura esteja disponível para atualizar sua configuração dentro de um período de tempo desejado com tempo de inatividade mínimo para o ambiente de produção. A Adobe recomenda colocar seu site no modo de manutenção durante a atualização do serviço.

Você pode exibir a lista de versões de serviço e datas de fim de vida útil no seguinte arquivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este arquivo não pode ser considerado uma única fonte da verdade. Se tiver dúvidas, consulte os sites oficiais dos fornecedores dessas tecnologias.

## Informações adicionais

[Requisitos do sistema](../../../installation/system-requirements.md)
