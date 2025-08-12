---
title: Notas de versão do patch de segurança do Adobe Commerce 2.4.4
description: Saiba mais sobre correções de bugs de segurança, aprimoramentos de segurança e outras atualizações relacionadas à segurança incluídas nas versões de patch de segurança para o Adobe Commerce versão 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: a5cdc9ee2d8c8632c40e0ced62182d5275b8b942
workflow-type: tm+mt
source-wordcount: '1775'
ht-degree: 0%

---


# Notas de versão de patches de segurança do Adobe Commerce 2.4.4

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p15

O Adobe Commerce 2.4.4-p15 é uma versão de segurança de suporte estendido que fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4. Ele está disponível somente para clientes do Adobe Commerce.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-71](https://helpx.adobe.com/security/products/magento/apsb25-71.html).

{{b2b-patches}}

## 2.4.4-p14

O Adobe Commerce 2.4.4-p14 é uma versão de segurança de suporte estendido que fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4. Ele está disponível somente para clientes do Adobe Commerce.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-50](https://helpx.adobe.com/br/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Destaques

Esta versão inclui os seguintes destaques:

* **Aprimoramento de desempenho da API**—Resolve a degradação de desempenho em pontos de extremidade de API da Web assíncronos em massa que foram introduzidos após o patch de segurança anterior.<!-- AC-14078 -->

* **Correção de acesso de Bloqueios do CMS** — Resolve um problema em que os usuários administradores com permissões restritas (como acesso somente de merchandising) não conseguiam exibir a página de listagem [!UICONTROL CMS Blocks].

  Anteriormente, esses usuários encontravam um erro devido a parâmetros de configuração ausentes após a instalação de patches de segurança anteriores.<!-- AC-14087 -->

* **Compatibilidade com limite de cookies** — Resolve uma alteração incompatível com versões anteriores envolvendo a constante `MAX_NUM_COOKIES` na estrutura. Esta atualização restaura o comportamento esperado e garante a compatibilidade para extensões ou personalizações que interagem com limites de cookies.<!-- AC-14475 -->

* **Operações assíncronas** — Operações assíncronas restritas para substituir pedidos de clientes anteriores.<!-- AC-13917 -->

## 2.4.4-p13

A versão de segurança do Adobe Commerce 2.4.4-p13 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB25-26](https://helpx.adobe.com/br/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

A versão de segurança do Adobe Commerce 2.4.4-p12 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB25-08](https://helpx.adobe.com/br/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

A versão de segurança do Adobe Commerce 2.4.4-p11 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-73](https://helpx.adobe.com/br/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

A versão de segurança do Adobe Commerce 2.4.4-p10 fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores do 2.4.4.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-61](https://helpx.adobe.com/br/security/products/magento/apsb24-61.html).

### Destaques

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Hotfixes incluídos nesta versão

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

A versão de segurança 2.4.4-p9 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores da 2.4.4.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-40](https://helpx.adobe.com/br/security/products/magento/apsb24-40.html).

### Aplicar hotfix para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Atualizações da plataforma

* **Suporte ao MariaDB 10.5**. Esta versão de patch apresenta compatibilidade com o MariaDB versão 10.5. O Adobe Commerce ainda é compatível com a versão 10.4 do MariaDB, mas a Adobe recomenda o uso do Adobe Commerce 2.4.4-p9 e de todas as próximas versões de patch somente de segurança 2.4.4 somente com a versão 10.5 do MariaDB, pois a manutenção do MariaDB 10.4 termina em 18 de junho de 2024. <!--AC-11530-->

### Destaques

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

A versão de segurança do Adobe Commerce 2.4.4-p8 fornece correções de bugs de segurança para a implantação do Adobe Commerce 2.4.4. Essas atualizações corrigem vulnerabilidades identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB24-18](https://helpx.adobe.com/br/security/products/magento/apsb24-18.html).

## 2.4.4-p7

A versão de segurança 2.4.4-p7 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB24-03](https://helpx.adobe.com/br/security/products/magento/apsb24-03.html).

### Destaques

Esta versão apresenta dois aprimoramentos significativos de segurança:

* **Alterações no comportamento de chaves de cache não geradas**:

   * As chaves de cache não geradas para blocos agora incluem prefixos que diferem dos prefixos para chaves geradas automaticamente. (As chaves de cache não geradas são chaves definidas por meio da sintaxe de diretiva de modelo ou pelos métodos `setCacheKey` ou `setData`.)
   * As chaves de cache não geradas para blocos agora devem conter apenas letras, dígitos, hifens (-) e caracteres de sublinhado (_). <!-- AC-9831 -->

* **Limitações sobre o número de códigos de cupom gerados automaticamente**. O Commerce agora limita o número de códigos de cupom gerados automaticamente. O máximo padrão é 250.000. Os comerciantes podem usar a nova opção de configuração **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar esse novo limite. <!-- AC-8753 -->

## 2.4.4-p6

A versão de segurança 2.4.4-p6 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB23-50](https://helpx.adobe.com/br/security/products/magento/apsb23-50.html).

Esta versão também inclui aprimoramentos de segurança que melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

### Destaques

Esta versão introduz uma nova definição de configuração de cache de página inteira que ajuda a reduzir os riscos associados ao ponto de extremidade `{BASE-URL}/page_cache/block/esi HTTP`. Esse endpoint oferece suporte a fragmentos de conteúdo irrestritos e carregados dinamicamente de manipuladores de layout e estruturas de bloco do Commerce. A nova definição de configuração **[!UICONTROL Handles Param]** define o valor do parâmetro `handles` desse ponto de extremidade, que determina o número máximo permitido de identificadores por API. O valor padrão dessa propriedade é 100. Os comerciantes podem alterar este valor de Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problemas conhecidos

**Problema**: o Adobe Commerce exibe um erro de **soma de verificação incorreta** durante o download pelo Composer de `repo.magento.com`, e o download do pacote foi interrompido. Esse problema pode ocorrer durante o download de pacotes de lançamento que foram disponibilizados durante o pré-lançamento e é causado por um reempacotamento do pacote `magento/module-page-cache`.

**Solução alternativa**: os comerciantes que visualizarem este erro durante o download podem executar estas etapas:

1) Exclua o diretório `/vendor` dentro do projeto, se existir.
2) Execute o comando `bin/magento composer update magento/module-page-cache`. Este comando atualiza somente o pacote `page cache`.

