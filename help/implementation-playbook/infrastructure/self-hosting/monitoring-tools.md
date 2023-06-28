---
title: Ferramentas de monitoramento do Adobe Commerce de auto-hospedagem
description: Saiba mais sobre as ideias das ferramentas de monitoramento de auto-hospedagem, os conceitos e as práticas recomendadas a serem considerados.
landing-page-description: Saiba mais sobre alguns conceitos e coisas a serem considerados nas ferramentas de monitoramento ao hospedar o Adobe Commerce por conta própria.
short-description: Saiba mais sobre estratégias e conceitos de ferramentas de monitoramento para hospedar o Adobe Commerce sozinho.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Telemetria e ferramentas de monitoramento do Adobe Commerce de auto-hospedagem

O uso de ferramentas de monitoramento permite oportunidades para detectar alterações sem precisar pagar alguém para assistir a tudo o tempo todo. Com a maioria das ferramentas, você pode adicionar alertas e notificações se um limite for atingido, como um disco rígido ficando sem espaço. Algumas ferramentas fornecem resultados que devem ser rastreados e calculados, como resultados de testes de carga. Independentemente da ferramenta, cada ferramenta tem um propósito e, quando usada de forma consistente, pode ajudá-lo a gerenciar seu aplicativo. Há opções gratuitas para cada ferramenta, mas lembre-se de pagar por um serviço, muitas vezes, garante um suporte mais rápido e confiável e pode valer o investimento. O New Relic é um exemplo de ferramenta que oferece um nível gratuito e uma versão paga que libera muito mais potência e recursos. Há outros, como o DataDog ou o Dynatrace. Encontre uma boa opção para você e use-a de maneira consistente.

## Monitoramento de infraestrutura

O termo infraestrutura é usado de forma bastante vaga para este contexto. Para este tópico, significa qualquer servidor, processo ou dispositivo usado para fazer o site funcionar. Por exemplo:

* Discos rígidos
* Uso da CPU
* Uso de RAM
* Redis
* Carga média por servidor
* tráfego de rede

Limites de pesquisa para criar alertas eficazes. Não atribua um para os aspectos importantes, como a capacidade do disco rígido. Configure alguns para notificar grupos diferentes conforme as coisas pioram. Por exemplo, este é um conjunto de regras quando um disco rígido está ficando cheio.

* Notificação de Slack de 70% para o canal DevOps
* 80% Notifique o canal DevOps da sala de Slack e uma lista de distribuição de email dos colegas de equipe do DevOps
* 90% Notifique o canal de Slack DevOps e o canal de Slack de suporte à produção, o grupo de distribuição de DevOps por email e o gerente de engenharia
* 95% Notifique Slack DevOps e canais Slack de suporte à produção, lista de distribuição de e-mail de todos os engenheiros e Director de engenharia
* 98% Notifique qualquer canal de Slack P1 e canais de Slack de DevOps e suporte de produção, lista de distribuição de e-mail de engenheiros e Director de engenharia e vice-presidente de tecnologia

Há muitas maneiras de notificar uma equipe, portanto, certifique-se de escolher um que seja confiável e não fique inundado de muitos alertas. É importante reservar alertas para quando é importante, caso contrário, você corre o risco de ficar sobrecarregado e começar a ignorar os alertas.

Geralmente, há bons modelos a serem seguidos para a maioria das ferramentas, como New Relic, DataDog e Dynatrace. Reserve um tempo para encontrar boas ideias que façam mais sentido para sua aplicação. Com o Adobe Commerce na infraestrutura em nuvem, há alertas e acionadores em vigor quando o projeto é provisionado. Isso permite que a equipe de suporte à produção de Adobe aplique suas ferramentas para monitoramento de tempo de atividade e alta disponibilidade.

Os painéis fornecem acesso rápido aos aspectos frequentes ou importantes do site. Os itens do painel podem consistir em exibições de página, uso da CPU por host, lista de todos os servidores, tempos de carregamento da página, durações de transações e até mesmo resultados de testes de monitoramento sintético dos últimos dias. Esses painéis devem ser criados para permitir a triagem rápida se algo estiver errado ou se painéis diferentes forem configurados para experiências de usuário diferentes. Esperamos que você possa criar vários painéis de controle e ver seu aplicativo monitorando em tempo real. É muito satisfatório, especialmente quando perguntado pelo proprietário do projeto ou um gerente como o site está funcionando, e você pode encontrar a resposta em segundos, não em horas.

## Agregação e rotação de logs

Os arquivos de log são encontrados em servidores de aplicativos que processam solicitações ou logs do MySQL quando a execução demora muito. O difícil é que os registros são separados uns dos outros e encontrar todos eles, analisar as informações de cada registro pode ser complicado. Há muitos anos, esse problema era resolvido com uma técnica chamada _agregação de log_. Isso leva os arquivos de log de todos os locais de log, os enviando por push para um local centralizado. Depois que as informações são movidas, um software pode lê-las e fornecer maneiras de pesquisar, filtrar e revisar as informações. Esse pode ser um processo complicado para corrigir. Há muitas opções, mas se você tiver sorte, suas ferramentas de monitoramento podem ler e agregar seus arquivos de log, como o New Relic. Ao encontrar uma boa ferramenta, você pode economizar uma quantidade imensurável de tempo no futuro. A menos que você tenha apenas um único servidor que faça tudo para que seu site funcione e opere, ter agregação de log é essencial. Isso é especialmente útil ao tentar descobrir se você está sob um ataque de DDoS ou enfrentando um pico de tráfego legítimo, ou ao pesquisar por que uma determinada solicitação está falhando.

