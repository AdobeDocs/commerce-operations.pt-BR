---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.71'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no  [!DNL Quality Patches Tool] (QPT) v1.1.71.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 4660942d90435eaeb6960206c29733bed6453b6a
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.71

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.71.

O QPT v1.1.71 inclui os seguintes patches:


* **ACSD-60624**: falha ao carregar Imagem para conteúdo vazio nas seções Imagem, Banner e Controle Deslizante em [!DNL Page Builder]
* **ACSD-67089**: problema de paginação na API `inventory/export-stock-salable-qty`, que limita incorretamente `total_count` ao tamanho da página.
* **ACSD-67093**: recuperar pedidos até [!DNL GraphQL] usando o filtro de intervalo de datas retorna resultados incorretos.
* **ACSD-67459**: não é possível importar produtos com descrições maiores que 65.536 caracteres.
* **ACSD-67603**: tempos de processamento longos de geração de mapas do site para produtos com inclusão de imagem habilitada
* **ACSD-67643**: entradas duplicadas são criadas durante atualizações agendadas em ambientes com um alto número de categorias aninhadas.
* **ACSD-67652**: o status do produto do pacote é retornado como indisponível em chamadas [!DNL GraphQL] mesmo com produtos filho e pai em estoque.
* **ACSD-67904**: os pedidos não podem ser feitos se o nome da cidade contiver dígitos (0-9), E comercial (&amp;), ponto (.) ou parênteses ().

Use o menu à esquerda para navegar até uma página de patch específica.
