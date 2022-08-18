---
title: '"O [!UICONTROL Infra] tab"'
description: O [!UICONTROL Infra] A guia isola problemas e causas de problemas de infraestrutura.
source-git-commit: b0d80d97f60b24bc801063dc484f3a495cf0a036
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# O [!UICONTROL Infra] guia

O **[!UICONTROL Infra]** A guia isola problemas e causas de problemas de infraestrutura. Além disso, estão descritos os quadros que podem ser vistos na guia .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertas de serviço](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

O **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** gráfico mostra os alertas de serviço coletados pelo [!DNL New Relic] agente de infraestrutura. Isso mostrará reinicializações de serviço, muitas associadas às implantações.

## [!UICONTROL Inode usage by mount]

![Uso do nó por montagem](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

O **[!UICONTROL Inode usage by mount]** quadro mostra o uso de nó por montagem no período selecionado. Embora possa haver bastante armazenamento livre, se um nó ficar sem nós, ele mostrará uma falta de armazenamento disponível. A remoção de arquivos (especialmente os pequenos) liberará espaço e disponibilizará nós.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Visualização da camada da vCPU na linha do tempo MAIOR 2 semanas](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

O **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** quadro mostra a exibição da camada da vCPU no período de mais de duas semanas selecionado. Este quadro observa o número de vCPUs atribuídas ao [!DNL New Relic] nome do aplicativo mostrado.

## [!UICONTROL vCPU tier view over timeline]

![Exibição da camada da vCPU na linha do tempo](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

O **[!UICONTROL vCPU tier view over timeline]** quadro mostra a exibição da camada da vCPU no período de tempo selecionado de mais de 24 horas. Este quadro observa o número de vCPUs atribuídas ao [!DNL New Relic] nome do aplicativo mostrado. Ele mostrará os tamanhos de atualização e downloads do cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Visualização da camada da vCPU na linha do tempo pelo NÓ](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

O **[!UICONTROL vCPU tier view over timeline BY NODE]** quadro mostra visualizações da camada da vCPU no período selecionado por nó. Esse quadro é útil para detectar a perda do(s) nó(s) ou quando os nós são atualizados ou baixados. A exibição da camada da vCPU na linha do tempo POR NÓ deve examinar a linha do tempo MENOS de 24 horas.

## [!UICONTROL Instance details]

![Detalhes da instância](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

O **[!UICONTROL Instance details]** tabela mostra detalhes da instância de cada [!DNL New Relic] aplicativo.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nó não responsivo](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

O **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** quadro mostra nós não responsivos em um período de tempo.
