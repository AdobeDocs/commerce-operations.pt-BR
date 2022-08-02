---
title: Configuração do sistema de desenvolvimento
description: Saiba como configurar um sistema de desenvolvimento para o aplicativo Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Configuração do sistema de desenvolvimento

Você pode ter qualquer número de sistemas de desenvolvimento, desde que o seguinte seja verdadeiro para todos eles:

- Todos executam o Commerce 2.2 ou posterior
- Todo o código do Commerce está sob controle de origem no mesmo repositório que os sistemas de criação e produção
- Cada sistema de desenvolvimento deve utilizar [modo padrão](../bootstrap/application-modes.md#default-mode) ou [modo desenvolvedor](../bootstrap/application-modes.md#developer-mode)
- Ele tem a propriedade do sistema de arquivos e as permissões definidas como discutido em [Pré-requisito para seus sistemas de desenvolvimento, criação e produção](../deployment/technical-details.md).
- Certifique-se de que todos os itens a seguir sejam _excluídos_ do controlo-fonte:

   - `vendor` diretório (e subdiretórios)
   - `generated` diretório (e subdiretórios)
   - `pub/static` diretório (e subdiretórios)
   - `app/etc/env.php` arquivo

- Certifique-se de `app/etc/config.php` é _included_ no controle de origem

Se você usar o Git, a variável `.gitignore` O arquivo fornece a maior parte das informações anteriores. Consulte a [`.gitignore` referência](../reference/config-reference-gitignore.md).
