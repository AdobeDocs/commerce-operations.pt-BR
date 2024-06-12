---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 aprimoramentos de segurança

Nenhum ataque confirmado relacionado a esses problemas ocorreu até o momento. No entanto, certas vulnerabilidades podem ser potencialmente exploradas para acessar informações do cliente ou assumir o controle de sessões de administrador. A maioria desses problemas exige que um invasor obtenha acesso ao Administrador primeiro. Como resultado, lembramos você de tomar todas as medidas necessárias para proteger seu administrador, incluindo, mas não limitado a, estes esforços:

* IP ➡ incluir na lista de permissões
* [Autenticação de dois fatores](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Uso de uma VPN
* Uso de um local único em vez de `/admin`
* Boa higiene de senha

Os aprimoramentos de segurança desta versão melhoram a conformidade com as práticas recomendadas de segurança mais recentes.

* **Alterações no comportamento de chaves de cache não geradas**:

   * As chaves de cache não geradas para blocos agora incluem prefixos que diferem dos prefixos para chaves geradas automaticamente. (As chaves de cache não geradas são chaves definidas por meio da sintaxe de diretiva de modelo ou do `setCacheKey` ou `setData` métodos.)
   * As chaves de cache não geradas para blocos agora devem conter apenas letras, dígitos, hifens (-) e caracteres de sublinhado (_).  <!-- AC-9831 -->

* **Limitações no número de códigos de cupom gerados automaticamente**. O Commerce agora limita o número de códigos de cupom gerados automaticamente. O máximo padrão é 250.000. Os comerciantes podem usar o novo **[!UICONTROL Code Quantity Limit]** opção de configuração (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para evitar que o sistema fique sobrecarregado com muitos cupons. <!-- AC-8753 -->

* **Otimização do processo padrão de geração de URL de administrador**. A geração do URL de administrador padrão é otimizada para aumentar a aleatoriedade, o que torna os URLs gerados menos previsíveis. <!-- AC-9028 -->

* **Adição de suporte à Integridade de sub-recursos (SRI)** para atender aos requisitos da PCI 4.0 para a verificação da integridade do script nas páginas de pagamento. O suporte à Integridade de sub-recursos (SRI) fornece hashes de integridade para todos os ativos JavaScript que residem no sistema de arquivos local. O recurso SRI padrão é implementado apenas nas páginas de pagamento para as áreas de Administração e vitrine eletrônica. No entanto, os comerciantes podem estender a configuração padrão para outras páginas. Consulte [Integridade de sub-recursos](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) no _Guia do desenvolvedor do Commerce PHP_.<!--AC-1153-->

* **Alterações na Política de segurança de conteúdo (CSP)**— atualiza çõ es e aprimora çõ es de configura çã o para as CSPs (Content Security Policies, políticas de seguran ç a de conte ú do) da Adobe Commerce para atender aos requisitos do PCI 4.0. Para obter detalhes, consulte [Políticas de segurança de conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Guia do desenvolvedor do Commerce PHP_. <!--AC-11513-->

   * A configuração padrão da CSP para páginas de pagamento para o Administrador do Commerce e áreas de vitrine agora é `restrict` modo. Para todas as outras páginas, a configuração padrão é `report-only` modo.  Em versões anteriores à 2.4.7, o CSP foi configurado no `report-only` para todas as páginas.

   * Adição de um provedor nonce para permitir a execução de scripts integrados em uma CSP. O provedor nonce facilita a geração de cadeias de caracteres nonce exclusivas para cada solicitação. As cadeias de caracteres são anexadas ao cabeçalho da CSP.

   * Adição de opções para configurar URIs personalizados para relatar violações de CSP para a página Criar pedido no Admin e a página Check-out na loja. Você pode adicionar a configuração do Administrador ou adicionando o URI à `config.xml` arquivo.

     >[!NOTE]
     >
     >Atualização da configuração da CSP para `restrict` O pode bloquear scripts incorporados existentes nas páginas de pagamento na Administração e na loja, o que causa o seguinte erro do navegador quando uma página é carregada: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrija esses erros atualizando a configuração da lista de permissões para permitir os scripts necessários. Consulte [Solução de problemas](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) no _Guia do desenvolvedor do Commerce PHP_.

* Uma nova definição de configuração de cache de página inteira pode ajudar a reduzir os riscos associados ao HTTP `{BASE-URL}/page_cache/block/esi` terminal. Esse endpoint oferece suporte a fragmentos de conteúdo irrestritos e carregados dinamicamente de manipuladores de layout e estruturas de bloco do Commerce. O novo **[!UICONTROL Handles params size]** definição de configuração define o valor desse parâmetro de `handles` que determina o número máximo permitido de identificadores por API. O valor padrão dessa propriedade é 100. Os comerciantes podem alterar esse valor do campo Administração (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Consulte [Configurar o aplicativo do Commerce para usar o verniz](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Limitação de taxa nativa para informações de pagamento transmitidas por meio de REST e APIs do GraphQL**. Os comerciantes agora podem [configurar limitação de taxa](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) para as informações de pagamento transmitidas usando REST e GraphQL. Essa camada adicional de proteção suporta a prevenção de ataques de cartões e potencialmente diminui o volume de ataques de cartões que testam muitos números de cartão de crédito de uma só vez. Essa é uma alteração no comportamento padrão de um endpoint REST existente. Consulte [Limitação de taxa](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* O comportamento padrão do [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) A consulta do GraphQL e o ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) O endpoint REST foi alterado. Por padrão, agora as APIs sempre retornam `true`. Os comerciantes podem habilitar o comportamento original definindo o *[Ativar o login de check-out de convidado](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* na opção Admin para `yes`, mas isso pode expor as informações do cliente a usuários não autenticados.
