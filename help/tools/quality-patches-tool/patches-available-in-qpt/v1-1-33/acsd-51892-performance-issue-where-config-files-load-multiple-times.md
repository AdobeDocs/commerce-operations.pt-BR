---
title: 'ACSD-51892: problema de desempenho em que os arquivos de configuração são carregados várias vezes'
description: Aplique o patch ACSD-51892 para corrigir o problema de desempenho do Adobe Commerce em que os arquivos de configuração são carregados várias vezes durante a implantação.
feature: Observability
role: Admin
exl-id: ef3d3b85-b6a0-4037-95c0-e84125fa9088
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51892: problema de desempenho em que os arquivos de configuração são carregados várias vezes

O patch ACSD-51892 corrige o problema de desempenho que surge do carregamento dos arquivos `app/etc/env.php` e `app/etc/config.php` sempre que os valores de configuração de implantação são acessados em uma única solicitação. A leitura excessiva de arquivos sobrecarrega o sistema, levando a uma deterioração no desempenho geral. Este patch está disponível quando o [!DNL Quality Patches Tool (QPT)] 1.1.33 está instalado. A ID do patch é ACSD-51892. Observe que o problema foi corrigido no Adobe Commerce 2.4.6-p2.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Há um problema de desempenho em que os arquivos de configuração são carregados várias vezes.

<u>Etapas a serem reproduzidas</u>:

1. Realizar implantação ou atualização para o Adobe Commerce 2.4.6 ou posterior.
1. Verifique os logs do sistema de arquivos para obter acesso aos arquivos `app/etc/env.php` e `app/etc/config.php` enquanto a implantação estiver em execução.

<u>Resultados esperados</u>:

A implantação foi bem-sucedida no período regular.

<u>Resultados reais</u>:

* Os servidores estão se esforçando para responder a todos os comandos inseridos. Isso resulta em *Tempo limite do primeiro byte do Erro 503* ao acessar o site.
* Há várias entradas nos arquivos de log com acesso a `app/etc/env.php` e `app/etc/config.php` arquivos.

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] lançamento: uma nova ferramenta para autoatender patches de qualidade](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) na base de dados de conhecimento de suporte.
* [Verifique se há patch disponível para o problema do Adobe Commerce usando o  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) no guia [!UICONTROL Quality Patches Tool].


Para obter informações sobre outros patches disponíveis no QPT, consulte [[!DNL Quality Patches Tool]: Pesquisar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR) no guia [!DNL Quality Patches Tool].
