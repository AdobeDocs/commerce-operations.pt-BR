---
title: Visão geral da política de segurança de conteúdo
description: Saiba como melhorar a postura de segurança do Adobe Commerce ou do armazenamento de Magento Open Source usando uma política de segurança de conteúdo.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Visão geral da política de segurança de conteúdo

Uma Política de segurança de conteúdo (CSP) pode fornecer camadas adicionais de defesa para instalações do Adobe Commerce e do Magento Open Source, ajudando a detectar e mitigar scripts entre sites (XSS) e ataques de injeção de dados relacionados. Esse vetor de ataque comum funciona injetando conteúdo mal-intencionado que se originará falsamente do site. Depois que o conteúdo mal-intencionado é carregado e executado, ele pode iniciar a transferência não autorizada de dados.

O CSP fornece um conjunto padronizado de diretivas que informa ao navegador quais recursos de conteúdo podem ser confiáveis e quais devem ser bloqueados. Usando políticas definidas cuidadosamente, a CSP pode restringir o conteúdo do navegador para permitir que apenas os recursos da lista de permissões sejam exibidos.

## Configuração

Para evitar interferências nas operações do site, a CSP pode ser implementada em fases. O CSP tem dois modos básicos de operação: `report-only mode` e `restrict mode`. A versão 2.3.5 do Adobe Commerce marca a primeira fase da implementação e disponibiliza a CSP em `report-only mode` por padrão. Em uma versão futura, `restrict mode` é ativado por padrão para proteção adicional pronta para uso.

**Modo somente de relatório**: o navegador é instruído a relatar violações de política, mas não aplicá-las. Toda vez que um recurso solicitado viola a CSP, o navegador registra os erros resultantes no console. O registro do console pode ser usado para investigar a causa de cada violação.

É importante revisar todos os erros da CSP à medida que ocorrem e refinar as políticas até que todos os recursos necessários sejam colocados na lista de permissões. É seguro alternar para `restrict mode` quando não ocorrerem mais erros. Caso contrário, uma CSP mal configurada pode fazer com que o navegador exiba uma página em branco com vários erros de console. Uma CSP corretamente configurada permite que o conteúdo da lista de permissões seja entregue sem nenhum impacto percebido no desempenho.

**Modo restrito**: o navegador é instruído a aplicar todas as políticas de conteúdo e limitar a publicação a recursos da lista de permissões. Como a CSP é configurada no servidor, em vez do Admin, a maioria dos comerciantes precisa da assistência de um integrador de sistema ou desenvolvedor para configurá-la corretamente. Consulte [Políticas de segurança de conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Extensões PHP do Commerce_ guia do desenvolvedor.

## Relatórios

Por padrão, o CSP envia erros para o console do navegador, mas pode ser configurado para coletar logs de erros por solicitação HTTP. Além disso, há vários serviços de terceiros que você pode usar para monitorar, coletar e relatar violações de CSP.

[URI do relatório](https://report-uri.io/) O é um serviço que monitora violações de CSP e exibe os resultados em um painel. Os comerciantes e desenvolvedores podem usar o serviço para receber relatórios sempre que violações de CSP ocorrerem.
