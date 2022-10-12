---
title: Biblioteca JavaScript de privacidade
description: Saiba como usar ferramentas personalizadas para acessar e excluir informações pessoais do cliente coletadas pelo Adobe Commerce e Magento Open Source.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---


<!-- TODO: Remove this topic and redirect to the adobe-privacy-javascript-library.md when the Adobe privacy library has been integrated with Commerce. -->

# Biblioteca JavaScript de privacidade

A Biblioteca JavaScript de privacidade é um conjunto de ferramentas que ajuda a criar um processo para acessar e excluir dados privados coletados pelo Adobe Commerce e Magento Open Source.

Os serviços de rastreamento de dados de comércio podem armazenar informações privadas aplicáveis a regulamentos de privacidade, como o [Regulamento Geral sobre a Proteção de Dados (GDPR)](gdpr.md) e [Lei de Privacidade do Consumidor da Califórnia (CCPA)](ccpa.md).

Essa biblioteca fornece um conjunto de funções para criar solicitações de dados de privacidade e coletar suas respostas. Use essa biblioteca para recuperar e remover os dados armazenados no navegador pelos serviços de rastreamento de dados Adobe Commerce e Magento Open Source.

>[!NOTE]
>
>If [Modo de restrição de cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, o Commerce não coletará dados comportamentais até que o comprador aceite. If [!UICONTROL **Modo de restrição de cookie**] estiver desativado, o Commerce coletará dados comportamentais por padrão.

## Instalação

A Biblioteca JavaScript de privacidade está disponível no seguinte local CDN: `commerce.adobe.net/magentoprivacy.js`

Depois de ter o arquivo, será necessário adicioná-lo a um módulo personalizado ou tema instalado na sua instância do Adobe Commerce ou Magento Open Source. Siga as instruções descritas em [Usar JavaScript personalizado](https://developer.adobe.com/commerce/frontend-core/javascript/custom/) para realizar essa tarefa.

### Inicialização

Importe e instancie um novo `MagentoPrivacy` ou use o `window` para acessar as funções do JavaScript de privacidade.

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

A Biblioteca JS de privacidade fornece várias funções para gerenciar os dados de identidade armazenados no navegador.

`retrieveIdentity()`
: Retorna uma promessa de JavaScript para um objeto de identidade de um serviço no navegador.

```js
magePriv.retrieveIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3"}
```

`removeIdentity()`
: Remove os dados de identidade de um serviço no navegador.
Essa função retorna uma promessa de JavaScript para um objeto de identidade com um `isDeleted` propriedade booleana para indicar se os dados foram excluídos.

```js
magePriv.removeIdentity().then((ids)=>console.log(ids))
// {"value":"1ccfd8c2-5159-433c-98d7-e937ce3b13f3","isDeleted":true}
```
