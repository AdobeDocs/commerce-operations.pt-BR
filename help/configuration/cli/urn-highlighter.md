---
title: Marca-texto URN
description: Saiba como configurar o realce de URN no IDE.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Visão geral do destacador de URN

{{file-system-owner}}

O código comercial faz referência a todos os esquemas XSD como [Uniform Resource Names (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Se você estiver desenvolvendo código e precisar fazer referência a XSDs, este comando configura o ambiente de desenvolvedor integrado (IDE) para reconhecer e realçar URNs. Isso facilita o desenvolvimento.

Por padrão, um IDE como o PhpStorm não está configurado para reconhecer URNs e, como resultado, eles são exibidos em texto vermelho da seguinte maneira:

![PhpStorm não configurado para reconhecer o URN](../../assets/configuration/urn-before.png)

A variável `bin/magento dev:urn-catalog:generate` permite que o IDE (atualmente, somente PhpStorm e Visual Studio Code) reconheça e realce URNs como o seguinte:

![Ativar IDE para reconhecer URN](../../assets/configuration/urn-after.png)

Especificamente, este comando cria a seguinte configuração do PhpStorm:

![Exemplo de configuração do PhpStorm](../../assets/configuration/urn-settings.png)

## Configurar o IDE

Atualmente, somente o PhpStorm e o Visual Studio Code são suportados.

Sintaxe de comando:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Onde `<path>` é o caminho para o seu PhpStorm `misc.xml` arquivo, que está localizado em relação à raiz do projeto. Normalmente, `<path>` é `.idea/misc.xml`.

>[!INFO]
>
>Para manter seus &quot;Esquemas e DTDs&quot; atualizados, execute o `dev:urn-catalog:generate` sempre que você adicionar, modificar ou remover módulos do Commerce 2 que contenham `*.xsd` arquivos.
