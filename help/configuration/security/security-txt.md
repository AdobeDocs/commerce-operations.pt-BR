---
title: Security.txt
description: Saiba como fornecer informações para ajudar pesquisadores de segurança a relatar vulnerabilidades.
contributor_name: Kalpesh Mehta from Corra
contributor_link: https://partners.magento.com/portal/details/partner/id/70/
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---


# Arquivo TXT de segurança

Quando as vulnerabilidades de segurança são descobertas por pesquisadores, os canais de relatórios adequados geralmente não têm acesso. Como resultado, algumas vulnerabilidades não são relatadas. O objetivo da `security.txt` [formato de arquivo](https://datatracker.ietf.org/doc/html/draft-foudil-securitytxt-09) O ficheiro destina-se a fornecer aos investigadores de segurança as informações que podem utilizar para comunicar os seus resultados.

Os comerciantes podem inserir suas informações de contato para [relatório de problemas de segurança](https://docs.magento.com/user-guide/stores/security-issue-reporting.html) do Commerce _Administrador_. Para desenvolvedores, a variável `Magento_Securitytxt` O módulo fornece a seguinte funcionalidade:

- Permite que as configurações de segurança sejam salvas do _Administrador_.
- Contém um roteador para corresponder à classe de ação do aplicativo para solicitações ao `.well-known/security.txt` e `.well-known/security.txt.sig` arquivos.
- Aplica o conteúdo da variável `.well-known/security.txt` e `.well-known/security.txt.sig` arquivos.

Um `security.txt` pode ser semelhante ao seguinte:

```text
Contact: mailto:security@example.com
Contact: tel:+1-201-555-0123
Encryption: https://example.com/pgp.asc
Acknowledgement: https://example.com/security/hall-of-fame
Policy: https://example.com/security-policy.html
Signature: https://example.com/.well-known/security.txt.sig
```

Para criar o `security.txt` assinatura (`security.txt.sig`) arquivo :

```bash
gpg -u KEYID --output security.txt.sig --armor --detach-sig security.txt
```

Para verificar a assinatura:

```bash
gpg --verify security.txt.sig security.txt
```
