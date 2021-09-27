---
title: Preparação para o Launch
description: Saiba como definir KPIs para iniciar sua solução Adobe Commerce e Adobe Experience Manager.
source-git-commit: 1cff7359ddb4caeca6773ff74b92048c89676f12
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---


# Preparar para iniciar

Para avaliar a eficácia de todas as alterações acima, deve ser executado um teste de desempenho completo antes da ativação e antes de qualquer implantação importante futura em seus ambientes de produção. Ao planejar seu teste de carga, é importante simular o mais possível o tráfego real do consumidor.

As áreas de mais recursos do site de Comércio de AEM/CIF/Adobe são aquelas que não podem ser armazenadas em cache, como o processo de finalização e a pesquisa no site. A navegação estática e, portanto, armazenável em cache de páginas, como para Páginas de detalhes do produto (PDPs) e Páginas de lista de produtos (PLPs), constituem a maioria do tráfego para um site de comércio eletrônico em geral, portanto, os scripts e cenários no teste devem refletir isso para medir os limites da plataforma.

Ter um único script em execução para o teste de carga que navega pelo site sem tempo de espera entre as etapas e também sempre conclui o processo de finalização sempre não daria uma indicação confiável dos limites da plataforma, pois não é esse o cenário da vida real.

A definição de KPIs deve ser a primeira etapa do seu plano de teste de desempenho: defina métricas que você pode testar durante seu teste inicial, mas depois medir novamente no futuro e de forma recorrente depois que o site estiver ativo. Isso permite que você acompanhe o desempenho do site ao longo do tempo - pré e pós-lançamento. Os KPIs de exemplo a serem definidos podem ser:

- Tempo médio de resposta - tempo até o primeiro byte ou o último byte
- Latência
- Bytes/s (Througput)
- Taxa de erro
- Pedidos por hora
- Exibições de página por hora
- Usuários únicos por hora (compradores simultâneos)

## Diretrizes do Jmetro

As seguintes diretrizes de alto nível de Jmetro devem ser consideradas ao desenvolver o teste de carga do AEM/CIF/Adobe Commerce:

- Divida seu script em cenários configuráveis, que devem abranger, por exemplo:
   - Abrir Página Inicial
   - Abrir página de categoria (PLP)
   - Exibir produtos simples (PDP) - 2 loops em cada iteração
   - Exibir produtos configuráveis - 2 loops de cada iteração
      - Por exemplo, defina as etapas acima para 60% do tráfego
   - Pesquisa de produto
      - Por exemplo, defina a pesquisa no catálogo para 37% do tráfego
   - Carrinho e Check-out
      - Por exemplo, um usuário que conclui a parte Carrinho e check-out do script deve se padronizar para uma taxa de conversão de site de comércio eletrônico padrão do setor de cerca de 3%
      - Como o fluxo de check-out não é armazenado em cache e geralmente é uma operação que consome muitos recursos, definir um valor irrealisticamente alto para o número de pessoas que concluem pedidos vs. o número de navegadores do site daria um resultado não confiável para o volume de tráfego que seu site poderia lidar.
- Limpe todos os caches antes de cada execução do teste:
   - O cache do dispatcher de AEM deve ser totalmente limpo
   - O cache rápido e interno do Adobe Commerce deve ser totalmente liberado e limpo, isso pode ser feito por meio do controle de cache no administrador do Adobe Commerce.
