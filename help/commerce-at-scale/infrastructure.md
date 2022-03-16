---
title: Alinhamento da infraestrutura Adobe Commerce e Adobe Experience Manager
description: Alinhe sua infraestrutura Adobe Commerce e Adobe Experience Manager para definir tempos limite e limites de conexão aceitáveis.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '671'
ht-degree: 0%

---

# Alinhamentos de infraestrutura (limites de tempo limite e de conexão)

Há configurações com AEM e Adobe Commerce e infraestrutura ao redor, como balanceadores de carga que precisam de alinhamento, relacionadas a limites de conexão e configurações de tempo limite.

Um desalinhamento entre esses limites significaria que as conexões poderiam acabar sendo aceleradas AEM lado, enquanto a Adobe Commerce é capaz de lidar com mais conexões. Da mesma forma, para as configurações de tempo limite, um alinhamento incorreto pode significar que erros de tempo limite ocorrem AEM lado, enquanto o Adobe Commerce ainda está processando uma solicitação.

Para as configurações de tempo limite, as configurações devem ser revisadas e alinhadas para evitar que erros de tempo limite 503 apareçam quando estão sob carregamento. Há várias configurações de infraestrutura e tempo limite do aplicativo a serem analisadas:

![Diagrama numerado que descreve tempos limite e limites de conexão para AEM](../assets/commerce-at-scale/timeout-settings.svg)

## Balanceador de carga de AEM

Supondo que haja um balanceador de carga do aplicativo AWS na infraestrutura e vários dispatchers/editores - as seguintes configurações devem ser consideradas para o balanceador de carga:

1. As verificações de integridade do editor devem ser revisadas para evitar que os despachantes saiam do serviço desnecessariamente cedo de sobrecargas. As configurações de tempo limite da verificação de integridade do balanceador de carga devem ser alinhadas com as configurações de tempo limite do editor.

   ![Captura de tela mostrando AEM verificações de integridade do balanceador de carga](../assets/commerce-at-scale/health-checks.png)

1. A adesão do grupo de destino do Dispatcher pode ser desativada e o algoritmo de balanceamento de carga Round Robin pode ser usado. Isso é suposto que não haja AEM funcionalidade específica ou AEM sessões de usuário usadas que exigiriam que a adesão à sessão fosse definida. Ele pressupõe que o logon do usuário e o gerenciamento de sessões estejam somente na Adobe Commerce via GraphQL.

   ![Captura de tela mostrando atributos de adesão AEM sessão](../assets/commerce-at-scale/session-stickiness.png)

1. Observe que se você ativar a adesão à sessão, isso pode fazer com que as solicitações não sejam armazenadas em cache de forma rápida, pois, por padrão, o Fastly não armazena páginas em cache com o cabeçalho Definir cookies . O Adobe Commerce define cookies mesmo em páginas que podem ser armazenadas em cache (TTL > 0), mas o VCL padrão Fastly remove esses cookies em páginas que podem ser armazenadas em cache para que o armazenamento em cache Fastly funcione. Se as páginas não estiverem sendo armazenadas em cache, verifique os cookies personalizados que você estiver usando e também carregue o VCL com rapidez e verifique novamente o site.

## Configurações de tempo limite do Dispatcher

As opções /timeout nas &quot;renders&quot; do dispatcher especificam o tempo limite de conexão acessando a instância de publicação AEM em milissegundos. Isso deve ser revisado e a configuração padrão de &quot;0&quot; (tempo limite indefinido) deve ser usada se um balanceador de carga separado estiver presente para lidar com as configurações de tempo limite.

Se não houver balanceador de carga na infraestrutura, as configurações de tempo limite devem ser especificadas nas configurações de dispatcher/timeout, com um valor que corresponda às configurações de tempo limite GraphQL no editor.

## Editores

Limites de conexão GraphQL do editor e tempos limite: Inicialmente, as conexões máximas HTTP nas configurações OSGI de fábrica de configurações do cliente GraphQL da CIF do Adobe Commerce devem ser definidas para o limite máximo padrão de conexões Fastly , que está atualmente definido como 200. Mesmo que haja vários editores no farm de AEM, o limite deve ser definido do mesmo modo em cada publicador, correspondendo à configuração Fastly . O motivo para isso é que em alguns casos, um editor pode estar lidando com mais tráfego do que outros editores, se um dispatcher associado for retirado do farm, por exemplo. Isso significaria que todo o tráfego seria roteado por meio do único dispatcher e editores restantes, nesse caso, o editor único pode precisar de todas as conexões HTTP.

O &quot;método HTTP padrão&quot; deve ser definido de POST para GET. Somente as solicitações do GET são armazenadas em cache no cache GraphQL da Adobe Commerce e, portanto, o método padrão deve sempre ser definido como GET.

O tempo limite da conexão http e o tempo limite do soquete http devem ser definidos com um valor que corresponda ao tempo limite Fastly.

A imagem a seguir mostra a Fábrica de configuração do cliente GraphQL da CIF do Magento. As configurações mostradas aqui são apenas exemplos e precisam ser ajustadas caso a caso:

![Captura de tela das configurações da estrutura de integração do Commerce](../assets/commerce-at-scale/cif-config.png)

As imagens a seguir mostram as configurações Fastly backend. As configurações mostradas aqui são apenas exemplos e precisam ser ajustadas caso a caso:

![Captura de tela das configurações do Administrador do Commerce para Fastly](../assets/commerce-at-scale/cif-config-advanced.png)
