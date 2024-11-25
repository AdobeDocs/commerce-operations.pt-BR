---
title: Suporte e manutenção pós-lançamento
description: Garanta o desempenho e a segurança ideais da loja Adobe Commerce com nosso abrangente suporte pós-lançamento e práticas recomendadas de manutenção.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Suporte e manutenção pós-lançamento do Adobe Commerce

O suporte e a manutenção pós-lançamento são cruciais para garantir que sua loja da Adobe Commerce funcione sem problemas, tenha bom desempenho, permaneça segura e continue a atender aos seus objetivos de negócios. Esta fase envolve monitoramento contínuo, otimização, correção de erros, atualizações e suporte ao usuário. As seguintes seções dividem o **suporte pós-inicialização** em categorias principais:

## Monitoramento regular do site e otimização de desempenho

### Monitoramento de desempenho

- **Teste de carga e velocidade do site**: o Adobe Commerce pode consumir muitos recursos, portanto, o monitoramento regular do desempenho é fundamental.

   - **Ferramentas para usar**: todos os projetos de infraestrutura em nuvem do Adobe Commerce incluem acesso ao New Relic, que auxilia no monitoramento do desempenho e na investigação de eventos no aplicativo e na infraestrutura em nuvem do Commerce. Ferramentas adicionais incluem Google PageSpeed Insights e GTMetrix.

   - **O que monitorar**: estes são os principais itens a serem monitorados para o Adobe Commerce na infraestrutura em nuvem:

      - **Notificações de integridade**: Alertas de espaço em disco e integridade do ambiente.

      - **Observação**: monitoramento abrangente combinando dados de log de várias fontes para um gerenciamento de site eficaz.

      - **Serviço New Relic**: monitora o desempenho no preparo e na produção, com foco nas métricas principais.

      - **Política de alertas gerenciada**: rastreia métricas com limites predefinidos para disparar notificações sobre problemas de infraestrutura ou aplicativos que afetam o desempenho.

  >[!TIP]
  >
  >Consulte o [monitoramento de desempenho](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) no _Guia da Nuvem_.


- **Otimizando o desempenho do banco de dados**: Para otimizar o desempenho do banco de dados no Adobe Commerce Cloud, implemente o seguinte:

   - **Monitorar e otimizar consultas do MySQL**: identifique e resolva consultas de execução lenta, o que pode ser feito usando os comandos SHOW FULL PROCESSLIST e EXPLAIN do MySQL. Para configurações mais complexas, os usuários da arquitetura Pro podem utilizar o Percona Toolkit para analisar registros de consultas para detectar problemas de desempenho.

   - **Gerenciamento de índice**: verifique se cada tabela tem uma chave primária e remova os índices duplicados, pois eles podem reduzir a eficiência e gerar conflitos durante gravações simultâneas.

   - **Otimização do trabalho do Cron**: os trabalhos do Cron devem ser agendados fora do horário de pico para minimizar o impacto no desempenho, especialmente se tarefas em segundo plano, como indexação, forem frequentes.

  >[!TIP]
  >
  >Consulte [práticas recomendadas para resolver problemas de desempenho do banco de dados](resolve-database-performance-issues.md).

- **Monitorar CDN**: para monitorar o desempenho do Fastly CDN no Adobe Commerce Cloud, você pode realizar as seguintes ações:

   - **Aproveite o New Relic para monitoramento**: a Adobe Commerce oferece o New Relic para monitorar o desempenho do Fastly e outras métricas em ambientes de preparo e produção. Essa ferramenta fornece informações sobre a integridade do servidor, o armazenamento em cache de CDN e as solicitações de rede ao longo do tempo, o que ajuda a identificar padrões e otimizar as configurações de CDN.

   - **Análise de logs do Fastly**: para projetos do Adobe Commerce Cloud Pro, você pode usar os Logs do New Relic para revisar e analisar os dados de log do Fastly CDN e do WAF para rastrear tendências de desempenho, eventos de segurança e diagnosticar erros ou problemas de latência.

   - **Usar comandos cURL**: execute comandos cURL com cabeçalhos específicos do Fastly para inspecionar o status do cache do site. Os principais cabeçalhos de resposta incluem `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` e `Cache-Control` para verificar o cache e o status do módulo. O Adobe fornece comandos cURL de amostra para ambientes de preparo e produção.

   - **Verifique as informações do cabeçalho**: cabeçalhos Inspect como `Cache-Control`, `Pragma` e `X-Magento-Tags` para confirmar o comportamento adequado de armazenamento em cache e o tratamento de marcas no conteúdo em cache. Os valores de cabeçalho adequados indicam se as configurações de cache são aplicadas efetivamente na CDN.

   - **Depuração e teste do Fastly**: use o recurso de depuração do Fastly para identificar e solucionar problemas com taxas de HIT e MISS de cache, lógica de cache ou respostas de cabeçalho incorretas, que podem apontar para problemas de configuração ou desalinhamento com as regras de cache esperadas.

