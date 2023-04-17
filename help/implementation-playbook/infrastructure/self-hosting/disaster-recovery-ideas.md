---
title: Recuperação de desastres Adobe Commerce de hospedagem própria
description: Saiba mais sobre ideias e conceitos e práticas recomendadas de recuperação de desastres de hospedagem própria.
landing-page-description: Saiba mais sobre alguns conceitos e coisas que devem ser considerados ao hospedar a Adobe Commerce por conta própria.
short-description: Saiba mais sobre estratégias e conceitos de recuperação de desastres para hospedar você mesmo a Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 6e361169889c8fe1c176d3a3283d52699dfa3b85
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---


# Ideias de recuperação de desastres Adobe Commerce de hospedagem própria

A recuperação de desastres para este artigo inclui uma implantação com falha. Embora todo o processo possa não ser o mesmo, aplicam-se princípios semelhantes. Um desastre pode ser devido a uma falha na implantação de produção, não-resposta do servidor, descoberta de uma exploração e muitos outros cenários. Quando o processo de recuperação de uma implantação com falha pode exigir apenas duas etapas simples, uma recuperação de uma exploração pode ser muito mais desafiante. Devido à complexidade de ambientes, variações de hospedagem e outras complexidades, este artigo fornece ideias e conceitos, mas você deve continuar a investigação sozinho. Dessa forma, você pode criar uma estratégia que atenda às suas necessidades comerciais.

## Prática do processo de recuperação

Prática, Prática, Prática. Há um motivo para as práticas aparecerem primeiro na lista de recuperação de desastres. É muito fácil configurar um plano de recuperação, mas nunca executá-lo. Se não praticar o suficiente, você estará sujeito a erros, etapas perdidas e provavelmente fará com que uma recuperação real demore mais. A cadência de recuperação de práticas depende de você e de seus parceiros comerciais. Tornar o processo de recuperação um evento anual pode ser bom o suficiente, mas uma conversa profunda com esses tomadores de decisão em sua empresa deve incluir vários tópicos principais. Esses tópicos os ajudam a entender por que a prática é importante e deve ser esperada. Estes são alguns tópicos que ajudam a iniciar a conversa:

* A prática reduz o tempo de inatividade real quando um evento ocorre em tempo real. Se um exercício de simulação de prática derrubar o site por uma hora por ano, ele pode reduzir o tempo de inatividade real de um evento real em várias horas. Não é raro a recuperação de um site demorar oito horas ou mais. Ao praticar esse evento com frequência, é possível reduzir a quantidade de tempo que cada fase leva e recuperar mais rapidamente.
* O tempo de inatividade programado para essas execuções de prática pode coincidir com patches de servidor, ajustes de inventário ou qualquer outra coisa que deve ser feita de acordo com uma programação regular.
* Pratique cenários diferentes em vez do mesmo. Ocasionalmente, faça uma recuperação completa de uma data anterior. Isso inclui coisas como localizar e usar uma cópia arquivada do banco de dados, revertendo o código para corresponder à data. Uma opção mais fácil poderia ser uma recuperação de uma implantação com falha, onde você simplesmente deve reverter para a confirmação anterior.
* Verifique se o processo de recuperação realmente funciona, às vezes os bancos de dados arquivados podem ficar corrompidos. Ao fazê-lo, garante que tudo possa ser recuperado e seja funcional. Encontrar e restaurar um banco de dados antigo leva tempo, é necessário saber por quanto tempo essa parte do processo pode demorar.
* Valide se todas as alterações nas configurações estão documentadas. Isso garante que qualquer recuperação de um banco de dados mais antigo obtenha quaisquer novas alterações na configuração do sejam funcionais. Por exemplo, se a chave da API mudou para o processador de pagamento nos últimos dias. Ao ter um bom processo de gerenciamento de alterações, encontrar essas atualizações principais faz com que o processo avance conforme planejado.

## Backups de banco de dados

