---
title: Versões do Beta
description: Saiba mais sobre as versões beta do Adobe Commerce e como participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplica-se somente a projetos do Adobe Commerce na nuvem (infraestrutura do PaaS gerenciada pela Adobe) e a projetos locais."
badgeSaas: label="SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce as a Cloud Service e do Adobe Commerce Optimizer (infraestrutura SaaS gerenciada pela Adobe)."
source-git-commit: bf0f269900468870a1da7b5360548d49e009097c
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# Versões beta do Adobe Commerce

Os programas do Beta para [soluções de produtos da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions) são uma maneira de os comerciantes obterem acesso a recursos e códigos de pré-lançamento, fornecer feedback e orientar o futuro do Adobe Commerce. Há dois tipos de programas beta:

- Beta público: um programa beta público está disponível para todos os clientes e parceiros da Adobe Commerce
- Private Beta: um programa beta privado pode exigir uma aprovação com base em critérios de qualificação para participar

>[!IMPORTANT]
>
>**Aviso de isenção legal**<br/>
>As versões do Beta incluem recursos de pré-lançamento e código que podem conter defeitos e são fornecidos &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantia de nenhum tipo. A Adobe tem o único critério de disponibilizar versões beta de modo geral. A Adobe não tem nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar, oferecer suporte (por meio dos Serviços de suporte da Adobe ou de outra forma) ou fornecer essas versões beta até qualquer data específica. Caso uma versão beta seja disponibilizada para o público em geral, ela poderá estar sujeita a termos e condições adicionais, incluindo taxas aplicáveis. As versões do Beta estão sujeitas a alterações sem aviso prévio, incluindo a descontinuação. Os clientes são aconselhados a ter cuidado e não depender de forma alguma do funcionamento ou do desempenho ininterrupto ou livre de erros das versões beta.  Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

## Benefícios da participação

A obtenção de acesso antecipado aos recursos que a Adobe está desenvolvendo oferece aos clientes e parceiros a capacidade de fornecer feedback, moldar o desenvolvimento do produto e se preparar para adotar novos recursos antes da disponibilidade geral.

## Programas atuais do Beta

Consulte as seções a seguir para obter uma lista de programas beta ativos.

### Correspondência de pesquisa e classificação (Private Beta)

A Adobe está aprimorando a forma como a descoberta de produtos classifica os resultados da pesquisa para [!DNL Live Search] em [!DNL Adobe Commerce] e para [!DNL Adobe Commerce Optimizer]. A atualização prioriza **correspondências de frase exata e próxima**, em seguida, correspondências em que **todos os termos de consulta aparecem no mesmo atributo pesquisável** e, por fim, **correspondências entre campos** (incluindo comportamento compatível com sugestões de estilo de preenchimento automático). Esse modelo em camadas ajuda as consultas de alta intenção a identificar os produtos mais relevantes primeiro, além de ainda retornar alternativas úteis.

O mesmo modelo de relevância interage com **pesos de pesquisa**, **classificação inteligente**, **sinônimos** e **regras de merchandising** (fixar, impulsionar, enterrar). As vitrines da Alemanha podem usar **decomposto** para palavras compostas, com a mesma abordagem de priorização geral.

**Principais benefícios**

- Aumentos mais fortes para correspondências de frases exatas e próximas (incluindo formas normalizadas, como singular e plural).
- Classificação mais alta quando todas as palavras de consulta aparecem juntas em um campo pesquisável.
- Expectativas mais claras sobre como os pesos, a classificação inteligente e as regras manuais se combinam no momento do query.
- Orientação para validar consultas de alto valor e ajustar regras de aumento após a alteração.

