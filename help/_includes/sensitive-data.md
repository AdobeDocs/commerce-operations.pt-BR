---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Dados sensíveis

O Adobe Commerce e o Magento Open Source usam sua chave de criptografia para criptografar o seguinte:

* Informações de cartão de crédito
* Nomes de usuários e senhas especificados na configuração do Administrador (por exemplo, logons em gateways de pagamento)
* Valores de CAPTCHA enviados pela rede

Adobe Commerce e Magento Open Source do *não* criptografia:

* Nomes de usuário e senhas administrativos e de clientes (essas senhas têm hash)
* Endereço
* Número de telefone
* Outros tipos de informações pessoalmente identificáveis, exceto para números de cartão de crédito