- Incluir um período de rampa no teste Jmetro: Não ter um período de rampa definido significa que o aumento gradual do tráfego não será realizado e nenhuma chance de o site armazenar em cache qualquer uma das páginas e componentes visitados com frequência na página. Na vida real, seria incomum que todo o tráfego de pico chegasse a um site totalmente sem cache exatamente ao mesmo tempo, portanto, um período de rampa deve ser incluído nos scripts de teste Jmetro para permitir que o cache se acumule como aconteceria em um site de comércio eletrônico real.
- Deve ser usado um &quot;Tempo de espera&quot; entre cada etapa de uma iteração - na realidade, um usuário não
Imediatamente para a próxima página no site durante a jornada - haveria um tempo de espera enquanto o usuário lia a página e decidia sobre sua próxima ação.
- Definir os grupos de encadeamento para loop infinitamente, mas para um tempo definido de x (por exemplo, 60 minutos), dará um teste repetível, com tempos de resposta medianos comparáveis a execuções de teste anteriores. Isso significa que, após o período de inicialização definido, haverá o número de usuários virtuais em execução simultaneamente e isso continuará para o tempo de loop definido.
- Deve utilizar-se o tempo médio para se obter uma melhoria/diminuição do tempo médio de resposta, e não a média. If
há vários resultados de borda que levam muito mais tempo do que os outros resultados, então isso distorceria esse resultado médio, mas o que nos interessa no tempo de resposta do usuário final para a maioria dos usuários, que é mais adequado para a medida mediana.
- Os recursos incorporados não são coletados por padrão no jmetro (por exemplo, JS, CSS e outros recursos baixados quando um usuário real visita a página). Isso pode ser ativado, mas somente para o domínio que você está testando - chamadas de recursos externos ainda devem ser excluídas (por exemplo, não queremos incluir tempos de resposta de serviços hospedados externamente, por exemplo. código do google analytics, pois não temos controle sobre eles).
- O Gerenciador de Cache HTTP deve estar habilitado, isso permite que o Jmetro armazene em cache elementos de página durante uma jornada como
a jornada de um usuário real seria exibida durante a navegação no site em seu próprio navegador. Durante a jornada pelo site, o navegador do usuário baixava os recursos incorporados relacionados somente uma vez e, em seguida, eles eram armazenados em cache pelo navegador do usuário. Além disso, se o mesmo usuário retornar ao site algum tempo após sua visita original, ainda assim, pode ser o cache em que esses ativos estão armazenados em cache.
- Os ouvintes devem ser mantidos dentro das execuções reais do teste de carga (por exemplo, &quot;Exibir árvore de resultados&quot; e &quot;Relatório agregado&quot;). Incluí-lo na execução de teste de carga real sem interface gráfica pode afetar os resultados de desempenho relatados pelo Jmetro, já que os recursos são usados durante a execução de teste real para gerar os relatórios. Esses ouvintes foram removidos do script de teste para serem substituídos por um arquivo de resultados JTL, que pode ser processado usando a funcionalidade Painel de relatórios do Jmetro.
- Um tempo de resposta do target para avaliado de forma que a &quot;Pontuação do Apdex&quot; do relatório de painel possa ser usada como uma forma rápida de medir o efeito das alterações no desempenho entre as execuções de teste. A pontuação do Apdex se baseia em uma certa quantidade de pessoas que podem acessar o site em um tempo tolerável . Se o tempo de resposta for acima de uma certa quantidade &quot;frustrante&quot;, isso diminuirá a pontuação. As horas podem ser definidas usando os parâmetros &quot;apdex_enabled_ threshold&quot; e &quot;apdex_tolerated_threshold&quot;.
- Defina uma métrica de meta &quot;Pedidos por hora&quot; para apresentar aos usuários comerciais, não uma contagem de Usuários Virtuais. &quot;Usuários virtuais&quot; pode ser um tópico complexo para entender o que o teste está medindo na vida real. Calculando a taxa de conversão do site, pedidos por hora, o tempo médio que um usuário gasta no site e o tempo de reflexão entre cada carregamento de página, os cálculos padrão do setor podem ser usados para apresentar diferentes cenários de teste de carga com base nos pedidos por hora a serem alcançados.
- Por fim, seu servidor de teste Jmetro deve ser executado em um servidor geograficamente próximo de onde a maior parte do tráfego de usuários vem e onde sua infraestrutura de nuvem está hospedada - espero que seja o mesmo.