Os backups do banco de dados devem ser bastante regulares. Não é incomum ter instantâneos por hora, dia, semana e mês. Os backups devem eventualmente ser transferidos para o armazenamento de longo prazo. Esse armazenamento de longo prazo pode ocorrer sempre que a equipe de negócios ou de tecnologia decidir que há tempo suficiente para que uma recuperação rápida deles provavelmente não seja mais necessária. Uma recuperação a partir de um armazenamento de longo prazo acrescenta tempo ao processo de recuperação, portanto, deve-se tomar cuidado ao decidir quando isso deve ocorrer. Os backups do banco de dados devem ser automatizados e não confiar na interação humana. Isso garante que você tenha o suficiente para fornecer um processo de recuperação seguro e previsível. Isso também ajuda em qualquer atividade forense, se tal atividade for necessária, é viável e confiável. Você pode achar a necessidade de pesquisa forense depois que uma exploração é detectada, ou ao tentar diagnosticar quando ocorreu uma fraude com cartão de crédito ou até mesmo quando alguém ingressou em seu site. Não há limite para a forma como você usa esses backups, mas ter uma boa cadência de backups é a sua graça de salvamento quando você realmente precisa.

Este é um exemplo de política de retenção de dados:

* A cada oito horas. Os backups devem ser facilmente acessíveis.
* Backups diários dos últimos sete dias e devem estar prontamente acessíveis. Uma cópia deles poderia ser um candidato para ser transferida para fora do local.
* Os backups semanais das últimas quatro semanas consideram mover-se fora do local.
* backups mensais dos últimos três meses foram transferidos para fora do local.
* Backups mais antigos são transferidos para armazenamento externo a longo prazo.

## Infraestrutura como código

Essa metodologia significa que você tem ferramentas e código disponíveis para reconstruir peças ou toda a infraestrutura do seu projeto. Isso pode ser necessário quando um servidor tiver problemas e deve ser retirado de uso. Ser capaz de colocar rapidamente um novo servidor online, implantar o código, fazer qualquer configuração PHP, Nginx ou Apache, e qualquer outra coisa, significa automaticamente menos tempo de inatividade. Mesmo etapas bem documentadas em um livro de execução são mais fáceis de configurar, a execução das etapas demora muito mais. Além disso, considere o erro humano que pode ocorrer enquanto está sob estresse para retornar online um site que não responde.

## Banco de dados secundário

O uso de um banco de dados secundário pode ser útil por alguns motivos:

* Espera aquecida se houver falha na unidade primária
* Permitir solicitações prontas do aplicativo
* Permitir que o mysqldump ocorra e permitir que as transações normais ocorram sem bloquear o banco de dados
* Permite o acesso de dados de uma fonte externa de dados sem reduzir a capacidade dos sites de transacionarem informações para solicitações de clientes.

O banco de dados secundário pode ser usado como um `warm standby`. Isso pode entrar em ação quando você estiver considerando como recuperar de uma falha do banco de dados principal. Promover o banco de dados secundário para primário é mais baixo em complexidade do que reconstruir e restaurar um banco de dados para uma instância Mysql recém-criada. Isso reduz o tempo de inatividade real durante uma operação de recuperação.

Há a oportunidade de desviar algumas das solicitações para o banco de dados secundário. Se esse método for usado, é sugerido tornar o banco de dados secundário somente leitura. Ao permitir que o aplicativo Adobe Commerce use esse banco de dados secundário para operações de leitura, você pode obter algumas das solicitações de leitura e permitir que o banco de dados secundário responda. No entanto, essa alteração representa apenas 30 a 50% de todas as solicitações, mas qualquer carga que você possa retirar do banco de dados principal é uma vitória.

## Criar um plano de implantação que inclua uma reversão

Cada implantação deve incluir um plano de reversão. Sim, cada implantação. Se você planeja isso, você nunca fica surpreso e está pronto para o mau evento. Às vezes, as atualizações de código mais simples podem falhar catastroficamente por qualquer motivo.

