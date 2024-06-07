---
title: Versões Beta
description: Saiba mais sobre as versões beta do Adobe Commerce e como participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 0e2dfc376a049a47348a7a913bd5181436227cc2
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Versões beta do Adobe Commerce

Os programas beta do Adobe Commerce são uma maneira de os comerciantes obterem acesso a recursos e código de pré-lançamento, fornecerem feedback e guiarem o futuro do Adobe Commerce. Há dois tipos de programas beta:

- Beta público: um programa beta público está disponível para todos os clientes e parceiros da Adobe Commerce
- Beta privado: um programa beta privado pode exigir uma aprovação com base em critérios de qualificação para participar

>[!IMPORTANT]
>
>As versões Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. O Adobe não terá nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte do Adobe ou de outra forma) às versões beta. Os clientes são aconselhados a ter cuidado e não depender de forma alguma do funcionamento ou do desempenho correto das versões beta e/ou de qualquer documentação ou material que as acompanhe. Os recursos e as APIs na versão beta estão sujeitos a alterações sem aviso prévio. Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

## Benefícios da participação

O acesso antecipado aos recursos que o Adobe está desenvolvendo oferece aos clientes e parceiros a capacidade de fornecer feedback, moldar o desenvolvimento de produtos e se preparar para adotar novos recursos antes da disponibilidade geral.

## Programas Beta Atuais

Consulte as seções a seguir para obter uma lista de programas beta ativos.

### Integração do Experience Manager Assets para o Commerce (Beta privado)

A Experience Manager Assets Integration for Commerce permite o gerenciamento e o fornecimento eficientes de um grande volume de imagens de produtos da Experience Manager Assets para a Adobe Commerce, com pouco ou nenhum esforço operacional necessário.

Principais recursos:

- Integração Plug and Play — forneça uma integração alimentada por Adobe, pronta para uso, entre o Experience Manager Assets e o Adobe Commerce para permitir que os comerciantes se concentrem no que é mais importante, com custos operacionais reduzidos e maior eficiência.

- Personalizar imagens do produto em escala - Use o Experience Manager Assets para gerar milhões de variações de produtos para experiências personalizadas do Commerce com ferramentas de edição fáceis baseadas na interface, criação de conteúdo generativo usando o Adobe Firefly e fluxos de trabalho de ativos atribuídos para garantir a consistência da marca. Quando estiver satisfeito com os ativos, forneça-os perfeitamente às suas lojas Commerce usando a Integração do Experience Manager Assets.

- Fácil integração - simplifique a integração ao comerciante com um processo de sincronização configurável que permite a sincronização completa entre o repositório da Experience Manager Assets e o catálogo da Commerce.

- Estratégia de correspondência flexível — a integração inclui algoritmos padrão de correspondência de ativos com base em SKUs de produtos que sincronizam imagens entre o AEM Assets e o Commerce, além de ser extensível usando o Construtor de aplicativos do Adobe Developer. Trabalhe com seu parceiro de soluções para criar uma estratégia de correspondência de ativos personalizada sobre a integração para acomodar qualquer estrutura do repositório de gerenciamento de ativos.

Para participar da versão beta, envie uma solicitação por email para [Shaun McCran](mailto:mccran@adobe.com).

### Integração do sistema IBM Sterling Order Management (Beta privado)

Esse acelerador de integração do IBM Sterling Order Management permite que os clientes da Adobe Commerce comecem a usar recursos avançados de gerenciamento de pedidos viabilizados pelo IBM Sterling OMS. Com essa integração, os comerciantes obtêm:
- Visibilidade em tempo real dos níveis de inventário e datas precisas de entrega para seus clientes.
- Seleção de fornecedor automatizada para pedidos com base em regras configuráveis, para que você possa otimizar sua rede de atendimento e inventário.
- Uma visualização universal de pedidos em canais a partir de um único painel, para que suas equipes de suporte possam fornecer serviços excepcionais e identificar e lidar com exceções rapidamente.
- Um fluxo de gerenciamento de devoluções modelado para simplificar o gerenciamento de devoluções.

Para participar deste beta, envie uma solicitação por email para [sbieber@adobe.com](mailto:sbieber@adobe.com).

### Conexão de dados e Audience Activation (Beta público)

Compartilhamento de dados expandido entre o Adobe Commerce e o Adobe Experience Platform para impulsionar experiências personalizadas mais avançadas. Esse recurso permite que os comerciantes:
- Compartilhar perfis de clientes do Commerce
- Criar atributos personalizados
- Obter insights do Commerce no Real-Time CDP e no Adobe Journey Optimizer
- Suporte a vários conjuntos de dados e fluxos de dados

Para participar deste beta, envie uma solicitação por email para [DataConnection@adobe.com](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (Beta público)

Cada versão beta do Adobe Commerce Foundation inclui todas as alterações fornecidas ao código principal do Adobe Commerce até a data de lançamento programada, incluindo, mas não limitado às seguintes áreas funcionais:

- Correções de segurança mais recentes
- Melhorias de desempenho
- Melhorias na GraphQL
- Correções de erros de qualidade geral
- Contribuições da Comunidade
- Alterações necessárias para suportar compatibilidade com o [Serviços da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convenção de nomenclatura e programação

A Adobe geralmente lança patches beta duas vezes por ano.

Os pacotes de versão beta têm uma `-betaX` sufixo. Por exemplo, os pacotes de versão beta do Adobe Commerce 2.4.7 usam a seguinte convenção de nomenclatura:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte a [programação de lançamento](schedule.md) para obter a lista das datas futuras de lançamento de beta público.


#### Acesso à versão beta

As versões beta do Adobe Commerce são distribuídas da mesma forma que qualquer outra versão de patch do Adobe Commerce: as Composer metapackages em `https://repo.magento.com`. O código-fonte está disponível em [GitHub](https://github.com/magento/magento2).

Consulte [Início rápido da instalação do Composer](../installation/composer.md) para obter mais detalhes.

#### Relatório de problemas

O Adobe não fornece o Serviço de suporte de Adobe padrão para versões beta.

Para enviar feedback relacionado às versões beta, siga o nosso [fluxo regular de relatórios de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) em [GitHub](https://github.com/magento/magento2).

Nossas equipes internas monitorarão todos os problemas críticos relatados em relação à versão beta mais recente e os priorizarão para serem resolvidos antes da data de lançamento no mercado.
