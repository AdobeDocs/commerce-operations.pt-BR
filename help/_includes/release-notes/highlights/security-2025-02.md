---
source-git-commit: 6ca34e8713f4f138961786de206cd360f0bc1be7
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---
# Destaques da correção de segurança de fevereiro de 2025

Esta versão inclui os seguintes destaques:

* **Gerenciando chaves de criptografia e criptografando dados novamente**—O gerenciamento de chaves de criptografia foi reprojetado para melhorar a usabilidade e eliminar bugs e limitações anteriores.<!-- AC-12679 -->

  Novos comandos CLI agora estão disponíveis para [alterar](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) chaves e [criptografar novamente](https://developer.adobe.com/commerce/php/development/security/data-encryption/) determinadas configurações do sistema, pagamento e dados de campos personalizados. Não há mais suporte para a alteração de chaves na interface do Administrador nesta versão. Você deve usar os comandos da CLI.

* **Correção para [CVE-2025-24434](https://nvd.nist.gov/vuln/detail/CVE-2025-24434)**—Resolve uma vulnerabilidade de autorização.

  Essa correção também está disponível como um patch isolado. Consulte o [artigo da Base de Dados de Conhecimento](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-08) para obter detalhes.<!-- AC-12755 -->

* **Downgrade de versão do TinyMCE**—A dependência do TinyMCE foi rebaixada da versão 7 para a 6.8.5 para resolver problemas de compatibilidade de licenciamento.

  Essa alteração garante a conformidade contínua enquanto a Adobe avalia um editor alternativo de código aberto do WYSIWYG.
