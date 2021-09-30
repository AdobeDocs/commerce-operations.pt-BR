---
title: Managed Services
description: Revise as responsabilidades dos serviços gerenciados da Adobe, dos clientes e dos provedores de serviços em nuvem para a implementação do Adobe Commerce na infraestrutura em nuvem.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Serviços gerenciados

O Adobe Commerce em serviços gerenciados de infraestrutura em nuvem é seguro por padrão.

![Diagrama que mostra os serviços gerenciados do Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Responsabilidade compartilhada

Os planos do Adobe Commerce Pro dependem de um modelo de segurança de responsabilidade compartilhada. Neste modelo, as diferentes partes têm diferentes áreas de responsabilidade pela manutenção da segurança do sistema. Essa abordagem permite flexibilidade e uso das melhores tecnologias em nuvem.

![Diagrama mostrando o modelo de responsabilidade compartilhada do Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Responsabilidades dos serviços gerenciados pela Adobe

O Adobe Managed Services é responsável pela segurança e disponibilidade do ambiente de nuvem do Adobe Commerce Pro, pelo código de aplicativo principal do Adobe Commerce Pro e pelos sistemas de comércio interno. Isso inclui, mas não se limita a:

- Patch no nível do servidor
- Operar os serviços necessários para fornecer planos do Adobe Commerce Pro
- Teste de vulnerabilidade
- Registro e monitoramento de eventos de segurança
- Gestão de incidentes
- Acompanhamento operacional
- Suporte 24 horas por dia, 7 dias por semana
- Garantir que a infraestrutura do cliente esteja disponível de acordo com os SLAs

O Adobe Managed Services também é responsável pelo gerenciamento de configurações de firewall do servidor (iptables) e configurações de firewall de perímetro (grupos de segurança). O Adobe também pode lançar atualizações de segurança no aplicativo principal periodicamente. É responsabilidade dos clientes aplicar esses patches. Todas essas áreas são cobertas pela Certificação PCI do Adobe Commerce on cloud Infrastructure System.

### Responsabilidades AWS

O Adobe Managed Services usa o Amazon Web Services (AWS) para infraestrutura de servidor em nuvem. A AWS é responsável pela segurança da rede, incluindo roteamento, comutação e segurança da rede de perímetro por meio de sistemas de firewall e sistemas de detecção de intrusão (IDS). A AWS é responsável pela segurança física dos data centers que gerenciam os ambientes de nuvem do Adobe Commerce, bem como pela segurança ambiental para garantir que a energia, o resfriamento e os controles de mecanismo adequados estejam em vigor.

Os planos do Adobe Commerce Pro usam:

- Nuvem de computação elástica Amazon (EC2)
- Serviço de Armazenamento Simples da Amazon (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Balanceador de Carga Elástico Amazon (ELB)
- Serviços de trilha da Amazon Cloud.

A Amazon tem um extenso programa de conformidade, que inclui certificação PCI DSS, SOC 2 e ISO 27001.

### Responsabilidades do parceiro/cliente da solução

O cliente é responsável principalmente pela segurança da implementação personalizada do aplicativo Adobe Commerce em execução no ambiente de nuvem do Adobe Commerce Pro plan. Isso inclui:

- Garantir uma configuração e codificação seguras das atividades de monitoramento de segurança e do aplicativo, incluindo testes de penetração e verificações regulares de vulnerabilidade.

- A segurança de qualquer personalização, extensões, outros aplicativos ou integrações usadas em seus sistemas.

- A segurança dos seus utilizadores e a concessão de acesso à sua configuração e aplicação.

- O cliente controla todas as implantações de código em seus ambientes não relacionados à produção. Esse controle também é da responsabilidade de aplicar patches de segurança de aplicativos ao aplicativo principal do Adobe Commerce, extensões ou qualquer código personalizado.

- O cliente deve realizar testes de penetração de seu aplicativo personalizado. Essas responsabilidades podem ser abordadas por recursos técnicos pelo cliente, parceiros de implementação ou serviços profissionais do Adobe Commerce.

- Os clientes são responsáveis pelos requisitos do PCI de seu aplicativo personalizado e seus próprios processos. A conformidade com o PCI do cliente baseia-se nas certificações PCI do AWS e do Adobe Commerce, para minimizar as áreas que devem ser revisadas.