Se o problema de soma de verificação persistir, remova o arquivo `composer.lock` antes de executar novamente o comando `bin/magento composer update` para atualizar cada pacote.

## 2.4.4-p5

A versão de segurança 2.4.4-p5 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores.

Para obter as últimas informações sobre as correções de erros de segurança, consulte [Boletim de Segurança do Adobe APSB23-42](https://helpx.adobe.com/br/security/products/magento/apsb23-42.html).

### Aplicar hotfix para CVE-2022-31160

A biblioteca do `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface do usuário do jQuery CVE-2022-31160 para 2.4.4, 2.4.5 e 2.4.6 versões](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=pt-BR).

## 2.4.4-p4

A versão de segurança 2.4.4-p4 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança e atualizações de plataforma para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB23-35](https://helpx.adobe.com/br/security/products/magento/apsb23-35.html).

### Aplicar hotfix para CVE-2022-31160

A biblioteca do `jQuery-UI` versão 1.13.1 tem uma vulnerabilidade de segurança conhecida (CVE-2022-31160) que afeta várias versões do Adobe Commerce e do Magento Open Source. Esta biblioteca é uma dependência do Adobe Commerce e do Magento Open Source 2.4.4, 2.4.5 e 2.4.6. Os comerciantes que executam implantações afetadas devem aplicar o patch especificado no artigo da Base de Dados de Conhecimento [vulnerabilidade de segurança da interface do usuário do jQuery CVE-2022-31160 para 2.4.4, 2.4.5 e 2.4.6 versões](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=pt-BR).

### Destaques

O comportamento padrão da consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) e do ponto de extremidade REST [`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable) foi alterado. Por padrão, a API agora sempre retorna `true`. Os comerciantes podem habilitar o comportamento original, que é retornar `true` se o email não existir no banco de dados e `false` se ele existir. <!-- AC-6695 -->

