---
title: 'Política de aplicação de segurança: ações e prazos obrigatórios'
description: Saiba mais sobre a aplicação de segurança para versões e dependências de software não compatíveis do Adobe Commerce na nuvem, incluindo prazos, ações necessárias e riscos.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2: id: b5f00040-57a0-4a6d-a39e-383b1936c2c9id: ba9e5be9-7de1-4f71-a5d2-baead0e425eeid: c32adafa-ed01-4b31-997e-2413013911b0id: cc250cf1-34eb-4863-80d0-d170d45ea067id: d1e21356-0064-4f48-9089-16e3f0dbd2a6id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2: id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2: id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Adobe Commerce somente na nuvem" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce na nuvem."
hide: true
source-git-commit: 93446d5be993e53e94f714a592d519a945dfbebd
workflow-type: tm+mt
source-wordcount: 1915
ht-degree: 0%

---

# Política de aplicação de segurança: ações e prazos necessários

O Adobe impõe requisitos de segurança para o Adobe Commerce em ambientes na nuvem, incluindo versões de dependência de software compatíveis e versões Adobe Commerce compatíveis. Esta página descreve o que é necessário, as datas de imposição e o que acontece se os requisitos não forem atendidos.

## O que está acontecendo?

A política de segurança corporativa da Adobe exige que todos os ambientes hospedados pela Adobe para o Adobe Commerce na nuvem sejam executados em software seguro e compatível.

1. Versões compatíveis de todas as dependências de software de terceiros (PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)

1. Adobe Commerce na nuvem (versão 2.4.8, 2.4.9 ou a versão mais recente)