Considere esta história verdadeira de uma equipe que cometeu uma pequena e simples solicitação de pull para executar uma alteração de schema no banco de dados. À medida que a implantação passava de 1 minuto, para 5, depois 10, e a equipe se preocupava mais. O que eles não verificaram e consideraram até este ponto foi qualquer discrepância do banco de dados de produção em comparação ao banco de dados de preparo. Eles tinham uma prática comum de remover todos os dados do cliente ao atualizar o ambiente de preparo com uma cópia da produção. Isso significava que todos os testes e QA anteriores refletiam que a implantação deveria levar apenas alguns minutos para ser concluída. Na realidade, eles tinham mais de 20 milhões de clientes e essa pequena mudança de esquema demorava um tempo excepcionalmente longo para ser concluída. Porque eles não tinham ideia de quanto tempo isto iria realmente demorar, eles foram compelidos a terminar o processo mysql e reverter a implantação.

A preparação de um processo de reversão para uma implantação demora apenas alguns minutos, pois o processo geral será semelhante. No entanto, você deve levar o tempo para documentar exatamente qual confirmação você redefiniria o HEAD do repositório Git. Você deve documentar exatamente qual instantâneo do db usar ou onde encontrar o atual, se ele estiver sempre no mesmo lugar. Ter horários definidos em que o status da implantação deve ser discutido e quando as coisas entrarem em vigor automaticamente. Por exemplo, se qualquer implantação demorar mais de 15 minutos, pergunte ao gerente do projeto e a outros interessados se as coisas devem continuar. No entanto, execute automaticamente o processo de reversão e notifique todos os participantes se o processo levar 45 minutos, independentemente de haver hesitação do gerente do projeto e do arquiteto para o projeto.

Certifique-se de que várias pessoas estejam envolvidas com todo o processo e em cada fase. Com desenvolvedores de nível médio revisando o processo de implantação, o procedimento de reversão e a localização dos arquivos são uma ótima maneira de envolvê-los. Eles eventualmente executarão as etapas para que entendam que todo o processo é fundamental para o sucesso a longo prazo. Certifique-se de que todos estejam capacitados para cancelar uma implantação. Dar a sua equipe essa quantidade de voz é empoderador e gratificante. Se um desenvolvedor experiente realmente sente que algo está faltando, ele deve se sentir obrigado a se manifestar e deixar que sua cautela seja ouvida. Deixem o arquiteto e os gerentes do projeto confirmarem ou mitirem seu medo. É importante ter uma equipe forte que esteja procurando o projeto e mantendo o registro de implantações sem falhas.

## Verificar o acesso ao Gerenciamento de nome de domínio, DMS, SSL, WAF

Como os nomes de domínio expiram, os registros DNS podem ser modificados acidentalmente, os certificados SSL podem expirar e muito mais; Certifique-se de ter a capacidade de fazer logon e verificar se a conectividade deve ocorrer com frequência. Fazer essa simples verificação a cada trimestre mantém você confiante de que sabe exatamente onde as coisas estão, especialmente em uma emergência. Não suponha que seu DNS seja gerenciado em seu registrador apenas para descobrir que ele foi gerenciado no Amazon. Esses registros não são usados com frequência, portanto, esquecer onde estão é uma alta probabilidade. Não confie na documentação escrita apenas para nomes de usuário e senhas. Faça logon em cada uma e verifique se as configurações que você está procurando são realmente gerenciadas lá. Muitas vezes, as coisas mudam durante o volume de negócios da administração ou a aquisição da empresa e só uma pessoa sabe o que aconteceu, porque foram eles que fizeram a atualização. Eles não sabiam que você dependia de um documento de palavras compartilhadas qual é o local, o nome de usuário e a senha. Encontre um processo de verificação que faça sentido para você e sua organização, mas fazer isso a cada três ou seis meses é um bom ponto de partida.

{{$include /help/_includes/hosting-related-links.md}}
