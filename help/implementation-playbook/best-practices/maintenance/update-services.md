---
title: Práticas recomendadas do Update Services
description: Saiba como manter sua Adobe Commerce atualizada na pilha de tecnologia de infraestrutura em nuvem.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%
---
# Práticas recomendadas do Update Services

Este artigo fornece recomendações para manter sua pilha de tecnologia do Adobe Commerce na infraestrutura em nuvem atualizada e fornece links para recursos úteis.

## Produtos e versões afetados

Adobe Commerce na infraestrutura em nuvem 2.4.x e posterior

## Serviços de atualização

Atualize os serviços e componentes usados pelo Adobe Commerce antes de atingirem ou estarem próximos da data de término da vida útil. Isso ajuda a manter a conformidade com o PCI e a diminuir as vulnerabilidades de segurança.

Os clientes com planos iniciais podem realizar ações de autoatendimento em atualizações de serviços. Consulte [Alterar versão do serviço](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml#change-service-version) para obter detalhes sobre como fazer isso.

Os clientes com planos Pro só podem realizar autoatendimento em atualizações de serviços em seu [ambiente de integração](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27242). Para atualizações de serviços em Produção, você deve [enviar um tíquete de suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) solicitando a atualização.

>[!WARNING]
>
>As atualizações de serviço não podem ser enviadas para um ambiente de produção sem aviso prévio de 48 horas úteis para a equipe de infraestrutura da Adobe. Isso é necessário para que a Adobe possa garantir que um engenheiro de suporte de infraestrutura esteja disponível para atualizar sua configuração dentro de um período de tempo desejado com tempo de inatividade mínimo para o ambiente de produção. A Adobe recomenda colocar seu site no modo de manutenção durante a atualização do serviço.

Você pode exibir a lista de versões de serviço e datas de fim de vida útil no seguinte arquivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este arquivo não pode ser considerado uma única fonte da verdade. Se tiver dúvidas, consulte os sites oficiais dos fornecedores dessas tecnologias.

## Informações adicionais

[Requisitos do sistema](../../../installation/system-requirements.md)
