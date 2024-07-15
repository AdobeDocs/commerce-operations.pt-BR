---
title: Biblioteca JavaScript de privacidade
description: Saiba como usar ferramentas personalizadas para acessar e excluir informações pessoais do cliente coletadas pelo Adobe Commerce.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Biblioteca JavaScript de privacidade

A Biblioteca de privacidade da JavaScript é um conjunto de ferramentas que ajudam a criar um processo para acessar e excluir dados privados coletados pela Adobe Commerce.

Os serviços de rastreamento de dados da Commerce podem armazenar informações privadas aplicáveis a regulamentos de privacidade, como o [Regulamento Geral sobre a Proteção de Dados (GDPR)](gdpr.md) e a [Lei de Privacidade do Consumidor da Califórnia (CCPA)](ccpa.md).

Essa biblioteca fornece um conjunto de funções para criar solicitações de dados de privacidade e coletar suas respostas. Use essa biblioteca para recuperar e remover os dados armazenados no navegador pelos serviços de rastreamento de dados da Adobe Commerce.

>[!NOTE]
>
>Se o [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, a Commerce não coletará dados comportamentais até que o comprador dê o seu consentimento. Se o [!UICONTROL **Modo de restrição de cookies**] estiver desativado, a Commerce coletará dados comportamentais por padrão.

## Instalação

A Biblioteca JavaScript de Privacidade está disponível no seguinte local CDN: `commerce.adobe.net/magentoprivacy.js`

Após ter o arquivo, será necessário adicioná-lo a um módulo personalizado ou tema instalado em sua instância do Adobe Commerce. Siga as instruções descritas no tópico [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar esta tarefa.

### Inicialização

Importe e instancie um novo objeto `MagentoPrivacy` ou use o objeto `window` para acessar as funções de Privacidade e JavaScript.

Exemplo usando `import`:

```js
import MagentoPrivacy from "./MagentoPrivacy"

const magePriv = new MagentoPrivacy()
```

Exemplo usando `window`:

```js
const magePriv = new window.MagentoPrivacy()
```

## Uso

A Biblioteca JS de privacidade fornece várias funções para gerenciar dados de identidade armazenados no navegador.

`retrieveIdentity()`
: retorna uma promessa do JavaScript para um objeto de identidade de um serviço no navegador.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: remove os dados de identidade de um serviço no navegador.
Esta função retorna uma promessa JavaScript para um objeto de identidade com uma propriedade booleana `isDeleted` para indicar se os dados foram excluídos.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
