---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Dados sensíveis

O Adobe Commerce usa sua chave de criptografia para criptografar o seguinte:

* Informações de cartão de crédito
* Nomes de usuários e senhas especificados na configuração do Administrador (por exemplo, logons em gateways de pagamento)
* Valores de CAPTCHA enviados pela rede

Adobe Commerce fazer *não* criptografar:

* Nomes de usuário e senhas administrativos e de clientes (essas senhas têm hash)
* Endereço
* Número de telefone
* Outros tipos de informações pessoalmente identificáveis, exceto para números de cartão de crédito
