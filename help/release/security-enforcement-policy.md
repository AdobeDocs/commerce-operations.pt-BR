---
title: 'Segurança e conformidade: ações e prazos obrigatórios'
description: Saiba mais sobre a aplicação de segurança para versões e dependências de software não compatíveis do Adobe Commerce na nuvem, incluindo prazos, ações necessárias e riscos.
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce somente na nuvem" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplica-se somente ao Adobe Commerce na versão 2.4.4 a 2.4.9"
color: blue
source-git-commit: 79afa4fa95c425dfd4bc0fd894abc24db2d1b33b
workflow-type: tm+mt
source-wordcount: 2040
ht-degree: 0%

---


# Aviso de segurança e conformidade: ações e prazos necessários

>[!NOTE]
>
> **Aplica-se a:** ambientes Adobe Commerce on Cloud (PaaS) que executam as versões 2.4.4 a 2.4.9 do Adobe Commerce.
>
> Esta orientação não se aplica a ambientes [!DNL Adobe Commerce as a Cloud Service] (SaaS) ou a implantações locais do Adobe Commerce.

O panorama da cibersegurança está a mudar fundamentalmente, e os mecanismos defensivos que as empresas têm em vigor têm de evoluir rapidamente. A segurança é fundamental para as empresas de comércio eletrônico porque as transações on-line exigem que elas lidem com dados pessoais e comerciais confidenciais, expondo-as a riscos financeiros e de identidade em caso de violação. Os ambientes de comércio eletrônico PaaS têm um modelo de responsabilidade de segurança compartilhada entre a Adobe e nossos clientes, em que os clientes são responsáveis pela manutenção das dependências da camada de aplicativo, pelas integrações com software de terceiros e pelos pipelines de implantação.

Na Adobe, abordamos proativamente a evolução dos riscos e garantimos que nossos clientes do Adobe Commerce on Cloud sejam configurados com os mais altos padrões de segurança. Isso inclui:

* Correções de segurança mensais e isoladas para uma proteção mais rápida e previsível contra vulnerabilidades críticas
* Versões anuais de patches com suporte a longo prazo
* Políticas de ciclo de vida simplificadas para cada versão com uma janela de suporte de 3 anos

Embora a Adobe siga as etapas necessárias para manter nossos clientes seguros, o [modelo de responsabilidade compartilhada](../security-and-compliance/shared-responsibility.md) para o Adobe Commerce na Nuvem exige que nossos clientes estejam sempre em uma versão com suporte do Adobe Commerce na Nuvem e de software de terceiros, apliquem patches de aplicativos, auditem extensões de terceiros e protejam o código personalizado. O software que passou pelo fim do suporte do fornecedor não recebe mais patches de segurança, deixando problemas de segurança no software sem solução. Continuar executando sua loja de comércio eletrônico em software não suportado cria um risco de segurança real e crescente.

Esta página descreve as ações que todos os clientes do Adobe Commerce na nuvem (versões 2.4.4 a 2.4.9) precisam tomar para garantir que seus ambientes de comércio eletrônico permaneçam seguros, juntamente com as datas de aplicação e o que esperar quando os requisitos de segurança não forem atendidos.

## Ações necessárias para manter um ambiente seguro e compatível

Para manter seu ambiente de comércio eletrônico seguro e compatível, todos os clientes do Adobe Commerce na nuvem devem usar:

1. Versões compatíveis de todas as dependências de software de terceiros: PHP, MariaDB, Elasticsearch/OpenSearch, Redis e RabbitMQ

1. Uma versão segura e compatível do Adobe Commerce na nuvem

Siga as diretrizes abaixo para verificar se é necessário tomar medidas para proteger o Adobe Commerce em ambientes na nuvem. Os ambientes que não atenderem aos requisitos de segurança dentro dos prazos descritos na Tabela 1 abaixo terão o tráfego de entrada suspenso, colocando a vitrine offline. Se você tiver dúvidas sobre o cumprimento do prazo e precisar de uma breve extensão, contate a equipe de conta ou o [Suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) da Adobe.