Essas etapas de monitoramento ajudam a manter o desempenho ideal do CDN e abordam problemas que afetam a velocidade e a confiabilidade do site.

>[!TIP]
>
>Consulte a [Visão geral dos serviços do Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) no _Guia da Nuvem_.

#### Monitoramento de segurança regular

Para manter um monitoramento de segurança regular no Adobe Commerce Cloud, a Adobe recomenda uma abordagem multifacetada que envolve verificação contínua, registro e práticas de segurança ativas. Estas são algumas das ações principais para garantir a segurança contínua:

- **Verificação de segurança**: use a ferramenta de Verificação de Segurança do Adobe para monitorar vulnerabilidades e malware conhecidos em seus sites do Commerce. Essa ferramenta fornece alertas para possíveis riscos de segurança e problemas de conformidade.

- **Manutenção de patch e atualização regular**: aplique patches e atualizações de segurança do Adobe conforme eles se tornam disponíveis. Atualizar para a versão mais recente do Adobe Commerce garante as defesas mais recentes contra ameaças.

- **Auditoria e monitoramento de logs**: aproveite ferramentas como os logs do New Relic (disponíveis para projetos Pro) para centralizar e analisar logs de segurança de ambientes de preparo e produção, melhorando a visibilidade de possíveis problemas e violações de segurança.

- **Gerenciamento de conta e acesso**: faça uma auditoria regular em contas de usuário e de administrador para remover contas não autorizadas ou desatualizadas. Reforce os controles de acesso com autenticação multifator (MFA) para usuários administradores.

- **Firewall de aplicativo Web (WAF)**: use o Fastly WAF integrado para detectar e mitigar ameaças de padrões de tráfego mal-intencionado, como tentativas de extração de dados não autorizadas.

- **Segurança de código personalizado e extensão**: proteja qualquer código personalizado ou extensões de terceiros realizando auditorias de código regulares e limitando extensões às verificadas pelo Adobe.

>[!TIP]
>
>Consulte [Segurança](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) no _Guia de Sistemas do Administrador_.

#### Registro e monitoramento de erros

Para monitorar o registro de erros no Adobe Commerce Cloud, o Adobe fornece várias ferramentas e práticas para a solução eficaz de problemas e o gerenciamento de desempenho:

- **Agregação de logs com o New Relic**: a New Relic coleta e centraliza logs de aplicativos da Adobe Commerce, incluindo logs relacionados à infraestrutura, CDN e WAF. Essa configuração permite um rastreamento de erros simplificado, a criação de painéis e a consulta de logs para obter insights mais profundos sobre o desempenho e os problemas do aplicativo. O acesso aos logs do New Relic permite pesquisar e filtrar logs por vários atributos para diagnosticar problemas rapidamente.

- **Tipos de log de erros**: os principais logs de erros no Adobe Commerce Cloud incluem `cloud.log`, que contém comentários de implantação, e `cloud.error.log`, que registra avisos e erros de implantação. Outros logs específicos para depuração incluem `debug.log`, `system.log` e `exception.log`, com cada um atendendo funções distintas no rastreamento de erros e eventos na plataforma do Commerce.

- **Logs personalizados com o Monolog**: o Adobe Commerce oferece suporte ao logon personalizado via Monolog, que permite que os desenvolvedores direcionem mensagens de log para vários destinos, como arquivos, bancos de dados e até mesmo alertas. Essa flexibilidade é útil para criar estratégias avançadas de registro que atendam a diferentes necessidades de monitoramento em ambientes de desenvolvimento e produção.

- **Monitoramento de exceções com a ferramenta de análise do site**: a ferramenta de análise do site ajuda a monitorar e gerenciar logs de exceções, identificando problemas recorrentes na implantação e eventos de aplicativo. Essa ferramenta destaca problemas frequentes, facilitando a priorização e o tratamento de problemas críticos que afetam o desempenho.