Isso é para reduzir os riscos de segurança em seus ambientes de comércio eletrônico. Os ambientes que não atenderem a esses requisitos dentro dos prazos da [Tabela 1](#determine-your-required-actions) terão o tráfego de entrada suspenso, colocando a vitrine offline. Considere este aviso como um requisito de segurança e conformidade com as datas de imposição.

Talvez seja necessário executar duas ações.

1. Verifique se as dependências de software de terceiros são suportadas. Caso contrário, atualize para uma versão compatível.

1. Verifique se é necessário atualizar a versão do Adobe Commerce na nuvem para uma versão compatível.

### Determine as ações necessárias

Na tabela a seguir, encontre sua versão do Adobe Commerce na nuvem abaixo para ver o que é necessário de você.

**Tabela 1: Ações e prazos obrigatórios por versão**

| **Sua versão** | **[Ação 1:<br>Atualizar dependências de software de terceiros](#action-1-upgrade-third-party-software-dependencies)** | **Ação 2:<br>[Atualize ou migre sua versão do Adobe Commerce](#action-2-upgrade-to-a-supported-adobe-commerce-version)** |
| --- | --- | --- |
| 2.4.4 ou 2.4.5 | Ação necessária até 30 de outubro de 2026. | Ação necessária até 1º de junho de 2027 |
| 2.4.6 ou 2.4.7 | Ação necessária até 30 de outubro de 2026 ou 31 de maio de 2027, dependendo do software. | Ação necessária até 1 de junho de 2028 |
| 2.4.8 ou 2.4.9 | Ação necessária até 30 de outubro de 2026 ou 31 de maio de 2027, dependendo do software. | Nenhuma ação necessária no momento |

## Quem não precisa tomar uma ação

O presente aviso não se aplica a:

* Clientes usando o [!DNL Adobe Commerce as a Cloud Service]
* Clientes que usam o Adobe Commerce na nuvem versão 2.4.8 ou 2.4.9 com dependências de software compatíveis em todos os ambientes

### Verificar suas versões atuais

Você precisa da ajuda do administrador de comércio eletrônico para percorrer as seguintes etapas e verificar qual versão está sendo executada em cada um dos ambientes do Adobe Commerce na nuvem.

#### Etapa 1: verificar a versão do Adobe Commerce na nuvem

1. Faça logon no painel de administração do Adobe Commerce.

   A versão atual deve ser exibida no canto inferior direito de qualquer página de Administrador.

1. Se a versão não for exibida no Admin, use a [Ferramenta de linha de comando do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"} para executar o comando da versão:

   ```shell
   bin/magento --version
   ```

#### Etapa 2: verificar versões de dependência de software

1. Faça logon no [Cloud Console](https://console.adobecommerce.com/).
1. Abra o projeto relevante e selecione o ambiente que deseja revisar.
1. Verifique a configuração de serviço desse ambiente no arquivo `.magento/services.yaml`, que define os nomes e as versões de serviço com suporte usados pelo Adobe Commerce na infraestrutura em nuvem.
Para obter instruções detalhadas, consulte a documentação [Configurar serviços](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}.

## Por que essa exigência de segurança é importante

O software que passou pelo fim do suporte do fornecedor não recebe mais patches de segurança, o que significa que os problemas de segurança conhecidos nesse software não podem ser corrigidos. Além disso, de acordo com a [Política de Ciclo de Vida do Adobe](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy):

* **As versões 2.4.4 e 2.4.5** do Adobe Commerce agora recebem apenas correções de segurança limitadas e isoladas para o aplicativo principal até 31 de maio de 2027. Esse suporte limitado não inclui correções de qualidade, suporte de compatibilidade para dependências de aplicativos (por exemplo, PHP) ou atualizações de dependência de plataforma

* O **Adobe Commerce 2.4.6** receberá suporte estendido até 30 de agosto de 2027 e receberá apenas correções de segurança limitadas e isoladas para o aplicativo principal até 31 de maio de 2028

* O **Adobe Commerce versão 2.4.7** receberá suporte padrão até 31 de maio de 2027, e suporte estendido até 31 de maio de 2028

* O **Adobe Commerce na Nuvem versões 2.4.8 e 2.4.9** permanece com suporte e não requer atualização de versão no momento.

Continuar a administrar sua loja de comércio eletrônico com software não suportado cria um risco real e crescente à segurança de sua empresa, incluindo sua capacidade de manter a conformidade com o PCI e proteger os dados de seus clientes.

>[!WARNING]
>
>Se o ambiente não atender aos requisitos pelos prazos detalhados na [Tabela de ações e prazos obrigatórios](#determine-your-required-actions), o Adobe será forçado a suspender o tráfego de entrada no ambiente afetado. Sua loja de comércio eletrônico ficará offline e não atenderá os compradores.

## O que é necessário para cada ação

### Ação 1: atualizar dependências de software de terceiros

Dependendo do software, todas as dependências de software não suportadas devem ser atualizadas com base nos cronogramas compartilhados na tabela abaixo. Você pode exibir seus ambientes no [Cloud Console](https://console.adobecommerce.com/). Para verificar as versões de dependência em execução em cada ambiente, consulte [Verificar versões de dependência de software](#check-software-dependency-versions). As atualizações de dependência de software se aplicam a todo o Adobe Commerce nas versões 2.4.4 a 2.4.9.

**Tabela 2: requisitos para atualização de dependência de software**

| Dependência | Versão | Deve atualizar para | Data de aplicação |
| --- | --- | --- | --- |
| PHP | 8.1 e inferior | 8.2 ou superior | 31 de maio de 2027 |
| MariaDB/Galera | 10.5 e inferior | 10.6 ou superior | 30 de outubro de 2026 |
| MariaDB/Galera | Maior que 10,5 mas inferior a 10,11 | 10.11 ou superior | 31 de maio de 2027 |
| Elasticsearch | qualquer versão | OpenSearch:<br><br>- versão 2.19 para clientes 2.4.4 e 2.4.5<br>- versão 3 para clientes 2.4.6 e superiores. | 30 de outubro de 2026 |
| OpenSearch | 1.x | versão 2.19 para clientes 2.4.4 e 2.4.5.<br>versão 3 para clientes 2.4.6 e superiores. | 31 de maio de 2027 |
| Redis | 5 e abaixo | Valkey 8 ou superior | 31 de maio de 2027 |
| RabbitMQ | 3.9 e inferior | 3.13 ou superior | 30 de outubro de 2026 |
| RabbitMQ | Maior que 3,9 mas inferior a 3,13 | 4.3 ou posterior | 31 de maio de 2027 |

#### Prepare-se para uma atualização de dependência de software de terceiros

O Adobe o ajudará a atualizar essas dependências de software diretamente.

* **Introdução**: abra um tíquete de suporte listando os ambientes que você precisa atualizar e as dependências envolvidas. Abra o tíquete pelo menos 30 dias antes da data de imposição para que nossa equipe possa agendar o trabalho.

* **Tempo de inatividade:** O Adobe confirmará a janela esperada com você ao agendar.

* **Testando:** atualize e valide um ambiente de não produção antes da produção. No mínimo, valide o check-out, a pesquisa, o carrinho e qualquer integração personalizada. Os requisitos se aplicam a todos os seus ambientes, portanto, planeje atualizar cada ambiente em vez de apenas a produção.

* **Compatibilidade:** A maioria dessas alterações são atualizações de versão no mesmo software e apresentam baixo risco. Os seguintes aspectos merecem mais atenção:

  * O **Elasticsearch para OpenSearch** e o **Redis para Valkey** são migrações para software diferente em vez de atualizações de versão. Talvez seja necessário atualizar o código personalizado, as extensões ou a configuração que fazem referência ao serviço original.
  * O **PHP 8.1 a 8.2** pode exibir descontinuações no código personalizado e em extensões de terceiros.

Se você usar extensões de terceiros, confirme com os fornecedores de extensão se as versões atuais deles são compatíveis com as versões de destino. Se você trabalhar com um integrador de soluções, envolva-o no planejamento e na validação.

### Ação 2: atualizar para uma versão compatível do Adobe Commerce

Se você precisar atualizar a versão do Adobe Commerce na nuvem, há duas opções:

1. [Atualizar para uma versão compatível do Adobe Commerce na nuvem](#upgrade-to-adobe-commerce-on-cloud-version-249)
1. [Migrar para o Adobe Commerce as a Cloud Service (plataforma SaaS)](#migrate-to-adobe-commerce-as-a-cloud-service)

A data de imposição da sua versão atual se aplica independentemente da opção escolhida.

**Tabela 3: Diretrizes e prazos para atualizar para um Adobe Commerce compatível na versão na nuvem**

| Versão atual | Ação | Data de aplicação |
| --- | --- | --- |
| Uso do Adobe Commerce na nuvem versão 2.4.4 ou 2.4.5 | Atualize para o Adobe Commerce na nuvem versão 2.4.9 (ou para a versão mais recente) ou migre para o Adobe Commerce as a Cloud Service | 1 de junho de 2027 |
| Uso do Adobe Commerce na nuvem versão 2.4.6 ou 2.4.7 | Atualize para o Adobe Commerce na nuvem versão 2.4.9 (ou para a versão mais recente) ou migre para o Adobe Commerce as a Cloud Service | 1 de junho de 2028 |
| Utilização do Adobe Commerce nas versões 2.4.8 ou 2.4.9 da nuvem | Nenhuma ação de atualização de versão do Adobe Commerce na nuvem é necessária no momento. Os prazos de dependência do software na Ação 1 ainda se aplicam. | n/d |

## Comparar suas opções

Para decidir qual opção se adapta às suas necessidades, consulte a tabela a seguir que compara o Adobe Commerce na nuvem versão 2.4.9 com o Adobe Commerce as a Cloud Service.

**Tabela 4: Adobe Commerce na nuvem vs. Adobe Commerce as a Cloud Service**

| | Adobe Commerce na nuvem versão 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| O que é | A versão mais recente do Adobe Commerce com cobertura de segurança completa, correções de qualidade e atualizações de dependência da plataforma. | A plataforma comercial totalmente gerenciada da Adobe, criada para inovação contínua sem a sobrecarga de atualização. [Saiba mais](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| Melhor para você se | Você deseja continuar gerenciando sua própria infraestrutura, upgrades e patches por enquanto. Você pode migrar para o Adobe Commerce as a Cloud Service quando estiver pronto. | Você quer deixar os ciclos de atualização para trás para sempre, reduzir seu custo total de propriedade e obter os recursos mais recentes da Adobe automaticamente, sem esforço extra. |
| Principal benefício | Atende aos requisitos de segurança atuais e, ao mesmo tempo, preserva a configuração existente. | Uma loja de ponta ultrarrápida, um catálogo altamente escalável, gerenciamento de ativos digitais nativos e IA gerativa integrada, tudo em uma infraestrutura gerenciada pela Adobe. |

## O que acontece se você não tomar uma ação?

Se um ambiente não atender a esses requisitos até as datas de imposição em [Determinar as ações necessárias](#determine-your-required-actions), a Adobe tomará as medidas apropriadas. Isso inclui a suspensão do tráfego para a infraestrutura afetada e, como resultado, sua loja de comércio eletrônico ficará offline.

Se um ambiente continuar a não ser compatível após a suspensão do tráfego, a Adobe poderá encerrar os serviços em nuvem, iniciando o processo de desativação. Como resultado da desativação, todos os dados e ativos no ambiente de comércio eletrônico hospedado, incluindo todas as instâncias, ambientes e ramificações, serão excluídos permanentemente e não poderão ser restaurados.

## Como o Adobe ajudará você

O Adobe oferece ferramentas e suporte para tornar sua transição o mais suave possível, seja para atualização ou migração.

### Atualização para o Adobe Commerce na nuvem versão 2.4.9

* **Relatório de Compatibilidade de Atualização:** O Adobe fornece um relatório detalhado que identifica exatamente o que a atualização para o Adobe Commerce versão 2.4.9 exige, incluindo tempo e escopo de custo. [Gerar seu relatório de compatibilidade de atualização](https://supportinsights.adobe.com/commerce/tab/main).

* **Atualização de Dependência de Software:** como não é possível atualizar diretamente as dependências de software, [abra um tíquete de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"} para que o Adobe resolva a atualização para você. Para obter detalhes, consulte [Configurar Serviços](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}.

### Migrar para o Adobe Commerce as a Cloud Service

O Adobe fornece ferramentas que reduzem o custo e o tempo de migração para o Adobe Commerce as a Cloud Service. Essas ferramentas se aplicam somente à migração. Eles não são usados para uma atualização de versão no Adobe Commerce na nuvem. Consulte a [visão geral da migração](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) para obter o guia de migração completo, incluindo caminhos e fases de migração.

* **Avaliação da migração:** classifica a complexidade da migração de suas personalizações. Consulte a [visão geral da Ferramenta de Avaliação de Migração](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migração de dados:** a [ferramenta de migração de dados em massa e incremental](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data) move seus dados para o novo ambiente do Adobe Commerce as a Cloud Service.

* **Migração de vitrine e extensão:** as [ferramentas de desenvolvedor e de migração assistidas por IA](https://developer.adobe.com/commerce/extensibility/developer-agent/) da Adobe, incluindo o [!DNL Adobe Developer App Builder] e o [!DNL Commerce Storefront powered by Edge Delivery Services], ajudam a acelerar a modernização da vitrine e a reformulação da extensão.

Em caso de dúvidas, entre em contato com a equipe de conta, o Gerente de Conta de Solução, o Especialista em Renovação ou os [Serviços de Suporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).
