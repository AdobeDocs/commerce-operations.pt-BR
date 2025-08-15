---
title: A guia [!UICONTROL Security]
description: Saiba mais sobre a guia [!UICONTROL Security] do  [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# A guia [!UICONTROL Security]

A guia **[!UICONTROL Security]** explica os problemas de segurança e isola suas possíveis causas. Além disso, os quadros da guia são descritos.

## [!UICONTROL API calls by IP, details by URL]

O quadro **[!UICONTROL API calls by IP, details by URL]** mostra várias chamadas de API por IP ao longo de um período selecionado. Esse quadro exibe o endereço IP e o URL da API que foi acessado por esse endereço IP.

![Chamadas de API por IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

O quadro de acesso **[!UICONTROL Forgot Password]** mostra o número de tentativas de senhas esquecidas em um período selecionado. A alta atividade em relação a um endereço IP pode ser um ataque ao site.

![Esqueceu a senha](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

O quadro **[!UICONTROL Create Account access]** mostra o número de novas atividades de conta em um período selecionado. A alta atividade de um único endereço IP pode indicar um ataque.

![criar-acesso-conta](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

O quadro **[!UICONTROL POST activities]** mostra as atividades `POST` do site, facetadas em `client_ip` dos logs [!DNL Fastly]. Ele também mostra o URL que é acessado pelo endereço IP.

![PÓS-Atividade](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

O quadro **[!UICONTROL POST activities summary table]** mostra as `POST` atividades resumidas para o site, facetadas em `client_ip` dos logs [!DNL Fastly]. Ele também mostra a contagem do URL que é acessado pelo endereço IP. A contagem é para o período selecionado.

![resumo-pós-atividades](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

O quadro **[!UICONTROL POST activities details table]** mostra as atividades `POST` do site dos logs [!DNL Fastly]. Ele também mostra todos os detalhes do log [!DNL Fastly] para essas solicitações. Está limitado às últimas 2000 solicitações.
![Detalhes-pós-atividades](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

O quadro **[!UICONTROL Guest Carts activities]** mostra o número de atividades do carrinho de convidado em um período selecionado, facetado por endereço IP e URL acessado. Carrinhos convidados podem ser usados em um ataque de cartão. Este quadro mostra o número total de solicitações nas quais os URLs dos carrinhos convidados são acessados.

![atividades-carrinhos-convidados](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

O quadro **[!UICONTROL API – forgot password, create account by Countries]** mostra o número de contas criadas e solicitações para redefinir uma senha esquecida em um período selecionado. Também é facetado mostrar o país de origem do pedido. Esse quadro focaliza o país de origem da solicitação.

![países-esquecidos-api](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

O quadro **[!UICONTROL API - forgot password, create account by Countries and IP address]** mostra o número de contas criadas e solicitações para redefinir uma senha esquecida em um período selecionado. Também é facetado mostrar o endereço IP, o URL acessado e o país de origem da solicitação. Esse quadro focaliza a contagem de IP.

![api-esqueci-países-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

O quadro **[!UICONTROL Guest cart activities by IP]** mostra as atividades do carrinho de convidado por IP em um período selecionado.

![carrinho de convidados-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

O quadro **[!UICONTROL Guest cart activities by Countries]** mostra as atividades do carrinho de convidado por países em um período selecionado.

![país-carrinho-convidado](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
