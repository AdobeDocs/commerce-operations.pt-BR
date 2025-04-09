---
title: Versões do Beta
description: Saiba mais sobre as versões beta do Adobe Commerce e como participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: c523b57270370d87be0f2ab0513f7908bb0a7173
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Versões beta do Adobe Commerce

Os programas beta do Adobe Commerce são uma maneira de os comerciantes obterem acesso a recursos e código de pré-lançamento, fornecerem feedback e guiarem o futuro do Adobe Commerce. Há dois tipos de programas beta:

- Beta público: um programa beta público está disponível para todos os clientes e parceiros da Adobe Commerce
- Private Beta: um programa beta privado pode exigir uma aprovação com base em critérios de qualificação para participar

>[!IMPORTANT]
>
>As versões do Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não terá nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões beta. Recomenda-se que os clientes usem cuidado e não confiem de forma alguma no funcionamento ou desempenho correto das versões beta e/ou em qualquer documentação ou material que a acompanhe. Os recursos e AS APIs na versão beta estão sujeitos a alterações sem aviso prévio. Assim, qualquer uso das versões beta é totalmente por conta própria do cliente.

## Benefícios de participar

Obter acesso antecipado aos recursos que a Adobe Systems está desenvolvendo fornece aos clientes e parceiros a capacidade de fornecer feedback, moldar o desenvolvimento de produtos e preparar-se para adotar novos recursos antes da disponibilidade geral.

## Programas beta atuais

Consulte as seções a seguir para obter uma lista de programas beta ativos.

### Adobe Commerce Optimizer

O Adobe Commerce Optimizer aprimora sua experiência de comércio eletrônico com uma loja de alto desempenho, aumentando o tráfego orgânico, o engajamento do cliente e a receita.

Com o Adobe Commerce Optimizer, você pode:

- Cresça e dimensione seu catálogo sem reaplacar toda a sua pilha de comércio.
- Ingera dados do catálogo de qualquer fonte.
- Definir canais e políticas de negócios.
- Crie pesquisas e recomendações personalizadas usando IA e ML.
- Visualize dados essenciais do produto disponíveis, incluindo o status da sincronização e dados de eventos da loja, para uma implementação precisa e solução de problemas.

