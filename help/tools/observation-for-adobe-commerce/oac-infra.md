---
title: A variável [!DNL Infra] guia
description: A variável [!DNL Infra] A guia isola os problemas e as causas dos problemas de infraestrutura.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# A variável [!DNL Infra] guia

A variável **[!DNL Infra]** A guia isola os problemas e as causas dos problemas de infraestrutura. Além disso, são descritos os quadros que você pode ver na guia.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertas de serviço](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

A variável **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** O gráfico mostra os alertas de serviço coletados pelo [!DNL New Relic] agente de infraestrutura. Isso mostrará reinicializações do serviço, muitas associadas a implantações.

## [!UICONTROL Inode usage by mount]

![Uso do Inode por montagem](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

A variável **[!UICONTROL Inode usage by mount]** mostra quadros [!DNL inode] uso por montagem durante o período selecionado. Embora possa haver muito armazenamento livre, se um nó ficar sem [!DNL inodes], isso mostrará uma falta de armazenamento disponível. A remoção de arquivos (especialmente os pequenos) liberará espaço e tornará [!DNL inodes] disponíveis.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Visualização da camada do vCPU na linha do tempo MAIOR que 2 semanas](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

A variável **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** O quadro mostra a exibição de camada do vCPU no período selecionado de mais de duas semanas. Esse quadro verifica o número de vCPUs atribuídas ao [!DNL New Relic] nome do aplicativo mostrado.

## [!UICONTROL vCPU tier view over timeline]

![Visualização da camada do vCPU na linha do tempo](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

A variável **[!UICONTROL vCPU tier view over timeline]** O quadro mostra a exibição de camada do vCPU no período selecionado de mais de 24 horas. Esse quadro verifica o número de vCPUs atribuídas ao [!DNL New Relic] nome do aplicativo mostrado. Ele mostrará tanto upsizing quanto downsizes do cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Visualização da camada do vCPU na linha do tempo por NÓ](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

A variável **[!UICONTROL vCPU tier view over timeline BY NODE]** O quadro mostra as visualizações de camada do vCPU através do período selecionado por nó. Esse quadro é útil para detectar a perda de nó(s) ou quando os nós são submetidos a upsizing ou downsizing. A visualização do nível da vCPU em relação à linha do tempo POR NÓ deve observar a linha do tempo MENOS de 24 horas.

## [!UICONTROL Instance details]

![Detalhes da instância](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

A variável **[!UICONTROL Instance details]** A tabela mostra os detalhes da instância de cada [!DNL New Relic] aplicação.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nó não responsivo](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

A variável **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** mostra nós não responsivos durante um período.
