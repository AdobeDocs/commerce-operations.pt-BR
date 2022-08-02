---
title: Realce de URN
description: Saiba como configurar o realce de URN no IDE.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Visão geral do realce de URN

{{file-system-owner}}

O código de comércio faz referência a todos os esquemas XSD como [Nomes de Recursos Uniformes (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Se você estiver desenvolvendo código e precisar fazer referência a XSDs, esse comando configurará seu ambiente de desenvolvedor integrado (IDE) para reconhecer e realçar URNs. Isso facilita o desenvolvimento.

Por padrão, um IDE como PhpStorm não é configurado para reconhecer URNs e, como resultado, é exibido em texto vermelho da seguinte maneira:

![O PhpStorm não está configurado para reconhecer o URN](../../assets/configuration/urn-before.png)

O `bin/magento dev:urn-catalog:generate` O comando permite que o IDE (atualmente, somente o PhpStorm e o Visual Studio Code) reconheça e realce URNs como o seguinte:

![Habilite o IDE para reconhecer o URN](../../assets/configuration/urn-after.png)

Especificamente, esse comando cria a seguinte configuração do PhpStorm:

![Exemplo de configuração do PhpStorm](../../assets/configuration/urn-settings.png)

## Configurar o IDE

Atualmente, somente o PhpStorm e o Visual Studio Code são compatíveis.

Sintaxe de comando:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Onde `<path>` é o caminho para seu PhpStorm `misc.xml` , que está localizado em relação à raiz do projeto. Normalmente, `<path>` é `.idea/misc.xml`.

>[!INFO]
>
>Para manter seus &quot;Schemas e DTDs&quot; atualizados, execute o `dev:urn-catalog:generate` comando sempre que adicionar, modificar ou remover módulos do Commerce 2 que contenham `*.xsd` arquivos.
