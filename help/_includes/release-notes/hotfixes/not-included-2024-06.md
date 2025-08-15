---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---
# Correções não incluídas nos patches de segurança de junho de 2024

>[!IMPORTANT]
>
>Esta é uma atualização urgente para nossa última comunicação sobre o [CVE-2024-34102](https://nvd.nist.gov/vuln/detail/CVE-2024-34102). A Adobe está ciente de que o CVE-2024-34102 foi explorado na natureza em ataques muito limitados direcionados aos comerciantes do Adobe Commerce. Tome medidas imediatas para resolver a vulnerabilidade, se ainda não tiver feito isso.

**Para clientes que não aplicaram o patch de segurança lançado em 11 de junho de 2024 ou o patch isolado lançado em 28 de junho de 2024:**

Opção 1:

1. Aplique um dos patches de segurança lançados em 11 de junho de 2024:

   * [2.4.7-p1](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/notes/security-patches/2-4-7-patches#adobe-commerce-247-p1)

   * [2.4.6-p6](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/notes/security-patches/2-4-6-patches#adobe-commerce-246-p6)

   * [2.4.5-p8](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/notes/security-patches/2-4-5-patches#adobe-commerce-245-p8)

   * [2.4.4-p9](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/notes/security-patches/2-4-4-patches#adobe-commerce-244-p9)

1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) lançado em 17 de julho de 2024.

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

Opção 2:

1. Aplicar o [patch isolado](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102).

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

**Para clientes que já aplicaram um patch de segurança lançado em 11 de junho de 2024 ou o patch isolado lançado em 28 de junho de 2024:**

1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) lançado em 17 de julho de 2024.

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

**Para clientes que já tenham 1) aplicado um patch de segurança lançado em 11 de junho de 2024 ou 2) o patch isolado lançado em 28 de junho de 2024 e 3) girado suas chaves de criptografia:**
 
1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) lançado em 17 de julho de 2024.
