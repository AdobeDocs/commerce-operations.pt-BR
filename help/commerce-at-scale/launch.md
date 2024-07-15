---
title: Dicas para testes de desempenho
description: Saiba como definir KPIs para iniciar sua solução Adobe Commerce e Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---

# Dicas de teste de desempenho

Para avaliar a eficácia de todas as alterações acima, deve-se executar um teste de desempenho completo antes da ativação e antes de qualquer implantação importante futura em seus ambientes de produção. Ao planejar o teste de carga, é importante simular o máximo possível o tráfego real do consumidor.

As áreas que mais consomem recursos do site AEM/CIF/Adobe Commerce são aquelas que não podem ser armazenadas em cache, como o processo de finalização e a pesquisa no site. A navegação de página estática e, portanto, armazenável em cache, como para as Páginas de detalhes do produto (PDPs) e as Páginas de listagem de produto (PLPs), compõem a maioria do tráfego para um site de comércio eletrônico em geral. Portanto, os scripts e cenários no teste devem refletir isso para medir os limites da plataforma.

Ter um único script em execução para o teste de carga que navega pelo site sem tempo de espera entre as etapas e também sempre conclui o processo de finalização toda vez não forneceria uma indicação confiável dos limites da plataforma, pois não é um cenário real.

A definição de KPIs deve ser a primeira etapa do plano de teste de desempenho: defina métricas que você pode testar durante o teste inicial, mas que podem ser medidas novamente no futuro e de forma recorrente depois que o site estiver ativo. Isso permite rastrear o desempenho do site ao longo do tempo, antes e depois do lançamento. Os KPIs de exemplo a serem definidos podem ser:

- Tempo médio de resposta - tempo até o primeiro ou o último byte
- Latência
- Bytes/s (Taxa de transferência)
- Taxa de erros
- Pedidos por hora
- Exibições de página por hora
- Usuários únicos por hora (compradores simultâneos)

## Diretrizes do Jm

As seguintes diretrizes de alto nível do Jm devem ser consideradas ao desenvolver o teste de carga do AEM/CIF/Adobe Commerce:

- Divida o script em cenários configuráveis, que devem abranger, por exemplo:
   - Abrir Página Inicial
   - Abrir página de categoria (PLP)
   - Visualizar produtos simples (PDP) - 2 loops em cada iteração
   - Visualizar produtos configuráveis - 2 loops em cada iteração
      - Por exemplo, defina as etapas acima para 60% do tráfego
   - Pesquisa de produto
      - Por exemplo, defina a pesquisa no catálogo para 37% do tráfego
   - Carrinho e check-out
      - Por exemplo, um usuário que conclui o carrinho e conclui a parte do script deve usar como padrão uma taxa de conversão de site de comércio eletrônico padrão do setor de cerca de 3%
      - Como o fluxo de check-out não é armazenado em cache e geralmente é uma operação que consome muitos recursos, definir um número irrealisticamente alto para o número de pessoas concluindo pedidos em comparação ao número de navegadores de site forneceria um resultado não confiável para o volume de tráfego que seu site poderia lidar.
- Limpar todos os caches antes de cada execução de teste:
   - O cache do Dispatcher do AEM deve ser totalmente limpo
   - O Fastly e o cache interno do Adobe Commerce devem ser totalmente liberados e limpos - isso pode ser feito por meio do controle de cache no administrador do Adobe Commerce.
