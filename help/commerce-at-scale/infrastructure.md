---
title: Alinhamento da infraestrutura Adobe Commerce e Adobe Experience Manager
description: Alinhe sua infraestrutura Adobe Commerce e Adobe Experience Manager para definir tempos limite e limites de conexão aceitáveis.
exl-id: f9cb818f-1461-4b23-b931-e7cee70912fd
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Alinhamentos de infraestrutura (tempos limite e limites de conexão)

Há configurações com AEM e Adobe Commerce e infraestrutura ao redor, como balanceadores de carga que precisam de alinhamento, relacionadas a limites de conexão e configurações de tempo limite.

Um desalinhamento entre esses limites significaria que as conexões poderiam acabar sendo reguladas no lado do AEM, enquanto o Adobe Commerce é capaz de lidar com mais conexões. Da mesma forma, para as configurações de tempo limite, um desalinhamento pode significar que erros de tempo limite ocorrem no lado do AEM, enquanto o Adobe Commerce ainda está processando uma solicitação.

Para as configurações de tempo limite, as configurações devem ser revisadas e alinhadas para impedir que erros de tempo limite 503 apareçam quando sob carga. Há várias configurações de infraestrutura e tempo limite de aplicativo a serem analisadas:

![Diagrama numerado descrevendo tempos limite e limites de conexão para AEM](../assets/commerce-at-scale/timeout-settings.svg)

## Balanceador de carga AEM

Supondo que haja um balanceador de carga de aplicativo do AWS na infraestrutura e vários dispatchers/editores, as seguintes configurações devem ser consideradas para o balanceador de carga:

1. As verificações de integridade do editor devem ser revisadas para evitar que os despachantes desistam do serviço desnecessariamente cedo devido a picos de carga. As configurações de tempo limite da verificação de integridade do balanceador de carga devem ser alinhadas às configurações de tempo limite do editor.

   ![Captura de tela mostrando as verificações de integridade do balanceador de carga AEM](../assets/commerce-at-scale/health-checks.png)

1. A aderência do grupo de destino do Dispatcher pode ser desativada e o algoritmo de balanceamento de carga Round Robin pode ser usado. Isso pressupõe que não haja nenhuma funcionalidade específica do AEM ou sessões de usuário do AEM usadas que exijam a definição da adesão à sessão. Ele pressupõe que o logon do usuário e o gerenciamento de sessão estejam somente no Adobe Commerce por meio do GraphQL.

   ![Captura de tela mostrando atributos de adesão à sessão AEM](../assets/commerce-at-scale/session-stickiness.png)

1. Observe que se você ativar a adesão à sessão, isso poderá fazer com que as solicitações do Fastly não sejam armazenadas em cache, pois, por padrão, o Fastly não armazena páginas em cache com o cabeçalho Set-Cookies. O Adobe Commerce define cookies mesmo em páginas armazenáveis em cache (TTL > 0), mas o Fastly VCL padrão remove esses cookies nas páginas armazenáveis em cache para que o armazenamento em cache do Fastly funcione. Se as páginas não estiverem armazenando em cache, verifique os cookies personalizados que você possa estar usando, faça upload do Fastly VCL e verifique novamente o site.

## Configurações de tempo limite do Dispatcher

As opções /timeout no dispatcher &quot;renders&quot; especificam o tempo limite da conexão acessando a instância de publicação AEM em milissegundos. Isso deve ser revisado e a configuração padrão de &quot;0&quot; (tempo limite indefinido) deve ser usada se um balanceador de carga separado estiver presente para lidar com as configurações de tempo limite.

Se não houver um balanceador de carga na infraestrutura, as configurações de tempo limite devem ser especificadas nas configurações /timeout do dispatcher, com um valor que corresponda às configurações de tempo limite do GraphQL no publicador.

## Editores

Limites de conexão e tempos limite do Publisher GraphQL: inicialmente, o número máximo de conexões HTTP nas configurações OSGI do Adobe Commerce CIF GraphQL Client Configuration Fatory deve ser definido como o limite máximo de conexões padrão do Fastly, que atualmente está definido como 200. Mesmo que haja vários editores no farm AEM, o limite deve ser definido da mesma maneira em cada editor, correspondendo à configuração Fastly. O motivo para isso é que, em alguns casos, um editor pode estar manipulando mais tráfego do que os outros editores, se um dispatcher associado for retirado do farm, por exemplo. Isso significaria que todo o tráfego seria roteado por meio do único dispatcher e editores restantes; nesse caso, o único editor pode precisar de todas as conexões HTTP.

O &quot;Método HTTP padrão&quot; deve ser definido de POST a GET. Somente as solicitações do GET são armazenadas em cache no cache do Adobe Commerce GraphQL e, portanto, o método padrão sempre deve ser definido como GET.

O tempo limite da conexão http e o tempo limite do soquete http devem ser definidos com um valor que corresponda ao tempo limite do Fastly.

A imagem a seguir mostra o Magento CIF GraphQL Client Configuration Fatory. As configurações mostradas aqui são apenas exemplos e precisam ser ajustadas caso a caso:

![Captura de tela das configurações de Commerce integration framework](../assets/commerce-at-scale/cif-config.png)

As imagens a seguir mostram as configurações de back-end do Fastly. As configurações mostradas aqui são apenas exemplos e precisam ser ajustadas caso a caso:

![Captura de tela das definições de configuração do administrador do Commerce para o Fastly](../assets/commerce-at-scale/cif-config-advanced.png)
