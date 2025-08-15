---
title: Versões do Beta
description: Saiba mais sobre as versões beta do Adobe Commerce e como participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 879160b11fe4840eb3af97c64f080deb5f002827
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 0%

---

# Versões beta do Adobe Commerce

Os programas beta do Adobe Commerce são uma maneira de os comerciantes obterem acesso a recursos e código de pré-lançamento, fornecerem feedback e guiarem o futuro do Adobe Commerce. Há dois tipos de programas beta:

- Beta público: um programa beta público está disponível para todos os clientes e parceiros da Adobe Commerce
- Private Beta: um programa beta privado pode exigir uma aprovação com base em critérios de qualificação para participar

>[!IMPORTANT]
>
>As versões do Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. A Adobe não terá nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) às versões beta. Os clientes são aconselhados a ter cuidado e não depender de forma alguma do funcionamento ou do desempenho correto das versões beta e/ou de qualquer documentação ou material que as acompanhe. Os recursos e as APIs na versão beta estão sujeitos a alterações sem aviso prévio. Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

## Benefícios da participação

A obtenção de acesso antecipado aos recursos que a Adobe está desenvolvendo oferece aos clientes e parceiros a capacidade de fornecer feedback, moldar o desenvolvimento do produto e se preparar para adotar novos recursos antes da disponibilidade geral.

## Programas atuais do Beta

Consulte as seções a seguir para obter uma lista de programas beta ativos.

### Recursos aprimorados de pesquisa para o Live Search (Beta público)

Esta versão beta oferece suporte a três novos recursos na consulta [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Pesquisa em camadas** - Pesquisar em outro contexto de pesquisa - Com esse recurso, você pode realizar até duas camadas de pesquisa para suas consultas de pesquisa. Por exemplo:

   - **Pesquisa de Camada 1** - Pesquise por &quot;motor&quot; em &quot;product_attribute_1&quot;.
   - **Pesquisa de camada 2** - Pesquise por &quot;part number 123&quot; em &quot;product_attribute_2&quot;. Este exemplo procura por &quot;número de peça 123&quot; nos resultados por &quot;motor&quot;.

  A pesquisa em camadas está disponível para a indexação de pesquisa `startsWith` e a indexação de pesquisa `contains`, conforme descrito abaixo:

- **startsWith indexação de pesquisa** - Pesquisar usando a indexação `startsWith`. Esse novo recurso permite:

   - Procurando produtos em que o valor do atributo começa com uma string específica.
   - Configurar uma pesquisa &quot;termina com&quot; para que os compradores possam pesquisar produtos em que o valor do atributo termina com uma determinada string. Para habilitar uma pesquisa &quot;termina com&quot;, o atributo de produto precisa ser assimilado na ordem inversa, e a chamada de API também deve ser uma sequência invertida.

- **contém a indexação de pesquisa** -Pesquise um atributo usando a indexação contains. Esse novo recurso permite:

   - Procurando uma consulta em uma cadeia de caracteres maior. Por exemplo, se um comprador procurar o número de produto &quot;PE-123&quot; na cadeia de caracteres &quot;HAPE-123&quot;.

      - Observação: este tipo de pesquisa é diferente da [pesquisa de frase](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase) existente, que executa uma pesquisa de preenchimento automático. Por exemplo, se o valor do atributo do seu produto for &quot;calças de ar livre&quot;, uma pesquisa de frase retornará uma resposta para &quot;fora da panela&quot;, mas não retornará uma resposta para &quot;ou formigas&quot;. A contém busca, no entanto, retorna uma resposta para &quot;ou formigas&quot;.

Essas novas condições aprimoram o mecanismo de filtragem de consultas de pesquisa para refinar os resultados da pesquisa. Essas novas condições não afetam a consulta de pesquisa principal. Para participar da versão beta, envie uma solicitação de email para [commerce-store-services](mailto:commerce-storefront-services@adobe.com).

Para instalar o Live Search beta, consulte o [Guia do Live Search](https://experienceleague.adobe.com/pt-br/docs/commerce/live-search/install#install-the-live-search-beta).

### Integração do sistema IBM Sterling Order Management (Private Beta)

Esse acelerador de integração do IBM Sterling Order Management permite que os clientes da Adobe Commerce comecem a usar recursos avançados de gerenciamento de pedidos viabilizados pelo IBM Sterling OMS. Com essa integração, os comerciantes obtêm:

- Visibilidade em tempo real dos níveis de inventário e datas precisas de entrega para seus clientes.
- Seleção de fornecedor automatizada para pedidos com base em regras configuráveis, para que você possa otimizar sua rede de atendimento e inventário.
- Uma visualização universal de pedidos em canais a partir de um único painel, para que suas equipes de suporte possam fornecer serviços excepcionais e identificar e lidar com exceções rapidamente.
- Um fluxo de gerenciamento de devoluções modelado para simplificar o gerenciamento de devoluções.

Para participar deste beta, envie uma solicitação de email para [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Alpha público/Beta)

Cada versão alfa e beta do Adobe Commerce Foundation inclui todas as alterações entregues ao código principal do Adobe Commerce até a data de lançamento programada, incluindo, mas não limitado às seguintes áreas funcionais:

- Correções de segurança mais recentes
- Melhorias de desempenho
- Melhorias na GraphQL
- Correções de erros de qualidade geral
- Contribuições da Comunidade
- Alterações necessárias para oferecer suporte à compatibilidade com [serviços da Adobe Commerce](https://experienceleague.adobe.com/pt-br/docs/commerce/user-guides/home)

#### Convenção de nomenclatura e programação

A Adobe normalmente lança patches alfa e beta várias vezes por ano.

Os pacotes de versão do Alpha têm um sufixo `-alphaX`. Por exemplo, os pacotes de versão alfa do Adobe Commerce 2.4.7 usam a seguinte convenção de nomenclatura:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Os pacotes de versão do Beta têm um sufixo `-betaX`. Por exemplo, os pacotes de versão beta do Adobe Commerce 2.4.7 usam a seguinte convenção de nomenclatura:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte a [programação de lançamento](schedule.md) para obter a lista das próximas datas de lançamento de versões alfa e beta públicas.

#### Acesso à versão

As versões alfa e beta do Adobe Commerce são distribuídas da mesma forma que qualquer outra versão de patch do Adobe Commerce: como metapackages do Composer no `https://repo.magento.com`. O código-fonte está disponível em [GitHub](https://github.com/magento/magento2).

Consulte [Início rápido da instalação do Composer](../installation/composer.md) para obter mais detalhes.

#### Relatório de problemas

A Adobe não fornece o serviço de suporte padrão da Adobe para versões alfa e beta.

Para enviar comentários relacionados às versões alfa e beta, siga o [fluxo regular de relatórios de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) no [GitHub](https://github.com/magento/magento2).

O Adobe monitora todos os problemas críticos relatados na versão alfa ou beta mais recente e prioriza que eles sejam resolvidos antes da data de lançamento no mercado.
