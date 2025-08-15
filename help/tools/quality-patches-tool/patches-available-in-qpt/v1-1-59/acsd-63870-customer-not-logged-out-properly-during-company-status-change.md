---
title: 'ACSD-63870: O cliente não efetuou logout corretamente durante a alteração do status da empresa'
description: Aplique o patch ACSD-63870 para corrigir o problema do Adobe Commerce em que um cliente da empresa não é desconectado corretamente quando o status da empresa é alterado durante uma sessão ativa do cliente.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870: O cliente não efetuou logout corretamente durante a alteração do status da empresa

O patch ACSD-63870 resolve o problema em que um cliente da empresa não é desconectado corretamente quando o status da empresa é alterado durante uma sessão ativa do cliente. Este patch está disponível quando o [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 está instalado. A ID do patch é ACSD-63870. Observe que o problema está programado para ser corrigido no Adobe Commerce 2.4.8.

## Produtos e versões afetados

**O patch foi criado para a versão do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4-p6

**Compatível com as versões do Adobe Commerce:**

* Adobe Commerce (todos os métodos de implantação) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>O patch pode se tornar aplicável a outras versões com as novas versões do [!DNL Quality Patches Tool]. Para verificar se o patch é compatível com a sua versão do Adobe Commerce, atualize o pacote `magento/quality-patches` para a versão mais recente e verifique a compatibilidade na [[!DNL Quality Patches Tool]: página Procurar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=pt-BR). Use a ID do patch como palavra-chave de pesquisa para localizar o patch.

## Problema

Falha de logout do cliente quando o status da empresa é alterado durante uma sessão de cliente ativa.

<u>Etapas a serem reproduzidas</u>:

1. Ativar funcionalidade B2B.
1. Crie um produto simples.
1. Crie uma nova empresa e marque-a como *Ativa*.
1. Faça logon como o usuário da empresa e adicione um produto ao carrinho.
1. Continue com o check-out até a etapa [!UICONTROL Shipping Address]. Não insira o endereço.
1. Vá para o administrador e altere o status da empresa para *Aprovação pendente*.
1. Volte para o front-end e preencha o endereço de envio.

<u>Resultados esperados</u>:

O cliente foi desconectado.

<u>Resultados reais</u>:

* Os usuários recebem o erro *Algo deu errado*.
* `var/log/exception.log` contém:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Aplicar o patch

Para aplicar patches individuais, use os links a seguir, dependendo do método de implantação:

* Adobe Commerce ou Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) no guia [!DNL Quality Patches Tool].
* Adobe Commerce na infraestrutura em nuvem: [Atualizações e patches > Aplicar patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=pt-BR) no guia do Commerce na infraestrutura em nuvem.

## Etapas adicionais necessárias após a instalação do patch

(Esta seção é opcional; pode haver algumas etapas necessárias após a aplicação do patch para corrigir o problema.) 

## Leitura relacionada

Para saber mais sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: uma ferramenta de autoatendimento para patches de qualidade](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) no guia Ferramentas.
