---
title: Security.txt
description: Saiba como fornecer informações para ajudar pesquisadores de segurança a relatar vulnerabilidades.
feature: Configuration, Security
badge: label="Contribuição de Kalpesh Mehta de Corra" type="Informative" url="https://solutionpartners.adobe.com/s/directory/detail/corra" tooltip="Kalpesh Mehta"
exl-id: ddafd03c-77b2-42e8-b593-7d655d08e9c3
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 0%

---

# Arquivo TXT de segurança

Quando vulnerabilidades de segurança são descobertas pelos pesquisadores, geralmente faltam canais de relatórios adequados. Como resultado, algumas vulnerabilidades não são relatadas. O objetivo da `security.txt` [formato de arquivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) O arquivo é para fornecer aos pesquisadores de segurança as informações que eles podem usar para relatar suas conclusões.

Os comerciantes podem inserir suas informações de contato para [relatório de problemas de segurança](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) do Commerce _Admin_. Para desenvolvedores, a variável `Magento_Securitytxt` O módulo de fornece a seguinte funcionalidade:

- Permite que as configurações de segurança sejam salvas do _Admin_.
- Contém um roteador para corresponder a classe de ação do aplicativo para solicitações ao `.well-known/security.txt` e `.well-known/security.txt.sig` arquivos.
- Atende ao conteúdo do `.well-known/security.txt` e `.well-known/security.txt.sig` arquivos.

Um válido `security.txt` O arquivo pode ter a seguinte aparência:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para criar o `security.txt` assinatura (`security.txt.sig`) arquivo:

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para verificar a assinatura:

```bash
gpg --verify security.txt.sig security.txt
```
