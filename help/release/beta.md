---
title: Versões Beta
description: Saiba mais sobre as versões beta do Adobe Commerce e como participar.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 07e616b26784a6e2e8994efc5816a5005619b5bb
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Versões beta do Adobe Commerce

Os programas beta do Adobe Commerce são uma maneira de os comerciantes obterem acesso a recursos e código de pré-lançamento, fornecerem feedback e guiarem o futuro do Adobe Commerce. Há dois tipos de programas beta:

- Beta público: um programa beta público está disponível para todos os clientes e parceiros da Adobe Commerce
- Private Bata: Um programa beta privado pode exigir uma aprovação com base em critérios de qualificação para participar

>[!IMPORTANT]
>
>As versões Beta podem conter defeitos e são fornecidas &quot;NO ESTADO EM QUE SE ENCONTRAM&quot; sem garantias de nenhum tipo. O Adobe não terá nenhuma obrigação de manter, corrigir, atualizar, alterar, modificar ou oferecer suporte (por meio dos Serviços de suporte do Adobe ou de outra forma) às versões beta. Os clientes são aconselhados a ter cuidado e não depender de forma alguma do funcionamento ou do desempenho correto das versões beta e/ou de qualquer documentação ou material que as acompanhe. Os recursos e as APIs na versão beta estão sujeitos a alterações sem aviso prévio. Portanto, qualquer uso das versões beta é de inteira responsabilidade do cliente.

## Benefícios da participação

O acesso antecipado aos recursos que o Adobe está desenvolvendo oferece aos clientes e parceiros a capacidade de fornecer feedback, moldar o desenvolvimento de produtos e se preparar para adotar novos recursos antes da disponibilidade geral.

## Programas Beta Atuais

Consulte as seções a seguir para obter uma lista de programas beta ativos.

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

### Kit Inicial De Integração Do Backoffice (Beta Privado)

O backoffice [kit inicial de integração](https://developer-stage.adobe.com/commerce/extensibility/app-development/starter-kit/) O fornece aos desenvolvedores um acelerador para criar integrações orientadas por eventos com sistemas como ERPs, CRMs e OMSs. Com o kit inicial, você pode reduzir os custos de desenvolvimento em até 50%. O kit inicial também segue as práticas recomendadas da Adobe Commerce que reduzem significativamente o custo de manutenção. Os destaques do Starter kit incluem:
- Sincronização de dados para objetos usados com frequência, como produto, pedido, cliente, estoque e remessa
- Esquemas de arquitetura seguindo as práticas recomendadas
- Integração de scripts para acelerar o desenvolvimento

Para participar deste beta, conclua o [formulário de inscrição](https://forms.office.com/r/YbYArqE3DT).

### Adobe Commerce Foundation (Beta público)

Cada versão beta do Adobe Commerce Foundation inclui todas as alterações fornecidas ao código principal do Adobe Commerce até a data de lançamento programada, incluindo, mas não limitado às seguintes áreas funcionais:

- Correções de segurança mais recentes
- Melhorias de desempenho
- Melhorias na GraphQL
- Correções de erros de qualidade geral
- Contribuições da Comunidade
- Alterações necessárias para suportar compatibilidade com o [Serviços da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

#### Convenção de nomenclatura e programação

O Adobe lançará patches beta duas vezes por ano. O primeiro patch beta é normalmente lançado três meses após a disponibilidade geral de uma nova versão de patch de aplicativo principal.

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
