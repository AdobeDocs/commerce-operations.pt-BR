---
title: Segurança.txt
description: Saiba como fornecer informações para ajudar pesquisadores de segurança a relatar vulnerabilidades.
feature: Configuration, Security
badge: label="Contribuição de Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# Arquivo TXT de segurança

Quando vulnerabilidades de segurança são descobertas pelos pesquisadores, geralmente faltam canais de relatórios adequados. Como resultado, algumas vulnerabilidades não são relatadas. A finalidade do arquivo `security.txt` [formato de arquivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) é fornecer aos pesquisadores de segurança as informações que eles podem usar para relatar suas descobertas.

Os comerciantes podem inserir suas informações de contato para [relatórios de problemas de segurança](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-issue-reporting) do _Administrador_ da Commerce. Para desenvolvedores, o módulo `Magento_Securitytxt` fornece a seguinte funcionalidade:

- Permite que as configurações de segurança sejam salvas do _Administrador_.
- Contém um roteador para corresponder à classe de ação do aplicativo para solicitações para os arquivos `.well-known/security.txt` e `.well-known/security.txt.sig`.
- Serve o conteúdo dos arquivos `.well-known/security.txt` e `.well-known/security.txt.sig`.

Um arquivo `security.txt` válido pode ser semelhante ao seguinte:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para criar o arquivo de assinatura (`security.txt.sig`) de `security.txt`:

```shell
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para verificar a assinatura:

```shell
gpg --verify security.txt.sig security.txt
```
