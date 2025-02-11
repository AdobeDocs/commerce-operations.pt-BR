---
title: Notas de versão para Patches de segurança do Adobe Commerce 2.4.3
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.3

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

A versão de segurança 2.4.3-p3 do Adobe Commerce fornece correções de segurança para vulnerabilidades que foram identificadas em versões anteriores da 2.4.3. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Aplique o `AC-3022.patch` para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.

### Destaques da segurança

* Os recursos de ACL foram adicionados ao Inventário.
* A segurança do modelo de estoque foi aprimorada.

## Adobe Commerce 2.4.3-p2

A versão de segurança 2.4.3-p2 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  A versão de patch também resolve a vulnerabilidade tratada pelo `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` e `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Aplique o `AC-3022.patch` para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.

### Destaques da segurança

* O uso da variável de email foi descontinuado na versão 2.3.4 como parte de uma mitigação de risco de segurança em favor de uma sintaxe de variável mais estrita. Esse comportamento herdado foi totalmente removido nesta versão como uma continuação dessa mitigação de riscos de segurança.

  Como resultado, os modelos de email ou de boletim informativo que funcionavam em versões anteriores podem não funcionar corretamente após a atualização para o Adobe Commerce 2.4.3-p2. Os modelos afetados incluem substituições de administrador, temas, temas secundários e modelos de módulos personalizados ou extensões de terceiros. Sua implantação ainda pode ser afetada mesmo após o uso da [Ferramenta de compatibilidade de atualização](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) para corrigir usos obsoletos. Consulte [Migrando modelos de email personalizados](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) para obter informações sobre os possíveis efeitos e diretrizes da migração de modelos afetados.

* Os tokens de acesso OAuth e os tokens de redefinição de senha agora são criptografados quando armazenados no banco de dados. <!-- AC-520 1323-->

* A validação foi fortalecida para impedir o upload de extensões de arquivo não alfanuméricas. <!-- AC-479-->

* O Swagger agora está desativado por padrão quando o Adobe Commerce está no modo de produção. <!-- AC-1450-->

* Os desenvolvedores agora podem configurar o limite de tamanho para arrays aceitos pelos endpoints RESTful da Adobe Commerce com base no endpoint. Consulte [Segurança de API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Adição de mecanismos para limitar o tamanho e o número de recursos que um usuário pode solicitar por meio de uma API da Web em todo o sistema e para substituir os padrões em módulos individuais. Este aprimoramento resolve o problema tratado por `MC-43048__set_rate_limits__2.4.3.patch`. Consulte [Segurança de API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

A versão de segurança do Adobe Commerce 2.4.3-p1 fornece correções de bugs de segurança para vulnerabilidades identificadas na versão anterior (Adobe Commerce 2.4.3 e Magento Open Source 2.4.3). Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.


Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). A versão de correção também fornece correções de erros para as [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) e [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) extensões desenvolvidas pelo fornecedor.

### Aplique o `AC-3022.patch` para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.

### Hotfixes

Esta versão inclui o seguinte hotfix e todos os hotfixes que foram lançados para a versão de patch anterior.

* Correção `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Consulte o artigo da Base de Dados de Conhecimento [Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) para obter informações sobre patch e problema.

### Destaques da segurança

**As IDs de sessão foram removidas do banco de dados**. Essa alteração de código pode resultar em alterações quebradas se os comerciantes tiverem personalizações ou extensões instaladas que usam as IDs de sessão brutas armazenadas no banco de dados. <!-- MC-40976-->

**Acesso de administrador restrito às pastas da Galeria de Mídia**. As permissões padrão da Galeria de mídia agora permitem somente operações de diretório (exibir, carregar, excluir e criar) que são permitidas explicitamente pela configuração. Os usuários administradores não podem mais acessar ativos de mídia pela Galeria de Mídia que foram carregados fora dos diretórios `catalog/category` ou `wysiwyg`. Os administradores que desejam acessar ativos de mídia devem movê-los para uma pasta explicitamente permitida ou ajustar suas configurações. Consulte [Modificar permissões de pasta da Biblioteca de Mídia](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Limites reduzidos para a complexidade da consulta GraphQL**. A complexidade máxima de consulta permitida do GraphQL foi reduzida para evitar ataques de negação de serviço (DOS). Consulte [configuração de segurança do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**Vulnerabilidades recentes no teste de penetração** foram corrigidas nesta versão. <!-- MC-42431-->

A expressão de origem sem suporte `unsafe-inline` foi removida da diretiva de Política de Segurança de Conteúdo `frame-ancestors`. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->
