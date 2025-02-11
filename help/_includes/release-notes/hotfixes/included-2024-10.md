---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Correções incluídas nos patches de segurança de outubro (exceto 2.4.4)

Esta versão inclui uma correção para resolver um problema com o gateway de pagamento da Braintree.

O sistema agora inclui os campos necessários para atender aos requisitos de autorização do 3DS VISA ao usar o Braintree como um gateway de pagamento. Isso garante que todas as transações cumpram com as mais recentes normas de segurança definidas pela VISA. Anteriormente, esses campos adicionais não eram incluídos nas informações de pagamento enviadas, o que poderia ter levado ao não cumprimento dos novos requisitos de VISTO.

<!--
BUNDLE-3360
-->