[Saiba mais](https://experienceleague.adobe.com/docs/commerce/optimizer/overview.html) sobre o Adobe Commerce Optimizer. Se você deseja participar do programa de acesso antecipado do Adobe Commerce Optimizer, envie uma solicitação de email para [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Recursos aprimorados de pesquisa para o Live Search (Beta público)

Esta versão beta oferece suporte a três novos recursos na consulta [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Pesquisa em camadas** - Pesquisar em outro contexto de pesquisa - Com esse recurso, você pode realizar até duas camadas de pesquisa para suas consultas de pesquisa. Por exemplo:

   - **Pesquisa de Camada 1** - Pesquise por &quot;motor&quot; em &quot;product_attribute_1&quot;.
   - **Pesquisa de camada 2** - Pesquise por &quot;part number 123&quot; em &quot;product_attribute_2&quot;. Este exemplo procura por &quot;número de peça 123&quot; nos resultados por &quot;motor&quot;.

  A pesquisa em camadas está disponível para a indexação de pesquisa `startsWith` e a indexação de pesquisa `contains`, conforme descrito abaixo:

- **startsWith pesquisa indexação** - Search usando `startsWith` indexação. Esse novo recurso permite:

   - Pesquisando por produtos nos quais o valor do atributo começa com uma determinada string.
   - Configurar uma pesquisa &quot;termina com&quot; para que os compradores possam pesquisa para produtos onde o valor do atributo termina com uma determinada string. Para habilitar uma pesquisa &quot;termina com&quot;, o atributo produto precisa ser assimilado ao contrário e a chamada da API também deve ser uma sequência de caracteres revertida.

- **contém a indexação de pesquisa** -Pesquise um atributo usando a indexação contains. Esse novo recurso permite:

   - Procurando uma consulta em uma cadeia de caracteres maior. Por exemplo, se um comprador procurar o número de produto &quot;PE-123&quot; na cadeia de caracteres &quot;HAPE-123&quot;.

      - Observação: este tipo de pesquisa é diferente da [pesquisa de frase](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) existente, que executa uma pesquisa de preenchimento automático. Por exemplo, se o valor do seu atributo de produto for &quot;calças ao ar livre&quot;, uma frase pesquisa retornará uma resposta para &quot;panela para fora&quot;, mas não retorna uma resposta para &quot;formigas oor&quot;. Uma contém pesquisa, no entanto, retorna uma resposta para &quot;formigas oor&quot;.

Essas novas condições aumentam o mecanismo de filtragem pesquisar consulta para refinar pesquisa resultados. Essas novas condições não afetam as pesquisar consulta principais. Para participar da beta, envie um solicitação de email para [commerce-storefront-services](mailto:commerce-storefront-services@adobe.com).

Para instalar o Live Search beta, consulte o [Guia do Live Search](https://experienceleague.adobe.com/en/docs/commerce/live-search/install#install-the-live-search-beta).

### Integração do sistema IBM Sterling Order Management (Private Beta)

Esse acelerador de integração do IBM Sterling Order Management permite que os clientes da Adobe Commerce comecem a usar recursos avançados de gerenciamento de pedidos viabilizados pelo IBM Sterling OMS. Com essa integração, os comerciantes obtêm:

- Visibilidade em tempo real dos níveis de inventário e datas precisas de entrega para seus clientes.
- Seleção de fornecedor automatizada para pedidos com base em regras configuráveis, para que você possa otimizar sua rede de atendimento e inventário.
- Uma visualização universal de pedidos em todos os canais a partir de uma única painel para que suas equipes de suporte possam prestar um serviço excepcional e identificar e lidar com exceções rapidamente.
- Um fluxo de gerenciamento de retorno de modelo para simplificar o gerenciamento de retornos.

Para participar deste beta, envie um email solicitação para [o sbieber@adobe.com](mailto:sbieber@adobe.com).

### Fundação Comércio Adobe Systems (beta público)

Cada Adobe Systems Comércio versão beta da Foundation inclui todas as alterações entregues a Adobe Systems Comércio código principal até a data de lançamento agendada, inclusive, mas não se limitando às seguintes áreas funcionais:

- Correções de segurança mais recentes
- Melhorias de desempenho
- Melhorias na GraphQL
- Correções de erros de qualidade geral
- Contribuições da Comunidade
- Alterações necessárias para suportar compatibilidade com [serviços Adobe Systems Comércio](https://experienceleague.adobe.com/docs/commerce/user-guides/home.html)

#### Convenção de nomenclatura e programação

A Adobe normalmente lança patches beta duas vezes por ano.

Os pacotes de versão do Beta têm um sufixo `-betaX`. Por exemplo, os pacotes de versão beta do Adobe Commerce 2.4.7 usam a seguinte convenção de nomenclatura:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte a [programação de lançamento](schedule.md) para obter a lista das próximas datas de lançamento do beta público.

#### Acesso à versão do Beta

As versões beta do Adobe Commerce são distribuídas da mesma forma que qualquer outra versão de patch do Adobe Commerce: como metapackages do Composer no `https://repo.magento.com`. O código-fonte está disponível em [GitHub](https://github.com/magento/magento2).

Consulte [Início rápido da instalação do Composer](../installation/composer.md) para obter mais detalhes.

#### Relatório de problemas

A Adobe não fornece o serviço de suporte padrão da Adobe para versões beta.

Para enviar feedback relacionado às versões beta, siga nosso [fluxo regular de relatórios de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) no [GitHub](https://github.com/magento/magento2).

Nossas equipes internas monitor todos os problemas crítico relatados na versão beta mais recente e priorizar que sejam resolvidos antes da data de lançamento do GA.
