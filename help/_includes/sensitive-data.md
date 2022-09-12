---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Dados sensíveis

O Adobe Commerce e o Magento Open Source usam sua chave de criptografia para criptografar o seguinte:

* Informações do cartão de crédito
* Nomes de usuários e senhas especificados na configuração de Administração (por exemplo, logons em gateways de pagamento)
* Valores CAPTCHA enviados pela rede

Adobe Commerce e Magento Open Source do *not* encrypt:

* Nomes de usuários e senhas administrativos e de clientes (essas senhas estão com hash)
* Endereço
* Número de telefone
* Outros tipos de informações pessoalmente identificáveis, exceto números de cartão de crédito