**Tabela 1: Requisitos e prazos de segurança**

| Sua versão do Adobe Commerce na nuvem | Atualização para dependências de software de terceiros compatíveis | Atualize para a versão mais recente do Adobe Commerce na nuvem ou migre para [!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4 ou 2.4.5 | Exigido até 30 de outubro de 2026. | Exigido até 1 de junho de 2027 |
| 2.4.6 ou 2.4.7 | Exigido até 30 de outubro de 2026 ou 31 de maio de 2027, dependendo do software. | Exigido até 1 de junho de 2028 |
| 2.4.8 ou 2.4.9 | Exigido até 30 de outubro de 2026 ou 31 de maio de 2027, dependendo do software. | Não é obrigatório neste momento |

## Etapas detalhadas para proteger seu ambiente

### Ação 1: verificar e atualizar dependências de software de terceiros

Verifique se o seu ambiente está executando versões compatíveis com fornecedores das seguintes dependências de software de terceiros: PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ. Caso contrário, atualize a dependência do software para uma versão compatível.

#### Etapa 1: verifique suas versões de dependência de software de terceiros

1. Entre no [Cloud Console](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/start/cloud-console).
2. Abra o projeto relevante e selecione o ambiente que deseja revisar.
3. Verifique a configuração de serviço desse ambiente no arquivo `.magento/services.yaml`, que define os nomes e as versões de serviço com suporte usados pelo Adobe Commerce na Nuvem.

Para obter instruções detalhadas, consulte [Configurar Serviços](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

Todas as dependências de software não suportadas devem ser atualizadas para as versões descritas pelos cronogramas na Tabela 2 abaixo.

**Tabela 2: atualizações de dependência necessárias**

| Dependência | Versão | Deve atualizar para | Prazo |
| --- | --- | --- | --- |
| PHP | 8.1 e inferior | 8.2 ou superior | 31 de maio de 2027 |
| MariaDB/Galera | 10.5 e inferior | 10.6 ou superior | 30 de outubro de 2026 |
| MariaDB/Galera | Maior que 10,5 mas inferior a 10,11 | Versão 10.11 ou superior | 31 de maio de 2027 |
| Elasticsearch | qualquer versão | OpenSearch: versão 2.19 para clientes 2.4.4 e 2.4.5. Versão 3 para clientes 2.4.6 e superiores. | 30 de outubro de 2026 |
| OpenSearch | 1.x | Versão 2.19 para clientes das versões 2.4.4 e 2.4.5. Versão 3 para clientes 2.4.6 e superiores. | 31 de maio de 2027 |
| Redis | 5 e abaixo | Valkey versão 8 ou superior | 31 de maio de 2027 |
| RabbitMQ | 3.9 e inferior | Versão 3.13 ou superior | 30 de outubro de 2026 |
| RabbitMQ | Maior que 3,9 mas inferior a 3,13 | 4.3 ou posterior | 31 de maio de 2027 |

#### Etapa 2: Prepare-se para uma atualização de dependência de software de terceiros

O Adobe o ajudará a atualizar essas dependências de software diretamente.

* **Introdução**: abra um [tíquete de suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) listando os ambientes que você precisa atualizar e as dependências envolvidas. Abra o tíquete pelo menos 30 dias antes da data de imposição para que a Adobe possa agendar o trabalho.

* **Tempo de inatividade:** o Adobe confirma a janela esperada com você ao agendar.

* **Testando:** atualize e valide um ambiente de não produção antes da produção. No mínimo, valide o check-out, a pesquisa, o carrinho e qualquer integração personalizada. Os requisitos se aplicam a todos os seus ambientes, portanto, planeje atualizar cada ambiente em vez de apenas a produção.

* **Compatibilidade:** A maioria dessas alterações são atualizações de versão no mesmo software e apresentam baixo risco. As seguintes mudanças exigem mais atenção:

  * O **Elasticsearch para OpenSearch** e o **Redis para Valkey** são migrações para software diferente em vez de atualizações de versão. Talvez seja necessário atualizar o código personalizado, as extensões ou a configuração que fazem referência ao serviço original.
  * A atualização do **PHP 8.1 para o 8.2** pode exibir avisos de desativação no código personalizado e em extensões de terceiros.

Se você usa extensões de terceiros, confirme com seus fornecedores que as versões atuais deles oferecem suporte às versões de software de destino. Se você trabalhar com um integrador de soluções, envolva-os antecipadamente no planejamento de atualização, no teste e na validação.

### Ação 2: verificar a versão do Commerce na nuvem e atualizar para uma versão compatível

Verifique qual versão do Adobe Commerce na nuvem seus ambientes executam. Se algum ambiente não tiver uma versão com suporte, você poderá atualizar para a versão 2.4.9 ou a versão com suporte mais recente, ou migrar para o [!DNL Adobe Commerce as a Cloud Service].

#### Etapa 1: verifique a versão do Adobe Commerce na nuvem e a ação necessária

1. Faça logon no painel de administração do Adobe Commerce.

   A versão atual é exibida no canto inferior direito de qualquer página de Administrador.

1. Se a versão estiver oculta no painel Admin:

   * Conecte-se ao [ambiente remoto](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/secure-connections#connect-to-a-remote-environment).
   * Use a [Ferramenta de linha de comando](../configuration/cli/config-cli.md) do Adobe Commerce para verificar a versão.

     ```shell
     bin/magento --version
     ```

Verifique as ações necessárias para a sua versão do Adobe Commerce na tabela abaixo.

**Tabela 3: requisitos de atualização da versão do Adobe Commerce na nuvem**

| Versão atual do Adobe Commerce na nuvem | Ação necessária | Prazo |
|---|---|---|
| Versão 2.4.4 ou 2.4.5 | Atualize para o Adobe Commerce na versão 2.4.9 (ou a versão mais recente) ou migre para o [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: as versões 2.4.4 e 2.4.5 recebem apenas correções de segurança limitadas e isoladas para o aplicativo principal até 31 de maio de 2027 — isso não inclui correções de qualidade, suporte de compatibilidade para dependências de aplicativos (por exemplo, PHP) ou atualizações de dependência de plataforma. Consulte a [Política de ciclo de vida](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) da Adobe. | 1 de junho de 2027 |
| Versão 2.4.6 ou 2.4.7 | Atualize para o Adobe Commerce na versão 2.4.9 (ou a versão mais recente) ou migre para o [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: a versão 2.4.6 recebe suporte estendido até 30 de agosto de 2027 e recebe apenas correções de segurança limitadas e isoladas para o aplicativo principal até 31 de maio de 2028. A versão 2.4.7 recebe suporte padrão até 31 de maio de 2027 e suporte estendido até 31 de maio de 2028. Consulte a [Política de ciclo de vida](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy) da Adobe. | 1 de junho de 2028 |
| Versão 2.4.8 ou 2.4.9 | Nenhuma ação de atualização de versão do Adobe Commerce na nuvem é necessária. Os prazos de dependência de software de terceiros na Ação 1 ainda se aplicam.<br>Motivo: nenhum prazo foi definido. | Não é obrigatório neste momento |

#### Etapa 2: Determinar o caminho de atualização ou migração

Se você precisar atualizar a versão do Adobe Commerce na nuvem, há duas opções:

1. Atualizar para uma versão compatível do Adobe Commerce na nuvem
1. Migrar para [!DNL Adobe Commerce as a Cloud Service] (SaaS)

Para ajudá-lo a decidir o melhor caminho, use a tabela a seguir para comparar suas opções:

**Tabela 4: Comparação entre o Adobe Commerce na nuvem e o[!DNL Adobe Commerce as a Cloud Service]**

| | Adobe Commerce na nuvem versão 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **O que é** | A versão mais recente do Adobe Commerce com cobertura de segurança completa, correções de qualidade e atualizações de dependência da plataforma. | A plataforma comercial totalmente gerenciada da Adobe, criada para inovação contínua sem a sobrecarga de atualização. [Saiba mais](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| **O melhor para você se** | Você deseja continuar gerenciando sua própria infraestrutura, upgrades e patches. | Você quer deixar os ciclos de atualização para trás para sempre, reduzir seu custo total de propriedade e obter os recursos mais recentes da Adobe automaticamente, sem esforço extra. |
| **Principais benefícios** | Atende aos requisitos de segurança e, ao mesmo tempo, preserva a configuração existente. | Uma loja de ponta ultrarrápida, um catálogo altamente escalável, gerenciamento de ativos digitais nativos e IA gerativa integrada, tudo em uma infraestrutura gerenciada pela Adobe. |

## O que acontece se nenhuma ação for tomada até o prazo?

A Adobe continua comprometida em ajudar você a tomar as medidas necessárias para atualizar para versões compatíveis do Adobe Commerce na nuvem e software de terceiros.

Se um ambiente não atender aos requisitos de segurança pelas datas de imposição compartilhadas acima, a Adobe será forçada a tomar as medidas apropriadas para garantir a segurança da base de instalação maior. Isso inclui a suspensão do tráfego para a infraestrutura afetada e, como resultado, sua loja de comércio eletrônico ficará offline.

Se um ambiente continuar a não ser compatível após a suspensão do tráfego, a Adobe poderá encerrar os serviços em nuvem, iniciando o processo de desativação. Como resultado da desativação, todos os dados e ativos no ambiente de comércio eletrônico hospedado, incluindo todas as instâncias, ambientes e ramificações, serão excluídos permanentemente e não poderão ser restaurados.

## Recursos para suporte de atualização ou migração

**Se você optar por atualizar para o Adobe Commerce na Cloud versão 2.4.9:**

* **Relatório de Compatibilidade de Atualização:** O Adobe fornece um relatório detalhado que identifica exatamente o que a atualização para o Adobe Commerce versão 2.4.9 exige, incluindo o escopo de custo. [Gere seu Relatório de Compatibilidade de Atualização](https://supportinsights.adobe.com/commerce/tab/main).

* **Atualização de dependência de software:** Como não é possível atualizar diretamente dependências de software, abra um [tíquete de suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) para que a Adobe possa realizar a atualização para você. Para obter detalhes, consulte [Configurar serviços](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

**Se você optar por migrar para [!DNL Adobe Commerce as a Cloud Service]:**

A Adobe fornece ferramentas que reduzem o custo e o tempo de migração para o [!DNL Adobe Commerce as a Cloud Service]. Eles estão disponíveis sem custo para você. Essas ferramentas se aplicam somente à migração. Eles não são usados para atualizações de versão do Adobe Commerce na nuvem. Consulte a [visão geral da migração](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) para obter o guia de migração completo, incluindo caminhos e fases de migração.

* **Avaliação da migração:** classifica a complexidade da migração de suas personalizações. Consulte a [visão geral da Ferramenta de Avaliação de Migração](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migração de dados:** a [ferramenta de migração de dados em massa e incremental](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool) move seus dados para o novo ambiente [!DNL Adobe Commerce as a Cloud Service].

* **Ferramentas de migração e desenvolvedor assistidas por IA:** a Adobe Developer App Builder e a Commerce Storefront, com a tecnologia da Edge Delivery Services, ajudam a acelerar a modernização da loja e a reformulação da extensão.

Em caso de dúvidas, entre em contato com a equipe de conta ou com os [Serviços de Suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

>[!MORELIKETHIS]
>
>* [Política de ciclo de vida](lifecycle-policy.md)
>* [Política de imposição de atualização de versão para Adobe Commerce na Nuvem](version-upgrade-enforcement-policy.md)
>* [Modelo operacional e de segurança de responsabilidade compartilhada](../security-and-compliance/shared-responsibility.md)
