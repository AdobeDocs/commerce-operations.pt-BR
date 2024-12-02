---
title: 'ACSD-62485: o consumidor "async.operations.all" para de funcionar quando a empresa é criada'
description: Aplique o patch ACSD-62485 para corrigir o problema do Adobe Commerce em que o consumidor "async.operations.all" para de funcionar quando uma empresa B2B é criada.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
source-git-commit: 9d0925ae06c3ccf9ed6b2d89cec07f8f5fe2f94f
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: o consumidor `async.operations.all` para de funcionar quando a empresa é criada

O patch ACSD-62485 corrige o problema em que o consumidor `async.operations.all` para de funcionar quando uma empresa B2B é criada. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 está instalado. A ID do patch é ACSD-62485. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p7

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

O consumidor `async.operations.all` para de processar mensagens se uma empresa B2B for criada de forma assíncrona enquanto o consumidor ainda estiver em execução.

<u>Pré-requisitos</u>:

Os módulos B2B são instalados e ativados.

<u>Etapas a serem reproduzidas</u>:

1. Crie dois clientes.
1. Envie uma solicitação REST em massa para criar duas empresas, atribuindo os clientes criados como administradores de empresas.
1. Inicie o consumidor usando o seguinte comando:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u>Resultados esperados</u>:

O consumidor processa 20.000 mensagens e termina com sucesso.

<u>Resultados reais</u>:

O consumidor pára de trabalhar imediatamente após a execução.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source no local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
