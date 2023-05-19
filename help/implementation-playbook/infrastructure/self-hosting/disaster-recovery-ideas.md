---
title: Auto-hospedagem da recuperação de desastres da Adobe Commerce
description: Saiba mais sobre ideias, conceitos e práticas recomendadas de auto-hospedagem para recuperação de desastres a serem consideradas.
landing-page-description: Saiba mais sobre alguns conceitos e aspectos da recuperação de desastres a serem considerados ao hospedar o Adobe Commerce por conta própria.
short-description: Conheça estratégias e conceitos de recuperação de desastres para hospedar você mesmo o Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cab6213b-da44-498f-b5c1-e7f89e95038e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Ideias de auto-hospedagem do Adobe Commerce Disaster Recovery

A recuperação de desastres deste artigo abrange uma implantação com falha. Embora todo o processo possa não ser o mesmo, princípios semelhantes se aplicam. Um desastre pode ocorrer devido a uma falha na implantação da produção, à falta de resposta do servidor, à descoberta de uma exploração e a muitos outros cenários. Quando o processo de recuperação de uma implantação com falha exigir apenas duas etapas simples, a recuperação de uma exploração pode ser muito mais desafiadora. Devido à complexidade dos ambientes, às variações de hospedagem e a outras complexidades, este artigo fornece ideias e conceitos, mas é necessário que você continue a investigação por conta própria. Dessa forma, você pode ter certeza de criar uma estratégia que atenda às necessidades de sua empresa.

## Praticar processo de recuperação com frequência

Pratique, Pratique, Pratique. Há um motivo pelo qual as práticas aparecem primeiro na lista de recuperação de desastres. É muito fácil configurar um plano de recuperação, mas nunca executá-lo. Se você não praticar o suficiente, estará sujeito a erros, etapas perdidas e provavelmente uma recuperação real levará mais tempo. A cadência para a recuperação prática depende de você e de seus parceiros de negócios. Tornar o processo de recuperação um evento anual pode ser bom o suficiente, mas uma conversa profunda com esses tomadores de decisão em sua empresa deve incluir vários tópicos principais. Esses tópicos os ajudam a entender por que praticar é importante e deve ser esperado. Estes são alguns tópicos que ajudam a iniciar a conversa:

* A prática reduz o tempo de inatividade real quando um evento ocorre. Se uma simulação prática derrubar seu site por uma hora por ano, ela pode reduzir o tempo de inatividade real de um evento real em várias horas. Não é incomum que a recuperação de um site demore oito horas ou mais. Ao praticar esse evento com frequência, é possível reduzir a quantidade de tempo que cada fase leva e você pode se recuperar mais rápido.
* O tempo de inatividade programado para essas execuções de prática pode coincidir com patches de servidor, ajustes de inventário ou qualquer outra coisa que deva ser feita regularmente.
* Pratique cenários diferentes em vez do mesmo. Leve o tempo ocasionalmente para fazer uma recuperação completa de uma data anterior. Isso inclui coisas como localizar e usar uma cópia arquivada do banco de dados, reverter o código para corresponder à data. Uma tarefa mais fácil pode ser a recuperação de uma implantação com falha, na qual você simplesmente deve reverter para a confirmação anterior.
* Verificar se o processo de recuperação realmente funciona, às vezes os bancos de dados arquivados podem ficar corrompidos. Ao fazer isso, ele garante que tudo possa ser recuperado e esteja funcional. Encontrar e restaurar um banco de dados antigo leva tempo, deve-se saber quanto tempo essa parte do processo pode demorar.
* Validar se todas as alterações nas configurações estão documentadas. Isso garante que qualquer recuperação de um banco de dados mais antigo obtenha quaisquer novas alterações de configuração que devam estar funcionando. Por exemplo, se sua chave de API mudou para seu processador de pagamento nos últimos dias. Ao ter um bom processo de gerenciamento de alterações, encontrar essas atualizações importantes faz com que o processo siga conforme planejado.

