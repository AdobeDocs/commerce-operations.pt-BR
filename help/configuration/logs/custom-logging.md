---
title: Registro personalizado
description: Saiba como investigar erros usando o registro personalizado.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Visão geral do registro personalizado

Os registros dão visibilidade aos processos do sistema; por exemplo, depurar informações que ajudam a entender quando ocorreu um erro ou o que leva ao erro.

Este tópico foca no registro em arquivo, embora o Commerce forneça a flexibilidade para armazenar logs no banco de dados também.

O Adobe recomenda usar o registro centralizado do aplicativo pelos seguintes motivos:

- Ele permite o armazenamento de logs em um servidor diferente do aplicativo e diminui as operações de E/S de disco, simplificando o suporte do servidor de aplicativos.

- Isso torna o processamento de dados de logs mais eficiente com o uso de ferramentas especiais, como [Logstash], [Logplex]ou [fluente]—sem impacto em um servidor de produção.

   >[!INFO]
   >
   >O Adobe não recomenda nem endossa nenhuma solução de registro específica.

## Conformidade com o PSR-3

O [Padrão PSR-3][laminas] define uma interface PHP comum para bibliotecas de registro. O principal objetivo do PSR-3 é permitir que as bibliotecas recebam um `Psr\Log\LoggerInterface` registrará e gravará registros nele de forma simples e universal.

Isso proporciona a capacidade de a implementação ser facilmente substituída, sem se preocupar que tal substituição possa quebrar o código do aplicativo. Também garante que um componente personalizado funcionará mesmo quando a implementação do log for alterada em uma versão futura do sistema.

## Monólogo

O Commerce 2 está em conformidade com o padrão PSR-3. Por padrão, o Commerce usa [Monólogo]. Monólogo implementado como preferência por `Psr\Log\LoggerInterface` no aplicativo Commerce [`di.xml`][di].

O Monólogo é uma solução popular de registro em PHP com uma grande variedade de manipuladores que permitem criar estratégias avançadas de registro. A seguir encontra-se um resumo de como o Monólogo funciona.

Um Monólogo _logger_ é um canal com seu próprio conjunto de _manipuladores_. A Monologia tem muitos manipuladores, incluindo:

- Faça logon em arquivos e syslog
- Enviar alertas e-mails
- Registrar servidores específicos e registro em rede
- Desenvolvimento de logon (integração com FireBug e Chrome Logger, entre outros)
- Faça logon no banco de dados

Cada manipulador pode processar a mensagem de entrada e parar a propagação ou passar o controle para o manipulador seguinte em uma cadeia.

As mensagens de log podem ser processadas de várias maneiras diferentes. Por exemplo, você pode armazenar todas as informações de depuração em um arquivo no disco, colocar as mensagens com níveis de log mais altos em um banco de dados e, finalmente, enviar mensagens com nível de log &quot;crítico&quot; por e-mail.

Outros canais podem ter um conjunto diferente de manipuladores e lógicas.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluente]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monólogo]: https://github.com/Seldaek/monolog
