---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Correções incluídas nos patches de segurança de outubro (exceto 2.4.4)

Esta versão inclui uma correção para resolver um problema com o gateway de pagamento Braintree.

O sistema agora inclui os campos necessários para atender aos requisitos de autorização do 3DS VISA ao usar o Braintree como gateway de pagamento. Isso garante que todas as transações cumpram com as mais recentes normas de segurança definidas pela VISA. Anteriormente, esses campos adicionais não eram incluídos nas informações de pagamento enviadas, o que poderia ter levado ao não cumprimento dos novos requisitos de VISTO.

<!--
BUNDLE-3360
-->