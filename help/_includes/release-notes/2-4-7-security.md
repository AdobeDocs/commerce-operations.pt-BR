---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 aprimoramentos de segurança

* **Suporte para SRI (Integridade de Sub-Recursos) adicionado** para atender aos requisitos da PCI 4.0 para verificação de integridade de script em páginas de pagamento. O suporte à Integridade de sub-recursos (SRI) fornece hashes de integridade para todos os ativos do JavaScript que residem no sistema de arquivos local. O recurso SRI padrão é implementado apenas nas páginas de pagamento para as áreas de Administração e vitrine eletrônica. No entanto, os comerciantes podem estender a configuração padrão para outras páginas. Consulte [Integridade de sub-recursos](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) no _Guia do Desenvolvedor do Commerce PHP_.<!--AC-1153-->

* **Alterações na Política de Segurança de Conteúdo (CSP)**—Atualizações e aprimoramentos de configuração nas Políticas de Segurança de Conteúdo (CSPs) da Adobe Commerce para atender aos requisitos da PCI 4.0. Para obter detalhes, consulte [Políticas de Segurança de Conteúdo](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) no _Guia do Desenvolvedor do Commerce PHP_. <!--AC-11513-->

   * A configuração padrão da CSP para páginas de pagamento para o Administrador do Commerce e áreas de vitrine agora é o modo `restrict`. Para todas as outras páginas, a configuração padrão é o modo `report-only`.  Nas versões anteriores à 2.4.7, o CSP foi configurado no modo `report-only` para todas as páginas.

   * Adição de um provedor nonce para permitir a execução de scripts integrados em uma CSP. O provedor nonce facilita a geração de cadeias de caracteres nonce exclusivas para cada solicitação. As cadeias de caracteres são anexadas ao cabeçalho da CSP.

   * Adição de opções para configurar URIs personalizados para relatar violações de CSP para a página Criar pedido no Admin e a página Check-out na loja. Você pode adicionar a configuração do Administrador ou adicionando o URI ao arquivo `config.xml`.

     >[!NOTE]
     >
     >Atualizar a configuração da CSP para o modo `restrict` pode bloquear scripts incorporados existentes nas páginas de pagamento na Administração e na loja, o que causa o seguinte erro do navegador quando uma página é carregada: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Corrija esses erros atualizando a configuração da lista de permissões para permitir os scripts necessários. Consulte [Solução de problemas](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) no _Guia do Desenvolvedor do Commerce PHP_.
