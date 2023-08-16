---
title: Managed Services
description: Analise as responsabilidades do Adobe Managed Services, dos clientes e dos provedores de serviços em nuvem com relação à implementação da infraestrutura em nuvem do Adobe Commerce.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Managed Services

Os serviços gerenciados do Adobe Commerce na infraestrutura em nuvem são seguros por padrão.

![Diagrama que mostra os serviços gerenciados da Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilidade compartilhada

Os planos do Adobe Commerce Pro dependem de um modelo de segurança de responsabilidade compartilhada. Neste modelo, as diferentes partes têm diferentes áreas de responsabilidade para manter a segurança do sistema. Essa abordagem permite flexibilidade e uso das melhores tecnologias em nuvem do setor.

![Diagrama que mostra o modelo de responsabilidade compartilhada do Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### responsabilidades do Adobe Managed Services

O Adobe Managed Services é responsável pela segurança e disponibilidade do ambiente de nuvem do Adobe Commerce Pro, do código principal do aplicativo Adobe Commerce Pro e dos sistemas de comércio interno. Isso inclui, mas não está limitado a:

- Patches no nível do servidor
- Operar os serviços necessários para fornecer os planos do Adobe Commerce Pro
- Teste de vulnerabilidade
- Registro e monitoramento de eventos de segurança
- Gerenciamento de incidentes
- Monitoramento operacional
- Suporte 24 horas
- Garantir que a infraestrutura do cliente esteja disponível de acordo com os SLAs

O Adobe Managed Services também é responsável pelo gerenciamento de configurações de firewall de servidor (iptables) e configurações de firewall de perímetro (grupos de segurança). O Adobe também pode lançar atualizações de segurança para o aplicativo principal periodicamente. É responsabilidade dos clientes aplicar esses patches. Todas essas áreas estão cobertas pela Certificação PCI do sistema de infraestrutura em nuvem da Adobe Commerce.

### Responsabilidades do AWS

O Adobe Managed Services usa o Amazon Web Services (AWS) para a infraestrutura do servidor em nuvem. A AWS é responsável pela segurança da rede, incluindo roteamento, comutação e segurança de perímetro através de sistemas de firewall e sistemas de detecção de intrusão (IDS). A AWS é responsável pela segurança física para os data centers que gerenciam os ambientes de nuvem do Adobe Commerce, bem como pela segurança ambiental para garantir que os controles adequados de energia, resfriamento e mecanismo estejam em vigor.

Os planos do Adobe Commerce Pro usam:

- Amazon Elastic Compute Cloud (EC2)
- Serviço de armazenamento simples Amazon (S3)
- Loja de bloco elástico (EBS) do Amazon
- Nuvem privada virtual (VPC) do Amazon
- Balanceador de carga elástico (ELB) do Amazon
- Serviços de rastreamento em nuvem da Amazon.

A Amazon tem um amplo programa de conformidade, que inclui certificações PCI DSS, SOC 2 e ISO 27001.

### Responsabilidades do parceiro/cliente da solução

O cliente é o principal responsável pela segurança da implementação personalizada do aplicativo do Adobe Commerce em execução no ambiente de nuvem do plano do Adobe Commerce Pro. Isso inclui:

- Garantir uma configuração e codificação seguras do aplicativo e atividades de monitoramento de segurança, incluindo testes de penetração e verificações regulares de vulnerabilidade.

- A segurança de qualquer personalização, extensão, outro aplicativo ou integração usada no sistema.

- A segurança de seus usuários e a concessão de acesso a sua configuração e aplicativo.

- O cliente controla todas as implantações de código em seus ambientes de não produção. Esse controle também tem a responsabilidade de aplicar patches de segurança de aplicativos ao aplicativo principal do Adobe Commerce, às extensões ou a qualquer código personalizado.

- O cliente deve realizar testes de inserção do aplicativo personalizado. Essas responsabilidades podem ser tratadas pelos recursos técnicos do cliente, pelos parceiros de implementação ou pelos serviços profissionais da Adobe Commerce.

- Os clientes são responsáveis pelos requisitos do PCI de seus aplicativos personalizados e de seus próprios processos. A conformidade PCI do cliente baseia-se nas certificações PCI da AWS e da Adobe Commerce para minimizar as áreas que devem ser analisadas.
