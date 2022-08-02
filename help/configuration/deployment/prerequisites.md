---
title: Pré-requisitos para implantação
description: Consulte uma lista de pré-requisitos para implantar o Commerce em um sistema de desenvolvimento, criação ou produção.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---


# Pré-requisitos para sistemas de desenvolvimento, criação e produção

As permissões e a propriedade de arquivo devem ser consistentes em todos os sistemas de desenvolvimento, criação e produção. Para fazer isso funcionar, você deve:

- Todos os itens a seguir:

   - Configure o mesmo [proprietário do sistema de arquivos](https://glossary.magento.com/magento-file-system-owner) nome de usuário em todos os sistemas
   - Certifique-se de que o servidor da Web seja executado como o mesmo usuário em todos os sistemas
   - Certifique-se de que o proprietário do sistema de arquivos esteja no grupo de servidores da Web em todos os sistemas

- Altere as permissões e a propriedade do sistema de arquivos do Commerce em cada sistema, conforme necessário, usando as seguintes diretrizes:

   - Desenvolvimento e construção: [Definir a propriedade e as permissões de pré-instalação (dois usuários)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produção: [Propriedade comercial e permissões em desenvolvimento e produção](file-system-permissions.md)

>[!INFO]
>
>Se você escolher essa abordagem, deverá definir as permissões e a propriedade do sistema de arquivos toda vez que obter o código do sistema de build (se o proprietário do sistema de arquivos ou o usuário do servidor da Web for diferente no sistema de build).
