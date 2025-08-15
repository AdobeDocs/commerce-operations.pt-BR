---
title: 'A guia  [!DNL Infra] '
description: A guia  [!DNL Infra]  isola os problemas e as causas dos problemas de infraestrutura.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# A guia [!DNL Infra]

A guia **[!DNL Infra]** isola os problemas e as causas dos problemas de infraestrutura. Além disso, são descritos os quadros que você pode ver na guia.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Alertas de serviço](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

O gráfico **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** mostra os alertas de serviço coletados pelo agente de infraestrutura [!DNL New Relic]. Isso mostrará reinicializações do serviço, muitas associadas a implantações.

## [!UICONTROL Inode usage by mount]

![Uso do nó por montagem](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

O quadro **[!UICONTROL Inode usage by mount]** mostra o uso de [!DNL inode] por montagem durante o período selecionado. Embora possa haver bastante armazenamento livre, se um nó ficar sem [!DNL inodes], isso mostrará uma falta de armazenamento disponível. A remoção de arquivos (especialmente os pequenos) liberará espaço e disponibilizará o [!DNL inodes].

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Exibição da camada vCPU na linha do tempo MAIOR que 2 semanas](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

O quadro **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** mostra a exibição de camada do vCPU no período selecionado de mais de duas semanas. Este quadro analisa o número de vCPUs atribuídas ao nome do aplicativo [!DNL New Relic] mostrado.

## [!UICONTROL vCPU tier view over timeline]

![Exibição de camada do vCPU na linha do tempo](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

O quadro **[!UICONTROL vCPU tier view over timeline]** mostra a exibição de camada vCPU no período selecionado de mais de 24 horas. Este quadro analisa o número de vCPUs atribuídas ao nome do aplicativo [!DNL New Relic] mostrado. Ele mostrará tanto upsizing quanto downsizes do cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Exibição da camada vCPU na linha do tempo por NÓ](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

O quadro **[!UICONTROL vCPU tier view over timeline BY NODE]** mostra exibições da camada vCPU por nó ao longo do período selecionado. Esse quadro é útil para detectar a perda de nó(s) ou quando os nós são submetidos a upsizing ou downsizing. A visualização do nível da vCPU em relação à linha do tempo POR NÓ deve observar a linha do tempo MENOS de 24 horas.

## [!UICONTROL Instance details]

![Detalhes da instância](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

A tabela **[!UICONTROL Instance details]** mostra os detalhes da instância de cada aplicativo [!DNL New Relic].

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nó não responsivo](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

O quadro **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** mostra nós sem resposta durante um período.
