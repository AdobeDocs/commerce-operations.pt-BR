---
title: 'ACSD-57570: correção para acesso restrito de usuário administrador a catálogos compartilhados'
description: Aplique o patch ACSD-57570 para corrigir o problema do Adobe Commerce em que um usuário administrador restrito com acesso a uma loja específica não consegue visualizar de forma consistente todos os catálogos compartilhados atribuídos aos produtos ou salvar informações do cliente, resultando em inconsistências no sistema.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570: correção para acesso restrito de usuário administrador a catálogos compartilhados

O patch ACSD-57570 corrige o problema em que um usuário administrador restrito com acesso a uma loja específica não consegue visualizar de forma consistente todos os catálogos compartilhados atribuídos a produtos ou salvar informações do cliente, resultando em inconsistências no sistema. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-57570. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.5.0.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p3

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Um usuário administrador restrito com acesso a uma loja específica nem sempre pode ver todos os catálogos compartilhados ou salvar clientes, gerando inconsistências. Com várias lojas, o administrador restrito não pode ver novas empresas ou catálogos compartilhados personalizados.

<u>Etapas a serem reproduzidas</u>:

1. Configurar armazenamentos na seguinte ordem:
   * Crie um novo site chamado W2.
   * Criar uma nova exibição de loja para o site padrão.
   * Crie uma nova loja chamada W2S2 para o site W2.
   * Crie uma nova visualização de loja chamada W2S2SV1 para a loja W2S2.
   * Crie outra nova visualização de loja chamada W2S2SV2 para a loja W2S2.
   * Crie uma empresa para o W2.
1. Atribuir produtos:
   * Atribua alguns produtos somente ao W1.
   * Atribua alguns produtos somente ao W2.
   * Atribua alguns produtos à W1 e à W2.
1. Crie um catálogo compartilhado personalizado e atribua todos os produtos a ele.
1. Crie uma função de administrador personalizada com acesso somente a **W2S2**, não a **W2**.
1. Atribua o usuário administrador restrito à nova função de administrador personalizada.
1. Faça logon como o usuário administrador restrito.
1. Verificar acesso:
   * Verifique quais empresas você pode ver.
   * Verifique quais catálogos compartilhados você pode ver.
   * Abra a lista de produtos e verifique se é possível visualizar todos os catálogos compartilhados aos quais os produtos estão atribuídos.

<u>Resultados esperados</u>:

O comportamento deve ser consistente.

<u>Resultados reais</u>:

Se você criar apenas uma visualização adicional de site, loja e loja, o usuário administrador restrito poderá ver a empresa, o catálogo compartilhado e ambos os catálogos compartilhados na lista de produtos. Com a configuração acima, o administrador restrito não pode ver a nova empresa ou o catálogo compartilhado personalizado e somente o catálogo compartilhado padrão é exibido na lista de produtos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
