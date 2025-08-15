---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Destaques da correção de segurança de agosto de 2024

Esta versão inclui os seguintes destaques:

* **Limitação de taxa para[!DNL one-time passwords]**—As novas opções de configuração do sistema a seguir estão disponíveis para habilitar a limitação de taxa na validação [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]:

   * [!UICONTROL **Limite de novas tentativas para Autenticação de Dois Fatores**]
   * [!UICONTROL **Tempo de bloqueio da Autenticação de Dois Fatores (segundos)**]

  A Adobe aconselha definir um limite para a validação OTP 2FA para limitar o número de tentativas de mitigação de ataques de força bruta. Consulte [Segurança > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) no _Guia de Referência de Configuração_ para obter mais informações. <!-- AC-12095 -->

* **Rotação de chave de criptografia**—Um novo comando da CLI agora está disponível para alterar sua chave de criptografia. Consulte o artigo da Base de Dados de Conhecimento [Solução de Problemas de Rotação de Chaves de Criptografia: CVE-2024-34102](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102) para obter detalhes.

* **Correção para [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**—Resolve uma vulnerabilidade de segurança [!DNL Prototype.js].<!-- AC-11936 -->

* **Correção para [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**—Resolve uma vulnerabilidade de segurança na execução remota de código. Essa vulnerabilidade afeta os comerciantes que usam o servidor Web Apache para implantações locais ou auto-hospedadas. Essa correção também está disponível como um patch isolado. Consulte o artigo [Atualização de segurança disponível para o Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61) Knowledge Base para obter detalhes.<!-- ACSD-60551 -->
