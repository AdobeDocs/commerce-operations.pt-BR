---
title: 'ACSD-63244: Resolva problemas do JavaScript do painel de administração, incluindo  [!DNL Google Maps] renderização e erros do console'
description: O patch ACSD-63244 corrige os vários problemas do JavaScript no painel de administração, incluindo problemas com a renderização  [!DNL Google Maps]  e o erro de tipo não detectado recorrente._each não é um erro de função&grave; no console do navegador.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
source-git-commit: 6b623811440238deee7a7fe859d887830f89782c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244: Resolva os problemas do JavaScript do painel de administração, incluindo a renderização de [!DNL Google Maps] e erros do console

O patch ACSD-63244 corrige os vários problemas do JavaScript no painel de administração, incluindo problemas com a renderização de [!DNL Google Maps] e erros recorrentes de `Uncaught TypeError: this._each is not a function` no console do navegador. Este patch está disponível com o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. A ID do patch é ACSD-63244. Observe que o problema foi agendado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

* O erro `Uncaught TypeError: this._each is not a function` aparece no console do navegador, interrompendo a funcionalidade da interface do usuário do Administrador.
* O erro do JavaScript impede que [!DNL Google Maps] seja renderizado corretamente.

<u>Etapas a serem reproduzidas</u>:

1. Carregue a interface do administrador do Adobe Commerce.
1. Abra o console do navegador e execute o seguinte script:

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Resultados esperados</u>:

As funções do JavaScript disponíveis na biblioteca JS padrão são executadas corretamente sem erros.

<u>Resultados reais</u>:

Os erros do JavaScript são exibidos no console do navegador:

```
Uncaught TypeError: this._each is not a function
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
