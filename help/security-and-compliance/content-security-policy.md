---
title: Visão geral da política de segurança de conteúdo
description: Saiba como melhorar a postura de segurança da Adobe Commerce ou da Magento Open Source store usando uma política de segurança de conteúdo.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Visão geral da política de segurança de conteúdo

Uma Política de segurança de conteúdo (CSP) pode fornecer camadas adicionais de defesa para instalações do Adobe Commerce e Magento Open Source, ajudando a detectar e mitigar scripts entre sites (XSS) e ataques de injeção de dados relacionados. Esse vetor de ataque comum funciona injetando conteúdo mal-intencionado que erroneamente alega se originar do site. Após o conteúdo mal-intencionado ser carregado e executado, ele poderá iniciar a transferência não autorizada de dados.

A CSP fornece um conjunto padronizado de diretivas que informa ao navegador quais recursos de conteúdo podem ser confiáveis e quais devem ser bloqueados. Usando políticas cuidadosamente definidas, a CSP pode restringir o conteúdo do navegador para permitir que apenas recursos da lista de permissões sejam exibidos.

## Configuração

Para evitar interferência nas operações do site, a CSP pode ser implementada em fases. A CSP tem dois modos básicos de operação: `report-only mode` e `restrict mode`. A versão do Adobe Commerce 2.3.5 marca a primeira fase de nossa implementação e disponibiliza a CSP em `report-only mode` por padrão. Em uma versão futura, `restrict mode` é ativada por padrão para proteção adicional pronta para uso.

**Modo somente relatório**: O navegador é instruído a relatar violações de política, mas não a aplicá-las. Toda vez que um recurso solicitado viola a CSP, o navegador registra os erros resultantes no console. O log do console pode ser usado para investigar a causa de cada violação.

É importante revisar todos os erros de CSP à medida que ocorrem e refinar as políticas até que todos os recursos necessários sejam colocados na lista de permissões. É seguro mudar para `restrict mode` quando não ocorrerem mais erros. Caso contrário, uma CSP mal configurada pode fazer com que o navegador exiba uma página em branco com vários erros de console. Uma CSP corretamente configurada permite que o conteúdo da lista de permissões seja entregue sem nenhum impacto percebido no desempenho.

**Modo de restrição**: O navegador é instruído a aplicar todas as políticas de conteúdo e limitar a publicação a recursos da lista de permissões. Como a CSP é configurada a partir do servidor, em vez do Administrador, a maioria dos comerciantes precisa da assistência de um integrador de sistemas ou desenvolvedor para configurá-la corretamente. Consulte [Políticas de segurança de conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Extensões PHP para Commerce_ guia do desenvolvedor.

## Relatório

Por padrão, o CSP envia erros para o console do navegador, mas pode ser configurado para coletar registros de erros por solicitação HTTP. Além disso, há vários serviços de terceiros que você pode usar para monitorar, coletar e relatar violações da CSP.

[URI do relatório](https://report-uri.io/) é um serviço que monitora violações de CSP e exibe os resultados em um painel. Comerciantes e desenvolvedores podem usar o serviço para receber relatórios sempre que ocorrerem violações de CSP.
