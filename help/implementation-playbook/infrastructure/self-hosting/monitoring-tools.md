---
title: Ferramentas de monitoramento Adobe Commerce de auto-hospedagem
description: Saiba mais sobre as ideias e os conceitos e as práticas recomendadas das ferramentas de monitoramento de auto-hospedagem.
landing-page-description: Saiba mais sobre alguns conceitos e coisas das ferramentas de monitoramento ao hospedar o Adobe Commerce por conta própria.
short-description: Saiba mais sobre estratégias e conceitos de ferramentas de monitoramento para hospedar você mesmo o Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 63fddb20673399bae397238a8dda866e1d740e6f
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---


# Telemetria e ferramentas de monitoramento da Adobe Commerce com auto-hospedagem

Usar ferramentas de monitoramento permite oportunidades para detectar alterações sem ter que pagar a alguém para assistir a tudo o tempo todo. Com a maioria das ferramentas, você pode adicionar alertas e notificações se um limite for atingido, como um disco rígido sem espaço. Algumas ferramentas fornecem resultados que devem ser rastreados e calculados, como resultados de testes de carga. Independentemente da ferramenta, cada ferramenta tem um propósito e, quando usada de forma consistente, pode ajudá-lo a gerenciar seu aplicativo. Existem opções gratuitas para cada ferramenta, mas lembre-se de que o pagamento de um serviço geralmente garante um suporte mais confiável e mais rápido e pode valer a pena investir. O New Relic é um exemplo de uma ferramenta que oferece um nível gratuito e uma versão paga que libera muito mais poder e recursos. Há outros como DataDog ou Dynatrace. Encontre uma boa opção e use-a de forma consistente.

## Acompanhamento da infraestrutura

O termo infraestrutura é utilizado de forma bastante vaga neste contexto. Para este tópico, isso significa qualquer servidor, processo ou dispositivo usado para fazer com que o site funcione. Por exemplo:

* Discos rígidos
* Uso da CPU
* Uso de RAM
* Redis
* Carga média por servidor
* tráfego na rede

Limiares de investigação para criar alertas eficazes. Não atribua um para coisas importantes, como a capacidade do disco rígido. Configure alguns para notificar grupos diferentes conforme as coisas pioram. Por exemplo, aqui está um conjunto de regras quando um disco rígido está ficando cheio.

* Notificação de 70% Slack para o canal DevOps
* 80% Notifique o canal DevOps do Slack e uma lista de distribuição de email de equipes DevOps
* Canal e Slack de suporte de produção do Slack DevOps de 90%, e-mail do grupo de distribuição DevOps e do gerente de engenharia
* 95% Notifique Slack DevOps e canais de Slack de suporte à produção, lista de distribuição de email de todos os engenheiros e Director de engenharia
* 98% Notifique quaisquer canais de Slack P1 e DevOps e canais de Slack de suporte de produção, lista de distribuição de email de engenheiros e Director sobre engenharia e VP de tecnologia

Existem muitas maneiras de notificar uma equipe, portanto, certifique-se de escolher uma que seja confiável e que não fique inundada de muitos alertas. É importante reservar alertas para quando for importante, caso contrário, você corre o risco de ficar sobrecarregado e começa a ignorar alertas.

Geralmente, há bons modelos a serem seguidos para a maioria das ferramentas, como New Relic, DataDog e Dynatrace. Reserve algum tempo para encontrar boas ideias que façam mais sentido para seu aplicativo. Com o Adobe Commerce na infraestrutura em nuvem, há alertas e acionadores em vigor quando o projeto é provisionado. Isso capacita a equipe de suporte à produção do Adobe a aplicar suas ferramentas para monitoramento de tempo de atividade e alta disponibilidade.

Os painéis fornecem acesso rápido aos aspectos frequentes ou importantes de seu site. Os itens do painel podem consistir em exibições de página, uso da CPU por host, lista de todos os servidores, tempos de carregamento de página, durações de transação e até mesmo resultados de testes de monitoramento sintético nos últimos dias. Esses painéis devem ser criados para permitir uma triagem rápida se algo estiver errado ou diferentes painéis configurados para diferentes experiências do usuário. Com sorte, você pode criar vários painéis e aproveitar o monitoramento de seu aplicativo em tempo real. É muito satisfatório, especialmente quando solicitado pelo proprietário do projeto ou por um gerente, como o site está funcionando, e você pode encontrar a resposta em segundos, não em horas.

## Agregação e rotação de logs

Os arquivos de log são encontrados em servidores de aplicativos que processam solicitações ou logs do MySQL quando as coisas levam muito tempo para serem executadas. O mais difícil sobre os logs é que eles são separados um do outro e encontram todos eles, analisar as informações de cada log pode ser complicado. Há muitos anos, esse problema foi resolvido usando uma técnica chamada _agregação de log_. Isso captura arquivos de log de todos os locais de log, enviando-os para um local centralizado. Depois que as forem movidas, um software poderá lê-las e fornecer maneiras de pesquisar, filtrar e analisar as informações. Este pode ser um processo complicado para se corrigir. Há muitas opções, mas se você tiver sorte suas ferramentas de monitoramento podem ler e agregar seus arquivos de log, como o New Relic. Encontrando uma boa ferramenta, você pode economizar um tempo imensurável no futuro. A menos que você tenha apenas um único servidor que faça tudo para que seu site execute e opere, ter agregação de log é essencial. Isso é especialmente útil ao tentar descobrir se você está sob um ataque de DDoS ou passando por um pico de tráfego legítimo, ou ao pesquisar por que uma determinada solicitação está falhando.

