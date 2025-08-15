---
title: 'ACSD-61622: [!DNL FedEx] taxas específicas de conta ausentes na resposta da API REST'
description: Aplique o patch ACSD-61622 para corrigir o problema do Adobe Commerce em que  [!DNL FedEx] taxas específicas da conta estão ausentes da resposta da API REST.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: [!DNL FedEx] taxas específicas da conta estão ausentes na resposta da API REST

O patch ACSD-61622 resolve o problema em que [!DNL FedEx's] taxas específicas da conta estão ausentes da resposta da API REST. Ele adiciona o tipo de solicitação de taxa `ACCOUNT` à solicitação da API REST enviada do Adobe Commerce para [!DNL FedEx], que retorna uma resposta semelhante à resposta da API SOAP. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 está instalado. A ID do patch é ACSD-61622. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p5

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

[!DNL FedEx's] taxas específicas da conta estão ausentes na resposta da API REST.

<u>Etapas a serem reproduzidas</u>:

1. Instale uma instância limpa do Adobe Commerce.
1. Crie um produto simples com peso de 5 lb.
1. Configurar [!DNL FedEx] para API REST.
1. Habilite o método de envio [!DNL FedEx] e limpe o cache.
1. Iniciar observação do arquivo de log: `var/log/shipping.log`
1. Adicione um produto simples ao carrinho e vá para a página de remessa no check-out. Exemplo de dados do cliente:

   * Código postal: 58601
   * Names: John Doe
   * Endereço: 196 Eulalia Burg
   * País: US
   * Estado: Dakota do Norte
   * Telefone: 187-563-3627

<u>Resultados esperados</u>:

`PAYOR_ACCOUNT_PACKAGE` taxas estão disponíveis na resposta da API REST, de modo semelhante às respostas da API do SOAP.

<u>Resultados reais</u>:

Somente `PAYOR_LIST_PACKAGE` taxas estão disponíveis na resposta, o que significa que não há taxas negociadas (conta) de [!DNL FedEx].

## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) no guia do Commerce na infraestrutura em nuvem.

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
