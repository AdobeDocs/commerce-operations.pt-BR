---
title: Visão geral da política de segurança de conteúdo
description: Saiba como melhorar a postura de segurança da loja do Adobe Commerce usando uma política de segurança de conteúdo.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Visão geral da política de segurança de conteúdo

Uma Política de segurança de conteúdo (CSP) pode fornecer camadas adicionais de defesa para instalações do Adobe Commerce, ajudando a detectar e mitigar scripts entre sites (XSS) e ataques de injeção de dados relacionados. Esse vetor de ataque comum funciona injetando conteúdo mal-intencionado que se originará falsamente do site. Depois que o conteúdo mal-intencionado é carregado e executado, ele pode iniciar a transferência não autorizada de dados.

O CSP fornece um conjunto padronizado de diretivas que informa ao navegador quais recursos de conteúdo podem ser confiáveis e quais devem ser bloqueados. Usando políticas definidas cuidadosamente, a CSP pode restringir o conteúdo do navegador para permitir que apenas os recursos da lista de permissões sejam exibidos.

## Configuração

Para evitar interferências nas operações do site, a CSP pode ser implementada em fases. O CSP tem dois modos básicos de operação: `report-only mode` e `restrict mode`.

**Modo somente relatório**: o navegador é instruído a relatar violações de política, mas não aplicá-las. Toda vez que um recurso solicitado viola a CSP, o navegador registra os erros resultantes no console. O registro do console pode ser usado para investigar a causa de cada violação.

É importante revisar todos os erros da CSP à medida que ocorrem e refinar as políticas até que todos os recursos necessários sejam colocados na lista de permissões. É seguro alternar para `restrict mode` quando não ocorrerem mais erros. Caso contrário, uma CSP mal configurada pode fazer com que o navegador exiba uma página em branco com vários erros de console. Uma CSP corretamente configurada permite que o conteúdo da lista de permissões seja entregue sem nenhum impacto percebido no desempenho.

**Modo restrito**: o navegador é instruído a impor todas as políticas de conteúdo e limitar a publicação a recursos da lista de permissões.

A primeira fase da implementação do CSP do Adobe Commerce foi introduzida no Adobe Commerce 2.3.5 e disponibilizada no `report-only mode` por padrão.  No Adobe Commerce 2.4.7 e posterior, o CSP é configurado em `restrict-mode` por padrão para páginas de pagamento nas áreas de vitrine e administração, e no modo `report-only` para todas as outras páginas. O cabeçalho da CSP correspondente não contém a palavra-chave `unsafe-inline` na diretiva `script-src` para páginas de pagamento. Além disso, somente scripts integrados na lista de permissões são permitidos.

Como a CSP é configurada no servidor, em vez do Admin, a maioria dos comerciantes precisa da assistência de um integrador de sistema ou desenvolvedor para configurá-la corretamente. Consulte [Políticas de Segurança de Conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Guia do Desenvolvedor do Commerce PHP_.


## Relatórios

Por padrão, o CSP envia erros para o console do navegador, mas pode ser configurado para coletar logs de erros por solicitação HTTP. Além disso, há vários serviços de terceiros que você pode usar para monitorar, coletar e relatar violações de CSP. Violações de CSP podem ser relatadas a um ponto de extremidade para coleção adicionando o URI do Administrador ou do arquivo `config.xml` para um módulo personalizado.  Consulte [Configuração do URI do relatório](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) no _Guia do desenvolvedor de extensões PHP do Commerce_.

[O URI do relatório](https://report-uri.io/) é um serviço que monitora violações de CSP e exibe os resultados em um painel. Os comerciantes e desenvolvedores podem usar o serviço para receber relatórios sempre que violações de CSP ocorrerem.
