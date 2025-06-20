---
title: 'MDVA-41236: Não é possível criar atualizações novas ou editar atualizações agendadas existentes para o produto'
description: O patch MDVA-41236 corrige o problema em que os usuários não conseguem criar novas atualizações ou editar atualizações programadas existentes para o produto se a "Data final" tiver sido removida anteriormente. Este patch está disponível quando a [Ferramenta de correções de qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-41236. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236: Não é possível criar atualizações novas ou editar atualizações agendadas existentes para o produto

O patch MDVA-41236 corrige o problema em que os usuários não conseguem criar novas atualizações ou editar atualizações programadas existentes para o produto se a &quot;Data final&quot; tiver sido removida anteriormente. Este patch está disponível quando a [Ferramenta de Patches de Qualidade (QPT)](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 está instalada. A ID do patch é MDVA-41236. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.5.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.2

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões da Ferramenta de patches de qualidade. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Os usuários não poderão criar novas programações ou editar as existentes para produtos se a &quot;Data final&quot; tiver sido removida anteriormente.

<u>Etapas a serem reproduzidas</u>:

1. Crie um produto com o Status definido como *disable*.
1. Adicione uma atualização agendada para habilitar este produto.
   * Adicionar datas de início e término futuras.
1. Edite a atualização agendada removendo a **Data Final**.
1. Edite o agendamento novamente e tente adicionar uma **Data Final**. Ocorrerá um erro.
1. Atualize a página e vá novamente para **Editar Atualização Agendada**.
1. Clique em **Remover da atualização** > **Excluir a atualização**.
1. Agora, você não deve ver a atualização agendada na parte superior da página de edição do produto.
1. Tente criar uma nova atualização agendada que se sobreponha à duração anterior.

<u>Resultados esperados</u>:

* Não há erro na etapa 4. O administrador pode atualizar a atualização agendada sem qualquer erro, pois o agendamento ainda não está ativo.
* O usuário administrador pode excluir a atualização anterior e criar uma nova.

<u>Resultados reais</u>:

Os usuários recebem a seguinte mensagem de erro:

*erro: a atualização futura já existe neste intervalo de tempo. Defina um intervalo diferente e tente novamente.*


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre a Ferramenta de correção de qualidade, consulte:

* [Ferramenta de correções de qualidade lançada: uma nova ferramenta para autoatender correções de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há um patch disponível para o problema do Adobe Commerce usando a Ferramenta de Patches de Qualidade](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!DNL Quality Patches Tool].

Para obter informações sobre outros patches disponíveis no QPT, consulte a seção [Patches disponíveis no QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR).
