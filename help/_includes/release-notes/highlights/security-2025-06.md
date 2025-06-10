---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Destaques da correção de segurança de junho de 2025

Esta versão inclui os seguintes destaques:

* **Aprimoramento de desempenho da API**—Resolve a degradação de desempenho em pontos de extremidade de API da Web assíncronos em massa que foram introduzidos após o patch de segurança anterior.<!-- AC-14078 -->

* **Correção de acesso de Bloqueios do CMS** — Resolve um problema em que os usuários administradores com permissões restritas (como acesso somente de merchandising) não conseguiam exibir a página de listagem [!UICONTROL CMS Blocks].

  Anteriormente, esses usuários encontravam um erro devido a parâmetros de configuração ausentes após a instalação de patches de segurança anteriores.<!-- AC-14087 -->

* **Compatibilidade com limite de cookies** — Resolve uma alteração incompatível com versões anteriores envolvendo a constante `MAX_NUM_COOKIES` na estrutura. Esta atualização restaura o comportamento esperado e garante a compatibilidade para extensões ou personalizações que interagem com limites de cookies.<!-- AC-14475 -->

* **Correção para CVE-2024-34104**—Resolve uma vulnerabilidade de autorização inadequada.<!-- AC-13917 -->

* **Correção para CVE-2025-47110**—Resolve uma vulnerabilidade de modelos de email.<!-- AC-14695 -->

* **Correção para VULN-31547**—Resolve uma vulnerabilidade de link canônico de categoria.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Correções para CVE-2025-47110 VULN-31547 também estão disponíveis como um patch isolado. Consulte o [artigo da Base de Dados de Conhecimento](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) para obter detalhes.

>[!ENDSHADEBOX]
