---
title: 'ACSD-63139: falha na exportação do produto quando os atributos do produto contêm milhares de valores de opção'
description: Aplique o patch ACSD-63139 para corrigir o problema do Adobe Commerce em que a exportação de produtos falha quando os atributos do produto contêm milhares de valores de opção.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 57970acb07948f0792856e5f60df6c297a26780a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# ACSD-63139: falha na exportação do produto quando os atributos do produto contêm milhares de valores de opção

O patch ACSD-63139 corrige o problema em que a exportação de produtos falha quando os atributos do produto contêm milhares de valores de opção. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 está instalado. A ID do patch é ACSD-63139. Observe que esse problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p8

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

A exportação de produtos falha quando os atributos de produto contêm milhares de valores de opção.

<u>Etapas a serem reproduzidas</u>:

1. Instale o Adobe Commerce com o módulo B2B.
1. Importar um dump de banco de dados grande com:
   - ~7.000 produtos
   - ~450 atributos de produto
   - Alguns atributos com mais de 100 opções
1. Execute o seguinte comando para instalar o cron (se ainda não estiver instalado):

   ```
   bin/magento cron:install
   ```

1. Configure o [!DNL RabbitMQ] seguindo as instruções em [[!DNL RabbitMQ] pré-requisitos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/rabbitmq).
1. Abra o arquivo `php.ini`, defina o limite de memória como 4G e reinicie o serviço PHP.
1. No Painel de Administração, vá para **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**.
1. Na seção *[!UICONTROL Export Settings]*, defina **[!UICONTROL Entity Type]** como *Produtos*, role até a parte inferior e clique em **[!UICONTROL Continue]**.
1. Execute o seguinte comando para iniciar o processador de exportação:

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Resultados esperados</u>:

A exportação do produto deve ser concluída com êxito.

<u>Resultados reais</u>:

O processo de exportação de produtos falha e retorna o seguinte erro fatal:

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