Outra peça essencial para os registros é garantir que a rotação ocorra. Isso historicamente diz respeito a `run-away logs` que pode encher acidentalmente o disco rígido e fazer com que o site desça. Uma versão da rotação de log pode ocorrer quando um arquivo de log atinge um determinado tamanho, como 1 GB. Existem ferramentas de nível de servidor como `logrotate` que pode removê-las automaticamente. Por exemplo, ele pode remover arquivos de log excessivamente grandes depois de se tornarem maiores que 1 GB ou remover arquivos de log com mais de 90 dias. Você define uma política de log, portanto, é importante entender suas limitações de recursos.

## Verificações de malware

Muitas empresas de hospedagem de sites dedicadas à Adobe Commerce teriam uma biblioteca de explorações conhecidas e malware. Eles devem oferecer uma verificação automaticamente ou mediante solicitação. Quando são eficazes, são reacionárias e funcionam somente como novo malware detectado. Pode ser uma boa ideia ter uma ferramenta proativa que possa examinar o código e o banco de dados para verificar se há malware conhecido. Há algumas opções disponíveis, como [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Eles podem fazer uma varredura remota de fora ou ser instalados e atualizar/digitalizar/monitorar proativamente após serem configurados nos servidores. Essas podem ser uma ótima opção, pois a biblioteca deles está sendo constantemente atualizada, pois estão instaladas e monitorando milhares de sites, se você escolher uma solução fornecida, como Sansec. À medida que um novo malware é detectado, todos os projetos que monitoram beneficiam das informações e agora são alertados se forem detectados.

Há algumas versões gratuitas a serem consideradas, mas para malware, você deve considerar uma solução paga. Esta pode ser a diferença entre o seu site estar infectado durante alguns minutos e alguns meses. Ter uma exploração em seu site causa enormes dores de cabeça, essa é uma área que você deve considerar pagar por um serviço.

## Ferramenta de análise do site do Adobe

A Ferramenta de análise do site é uma ferramenta de autoatendimento proativa e um repositório central que inclui informações e recomendações detalhadas do sistema para garantir a segurança e a operabilidade de sua instalação do Adobe Commerce. Ele fornece monitoramento, relatórios e conselhos em tempo real 24 horas por dia, 7 dias por semana, para identificar possíveis problemas e melhor visibilidade sobre a integridade do site, a segurança e as configurações do aplicativo. Ajuda a reduzir o tempo de resolução e a melhorar a estabilidade e o desempenho do site.

A página do Recommendations da Ferramenta de análise do site lista recomendações baseadas nas práticas recomendadas para solucionar problemas detectados em seu site. As recomendações são classificadas por OC prioritária para P4, onde OC é crítica e P4 é baixa. Os resultados incluem descrição, recomendação, impacto no site, causa raiz, cenários/pré-condições, resultado esperado e ferramentas usadas.

Saiba mais sobre as práticas recomendadas para melhorar o desempenho do seu site. Rastreie e implemente as recomendações listadas por prioridade.

Para obter mais informações sobre como instalar isso em seu projeto, visite [Guia de instalação da ferramenta de análise em todo o site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Monitoramento de SSL

Um dos itens mais esquecidos de um projeto é o certificado SSL. Eles só precisam de atenção uma vez por ano, então esquecê-los é muito fácil. A expiração do seu certificado de segurança pode resultar em avisos ou recusa dos navegadores modernos em exibir as páginas do site. Os clientes podem começar a enviar emails ou chamar o suporte se tiverem esse problema e talvez você não possa operar até que o problema seja resolvido. Cada minuto conta, portanto, reconhecer a expiração está chegando com antecedência e garantir que as coisas sejam renovadas é fundamental para manter o site em funcionamento. Há muitas maneiras de realizar o monitoramento de SSL. Considere o uso de ferramentas de monitoramento sintético para seu site, usando ferramentas gratuitas ou de baixo custo, como Pingdom, Keychest ou Sucuri, e até assine um serviço que oferece alertas de expiração de certificado SSL. Essas ferramentas simples podem garantir que os certificados do site sejam válidos e reduzir o risco de tempo de inatividade dos clientes.

## Teste automatizado

A realização de testes automatizados, como testes funcionais ou testes de unidade, geralmente ajuda a detectar problemas do código recém-introduzido. Esses testes podem não capturar tudo, já que a Adobe Commerce e os testes de unidade normalmente têm menos de 50% de cobertura. Isso não significa que você deve evitar gravar e testar. Essas ferramentas estão aqui para adicionar outra camada de segurança e segurança que tudo o que está sendo cometido não afeta negativamente o teste imediato e qualquer teste personalizado criado pela equipe de desenvolvimento. Ao executar esses testes em cada implantação, todos os problemas principais são detectados precocemente e evitam permitir que as coisas abram caminho para a produção.

Testes de carga podem ser desafiadores para acertar. A maior parte da complexidade vem de como o front-end é usado e implementado. Se o site tiver um front-end sem periféricos, talvez você queira carregar o teste para APIs REST e GraphQL. A forma como você acaba testando o carregamento depende de você e da equipe DevOps. Saiba que cada teste de carga, executado assim que possível, fornece informações sobre o status do projeto. Ele também fornece referências para testes futuros para ver se há mudanças drásticas nos resultados do teste de carga. Em caso positivo e negativo, essa é uma boa oportunidade para revisar as alterações mais recentes do código e procurar seções de impacto no desempenho para melhorar.

A Adobe Commerce tem boas orientações para ajudar a entender como executar testes de Unidade, consulte [teste de unidade PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} no _Guia de teste de aplicativo_ no site da documentação do Adobe Developer.

Para obter mais informações sobre testes funcionais, visite [Introdução à estrutura de testes funcionais](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
