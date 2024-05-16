---
title: Notas de versão para Patches de segurança do Adobe Commerce 2.4.4
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Notas de versão do patch de segurança do Adobe Commerce 2.4.4

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p8

A versão de segurança do Adobe Commerce 2.4.4-p8 fornece correções de bugs de segurança para a implantação do Adobe Commerce 2.4.4. Essas atualizações corrigem vulnerabilidades identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

A versão de segurança 2.4.4-p7 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Destaques da segurança

Esta versão apresenta dois aprimoramentos significativos de segurança:

* **Alterações no comportamento de chaves de cache não geradas**:

   * As chaves de cache não geradas para blocos agora incluem prefixos que diferem dos prefixos para chaves geradas automaticamente. (As chaves de cache não geradas são chaves definidas por meio da sintaxe de diretiva de modelo ou do `setCacheKey` ou `setData` métodos.)
   * As chaves de cache não geradas para blocos agora devem conter apenas letras, dígitos, hifens (-) e caracteres de sublinhado (_). <!-- AC-9831 -->

* **Limitações no número de códigos de cupom gerados automaticamente**. O Commerce agora limita o número de códigos de cupom gerados automaticamente. O máximo padrão é 250.000. Os comerciantes podem usar o novo **[!UICONTROL Code Quantity Limit]** opção de configuração (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar esse novo limite. <!-- AC-8753 -->

## 2.4.4-p6

A versão de segurança 2.4.4-p6 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

### Realce de segurança

Esta versão apresenta uma nova configuração de cache de página inteira que ajuda a reduzir os riscos associados à `{BASE-URL}/page_cache/block/esi HTTP` terminal. Esse endpoint oferece suporte a fragmentos de conteúdo irrestritos e carregados dinamicamente de manipuladores de layout e estruturas de bloco do Commerce. O novo **[!UICONTROL Handles Param]** definição de configuração define o valor desse parâmetro de `handles` que determina o número máximo permitido de identificadores por API. O valor padrão dessa propriedade é 100. Os comerciantes podem alterar esse valor do campo Administração (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema conhecido

**Problema**: o Adobe Commerce exibe um **soma de verificação incorreta** erro durante o download pelo Composer de `repo.magento.com`, e o download do pacote for interrompido. Esse problema pode ocorrer durante o download de pacotes de lançamento que foram disponibilizados durante o pré-lançamento e é causado por um reempacotamento do `magento/module-page-cache` pacote.

**Solução alternativa**: os comerciantes que veem esse erro durante o download podem executar estas etapas:

1) Exclua o `/vendor` diretório dentro do projeto, se existir.
2) Execute o `bin/magento composer update magento/module-page-cache` comando. Esse comando atualiza somente o `page cache` pacote.

Se o problema de checksum persistir, remova o `composer.lock` antes de executar novamente a `bin/magento composer update` para atualizar cada pacote.

## 2.4.4-p5

A versão de segurança 2.4.4-p5 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar patch para resolver a vulnerabilidade de segurança CVE-2022-31160 na biblioteca jQuery-UI

`jQuery-UI` A versão 1.13.1 da biblioteca do tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no [Correção CVE-2022-31160 de vulnerabilidade de segurança da interface do jQuery para versões 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artigo da knowledge base.

## 2.4.4-p4

A versão de segurança 2.4.4-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança e atualizações de plataforma para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar patch para resolver a vulnerabilidade de segurança CVE-2022-31160 na biblioteca jQuery-UI

`jQuery-UI` A versão 1.13.1 da biblioteca do tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no [Correção CVE-2022-31160 de vulnerabilidade de segurança da interface do jQuery para versões 2.4.4, 2.4.5 e 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artigo da knowledge base.

### Realce de segurança

O comportamento padrão do [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) consulta do GraphQL e ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) O endpoint REST foi alterado. Por padrão, a API agora sempre retorna `true`. Os comerciantes podem habilitar o comportamento original, que é retornar `true` se o email não existir no banco de dados e `false` se existir. <!-- AC-6695 -->

### Atualizações da plataforma

As atualizações de plataforma para esta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

* **Suporte ao cache vernish 7.3**. Esta versão é compatível com a versão mais recente do Varnish Cache 7.3. A compatibilidade permanece com as versões 6.0.x e 7u.2.x, mas a Adobe recomenda usar o Adobe Commerce 2.4.4-p4 somente com o Cache de Varnish versão 7.3 ou versão 6.0 LTS.

* **Suporte ao RabbitMQ 3.11**. Esta versão é compatível com a versão mais recente do RabbitMQ 3.11. A compatibilidade permanece com o RabbitMQ 3.9, compatível até agosto de 2023, mas o Adobe recomenda usar o Adobe Commerce 2.4.4-p4 somente com o RabbitMQ 3.11.

* **Bibliotecas de JavaScript do**. As bibliotecas JavaScript desatualizadas foram atualizadas para as versões secundárias ou de patch mais recentes, incluindo `moment.js` biblioteca (v2.29.4), `jQuery UI` biblioteca (v1.13.2), e `jQuery` biblioteca de plug-in de validação (v1.19.5).

## 2.4.4-p3

A versão de segurança 2.4.4-p3 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

A versão de segurança 2.4.4-p2 do Adobe Commerce fornece correções para vulnerabilidades identificadas em versões anteriores. Uma correção inclui a criação de uma nova definição de configuração. A variável **Exigir confirmação por email se o email tiver sido alterado** a configuração do permite que os administradores exijam a confirmação por email quando um usuário administrador alterar seu endereço de email. <!-- AC-6292-->

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Aplique o AC-3022.patch para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar `AC-3022.patch` continuar a oferecer a DHL como transportadora. Consulte a [Aplique um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Artigo da Base de conhecimento para obter informações sobre como baixar e instalar o patch.

## 2.4.4-p1

A versão de segurança 2.4.4-p1 do Adobe Commerce fornece correções para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte [Boletim de segurança do Adobe](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Aplicar `AC-3022.patch` continuar a oferecer a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar `AC-3022.patch` continuar a oferecer a DHL como transportadora. Consulte a [Aplique um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artigo da Base de conhecimento para obter informações sobre como baixar e instalar o patch.

### Destaques da segurança

Os aprimoramentos de segurança desta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes, incluindo:

* Os recursos de ACL foram adicionados ao Inventário.
* A segurança do modelo de estoque foi aprimorada.

### Problemas conhecidos

**Problema**: os testes de API da Web e integração exibem esse erro quando executados no pacote 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Solução alternativa**: instale a versão anterior do Monolog executando o `require monolog/monolog:2.6.0` comando. <!-- AC-3651-->

**Problema**: os comerciantes podem notar avisos de downgrade de versão do pacote durante uma atualização do Adobe Commerce 2.4.4 para o Adobe Commerce 2.4.4-p1. Essas mensagens podem ser ignoradas. A discrepância nas versões do pacote resulta de anomalias durante a geração do pacote. Nenhuma funcionalidade do produto foi afetada. Consulte a [Pacotes rebaixados após a atualização de 2.4.4 para 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Artigo da Base de conhecimento para uma discussão sobre cenários afetados e soluções alternativas.