- Incluir um período de rampa no teste Jm: não ter um período de rampa definido significa que não há aumento gradual de tráfego e não há chance para o site armazenar em cache nenhuma das páginas e componentes comumente visitados da página. Na vida real, seria incomum que todo o tráfego de pico chegasse em um site totalmente sem cache exatamente ao mesmo tempo, portanto, um período de aumento deve ser incluído nos scripts de teste Jm para permitir que o cache seja construído como aconteceria em um site real de comércio eletrônico.
- Um &quot;tempo de espera&quot; entre cada etapa em uma iteração deve ser usado - na realidade, um usuário não
ir imediatamente para a próxima página no site durante a jornada - haveria um tempo de espera enquanto o usuário lia a página e decidia sobre sua próxima ação.
- Configurar os grupos de segmentos para fazer um loop infinito, mas para um tempo definido de x (por exemplo, 60 minutos), fornecerá um teste repetível, com tempos de resposta medianos comparáveis aos de execuções de teste anteriores. Isso significa que após o período de aumento definido, haverá o número alvo de usuários virtuais em execução simultânea e isso continuará pelo tempo de loop definido.
- A mediana do tempo deve ser utilizada para fornecer uma melhora/declínio no tempo médio de resposta, não na média. Se
há vários resultados de borda que demoram muito mais do que os outros resultados, isso distorceria esse resultado médio, mas no que estamos interessados no tempo de resposta do usuário final para a maioria dos usuários, que é mais adequado para a medida mediana.
- Por padrão, os recursos incorporados não são coletados em jmeter (por exemplo, JS, CSS e outros recursos baixados quando um usuário real visita a página). Isso pode ser ativado, mas somente para o domínio que você está testando - as chamadas de recursos externos ainda devem ser excluídas (por exemplo, não queremos incluir tempos de resposta de serviços hospedados externamente, por exemplo, código do google analytics, já que não temos controle sobre ele).
- O HTTP Cache Manager deve estar ativado, isso permite que o Jm armazene em cache elementos de página durante uma jornada como
a jornada de um usuário real ocorreria durante a navegação do site em seu próprio navegador. Durante a jornada pelo site, o navegador do usuário baixava o recurso incorporado relacionado apenas uma vez e, em seguida, eles eram armazenados em cache pelo navegador do usuário. Além disso, se o mesmo usuário retornar ao site algum tempo após sua visita original, ainda poderá ser o cache em que esses ativos são armazenados.
- Os ouvintes devem ser mantidos dentro das execuções de teste de carga reais (por exemplo, &quot;Exibir árvore de resultados&quot; e &quot;Relatório agregado&quot;). A inclusão disso na execução do teste de carga real não-GUI pode afetar os resultados de desempenho relatados pelo Jmeter, pois os recursos são usados durante a execução do teste real para gerar os relatórios. Esses ouvintes foram removidos do script de teste para serem substituídos por um arquivo de resultados JTL, que pode ser processado usando a funcionalidade Report Dashboard do Jm.
- Um tempo de resposta alvo para ser avaliado, de modo que a &quot;pontuação Apdex&quot; do relatório do painel possa ser usada como uma maneira rápida de medir o efeito das alterações no desempenho entre execuções de teste. A pontuação do Apdex é baseada em uma certa quantidade de pessoas capazes de acessar o site em um tempo tolerável . Se o tempo de resposta ultrapassar uma determinada quantia &quot;frustrante&quot;, a pontuação será reduzida. Os horários podem ser definidos usando os parâmetros &quot;apdex_completed_ threshold&quot; e &quot;apdex_tolerated_threshold&quot;.
- Defina uma métrica de destino &quot;Pedidos por hora&quot; para apresentar aos usuários empresariais, não uma contagem de Usuários virtuais. &quot;Usuários virtuais&quot; pode ser um tópico complexo para entender o que, na vida real, o teste está medindo. Calculando a taxa de conversão do site, os pedidos por hora, o tempo médio que um usuário gasta no site e o tempo de processamento entre cada carregamento de página, os cálculos padrão do setor podem ser usados para apresentar diferentes cenários de teste de carga com base nos pedidos por hora a serem realizados.
- Por fim, o servidor de testes Jm deve ser executado em um servidor geograficamente próximo de onde a maioria do tráfego de usuários vem e onde sua infraestrutura em nuvem está hospedada - espera-se que sejam os mesmos.
