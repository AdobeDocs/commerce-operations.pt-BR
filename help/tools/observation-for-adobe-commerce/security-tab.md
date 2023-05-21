---
title: A variável [!UICONTROL Security] guia
description: Saiba mais sobre o [!UICONTROL Security] guia de [!DNL Observation for Adobe Commerce].
exl-id: b567e4a4-534e-4151-b6f6-bf59b1bd4028
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# A variável [!UICONTROL Security] guia

A variável **[!UICONTROL Security]** A guia explica os problemas de segurança e isola suas possíveis causas. Além disso, os quadros da guia são descritos.

## [!UICONTROL API calls by IP, details by URL]

A variável **[!UICONTROL API calls by IP, details by URL]** O quadro mostra várias chamadas de API por IP em um período selecionado. Esse quadro exibe o endereço IP e o URL da API que foi acessado por esse endereço IP.

![Chamadas de API por IP](../../assets/tools/observation-for-adobe-commerce/calls-by-ip.jpg)

## [!UICONTROL Forgot Password]

A variável **[!UICONTROL Forgot Password]** quadro de acesso mostra o número de tentativas de senhas esquecidas em um período selecionado. A alta atividade em relação a um endereço IP pode ser um ataque ao site.

![Esqueceu a senha](../../assets/tools/observation-for-adobe-commerce/forgot-password.jpg)

## [!UICONTROL Create Account access]

A variável **[!UICONTROL Create Account access]** quadro mostra o número de novas atividades de conta em um período selecionado. A alta atividade de um único endereço IP pode indicar um ataque.

![create-account-access](../../assets/tools/observation-for-adobe-commerce/create-account-access.png)

## [!UICONTROL POST activities]

A variável **[!UICONTROL POST activities]** o quadro mostra o `POST` atividades do site, facetadas em `client_ip` do [!DNL Fastly] logs. Ele também mostra o URL que é acessado pelo endereço IP.

![POST-activities](../../assets/tools/observation-for-adobe-commerce/POST-activities.jpg)

## [!UICONTROL POST activities summary table]

A variável **[!UICONTROL POST activities summary table]** o quadro mostra o resumo `POST` atividades do site, facetadas em `client_ip` do [!DNL Fastly] logs. Ele também mostra a contagem do URL que é acessado pelo endereço IP. A contagem é para o período selecionado.

![POST-activities-summary](../../assets/tools/observation-for-adobe-commerce/POST-activities-summary.jpg)

## [!UICONTROL POST activities details table]

A variável **[!UICONTROL POST activities details table]** o quadro mostra o `POST` atividades para o site a partir de [!DNL Fastly] logs. Ele também mostra todos os detalhes do [!DNL Fastly] registro para essas solicitações. Está limitado às últimas 2000 solicitações.
![POST-activities-details](../../assets/tools/observation-for-adobe-commerce/POST-activities-details.jpg)

## [!UICONTROL Guest Carts activities]

A variável **[!UICONTROL Guest Carts activities]** O quadro mostra o número de atividades do carrinho de convidado em um período selecionado, facetado pelo endereço IP e URL acessado. Carrinhos convidados podem ser usados em um ataque de cartão. Este quadro mostra o número total de solicitações nas quais os URLs dos carrinhos convidados são acessados.

![guest-carts-activities](../../assets/tools/observation-for-adobe-commerce/guest-carts-activities.jpg)

## [!UICONTROL API – forgot password, create account by Countries]

A variável **[!UICONTROL API – forgot password, create account by Countries]** quadro mostra o número de contas criadas e solicitações para redefinir uma senha esquecida em um período selecionado. Também é facetado mostrar o país de origem do pedido. Esse quadro focaliza o país de origem da solicitação.

![api-esqueci-países](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries.jpg)

## [!UICONTROL API - forgot password, create account by Countries and IP address]

A variável **[!UICONTROL API - forgot password, create account by Countries and IP address]** quadro mostra o número de contas criadas e solicitações para redefinir uma senha esquecida em um período selecionado. Também é facetado mostrar o endereço IP, o URL acessado e o país de origem da solicitação. Esse quadro focaliza a contagem de IP.

![api-esqueci-países-ip](../../assets/tools/observation-for-adobe-commerce/api-forgot-countries-ip.png)

## [!UICONTROL Guest cart activities by IP]

A variável **[!UICONTROL Guest cart activities by IP]** O quadro mostra as atividades do carrinho de convidado por IP em um período selecionado.

![guest-cart-ip](../../assets/tools/observation-for-adobe-commerce/guest-cart-ip.png)

## [!UICONTROL Guest cart activities by Countries]

A variável **[!UICONTROL Guest cart activities by Countries]** O quadro mostra as atividades do carrinho de convidado por países em um período selecionado.

![guest-cart-country](../../assets/tools/observation-for-adobe-commerce/guest-cart-country.png)