Outra parte importante dos registros é garantir que a rotação ocorra. Isso historicamente se refere a `run-away logs` que pode encher acidentalmente o disco rígido e fazer com que o site fique inativo. Uma versão de rotação de log pode ocorrer quando um arquivo de log atinge um determinado tamanho, como 1 GB. Há ferramentas de nível de servidor, como `logrotate` que pode removê-los automaticamente. Por exemplo, ele pode remover arquivos de log muito grandes quando eles se tornarem maiores que 1 GB ou remover arquivos de log com mais de 90 dias. Você define uma política de log, portanto, é importante entender as limitações de recursos.

## Verificações de malware

Muitas empresas de hospedagem de sites dedicadas ao Adobe Commerce teriam uma biblioteca de explorações conhecidas e malware. Eles devem oferecer uma verificação automaticamente ou mediante solicitação. Quando são eficazes, são reacionários e funcionam somente quando novos malwares são detectados. Pode ser uma boa ideia ter uma ferramenta proativa que possa examinar o código e o banco de dados em busca de malware conhecido. Há algumas opções disponíveis, como [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Eles podem fazer uma varredura remota externa ou ser instalados e atualizar/examinar/monitorar proativamente após serem configurados nos servidores. Essas podem ser uma ótima opção, pois a biblioteca deles é constantemente atualizada porque estão instalados e monitorando milhares de sites se você escolher uma solução fornecida, como a Sansec. À medida que um novo malware é detectado, todos os projetos que eles monitoram se beneficiam das informações e agora serão alertados se forem detectados.

Há algumas versões gratuitas a considerar, mas para malware, você realmente deve considerar uma solução paga. Pode ser uma diferença entre o fato de seu site ter sido infectado por alguns minutos e alguns meses. Ter uma exploração em seu site causa enormes dores de cabeça, esta é uma área que você deve considerar pagar por um serviço.

## Ferramenta de análise do site Adobe

A Ferramenta de análise do site é uma ferramenta de autoatendimento proativa e um repositório central que inclui insights e recomendações detalhados do sistema para garantir a segurança e a operabilidade da instalação do Adobe Commerce. Ele fornece monitoramento de desempenho em tempo real, relatórios e conselhos 24 horas por dia, 7 dias por semana, para identificar possíveis problemas e melhor visibilidade das configurações de integridade, segurança e aplicativos do site. Ele ajuda a reduzir o tempo de resolução e a melhorar a estabilidade e o desempenho do site.

A página Recommendations da Ferramenta de análise do site lista recomendações com base nas práticas recomendadas para resolver problemas detectados no site. As recomendações são classificadas por ordem de compra de prioridade para P4, em que a ordem de compra é crítica e P4 é baixa. As conclusões incluem descrição, recomendação, impacto no local, causa básica, cenários/pré-condições, resultado esperado e ferramentas usadas.

Saiba mais sobre as práticas recomendadas para melhorar o desempenho do site. Rastrear e implementar as recomendações listadas de acordo com a prioridade.

Para obter mais informações sobre como instalar isso no seu projeto, visite [Guia de instalação da ferramenta de análise do site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Monitoramento de SSL

Um dos itens mais esquecidos de um projeto é o certificado SSL. Eles só precisam de atenção uma vez por ano, então esquecê-los é muito fácil. A expiração do certificado de segurança pode resultar em aviso ou recusa dos navegadores modernos para exibir as páginas do site. Os clientes podem começar a enviar emails ou ligar para o suporte se tiverem esse problema e você pode não conseguir operar até que ele seja resolvido. Cada minuto é importante, portanto, reconhecer a expiração antecipadamente e garantir que tudo seja renovado é fundamental para manter o site em funcionamento. Há muitas maneiras de fazer o monitoramento de SSL. Considere usar ferramentas de monitoramento sintético para o seu site, usando ferramentas gratuitas ou de baixo custo, como PKingdom, Keypeito ou Sucuri e até mesmo assine um serviço que oferece alertas de expiração de certificados SSL. Essas ferramentas simples podem garantir que os certificados de seu site sejam válidos e reduzir o risco de inatividade para seus clientes.

## Teste automatizado

A execução de testes automatizados, como testes funcionais ou testes de unidade, geralmente ajuda a detectar problemas de códigos recém-introduzidos. Esses testes podem não capturar tudo, já que os testes de Adobe Commerce e unidade normalmente têm menos de 50% de cobertura. Isso não significa que você deve evitar escrevê-los e testar. Essas ferramentas estão aqui para adicionar outra camada de segurança, de modo que tudo o que está sendo comprometido não afete negativamente o produto pronto para uso e os testes personalizados criados pela sua equipe de desenvolvimento. Ao executar esses testes em cada implantação, os principais problemas são detectados antecipadamente e evitam permitir que as coisas cheguem à produção.

Testes de carga podem ser desafiadores para acertar. Grande parte da complexidade vem de como o front-end é usado e implementado. Se o site tiver um front-end headless, talvez você queira testar a carga do GraphQL e as APIs REST. O teste de carga depende de você e da equipe de DevOps. Saber que cada teste de carga, executado assim que possível, fornece informações sobre o status do projeto. Ele também fornece referências para testes futuros para ver se há alterações drásticas nos resultados do teste de carga. Em caso afirmativo, e se forem negativos, esta é uma boa oportunidade para analisar as alterações de código mais recentes e procurar seções que afetam o desempenho para melhorar.

A Adobe Commerce tem uma boa orientação para ajudar a entender como executar testes de unidade. Consulte [Teste de unidade PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} no _Guia de teste do aplicativo_ no site de documentação do Adobe Developer.

Para obter mais informações sobre teste funcional, visite [Introdução à estrutura de teste funcional](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
