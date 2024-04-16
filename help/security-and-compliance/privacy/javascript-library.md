---
title: Biblioteca JavaScript de privacidade
description: Saiba como usar ferramentas personalizadas para acessar e excluir informações pessoais do cliente coletadas pelo Adobe Commerce.
exl-id: bcfea656-2cf0-48ae-9049-d91679166d05
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Biblioteca JavaScript de privacidade

A Biblioteca JavaScript de privacidade é um conjunto de ferramentas que ajudam a criar um processo para acessar e excluir dados privados coletados pela Adobe Commerce.

Os serviços de rastreamento de dados da Commerce podem armazenar informações privadas aplicáveis a regulamentos de privacidade, como o [Regulamento Geral sobre a Proteção de Dados (GDPR)](gdpr.md) e [Lei de Privacidade do Consumidor da Califórnia (CCPA)](ccpa.md).

Essa biblioteca fornece um conjunto de funções para criar solicitações de dados de privacidade e coletar suas respostas. Use essa biblioteca para recuperar e remover os dados armazenados no navegador pelos serviços de rastreamento de dados da Adobe Commerce.

>[!NOTE]
>
>Se [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver ativado, a Commerce não coletará dados comportamentais até que o comprador dê o seu consentimento. Se [!UICONTROL **Modo de restrição de cookies**] estiver desativado, o Commerce coletará dados comportamentais por padrão.

## Instalação

A Biblioteca JavaScript de privacidade está disponível no seguinte local CDN: `commerce.adobe.net/magentoprivacy.js`

Após ter o arquivo, será necessário adicioná-lo a um módulo personalizado ou tema instalado em sua instância do Adobe Commerce ou Magento Open Source. Siga as instruções descritas em [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) tópico para realizar esta tarefa.

### Inicialização

Importar e instanciar um novo `MagentoPrivacy` objeto ou use o `window` para acessar as funções de privacidade do JavaScript.

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
: retorna uma promessa JavaScript para um objeto de identidade de um serviço no navegador.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: remove os dados de identidade de um serviço no navegador.
Esta função retorna uma promessa JavaScript para um objeto de identidade com uma `isDeleted` propriedade booleana para indicar se os dados foram excluídos.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
