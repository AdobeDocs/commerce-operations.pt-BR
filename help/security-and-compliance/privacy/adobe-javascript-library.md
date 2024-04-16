---
title: Biblioteca JavaScript de Privacidade Adobe
description: Saiba como usar ferramentas personalizadas para acessar e excluir informações pessoais do cliente coletadas pelo Adobe Commerce.
hide: true
hidefromtoc: true
exl-id: 5080e03b-0a83-405c-a232-b93311e284a3
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Biblioteca JavaScript de Privacidade Adobe

<!-- TODO: Remove hide metadata when the library has been integrated with Commerce. -->

A variável [Biblioteca JavaScript de Privacidade Adobe](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) O é um conjunto de ferramentas que ajudam a criar um processo para acessar e excluir dados privados.

Os serviços de rastreamento de dados da Adobe Commerce podem armazenar informações privadas aplicáveis a regulamentos de privacidade, como o [Regulamento Geral sobre a Proteção de Dados (GDPR)](gdpr.md) e [Lei de Privacidade do Consumidor da Califórnia (CCPA)](ccpa.md).

Essa biblioteca fornece um conjunto unificado de funções para criar solicitações de dados de privacidade, enviá-las para as implementações de cada produto e coletar as respostas. Use essa biblioteca para recuperar e remover os dados armazenados no navegador por esses serviços de rastreamento de dados.

## Instalação

Use um dos métodos a seguir para baixar o arquivo de biblioteca:

- npm: `npm install @adobe/adobe-privacy`
- GitHub: [https://github.com/Adobe-Marketing-Cloud/adobe-privacy](https://github.com/Adobe-Marketing-Cloud/adobe-privacy)

Após ter o arquivo, será necessário adicioná-lo a um módulo personalizado ou tema instalado em sua instância do Adobe Commerce. Siga as instruções descritas em [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) tópico para realizar esta tarefa.

## Uso

A Biblioteca JS do Adobe Privacy fornece várias funções para gerenciar dados de identidade armazenados no navegador.

`retrieveIdentities()`
: retorna uma matriz de identidades de um serviço, juntamente com uma matriz de identidades não encontradas no serviço

`removeIdentities()`
: remove identidades do navegador e retorna uma matriz de objetos de identidade com um `isDeleteClientSide` propriedade booleana para indicar se os dados foram excluídos.

`retrieveThenRemoveIdentities()`
: Essa função é semelhante a `removeIdentities()` na medida em que recupera uma matriz de identidades e as remove do navegador.

Para obter mais informações e exemplos para usar essas funções, consulte a [documentação oficial da biblioteca](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html).

### Inicialização

Instanciar um novo `AdobePrivacy` para usar a Biblioteca JS do AdobePrivacy no código de implementação.

```js
var adobePrivacy = new AdobePrivacy({});
```

O construtor aceita um objeto de configuração com parâmetros durante a instância.
Consulte a [documentação oficial da biblioteca](https://experienceleague.adobe.com/docs/experience-platform/privacy/js-library.html) para obter uma lista desses parâmetros de configuração.
