---
title: Obter suas chaves de autenticação
description: Siga estas etapas para recuperar credenciais para acessar os pacotes do Adobe Commerce e do Magento Open Source Composer em repo.magento.com.
exl-id: 7ec2a410-d81f-476a-bf6a-f3c61982a734
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Obter suas chaves de autenticação

A variável `repo.magento.com` O repositório do é onde os pacotes do Adobe Commerce e do Magento Open Source e de terceiros do Composer são armazenados e exigem autenticação. Use a conta Commerce Marketplace para gerar um par de 32 caracteres *chaves de autenticação* para acessar o repositório.

Para obter direito de acesso a pacotes Adobe Commerce e Magento Open Source, você deve usar chaves associadas a uma MAGEID que recebeu acesso a esses pacotes. Normalmente, a MAGEID é o contato principal na conta da Adobe Commerce e nem sempre é o proprietário do projeto Adobe Commerce na infraestrutura em nuvem.

>[!TIP]
>
>Se você encontrar [erros](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/deployment/magento-commerce-cloud-repo-could-not-be-accessed-403-forbidden-or-404-not-found-error-when-deploying.html), talvez você não tenha autorização para acessar o pacote ou o direito de acesso tenha expirado devido a uma fatura pendente em sua conta.
>
>* Se você for a pessoa de contato principal na conta, verifique se não há nenhuma fatura pendente listada na conta.
>* Se as chaves fornecidas pelo contato principal não estiverem funcionando e não houver faturas pendentes na conta, entre em contato com [Suporte ao Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para obter assistência usando a MAGEID do contato principal.


Para criar chaves de autenticação:

1. Faça logon no [Commerce Marketplace](https://marketplace.magento.com). Se você não tiver uma conta, clique em **Registrar**.
1. Clique no nome da conta na parte superior direita da página e selecione **Meu perfil**.

1. Clique em **Teclas de acesso** na guia Marketplace.

   ![Obtenha suas chaves de acesso seguras no Commerce Marketplace](../../assets/installation/cloud_access-key.png)

1. Clique em **Criar uma nova chave de acesso**. Insira um nome específico para as chaves (por exemplo, o nome do desenvolvedor que recebe as chaves) e clique em **OK**.

1. Agora estão associadas à sua conta novas chaves públicas e privadas em que você pode clicar para copiá-las. Salve essas informações ou mantenha a página aberta ao trabalhar com seu projeto. Use o **Chave pública** como seu nome de usuário e o **Chave privada** como sua senha.

## Gerenciar suas chaves de autenticação

Você também pode desativar ou excluir chaves de autenticação. Por exemplo, você pode desativar ou excluir chaves por motivos de segurança depois que alguém sair da organização.

* Para desativar teclas: Clique em **Desativar**. Você pode fazer isso se quiser suspender o uso das chaves.
* Para habilitar uma chave desabilitada anteriormente: clique **Ativar**.
* Para excluir chaves: Clique em **Excluir**.

### Gerenciar token de acesso SSH

Para baixar versões do Adobe Commerce usando SSH, você deve gerar um token de acesso de download. Para gerar um token:

1. Faça logon no [Conta do magento.com](https://account.magento.com/customer/account/login).
1. Clique em **Minha conta** na parte superior da página.
1. Clique em **Configurações da conta** > **Baixar token de acesso**.

   ![Acessar suas chaves](../../assets/installation/connect_keys1.png)

1. Clique em **Gerar novo token** para substituir e desativar um token existente.

Você deve usar sua MAGEID e seu token para baixar uma versão. Sua MAGEID é exibida na parte superior esquerda da página da conta.

Por exemplo:

```bash
curl -k https://MAGEID:TOKEN@www.magentocommerce.com/products/downloads/info/help
```

Use suas chaves de autenticação para:

* [Obter o metapackage (integradores, packagers)](../composer.md)
* [Clonar o repositório GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) (somente desenvolvedores contribuintes)
* [Atualizar e gerenciar módulos](../../upgrade/modules/upgrade.md)
