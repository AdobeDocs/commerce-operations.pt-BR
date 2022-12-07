---
title: Obter as chaves de autenticação
description: Siga estas etapas para recuperar credenciais para acessar os pacotes do Adobe Commerce e do Magento Open Source Composer no repo.magento.com.
source-git-commit: d209d3f7fde55f7495488f2cbeeebf21024875ed
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---


# Obter as chaves de autenticação

O `repo.magento.com` O repositório é onde os pacotes Adobe Commerce e Magento Open Source e Composer de terceiros são armazenados e exigem autenticação. Use sua conta Commerce Marketplace para gerar um par de 32 caracteres *chaves de autenticação* para acessar o repositório.

Para obter o direito de acesso aos pacotes Adobe Commerce e Magento Open Source, você deve usar chaves associadas a um MAGEID que recebeu acesso a esses pacotes. Normalmente, o MAGEID é o Contato principal na conta da Adobe Commerce e nem sempre pode ser o Proprietário do Projeto do Adobe Commerce no projeto de infraestrutura em nuvem.

>[!TIP]
>
>Se encontrar [erros](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), você pode não ter autorização para acessar o pacote ou o direito de acesso expirou devido a uma fatura pendente em sua conta.
>
>* Se você for o contato principal na conta, verifique se não há nenhuma fatura pendente listada na conta.
>* Se as chaves fornecidas pelo Contato Principal não estiverem funcionando e não houver faturas pendentes na conta, entre em contato com [Suporte Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para obter assistência com o MAGEID do Contato Principal.


Para criar chaves de autenticação:

1. Faça logon no [Commerce Marketplace](https://marketplace.magento.com). Se você não tiver uma conta, clique em **Registrar**.
1. Clique no nome da sua conta no canto superior direito da página e selecione **Meu perfil**.

1. Clique em **Teclas de acesso** na guia Marketplace .

   ![Obter as chaves de acesso seguras no Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Clique em **Criar uma nova chave de acesso**. Insira um nome específico para as chaves (por exemplo, o nome do desenvolvedor que recebe as chaves) e clique em **OK**.

1. Agora, novas chaves públicas e privadas estão associadas à sua conta que você pode clicar para copiar. Salve essas informações ou mantenha a página aberta ao trabalhar com o projeto. Use o **Chave pública** como seu nome de usuário e o **Chave privada** como sua senha.

## Gerenciar suas chaves de autenticação

Você também pode desativar ou excluir chaves de autenticação. Por exemplo, você pode desativar ou excluir chaves por motivos de segurança depois que alguém sair da organização.

* Para desativar chaves: Clique em **Desativar**. Você pode fazer isso se quiser suspender o uso de suas chaves.
* Para ativar uma chave desativada anteriormente: Clique em **Habilitar**.
* Para excluir chaves: Clique em **Excluir**.

### Gerenciar token de acesso SSH

Para baixar versões do Adobe Commerce usando SSH, você deve gerar um Token de acesso a downloads. Para gerar um token:

1. Faça logon no [conta magento.com](https://account.magento.com/customer/account/login).
1. Clique em **Minha conta** na parte superior da página.
1. Clique em **Configurações da conta** > **Token de acesso a downloads**.

   ![Acessar suas chaves](../../assets/installation/connect_keys1.png)

1. Clique em **Gerar novo token** para substituir e desativar um token existente.

Você deve usar o MAGEID e o token para baixar uma versão. Seu MAGEID é exibido no canto superior esquerdo da página da conta.

Por exemplo:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Use suas chaves de autenticação para:

* [Obter o metapackage (integradores, empacotadores)](../composer.md)
* [Clonar o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (somente desenvolvedores contribuidores)
* [Atualizar e gerenciar módulos](../../upgrade/modules/upgrade.md)
