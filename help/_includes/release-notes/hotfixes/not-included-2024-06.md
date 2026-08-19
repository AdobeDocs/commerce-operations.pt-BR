---
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---
# Correções não incluídas nos patches de segurança de junho de 2024

>[!IMPORTANT]
>
>Esta é uma atualização urgente para nossa última comunicação sobre o [CVE-2024-34102](https://nvd.nist.gov/vuln/detail/CVE-2024-34102). A Adobe está ciente de que o CVE-2024-34102 foi explorado na natureza em ataques muito limitados direcionados aos comerciantes do Adobe Commerce. Tome medidas imediatas para resolver a vulnerabilidade, se ainda não tiver feito isso.

**Para clientes que não aplicaram o patch de segurança lançado em 11 de junho de 2024 ou o patch isolado lançado em 28 de junho de 2024:**

Opção 1:

1. Aplique um dos patches de segurança lançados em 11 de junho de 2024:

   * [2.4.7-p1](/help/release/release-notes/security/2-4-7-patches.md#adobe-commerce-247-p1)

   * [2.4.6-p6](/help/release/release-notes/security/2-4-6-patches.md#adobe-commerce-246-p6)

   * [2.4.5-p8](/help/release/release-notes/security/2-4-5-patches.md#adobe-commerce-245-p8)

   * [2.4.4-p9](/help/release/release-notes/security/2-4-4-patches.md#adobe-commerce-244-p9)

1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27136) lançado em 17 de julho de 2024.

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

Opção 2:

1. Aplicar o [patch isolado](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27136).

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

**Para clientes que já aplicaram um patch de segurança lançado em 11 de junho de 2024 ou o patch isolado lançado em 28 de junho de 2024:**

1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27136) lançado em 17 de julho de 2024.

1. [Girar](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/systems/security/encryption-key) chaves de criptografia.

**Para clientes que já tenham 1) aplicado um patch de segurança lançado em 11 de junho de 2024 ou 2) o patch isolado lançado em 28 de junho de 2024 e 3) girado suas chaves de criptografia:**
 
1. Aplique o [hotfix](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-27136) lançado em 17 de julho de 2024.
