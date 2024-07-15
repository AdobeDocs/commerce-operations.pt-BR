---
title: Logon personalizado
description: Saiba como investigar erros usando o registro personalizado.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# Visão geral do log personalizado

Os registros fornecem visibilidade sobre os processos do sistema; por exemplo, informações de depuração que ajudam você a entender quando ocorreu um erro ou o que levou ao erro.

Este tópico se concentra no registro baseado em arquivos, embora o Commerce também forneça a flexibilidade para armazenar logs no banco de dados.

O Adobe recomenda o uso de registro de aplicativo centralizado pelos seguintes motivos:

- Ele permite o armazenamento de registros em um servidor diferente do servidor de aplicativos e diminui as operações de I/O de disco, simplificando o suporte do servidor de aplicativos.

- Isso torna o processamento de dados de logs mais eficaz usando ferramentas especiais, como [Logstash], [Logplex] ou [fluentd], sem impacto em um servidor de produção.

  >[!INFO]
  >
  >O Adobe não recomenda ou endossa nenhuma solução de registro específica.

## Conformidade com a PSR-3

O [padrão PSR-3][laminas] define uma interface PHP comum para bibliotecas de log. A principal meta do PSR-3 é permitir que as bibliotecas recebam um objeto `Psr\Log\LoggerInterface` e gravem logs nele de forma simples e universal.

Isso permite que a implementação seja substituída facilmente, sem preocupação de que essa substituição possa quebrar o código do aplicativo. Ele também garante que um componente personalizado funcione mesmo quando a implementação do log for alterada em uma versão futura do sistema.

## Monólogo

O Commerce 2 está em conformidade com o padrão PSR-3. Por padrão, o Commerce usa [Monolog]. Monólogo implementado como preferência para `Psr\Log\LoggerInterface` no aplicativo do Commerce [`di.xml`][di].

Monolog é uma solução de registro PHP popular com uma ampla gama de manipuladores que permitem construir estratégias de registro avançadas. Veja a seguir um resumo de como o Monolog funciona.

Um _logger_ de Monólogo é um canal que tem seu próprio conjunto de _manipuladores_. O monólogo tem muitos manipuladores, incluindo:

- Registro em arquivos e syslog
- Enviar alertas e emails
- Registra servidores específicos e registros em rede
- Logon no desenvolvimento (integração com o FireBug e o Chrome Logger, entre outros)
- Fazer logon no banco de dados

Cada manipulador pode processar a mensagem de entrada e interromper a propagação ou passar o controle para o próximo manipulador em uma cadeia.

As mensagens de log podem ser processadas de várias maneiras diferentes. Por exemplo, você pode armazenar todas as informações de depuração em um arquivo no disco, colocar as mensagens com níveis de log mais altos em um banco de dados e, finalmente, enviar mensagens com nível de log &quot;crítico&quot; por e-mail.

Outros canais podem ter um conjunto diferente de manipuladores e lógicas.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[fluente]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monólogo]: https://github.com/Seldaek/monolog
