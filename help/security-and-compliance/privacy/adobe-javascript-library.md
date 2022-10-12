---
title: Biblioteca JavaScript de privacidade do Adobe
description: Saiba como usar ferramentas personalizadas para acessar e excluir informações pessoais do cliente coletadas pelo Adobe Commerce e Magento Open Source.
hide: true
hidefromtoc: true
source-git-commit: 495dfd515759e4df507479de57118586eac14fda
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---


# Biblioteca JavaScript de privacidade do Adobe

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

O [Biblioteca JavaScript de privacidade do Adobe](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) é um conjunto de ferramentas que ajuda a criar um processo para acessar e excluir dados privados.

Os serviços de rastreamento de dados Adobe Commerce e Magento Open Source podem armazenar informações privadas aplicáveis a regulamentos de privacidade, como o [Regulamento Geral sobre a Proteção de Dados (GDPR)](gdpr.md) e [Lei de Privacidade do Consumidor da Califórnia (CCPA)](ccpa.md).

Essa biblioteca fornece um conjunto unificado de funções para criar solicitações de dados de privacidade, enviá-las para as implementações de cada produto e coletar as respostas. Use essa biblioteca para recuperar e remover os dados armazenados no navegador por esses serviços de rastreamento de dados.

## Instalação

Use um dos métodos a seguir para baixar o arquivo da biblioteca:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Depois de ter o arquivo , será necessário adicioná-lo a um módulo personalizado ou tema instalado na sua instância do Adobe Commerce e Magento Open Source. Siga as instruções descritas em [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar essa tarefa.

## Uso

A Biblioteca JS do AdobePrivacy fornece várias funções para gerenciar dados de identidade armazenados no navegador.

`retrieveIdentities()`
: Retorna uma matriz de identidades de um serviço junto com uma matriz de identidades não encontradas no serviço

`removeIdentities()`
: Remove identidades do navegador e retorna uma matriz de objetos de identidade com uma `isDeleteClientSide` propriedade booleana para indicar se os dados foram excluídos.

`retrieveThenRemoveIdentities()`
: Essa função é semelhante a `removeIdentities()` ao recuperar uma matriz de identidades e removê-las do navegador.

Para obter mais informações e exemplos para usar essas funções, consulte o [documentação da biblioteca oficial](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html).

### Inicialização

Instanciamento de um novo `AdobePrivacy` objeto para usar a Biblioteca JS do AdobePrivacy no código de implementação.

```js
var adobePrivacy = new AdobePrivacy({});
```

O construtor aceita um objeto de configuração com parâmetros durante a instanciação.
Consulte a [documentação da biblioteca oficial](https://developer.adobe.com/apis/experienceplatform/gdpr/services/allservices.html) para obter uma lista desses parâmetros de configuração.