## Backups do BD

Os backups do banco de dados devem ser bastante regulares. Não é incomum ter snapshots por hora, dia, semana e mês. Os backups devem ser transferidos para um armazenamento de longo prazo. Esse armazenamento de longo prazo pode ocorrer sempre que a equipe de negócios ou de tecnologia decidir que, decorrido um tempo suficiente, provavelmente não será mais necessária uma rápida recuperação. A recuperação de um armazenamento de longo prazo adiciona tempo ao processo de recuperação, portanto, deve-se tomar cuidado ao decidir quando isso deve ocorrer. Os backups do banco de dados devem ser automatizados e não depender da interação humana. Isso garante que você tenha uma quantidade suficiente deles para oferecer um processo de recuperação seguro e previsível. Isso também ajuda em quaisquer atividades forenses, se tal atividade for necessária, for viável e confiável. Você pode encontrar uma necessidade de pesquisa forense após uma exploração ser detectada, ou ao tentar diagnosticar quando uma atividade de fraude de cartão de crédito ocorreu ou até mesmo quando alguém se juntou ao seu site. Não há limite para a forma como você usa esses backups, mas ter uma boa cadência de backups é a sua graça de salvamento quando você realmente precisa.

Veja a seguir um exemplo de política de retenção de dados:

* A cada oito horas. Os backups devem ser facilmente acessíveis.
* Backups diários dos últimos sete dias e devem estar prontamente acessíveis. Uma cópia deles pode ser candidata para ser transferida para um local externo.
* Os backups semanais das últimas quatro semanas consideram mover para outro local.
* backups mensais dos últimos três meses transferidos para um local externo.
* Os backups mais antigos são movidos para um armazenamento externo de longo prazo.

## Infraestrutura como código

Essa metodologia significa que você tem ferramentas e código em vigor para reconstruir partes ou toda a infraestrutura do seu projeto. Isso pode ser necessário quando um servidor apresenta problemas e deve ser desativado. Ser capaz de colocar rapidamente um novo servidor on-line, implantar o código, fazer qualquer configuração PHP, Nginx ou Apache e qualquer outra coisa que signifique automaticamente menos tempo de inatividade. Mesmo etapas bem documentadas em um livro de execução são mais fáceis de configurar, executar as etapas demora muito mais. Além disso, considere o erro humano que pode ocorrer enquanto estiver sob estresse para colocar um site sem resposta on-line novamente.

## Banco de dados secundário

O uso de um banco de dados secundário pode ser útil por alguns motivos:

* Espera quente se houver falha na unidade primária
* Permitir solicitações prontas do aplicativo
* Permitir que o mysqldump ocorra e permitir que transações normais ocorram sem bloquear o banco de dados
* Permite o acesso de dados de uma fonte externa de dados sem reduzir a capacidade dos sites de transacionar informações para a solicitação do cliente.

O banco de dados secundário pode ser usado como `warm standby`. Isso pode entrar em ação quando você estiver pensando em como se recuperar de uma falha no banco de dados principal. A promoção do banco de dados secundário para o principal tem complexidade menor do que a reconstrução e restauração de um banco de dados para uma instância Mysql recém-criada. Isso reduz o tempo de inatividade real durante uma operação de recuperação.

Há a oportunidade de desviar algumas das solicitações para o banco de dados secundário. Se esse método for usado, é sugerido tornar o banco de dados secundário somente leitura. Permitir que o aplicativo do Adobe Commerce use esse banco de dados secundário para operações de leitura ajuda a obter algumas solicitações de leitura e permitir que o banco de dados secundário responda. No entanto, essa alteração responde por apenas 30 a 50% de todas as solicitações, mas qualquer carga que você puder retirar do banco de dados principal é uma vitória.

## Criar um plano de implantação que inclua uma reversão

Cada implantação deve incluir um plano de reversão. Sim, a cada implantação. Se você planeja fazê-lo, nunca fica surpreso e está pronto para o evento ruim. Às vezes, as atualizações de código mais simples podem falhar catastroficamente por qualquer motivo.

