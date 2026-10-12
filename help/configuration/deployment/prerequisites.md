---
title: Pré-requisitos para implantação
description: Consulte uma lista de pré-requisitos para implantar o Commerce em um sistema de desenvolvimento, compilação ou produção.
feature: Configuration, Deploy
exl-id: 9ea0eeff-e0f8-4532-887c-5d7f07d89ddd
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%
---
# Pré-requisitos para sistemas de desenvolvimento, compilação e produção

As permissões e a propriedade de arquivos devem ser consistentes em todos os sistemas de desenvolvimento, compilação e produção. Para fazer isso funcionar, você deve:

- Todos os itens a seguir:

  - Configurar o mesmo nome de usuário do proprietário do sistema de arquivos em todos os sistemas
  - Verifique se o servidor Web é executado como o mesmo usuário em todos os sistemas
  - Verifique se o proprietário do sistema de arquivos está no grupo de servidores Web em todos os sistemas

- Altere as permissões e a propriedade do sistema de arquivos Commerce em cada sistema, conforme necessário, usando as seguintes diretrizes:

  - Desenvolvimento e compilação: [Definir propriedade e permissões de pré-instalação (dois usuários)](file-system-permissions.md#set-up-two-owners-for-default-or-developer-mode)
  - Produção: [Propriedade e permissões do Commerce no desenvolvimento e produção](file-system-permissions.md)

>[!INFO]
>
>Se você escolher essa abordagem, deverá definir as permissões e a propriedade do sistema de arquivos sempre que extrair o código do sistema de compilação (se o proprietário do sistema de arquivos ou o usuário do servidor Web for diferente no sistema de compilação).
