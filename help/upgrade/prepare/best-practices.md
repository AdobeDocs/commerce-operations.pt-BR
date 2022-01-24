---
title: Práticas recomendadas
description: Use as práticas recomendadas do Adobe para gerenciar o processo de atualização para seus projetos do Adobe Commerce e do Magento Open Source.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---


# Práticas recomendadas para atualização

Este tópico lista as ações que você deve tomar para gerenciar a complexidade da atualização de projetos do Adobe Commerce e do Magento Open Source. Sua equipe deve estar pensando nas atualizações a partir do momento em que o desenvolvimento do projeto começar e continuar em cada versão. Seguindo essas práticas recomendadas, o processo de atualização será muito mais fácil, mais rápido e mais barato.

>[!TIP]
>
>Essas recomendações são baseadas em práticas recomendadas apoiadas por provas de seu impacto e eficácia de parceiros, comerciantes, especialistas em Adobe e da comunidade.

## O que afeta uma atualização?

É importante entender as variáveis que determinam a complexidade de uma atualização. Você deve considerar essas variáveis no início de cada projeto, não apenas quando é hora de atualizar. O desenvolvimento de um projeto é fundamental para garantir que as atualizações futuras sejam suaves e que você possa controlar o esforço necessário para concluí-las.

O nível de esforço para atualizar sua instância do Adobe Commerce depende desses fatores:

- **Como você criou seu site?** A quantidade de trabalho personalizado e o número de módulos de terceiros instalados afetam fortemente a complexidade de uma atualização. A qualidade do trabalho e dos módulos personalizados pode determinar se uma atualização ocorre sem problemas.

- **Você está ignorando várias versões?** Ignorar as versões torna a próxima atualização mais complexa, atualizar das versões resultantes torna o processo mais fácil e barato.

- **Que tipo de atualização você está realizando?** Uma atualização para uma versão secundária (de 2.3.x para 2.4.0, por exemplo) é mais extensa do que uma atualização entre as versões de patch (como de 2.4.2 para 2.4.3). As atualizações de segurança são o tipo mais fácil de implementar.

## Práticas recomendadas para o planejamento de atualizações

Se você estiver trabalhando em um projeto que já está em produção, as atualizações são uma oportunidade para melhorar a qualidade do código e das personalizações, além de otimizar para atualizações futuras. O tempo que você investe hoje é o tempo que economiza a longo prazo.

Se você gerenciar vários sites para diferentes comerciantes, a melhor abordagem é ter uma instância básica com os principais recursos e personalizações que você normalmente usa. Use essa instância base como site de teste para concluir uma atualização e, em seguida, faça isso em outras pessoas. Essa prática oferece a flexibilidade de reutilizar módulos personalizados para diferentes clientes e simplificar atualizações em todos os projetos.

Caso seu projeto esteja em execução, sugerimos que você execute uma auditoria para determinar sua qualidade e entenda como você pode melhorá-la para tornar as atualizações mais eficientes.

### Desenvolvimento com atualizações em mente

A partir do momento em que você começar a trabalhar em um projeto, deve considerar como as atualizações futuras serão afetadas pelo seu trabalho atual. Siga sempre as práticas recomendadas de desenvolvimento do Adobe Commerce conforme descrito aqui:

- [Práticas recomendadas de desenvolvimento](https://devdocs.magento.com/guides/v2.4/ext-best-practices/bk-ext-best-practices.html)
- [Normas de codificação](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html)

Comece a adotar a plataforma Adobe Commerce Extensibility, se ainda não tiver feito. A plataforma permite personalizar com eficiência os processos, integrar sistemas e implantar novos recursos, mantendo a capacidade de atualização semelhante ao SaaS. Seus recursos incluem:

- **Extensibilidade da interface do usuário**. Estenda e desenvolva sua loja independentemente do seu back-end e do middleware usando [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensibilidade da API**. Use [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) estender a camada da API da Web, desenvolvendo o modelo de dados de gráfico e executando funções lambda diretamente da camada de gráfico.

- **Middleware e serviços de Adobe I/O**. Conecte seus sistemas com a Adobe Commerce usando o middleware Adobe e um conjunto de conexões de aplicativos criadas em [Adobe I/O](https://www.adobe.io/). Além disso, você pode estender os recursos da plataforma principal, substituindo o comportamento padrão por sua própria lógica comercial, que é executada no Adobe I/O.

### Planejamento de atualizações

À medida que expandimos continuamente os recursos do Adobe Commerce, é essencial desenvolver a versão mais recente disponível e definir uma estratégia de atualização nos planos de projeto. Isso o ajuda a manter-se seguro, compatível e atualizado com os aprimoramentos mais recentes que permitem aumentar as vendas mais rapidamente, operar mais eficientemente e manter-se à frente de sua concorrência agora e no futuro.

Para ajudá-lo a planejar e orçar atualizações, você deve monitorar nossa [cronograma de lançamento](https://devdocs.magento.com/release). Planeje as tarefas de atualização com antecedência no backlog da sua equipe. Pretende concluir este trabalho com GA.

- Use a versão de pré-lançamento para saber mais sobre cada nova versão. O pré-lançamento é o código de Disponibilidade Geral que está disponível para os comerciantes da Adobe Commerce e todos os parceiros duas semanas antes da Disponibilidade Geral. Se você tiver várias lojas, use o pré-lançamento na loja base e verifique se os módulos e temas personalizados são compatíveis com ele.

- Revise o [Atualizar lista de verificação do plano](https://support.magento.com/hc/en-us/articles/360057968951) para a Adobe Commerce para ajudá-lo a planejar sua atualização.

- Plano de atualizações no início do ano. Você deve reservar um orçamento e recursos para concluir cada atualização. Lembre-se, o esforço de atualização pode variar significativamente de projeto para projeto. Use suas experiências e conhecimento para tornar um plano o mais preciso possível.

- Se as atualizações estiverem se esforçando mais do que o descrito aqui, recomendamos que você faça auditoria em seu projeto e faça ajustes no ambiente para reduzir a manutenção de longo prazo.

### Execução de atualizações

As atualizações devem ser feitas regularmente e sob um orçamento predefinido. Recomendamos o agendamento de atualizações pré-aprovadas no início do ano para garantir que as atualizações sejam planejadas e concluídas a tempo.

Avalie o trabalho a ser feito para atualizar:

- Revise o [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para compreender o escopo e o impacto da nova versão.

- Use o [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) para identificar possíveis problemas que devem ser corrigidos em seu código personalizado antes de tentar atualizar para uma versão mais recente.

- Se estiver usando extensões de terceiros, valide a compatibilidade com a versão de destino para a qual você pretende atualizar.

### Teste pós-atualização

O teste é a fase de uma atualização que requer mais tempo. Consequentemente, este processo deve ser tão automatizado quanto possível. Você pode se beneficiar do uso das ferramentas de teste principais. O [Guia de teste de aplicativo](https://devdocs.magento.com/guides/v2.4/test/testing.html) fornece detalhes.

Use um ambiente de preparo para testar e validar sua atualização antes de migrar para a produção.

Utilizar um **página de manutenção**. Preparar essa página antecipadamente permite que você se comunique com seus clientes, notificando-os de que o trabalho está acontecendo em segundo plano. Essa página deve estar visível por alguns minutos, mas se houver um problema, talvez seja necessário usá-la por mais tempo. Ter o conteúdo e o design apropriados para a sua página de manutenção fornece uma boa experiência aos usuários, mesmo quando a loja não está disponível.
