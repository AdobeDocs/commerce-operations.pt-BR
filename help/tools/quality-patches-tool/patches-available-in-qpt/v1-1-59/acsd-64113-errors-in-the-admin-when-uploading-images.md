---
title: 'ACSD-64113: Erro no administrador ao carregar imagem com largura menor do que altura via [!DNL Media Gallery]'
description: Aplique o patch ACSD-64113 para corrigir o problema do Adobe Commerce em que erros ocorrem no administrador ao carregar imagens com uma largura relativamente pequena em comparação à sua altura (ou vice-versa) por meio do  [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: Erro no administrador ao carregar imagem com largura menor do que altura via [!DNL Media Gallery]

O patch ACSD-64113 corrige o problema em que erros ocorrem no administrador ao carregar imagens com uma largura relativamente pequena em comparação à sua altura (ou vice-versa) por meio do [!DNL Media Gallery]. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-64113. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.7-p3

**Compatível com as versões do Adobe Commerce:**

Adobe Commerce (todos os métodos de implantação) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Erros ocorrem no administrador ao carregar imagens com uma largura relativamente pequena em comparação à sua altura (ou vice-versa) por meio do [!DNL Media Gallery].

<u>Etapas a serem reproduzidas</u>:

1. Vá para **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** e selecione o diretório **[!UICONTROL wysiwyg]**.
1. Carregue a imagem com uma largura relativamente pequena em comparação à sua altura (ou vice-versa).

<u>Resultados esperados</u>:

A imagem é carregada sem erros.

<u>Resultados reais</u>:

1. A seguinte mensagem de erro é emitida:

   *Um problema técnico com o servidor criou um erro. Tente novamente para continuar o que estava fazendo. Se o problema persistir, tente novamente mais tarde.*
1. `var/log/exception.log` contém:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   ou

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.


## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
