---
title: 'Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.30'
description: Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.30.
feature: Tools and External Services
role: Admin
exl-id: 36c6e0cc-fd8c-4583-b147-fe4897b101d8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%
---
# Visão geral: [!DNL Quality Patches Tool] (QPT) v1.1.30

Esta subseção fornece uma descrição detalhada dos problemas corrigidos pelos patches disponíveis no [!DNL Quality Patches Tool] (QPT) v1.1.30.

O QPT v1.1.30 inclui os seguintes patches:

1. **ACSD-50336**: corrige o problema em que emails de alerta de produtos não são enviados quando um produto está de volta ao estoque ou quando o preço é alterado.
1. **ACSD-50367**: corrige o problema em que a exportação de endereço do cliente não funciona quando um atributo de endereço do cliente de seleção múltipla sem valores é criado.
1. **ACSD-49877**: corrige o problema em que a reprodução automática de vídeo não funciona no [!DNL Safari] móvel quando o vídeo é vinculado diretamente a um arquivo de vídeo remoto e não a um serviço de streaming.
1. **ACSD-50165**: corrige o erro *Não é possível excluir o arquivo. Aviso!unlink: esse arquivo ou diretório não existe ao liberar o cache JS/CSS do Admin*.
1. **ACSD-49737**: corrige o problema em que um cupom é marcado incorretamente como usado após uma falha no pagamento por cartão.
1. **ACSD-50814**: corrige o problema em que um usuário administrador não pode criar um memorando de crédito.
1. **ACSD-50116**: corrige o problema em que um usuário administrador não pode criar uma regravação de URL para subcategorias de nível 3 ou inferior.
1. **ACSD-49513**: corrige o problema em que a sincronização do armazenamento remoto falha devido a arquivos de 0 bytes.
1. **ACSD-46683**: corrige o problema em que o preço de envio mostra *Ainda não calculado*.
1. **ACSD-49129**: corrige o problema em que o atributo de conteúdo ([!UICONTROL base64 image code]) não é retornado em `rest/V1/products/sku/media` respostas da API de mídia do produto.
1. **ACSD-50276**: corrige o problema em que o formulário de registro do cliente não funciona na loja se um atributo de cliente de seleção múltipla for criado.
1. **ACSD-50527**: corrige o erro que ocorre ao salvar uma página com um bloco dinâmico vazio.
1. **ACSD-49973**: melhora o desempenho da busca de produtos agrupados por meio do GraphQL.
1. **ACSD-51114**: corrige o problema em que um produto aleatório desaparece de catálogos grandes quando a indexação assíncrona está habilitada. Melhora o desempenho da reindexação assíncrona para catálogos grandes.
1. **B2B-2598**: adiciona o recurso de cache às consultas do GraphQL `availableStores`, `countries`, `country`, `currency` e `storeConfig`.

Use o menu à esquerda para navegar até uma página de patch específica.
