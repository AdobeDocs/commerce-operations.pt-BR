---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 aprimoramentos de segurança

* **Adição de suporte à Integridade de sub-recursos (SRI)** para atender aos requisitos da PCI 4.0 para a verificação da integridade do script nas páginas de pagamento. O suporte à Integridade de sub-recursos (SRI) fornece hashes de integridade para todos os ativos JavaScript que residem no sistema de arquivos local. O recurso SRI padrão é implementado apenas nas páginas de pagamento para as áreas de Administração e vitrine eletrônica. No entanto, os comerciantes podem estender a configuração padrão para outras páginas. Consulte [Integridade de sub-recursos](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) no _Guia do desenvolvedor do Commerce PHP_.<!--AC-1153-->

* **Alterações na Política de segurança de conteúdo (CSP)**— atualiza çõ es e aprimora çõ es de configura çã o para as CSPs (Content Security Policies, políticas de seguran ç a de conte ú do) da Adobe Commerce para atender aos requisitos do PCI 4.0. Para obter detalhes, consulte [Políticas de segurança de conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Guia do desenvolvedor do Commerce PHP_. <!--AC-11513-->

   * A configuração padrão da CSP para páginas de pagamento para o Administrador do Commerce e áreas de vitrine agora é `restrict` modo. Para todas as outras páginas, a configuração padrão é `report-only` modo.  Em versões anteriores à 2.4.7, o CSP foi configurado no `report-only` para todas as páginas.

   * Adição de um provedor nonce para permitir a execução de scripts integrados em uma CSP. O provedor nonce facilita a geração de cadeias de caracteres nonce exclusivas para cada solicitação. As cadeias de caracteres são anexadas ao cabeçalho da CSP.

   * Adição de opções para configurar URIs personalizados para relatar violações de CSP para a página Criar pedido no Admin e a página Check-out na loja. Você pode adicionar a configuração do Administrador ou adicionando o URI à `config.xml` arquivo.

     >[!NOTE]
     >
     >Atualização da configuração da CSP para `restrict` O pode bloquear scripts incorporados existentes nas páginas de pagamento na Administração e na loja, o que causa o seguinte erro do navegador quando uma página é carregada: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrija esses erros atualizando a configuração da lista de permissões para permitir os scripts necessários. Consulte [Solução de problemas](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) no _Guia do desenvolvedor do Commerce PHP_.
