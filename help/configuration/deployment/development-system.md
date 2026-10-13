---
title: Configuração do sistema de desenvolvimento
description: Saiba como configurar um sistema de desenvolvimento para o aplicativo do Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
source-wordcount: '131'
ht-degree: 0%
---
# Configuração do sistema de desenvolvimento

Você pode ter qualquer número de sistemas de desenvolvimento, desde que o seguinte seja verdadeiro para todos eles:

- Todos executam o Commerce 2.2 ou posterior
- Todo o código Commerce está sob controle do código-fonte no mesmo repositório dos sistemas de compilação e produção
- Cada sistema de desenvolvimento deve usar [modo padrão](../bootstrap/application-modes.md#default-mode) ou [modo de desenvolvedor](../bootstrap/application-modes.md#developer-mode)
- Ele tem a propriedade e as permissões do sistema de arquivos definidas conforme discutido em [Pré-requisito para seus sistemas de desenvolvimento, compilação e produção](../deployment/technical-details.md).
- Verifique se todos os itens a seguir foram _excluídos_ do controle do código-fonte:

  - Diretório `vendor` (e subdiretórios)
  - Diretório `generated` (e subdiretórios)
  - Diretório `pub/static` (e subdiretórios)
  - `app/etc/env.php` arquivo

- Verifique se `app/etc/config.php` está _incluído_ no controle de origem

Se você usar o Git, o arquivo `.gitignore` fornecerá a maioria dos arquivos anteriores. Consulte a [`.gitignore` referência](../reference/config-reference-gitignore.md).
