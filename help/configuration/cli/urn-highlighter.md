---
title: Marca-texto URN
description: Saiba como configurar o realce de URN no IDE para desenvolvimento do Adobe Commerce. Descubra a configuração do esquema XSD e a otimização do desenvolvimento.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
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
source-wordcount: '191'
ht-degree: 0%
---
# Visão geral do destacador de URN

{{file-system-owner}}

O código Commerce faz referência a todos os esquemas XSD como [Uniform Resource Names (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Se você estiver desenvolvendo código e precisar fazer referência a XSDs, este comando configura o ambiente de desenvolvedor integrado (IDE) para reconhecer e realçar URNs. Isso facilita o desenvolvimento.

Por padrão, um IDE como o PhpStorm não está configurado para reconhecer URNs e, como resultado, eles são exibidos em texto vermelho da seguinte maneira:

![PhpStorm não configurado para reconhecer o URN](../../assets/configuration/urn-before.png)

O comando `bin/magento dev:urn-catalog:generate` habilita seu IDE (atualmente, somente PhpStorm e Visual Studio Code) para reconhecer e realçar URNs como o seguinte:

![Habilitar IDE para reconhecer URN](../../assets/configuration/urn-after.png)

Especificamente, este comando cria a seguinte configuração do PhpStorm:

![Exemplo de configuração do PhpStorm](../../assets/configuration/urn-settings.png)

## Configurar o IDE

Atualmente, somente o PhpStorm e o Visual Studio Code são suportados.

Sintaxe de comando:

```shell
bin/magento dev:urn-catalog:generate <path>
```

Onde `<path>` é o caminho para o arquivo PhpStorm `misc.xml`, que está localizado em relação à raiz do projeto. Normalmente, `<path>` é `.idea/misc.xml`.

>[!INFO]
>
>Para manter seus &quot;Esquemas e DTDs&quot; atualizados, execute o comando `dev:urn-catalog:generate` sempre que adicionar, modificar ou remover módulos do Commerce 2 que contenham arquivos `*.xsd`.
