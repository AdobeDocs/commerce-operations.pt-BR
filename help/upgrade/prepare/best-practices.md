---
title: Práticas recomendadas
description: Use as práticas recomendadas pelo Adobe para gerenciar o processo de atualização de seus projetos do Adobe Commerce.
feature: Upgrade, Best Practices
exl-id: 53c505a3-8b99-4fc3-b1b4-f2f75208a51b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 0%

---

# Práticas recomendadas para atualização

Este tópico lista as ações que você deve tomar para gerenciar a complexidade da atualização de projetos do Adobe Commerce. Sua equipe deve pensar em atualizações a partir do momento em que o desenvolvimento do projeto começa e continuar em cada versão. Seguindo essas práticas recomendadas, o processo de atualização será muito mais fácil, mais rápido e mais barato.

>[!TIP]
>
>Essas recomendações se baseiam em práticas recomendadas apoiadas por evidências de seu impacto e eficácia de parceiros, comerciantes, especialistas em Adobe e da comunidade.

## O que afeta uma atualização?

É importante entender as variáveis que determinam a complexidade de uma atualização. Você deve considerar essas variáveis no início de cada projeto, não apenas quando é hora de atualizar. O desenvolvimento de um projeto é fundamental para garantir que as atualizações futuras sejam tranquilas e que você seja capaz de controlar o esforço necessário para concluí-las.

O nível de esforço para atualizar a instância do Adobe Commerce depende destes fatores:

- **Como você criou seu site?** A quantidade de trabalho personalizado e o número de módulos de terceiros instalados afetam fortemente a complexidade de uma atualização. A qualidade do trabalho e dos módulos personalizados pode determinar se uma atualização ocorre sem problemas.

- **Você está ignorando várias versões?** Ignorar as versões torna a próxima atualização mais complexa, atualizar das versões subsequentes torna o processo mais fácil e barato.

- **Que tipo de atualização você está executando?** Uma atualização para uma versão secundária (de 2.3.x para 2.4.0, por exemplo) é mais extensa do que uma atualização entre versões de patch (como de 2.4.2 para 2.4.3). As atualizações de segurança são o tipo mais fácil de implementar.

## Práticas recomendadas para o planejamento de atualizações

Se você estiver trabalhando em um projeto que já está em produção, as atualizações são uma oportunidade para melhorar a qualidade do código e das personalizações, e otimizar para atualizações futuras. O tempo que você investe hoje economiza tempo a longo prazo.

Se você gerenciar vários sites para diferentes comerciantes, a melhor abordagem é ter uma instância base com os principais recursos e personalizações que você normalmente usa. Use essa instância base como seu site de teste para concluir uma atualização e, em seguida, faça isso em outras pessoas. Essa prática oferece flexibilidade para reutilizar módulos personalizados para clientes diferentes e simplificar atualizações entre projetos.

Se o projeto estiver ativo, sugerimos executar uma auditoria para determinar sua qualidade e entender como você pode melhorá-lo para tornar as atualizações mais eficientes.

### Desenvolvimento tendo em mente atualizações

A partir do momento em que você começa a trabalhar em um projeto, considere como as atualizações futuras serão afetadas pelo seu trabalho atual. Siga sempre as práticas recomendadas de desenvolvimento do Adobe Commerce, conforme descrito aqui:

- [Práticas recomendadas de desenvolvimento](https://developer.adobe.com/commerce/php/best-practices/)
- [Padrões de codificação](https://developer.adobe.com/commerce/php/coding-standards/)

Comece a adotar a plataforma Adobe Commerce Extensibility, se ainda não tiver adotado. A plataforma permite que você personalize processos, integre sistemas e implante novos recursos com eficiência, mantendo a capacidade de atualização semelhante ao SaaS. Seus recursos incluem:

- **Extensibilidade da interface**. Amplie e evolua sua loja independentemente de seu back-end e middleware usando [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/).

- **Extensibilidade de API**. Uso [GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/index.html) estender a camada da API da Web evoluindo o modelo de dados do gráfico e executando funções lambda diretamente da camada do gráfico.

- **middleware e serviços Adobe I/O**. Conecte seus sistemas com o Adobe Commerce usando o Adobe middleware e um conjunto de conexões de aplicativos incorporados [Adobe I/O](https://www.adobe.io/). Além disso, você pode estender os principais recursos da plataforma, substituindo o comportamento padrão pela sua própria lógica de negócios que é executada no Adobe I/O.

### Atualizações do Planning

À medida que expandimos continuamente os recursos do Adobe Commerce, é essencial desenvolver na versão mais recente disponível e definir uma estratégia de atualização em seus planos de projeto. Dessa forma, você permanecerá seguro, em conformidade e atualizado com os últimos aprimoramentos que lhe permitem aumentar as vendas mais rapidamente, operar com mais eficiência e manter-se à frente da concorrência agora e no futuro.

Para ajudá-lo a planejar e orçar atualizações, você deve monitorar nossa [programação de lançamento](https://devdocs.magento.com/release). Planeje tarefas de atualização na lista de pendências da sua equipe com antecedência. Pretende concluir este trabalho com a DG.

- Use a versão de pré-lançamento para saber mais sobre cada nova versão. O pré-lançamento é o código de Disponibilidade geral disponível para os comerciantes da Adobe Commerce e todos os parceiros duas semanas antes da Disponibilidade geral. Se você tiver vários armazenamentos, use o pré-lançamento em seu armazenamento básico e verifique se os módulos e temas personalizados são compatíveis com ele.

- Revise o [Lista de verificação do plano de atualização](https://support.magento.com/hc/en-us/articles/360057968951) para que o Adobe Commerce o ajude a planejar sua atualização.

- Planeje atualizações no início do ano. Você deve reservar um orçamento e recursos para concluir cada atualização. Lembre-se, o esforço de atualização pode variar significativamente de projeto para projeto. Use suas experiências e conhecimento para fazer um plano o mais preciso possível.

- Se suas atualizações estiverem se esforçando mais do que o que descrevemos aqui, recomendamos que você faça uma auditoria de seu projeto e faça ajustes em seu ambiente para reduzir a manutenção de longo prazo.

### Atualizações

As atualizações devem ser feitas regularmente e com um orçamento predefinido. Recomendamos a programação de atualizações pré-aprovadas no início do ano para garantir que as atualizações sejam planejadas e concluídas a tempo.

Avaliar o trabalho a ser feito para atualização:

- Revise o [notas de versão](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) para entender o escopo e o impacto da nova versão.

- Use o [[!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/overview.md) para identificar possíveis problemas que devem ser corrigidos em seu código personalizado antes de tentar atualizar para uma versão mais recente.

- Se você estiver usando extensões de terceiros, valide a compatibilidade delas com a versão de destino para a qual você está planejando atualizar.

### Teste pós-atualização

Os testes são a fase de uma atualização que requer mais tempo. Como resultado, esse processo deve ser o mais automatizado possível. Você pode se beneficiar usando as ferramentas de teste principais. A variável [Guia de teste do aplicativo](https://developer.adobe.com/commerce/testing/guide/) fornece detalhes.

Use um ambiente de preparo para testar e validar sua atualização antes de passar para a produção.

Utilizar um **página de manutenção**. Preparar essa página com antecedência permite que você se comunique com seus clientes, notificando-os de que o trabalho está acontecendo em segundo plano. Esta página deve ficar visível por alguns minutos, mas se houver um problema, talvez seja necessário usá-la por mais tempo. Ter o conteúdo e o design apropriados para sua página de manutenção oferece aos usuários uma boa experiência, mesmo quando sua loja não está disponível.
