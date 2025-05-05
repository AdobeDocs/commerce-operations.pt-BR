---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 0%

---
# Destaques da correção de segurança de outubro de 2024

Esta versão inclui os seguintes destaques:

* **Atualização do TinyMCE**—O [editor do WYSIWYG](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/content-design/wysiwyg/editor) no Administrador agora usa a versão mais recente da dependência do TinyMCE (7.3&#x200B;).

   * O TinyMCE 7.3 oferece uma experiência de usuário aprimorada, melhor colaboração e maior eficiência. O TinyMCE 5 foi removido da linha da versão 2.4.8&#x200B;

   * Como havia uma vulnerabilidade de segurança ([CVE-2024-38357](https://nvd.nist.gov/vuln/detail/CVE-2024-38357)) relatada no TinyMCE 5.10, a dependência também foi atualizada para todas as linhas de versão atualmente com suporte e incluídas em todos os patches de segurança de outubro de 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

* **Atualização do Require.js**—O Adobe Commerce agora usa a versão mais recente do Require.js (2.3.7).

   * Como havia uma vulnerabilidade de segurança ([CVE-2024-38999](https://nvd.nist.gov/vuln/detail/CVE-2024-38999)) relatada no Require.js 2.3.6, a dependência também foi atualizada para todas as linhas de versão atualmente com suporte e incluída em todos os patches de segurança de outubro de 2024:

      * 2.4.7-p3
      * 2.4.6-p8
      * 2.4.5-p10
      * 2.4.4-p11

>[!NOTE]
>
>Essas atualizações são compatíveis com versões anteriores e não devem afetar personalizações e extensões.&#x200B;