Saiba mais sobre a estratégia de correspondência e classificação de pesquisa no [Adobe Commerce Optimizer (SaaS)](https://experienceleague.adobe.com/en/docs/commerce/optimizer/manage-results/search-relevance-matching) e no [Live Search (PaaS)](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/search-relevance-matching).

Para solicitar um convite para este beta privado, envie um email para [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com). A equipe do Adobe responderá com as próximas etapas e os requisitos de qualificação.

### Filtros de preço de recomendação (Beta público) {#recommendation-price-filters-public-beta}

[!BADGE Somente SaaS]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplicável somente a projetos do Adobe Commerce as a Cloud Service e do Adobe Commerce Optimizer (infraestrutura SaaS gerenciada pela Adobe)."}

[!DNL Adobe Commerce Optimizer] adiciona **filtros de preço** às Recomendações de Produto para que você possa incluir ou excluir produtos recomendados com base no preço ao criar ou editar uma unidade de recomendação. Os filtros usam o **preço calculado final** de cada produto do **catálogo de preços ativo** da loja, incluindo descontos e promoções desse catálogo de preços (não apenas o preço de lista). As regras de preços refinam o conjunto de candidatos; elas não reclassificam os produtos.

Você pode definir intervalos **estáticos** com valores mínimos e máximos fixos na moeda base da sua loja, ou regras **dinâmicas** nas páginas de detalhes do produto que comparam produtos recomendados ao **produto exibido no momento** usando operadores como menor que ou igual a, maior que ou igual a, ou dentro de um valor ou intervalo de porcentagem do preço de âncora. Filtros dinâmicos estão disponíveis para tipos de recomendação relacionados a SKU que são executados no contexto do produto (por exemplo, *Visualizou isto, visualizou aquilo* e *Mais itens semelhantes*).

**Principais benefícios**

- Inclua ou exclua candidatos a recomendação por preço usando regras de inclusão e exclusão na etapa **Filtrar produtos**.
- Use faixas de preço estáticas para objetivos de merchandising fixos (por exemplo, complementos econômicos ou vendas adicionais premium).
- Use as regras de preço dinâmicas na página de detalhes do produto para mostrar alternativas em uma faixa de preço comparável em relação ao produto que está sendo visualizado.
- Alinhe a filtragem com o preço que os compradores veem, que é o mesmo preço final do catálogo de preços ativo usado para filtragem e exibição.

Para saber mais, consulte [Filtros de recomendação — Preço](https://experienceleague.adobe.com/en/docs/commerce/optimizer/merchandising/recommendations/filters#price) no guia do comerciante e [Configuração de recomendações de produto](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/content-customizations/product-recommendations/) no guia de entrega da loja.

Para compartilhar seus comentários enquanto você usa este recurso beta, envie um email para [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Serviço de patch de automação de nuvem (Private Beta)

[!BADGE Somente PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplica-se somente a projetos do Adobe Commerce na nuvem (infraestrutura do PaaS gerenciada pela Adobe) e a projetos locais."}

O [Serviço de Patch de Automação da Nuvem](../tools/caps-tool/intro.md) automatiza o processo de aplicação de patches de segurança isolados aos ambientes do [Adobe Commerce na Infraestrutura da Nuvem](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview).

Em outubro de 2025, a versão beta do Serviço de patch de automação de nuvem será adicionada ao [painel de ferramentas de Análise do site](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/dashboard). Este serviço oferece suporte aos administradores de projetos da Commerce com um fluxo de trabalho simplificado de patch que inclui:

- Instalação de patch automatizada
- Reverter recuperação
- Verificação pós-implantação.

O serviço garante que você possa manter ambientes seguros, estáveis e atualizados com o mínimo de esforço e risco manual.

O beta inclui os seguintes recursos:

- **Automatizar a instalação de patches**: simplifique e automatize o processo de correção de vulnerabilidades críticas em ambientes.
- **Minimizar risco**: Evite interrupções do site com recursos de verificação de integridade e reversão pós-implantação.

>[!NOTE]
>
>Como o Serviço de patch de automação de nuvem aplica automaticamente patches de segurança isolados, você deve ter a [função de Colaborador ou Administrador de projeto](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/project/user-access) para usá-los.

Para participar deste beta, preencha e envie o [Serviço de patch de automação de nuvem - Formulário de inscrição no Beta](https://forms.office.com/r/3Wfxj5nPdB).

### Assistente de IA de produtividade do comerciante (Beta público)

O Merchant Productivity AI Assistant é uma interface conversacional incorporada ao Adobe Commerce Admin que ajuda os comerciantes a concluírem tarefas de rotina e acessarem insights de negócios sob demanda usando linguagem natural. Ele permite que os comerciantes gerenciem promoções, atualizem informações do catálogo de produtos e recuperem dados operacionais, como pedidos recentes ou promoções ativas, diretamente nos fluxos de trabalho existentes. O assistente também fornece orientação no contexto para ajudar os comerciantes a navegar e usar o Administrador com mais eficiência.

**Principais benefícios**

- Automatize tarefas comuns de merchandising, incluindo a criação de promoções e atualizações de metadados de catálogos, usando instruções em linguagem natural.
- Acesse a assistência e as orientações contextuais diretamente no fluxo de trabalho do Administrador.
- Consultar dados do armazenamento em tempo real sob demanda — por exemplo, recuperar os últimos 10 pedidos, exibir promoções ativas no momento ou verificar o status do estoque.
- Reduza o tempo gasto com tarefas repetitivas de administrador, permitindo que os comerciantes se concentrem na estratégia e no crescimento.

Para participar deste beta, envie um email para [commerce-storefront-services@adobe.com](mailto:commerce-storefront-services@adobe.com).

### Adobe Commerce Foundation (Alpha público/Beta)

[!BADGE Somente PaaS]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Aplica-se somente a projetos do Adobe Commerce na nuvem (infraestrutura do PaaS gerenciada pela Adobe) e a projetos locais."}

Cada versão alfa e beta do Adobe Commerce Foundation inclui todas as alterações fornecidas ao código principal do Adobe Commerce até a data de lançamento programada, incluindo, mas não limitado às seguintes áreas funcionais:

- Correções de segurança mais recentes
- Melhorias de desempenho
- Melhorias na GraphQL
- Correções de erros de qualidade geral
- Contribuições da Comunidade
- Alterações necessárias para oferecer suporte à compatibilidade com [serviços da Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce/user-guides/home)

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