### Atualizações da plataforma

As atualizações de plataforma para esta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

* **Suporte ao cache de verniz 7.3**. Esta versão é compatível com a versão mais recente do Varnish Cache 7.3. A compatibilidade permanece com as versões 6.0.x e 7u.2.x, mas a Adobe recomenda usar o Adobe Commerce 2.4.4-p4 somente com o Varnish Cache versão 7.3 ou versão 6.0 LTS.

* **Suporte a RabbitMQ 3.11**. Esta versão é compatível com a versão mais recente do RabbitMQ 3.11. A compatibilidade permanece com o RabbitMQ 3.9, que é compatível até agosto de 2023, mas a Adobe recomenda usar o Adobe Commerce 2.4.4-p4 somente com o RabbitMQ 3.11.

* **Bibliotecas JavaScript**. As bibliotecas JavaScript desatualizadas foram atualizadas para as versões secundárias ou de patch mais recentes, incluindo a biblioteca `moment.js` (v2.29.4), a biblioteca `jQuery UI` (v1.13.2) e a biblioteca de plug-in de validação `jQuery` (v1.19.5).

## 2.4.4-p3

A versão de segurança 2.4.4-p3 do Adobe Commerce fornece correções de bugs de segurança para vulnerabilidades que foram identificadas em versões anteriores.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB23-17](https://helpx.adobe.com/br/security/products/magento/apsb23-17.html).

## 2.4.4-p2

A versão de segurança 2.4.4-p2 do Adobe Commerce fornece correções para vulnerabilidades identificadas em versões anteriores. Uma correção inclui a criação de uma nova definição de configuração. A configuração [!UICONTROL **Exigir confirmação por email se o email tiver sido alterado**] permite que os administradores exijam confirmação por email quando um usuário administrador alterar seu endereço de email. <!-- AC-6292-->

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe APSB22-48](https://helpx.adobe.com/br/security/products/magento/apsb22-48.html).

### Aplique o AC-3022.patch para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) para obter informações sobre como baixar e instalar o patch.

## 2.4.4-p1

A versão de segurança 2.4.4-p1 do Adobe Commerce fornece correções para vulnerabilidades identificadas em versões anteriores. Esta versão também inclui aprimoramentos de segurança para melhorar a conformidade com as práticas recomendadas de segurança mais recentes.

Para obter as informações mais recentes sobre as correções de erros de segurança, consulte o [Boletim de Segurança do Adobe](https://helpx.adobe.com/br/security/products/magento/apsb22-38.html).t

### Aplique o `AC-3022.patch` para continuar oferecendo a DHL como transportadora

A DHL apresentou o schema versão 6.2 e descontinuará o schema versão 6.0 em breve. Adobe Commerce 2.4.4 e versões anteriores que suportam a integração DHL suportam apenas a versão 6.0. Os comerciantes que implantarem essas versões devem aplicar o `AC-3022.patch` o mais rápido possível para continuarem oferecendo a DHL como transportadora. Consulte o artigo da Base de conhecimento [Aplicar um patch para continuar oferecendo a DHL como transportadora](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obter informações sobre como baixar e instalar o patch.

### Destaques

Os aprimoramentos de segurança desta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes, incluindo:

* Os recursos de ACL foram adicionados ao Inventário.
* A segurança do modelo de estoque foi aprimorada.

### Problemas conhecidos

**Problema**: a API da Web e os testes de integração exibem este erro quando executados no pacote 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Solução alternativa**: instale a versão anterior do Monolog executando o comando `require monolog/monolog:2.6.0`. <!-- AC-3651-->

**Problema**: os comerciantes podem notar avisos de downgrade de versão do pacote durante uma atualização do Adobe Commerce 2.4.4 para o Adobe Commerce 2.4.4-p1. Essas mensagens podem ser ignoradas. A discrepância nas versões do pacote resulta de anomalias durante a geração do pacote. Nenhuma funcionalidade do produto foi afetada. Consulte o artigo da Base de Dados de Conhecimento [Pacotes desatualizados após a atualização de 2.4.4 para 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) para obter uma discussão sobre cenários afetados e soluções alternativas.