>[!TIP]
>
>Para obter mais detalhes sobre práticas de registro e rastreamento de erros no Adobe Commerce Cloud, consulte [Gerenciamento de logs do New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) e [monitoramento de exceções](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Segurança e atualizações

#### Patches e atualizações de segurança

Para permanecer atualizado e garantir a segurança do seu sistema Adobe Commerce Cloud, veja a seguir algumas práticas importantes para o monitoramento de patches e atualizações de segurança:

- **Assinar alertas de segurança do Adobe Commerce**: mantenha-se informado sobre vulnerabilidades de segurança ao [se registrar para receber notificações do Adobe](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **Verificar notas de versão**: examine regularmente as [notas de versão de correção de segurança](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), que estão marcadas com &quot;-pN&quot; para versões (por exemplo, 2.3.5-p1), e contêm correções críticas e melhorias.

- **Aplicar patches de segurança imediatamente**: aplique patches de segurança assim que estiverem disponíveis. Isso inclui a atualização para as versões mais recentes ou a aplicação de arquivos de patch específicos.

- **Usar patches de nuvem**: para o Adobe Commerce Cloud, os patches de segurança podem ser agrupados no Conjunto de Ferramentas da Nuvem. Atualize o conjunto ou a versão do Commerce para receber essas correções.

- **Gerenciamento automatizado de patches**: considere usar ferramentas como o patcher centralizado para [gerenciar e aplicar patches em vários armazenamentos automaticamente](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Para obter mais detalhes e instruções passo a passo sobre como aplicar patches e manter a segurança, consulte [notas de versão de patch de segurança](../../../release/release-notes/security/overview.md) e [Como aplicar patches de segurança](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). Você também deve revisar os relatórios da [Ferramenta de Análise do Site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access).

#### Conformidade com o PCI

Para garantir a conformidade com o PCI na Adobe Commerce Cloud, siga estas práticas principais:

- **Dados de titulares de cartão da Protect**: nunca armazene dados de titulares de cartão na Adobe Commerce. Se o armazenamento for necessário, use métodos criptografados e tokenizados para protegê-lo.

- **Usar protocolos de transmissão seguros**: sempre transmita dados de pagamento através de protocolos seguros, como TLS, com criptografia e gerenciamento de chaves adequado.

- **Utilizar o WAF (firewall de aplicativo da Web)**: o serviço WAF com tecnologia Fastly ajuda a atender aos requisitos do PCI DSS 6.6 e protege contra vulnerabilidades comuns, bloqueando o tráfego mal-intencionado antes que ele chegue ao seu site. Veja mais informações [aqui](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) e [aqui](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Limitar acesso**: certifique-se de que somente a equipe autorizada tenha acesso aos dados confidenciais de pagamento e [aplique o controle de acesso para reduzir o risco de exposição](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Verificação de segurança regular**: execute verificações PCI ASV regulares e [monitore seu ambiente](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) para resolver possíveis vulnerabilidades.

>[!TIP]
>
>Para obter diretrizes mais detalhadas sobre como manter a conformidade do PCI com o Adobe Commerce, consulte [práticas recomendadas para processamento e armazenamento de pagamentos](../planning/payment-processing-storage.md).

### Suporte ao usuário e ao cliente

#### Configuração

- **Canais de suporte**: implementar canais de suporte ao cliente como:

   - **Chat ao vivo**: ofereça suporte ao chat ao vivo para assistência imediata. As soluções populares incluem Zendesk, Intercom e Tidio.

   - **Suporte por email**: use um sistema de emissão de tíquetes de suporte, como o Freshdesk ou o Zoho Desk, para gerenciar consultas de clientes com eficiência.

   - **Suporte telefônico**: se você tiver uma grande base de clientes, considere oferecer suporte telefônico durante o horário comercial.

#### Treinamento do usuário administrador

- **Treinamento interno**: treine sua equipe sobre como usar o Administrador da Adobe Commerce, processar pedidos, gerenciar produtos e lidar com problemas de atendimento ao cliente.

- **Documentação**: mantenha uma base de dados de conhecimento interna ou um manual do usuário para perguntas frequentes, solução de problemas e tarefas comuns.

#### Otimização da experiência do cliente

- **Pesquisas e comentários**: use pesquisas para coletar comentários de clientes e otimizar a experiência do cliente. O Adobe Commerce oferece suporte a integrações com ferramentas como SurveyMonkey ou Google Forms.

- **Gerenciamento de análises**: gerencie análises e classificações de clientes sobre seus produtos. Incentive os clientes felizes a deixar análises, respondendo adequadamente a análises negativas.

- **Personalization**: implemente recursos de personalização, como recomendações personalizadas de produtos ou promoções direcionadas.

### Manutenção e otimização contínuas da loja

#### Otimização do mecanismo de pesquisa (SEO)

- **Otimização do conteúdo**: atualize regularmente as descrições do produto, postagens de blog e páginas de categoria para manter o conteúdo atualizado e relevante para mecanismos de pesquisa.

- **Auditorias de SEO**: faça auditorias de SEO regulares usando ferramentas como o Google Search Console ou o Screaming Frog para identificar problemas de SEO (por exemplo, links quebrados, metadados ausentes, conteúdo duplicado).

- **Estrutura de URL**: mantenha uma estrutura de URL lógica e limpa e verifique se não há links desfeitos ou redirecionamentos.

#### Otimização do índice de conversão (CRO)

- **Teste A/B**: execute testes A/B em diferentes elementos da página, como páginas de produtos ou processo de check-out, para melhorar as taxas de conversão.

- **Abandono do carrinho**: implemente campanhas de email de abandono do carrinho ou pop-ups de intenção de saída para recuperar vendas perdidas.

- **Otimização do check-out**: simplifique o processo de check-out reduzindo o número de etapas e oferecendo check-out de convidado para melhorar as conversões.

#### Integração de marketing

- **Campanhas de email**: configure fluxos automatizados de marketing por email para emails de boas-vindas, emails de carrinho abandonados e acompanhamento pós-compra. Plataformas como o Adobe Marketo, Mailchimp ou Klaviyo se integram bem com o Adobe Commerce.

- **Integração de redes sociais e anúncios**: integre-se a plataformas como Facebook, Instagram e Google Ads para executar campanhas direcionadas e acompanhar o desempenho.

#### Otimização móvel

- **Agilidade móvel**: teste regularmente a capacidade de resposta e utilização móvel do seu site. Dado que o comércio móvel está crescendo, uma abordagem mobile-first é essencial para o sucesso contínuo.

- **Desempenho móvel**: use as ferramentas de teste e desempenho compatíveis com dispositivos móveis da Google para otimizar sua experiência na loja de dispositivos móveis.

### Dimensionamento e desenvolvimento de novos recursos

- **Dimensionamento automático para tratamento de tráfego**:

   - O Adobe Commerce Cloud oferece suporte ao dimensionamento automático para ajustar dinamicamente os recursos do servidor (por exemplo, nós da Web) com base nas demandas de tráfego em tempo real, garantindo que sua loja possa lidar com grandes volumes de visitantes sem intervenção manual. Consulte [dimensionamento automático](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) no _Guia da Nuvem_.

   - As camadas de serviço e da Web podem ser dimensionadas independentemente, adicionando mais nós da Web para aumentar o tráfego e dimensionando nós de serviço ou banco de dados para desempenho de back-end durante períodos de pico. Consulte [arquitetura escalada](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) no _Guia da Nuvem_.

- **Monitoramento de desempenho**:

   - Use o **New Relic** para monitorar métricas de desempenho em tempo real (por exemplo, uso da CPU, níveis de tráfego) e fazer ajustes, conforme necessário.

   - Teste o desempenho em ambientes de preparo antes do dimensionamento para evitar problemas na produção.

- **Desenvolvimento de novos recursos**:

   - Integre recursos avançados, como **personalização orientada por IA**, **gerenciamento de assinaturas** e soluções personalizadas.

   - Teste e refine continuamente os recursos em ambientes de preparo antes da implantação na produção para minimizar o tempo de inatividade.

- **Manutenção do site em andamento**:

   - Analise regularmente os registros do sistema e as métricas de desempenho para identificar áreas que precisam ser melhoradas.

   - Garantir que a infraestrutura permaneça escalável e adaptável às novas necessidades e ao crescimento dos negócios.

>[!TIP]
>
>Para obter orientações detalhadas, consulte [práticas recomendadas de manutenção](overview.md), [personalização](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) e [desenvolvimento de recursos](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Relatórios e análises

- **O Adobe Commerce Intelligence Commerce Intelligence:**, um recurso principal do Adobe Commerce, fornece informações de práticas recomendadas em várias fontes de dados, permitindo que os comerciantes tomem decisões científicas orientadas por dados e tomem ações claras e informadas. Consulte o [_Guia do Usuário do Commerce Intelligence_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** o Adobe Analytics oferece uma solução poderosa para rastrear, analisar e otimizar o desempenho da sua loja online. O Adobe Analytics ajuda as empresas de comércio eletrônico a obter insights mais profundos sobre o comportamento do cliente, o desempenho do produto, as taxas de conversão e outras métricas principais, permitindo a tomada de decisões orientadas por dados.

- **Google Analytics:** use Google Analytics para rastrear o comportamento do cliente, as fontes de tráfego e as taxas de conversão.

- **Ferramentas adicionais do Commerce Intelligence:** o Adobe Commerce inclui Relatórios Avançados. Este recurso fornece acesso a um conjunto de relatórios dinâmicos com base em seus produtos, pedidos e dados do cliente, com um painel personalizado adaptado às suas necessidades comerciais, consulte [relatórios avançados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) no _Guia do Usuário do Administrador_ para obter mais informações.

### Conclusão

O suporte e a manutenção pós-lançamento são esforços contínuos que exigem atenção regular para garantir que sua loja da Adobe Commerce continue funcionando bem, permaneça segura e se adapte às necessidades da sua empresa. A implementação de uma abordagem estruturada para monitoramento do site, suporte ao cliente, otimização e atualizações é crucial para o sucesso a longo prazo.