Considere essa história real de uma equipe que enviou uma pequena solicitação de pull para executar uma alteração de esquema no banco de dados. À medida que a implantação ia de 1 minuto, para 5, depois 10, a equipe ficou mais preocupada. Falharam ao verificar e considerar até esse ponto qualquer discrepância do banco de dados de produção em comparação ao banco de dados de preparo. A empresa tinha uma prática comum de remover todos os dados do cliente ao atualizar o ambiente de preparo com uma cópia da produção. Isso significa que todos os testes e o controle de qualidade anteriores a isso refletiam que a implantação deveria levar apenas alguns minutos para ser concluída. Na realidade, eles tinham mais de 20 milhões de clientes e essa pequena alteração de esquema demorava muito para ser concluída. Como eles não tinham ideia de quanto tempo isso realmente levaria, foram obrigados a encerrar o processo mysql e reverter a implantação.

A preparação de um processo de reversão para uma implantação leva apenas alguns minutos, pois o processo geral será semelhante. No entanto, você deve reservar um tempo para documentar exatamente a qual confirmação redefiniria o HEAD do repositório Git para. Você deve documentar exatamente qual instantâneo de banco de dados usar ou onde encontrar o atual, se ele estiver sempre no mesmo lugar. Definir horários em que o status da implantação deve ser discutido e quando as coisas entram em vigor automaticamente. Por exemplo, se qualquer implantação demorar mais de 15 minutos, pergunte ao gerente de projeto e a outras partes interessadas se as coisas devem continuar. No entanto, execute automaticamente o processo de reversão e notifique todas as partes interessadas se o processo levar 45 minutos, independentemente de haver hesitação do gerente e do arquiteto do projeto.

Verifique se várias pessoas estão envolvidas em todo o processo e em cada fase. Fazer com que desenvolvedores intermediários revisem o processo de implantação, o procedimento de reversão e o local dos arquivos é uma ótima maneira de envolvê-los. Eles eventualmente executarão as etapas, de modo que entendam que todo o processo é a chave para o sucesso a longo prazo. Certifique-se de que todos estejam capacitados para cancelar uma implantação. Dar à sua equipe essa quantidade de voz é empoderador e gratificante. Se um desenvolvedor júnior realmente achar que algo está faltando, ele deve se sentir obrigado a falar e deixar que sua cautela seja ouvida. Deixe o arquiteto e os gerentes de projeto confirmarem ou mitigarem seu medo. É importante ter uma equipe forte que esteja cuidando do projeto e mantendo seu histórico de implantações sem falhas.

## Verificar acesso ao Gerenciamento de nome de domínio, DMS, SSL, WAF

Como os nomes de domínio expiram, os registros DNS podem ser modificados acidentalmente, os certificados SSL podem expirar e muito mais, garantindo que você tenha a capacidade de fazer logon e verificar se a conectividade deve ocorrer com frequência. Fazer essa simples verificação a cada trimestre mantém você confiante de que sabe exatamente onde as coisas estão localizadas, especialmente em uma emergência. Não presuma que o DNS é gerenciado no seu registrador apenas para descobrir que ele é gerenciado no Amazon. Esses registros não são usados com frequência, portanto, esquecer onde eles estão é uma alta probabilidade. Não confiar em documentação escrita apenas para nomes de usuário e senhas. Faça logon em cada um e verifique se as configurações que você está procurando são realmente gerenciadas lá. Muitas vezes, as coisas mudam durante o volume de negócios da gestão ou a aquisição da empresa e apenas uma pessoa sabe o que aconteceu, porque foram elas que fizeram a atualização. Eles não sabiam que você dependia de um documento do Word compartilhado qual é o local, o nome de usuário e a senha. Encontre um processo de verificação que faça sentido para você e para sua organização, mas fazer isso a cada três ou seis meses é um bom ponto de partida.

{{$include /help/_includes/hosting-related-links.md}}
