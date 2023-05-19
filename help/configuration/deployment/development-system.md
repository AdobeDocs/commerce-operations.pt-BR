---
title: Configuração do sistema de desenvolvimento
description: Saiba como configurar um sistema de desenvolvimento para o aplicativo Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Configuração do sistema de desenvolvimento

Você pode ter qualquer número de sistemas de desenvolvimento, desde que o seguinte seja verdadeiro para todos eles:

- Todos executam o Commerce 2.2 ou posterior
- Todo o código do Commerce está sob controle do código-fonte no mesmo repositório que os sistemas de compilação e produção
- Cada sistema de desenvolvimento deve usar [modo padrão](../bootstrap/application-modes.md#default-mode) ou [modo de desenvolvedor](../bootstrap/application-modes.md#developer-mode)
- Ele tem a propriedade e as permissões do sistema de arquivos definidas conforme discutido em [Pré-requisito para seus sistemas de desenvolvimento, compilação e produção](../deployment/technical-details.md).
- Verifique se todos os itens a seguir estão _excluído_ do controle de origem:

   - `vendor` diretório (e subdiretórios)
   - `generated` diretório (e subdiretórios)
   - `pub/static` diretório (e subdiretórios)
   - `app/etc/env.php` arquivo

- Verifique se `app/etc/config.php` é _incluído_ no controle de origem

Se você usar o Git, a variável `.gitignore` O arquivo fornece a maioria dos itens anteriores. Consulte a [`.gitignore` referência](../reference/config-reference-gitignore.md).
