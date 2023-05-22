---
title: Pré-requisitos para implantação
description: Consulte uma lista de pré-requisitos para implantar o Commerce em um sistema de desenvolvimento, compilação ou produção.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Pré-requisitos para sistemas de desenvolvimento, compilação e produção

As permissões e a propriedade de arquivos devem ser consistentes em todos os sistemas de desenvolvimento, compilação e produção. Para fazer isso funcionar, você deve:

- Todos os itens a seguir:

   - Configurar o mesmo nome de usuário do proprietário do sistema de arquivos em todos os sistemas
   - Verifique se o servidor Web é executado como o mesmo usuário em todos os sistemas
   - Verifique se o proprietário do sistema de arquivos está no grupo de servidores Web em todos os sistemas

- Altere as permissões e a propriedade do sistema de arquivos do Commerce em cada sistema, conforme necessário, usando as seguintes diretrizes:

   - Desenvolvimento e criação: [Definir propriedade e permissões de pré-instalação (dois usuários)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
   - Produção: [Propriedade e permissões de comércio no desenvolvimento e na produção](file-system-permissions.md)

>[!INFO]
>
>Se você escolher essa abordagem, deverá definir as permissões e a propriedade do sistema de arquivos sempre que extrair o código do sistema de compilação (se o proprietário do sistema de arquivos ou o usuário do servidor Web for diferente no sistema de compilação).
