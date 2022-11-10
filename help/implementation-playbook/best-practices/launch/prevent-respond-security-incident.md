---
title: Evitar e responder a um incidente de segurança
description: Saiba mais sobre as práticas recomendadas para evitar e responder a incidentes de segurança em seu projeto de infraestrutura em nuvem do Adobe Commerce.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---


# Práticas recomendadas para ajudar a prevenir e responder um incidente de segurança

A segurança da Adobe Commerce opera sob uma [Responsabilidade compartilhada](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modelo. É fundamental entender por que o Adobe e suas equipes técnicas são responsáveis. Abaixo, resumimos [Práticas recomendadas de segurança](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) para garantir que seu projeto tenha os melhores controles de segurança em vigor e como melhor responder a um incidente de segurança.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem

## Responder a um incidente

Há muitas considerações à medida que você responde a um incidente de segurança. Se você suspeitar que tenha encontrado um incidente de segurança recente para o seu projeto de infraestrutura em nuvem da Adobe Commerce, é importante auditar todo o acesso à conta de usuário do administrador, habilitar controles avançados de autenticação multifator (MFA), preservar registros críticos e revisar as atualizações de segurança para sua versão do Adobe Commerce.

Mais recomendações são detalhadas abaixo. Eles podem ajudar a impedir o acesso não autorizado e iniciar o processo para análise de incidentes adicionais.

## Como evitar incidentes de segurança

Siga estas práticas recomendadas de segurança para evitar incidentes de segurança proativos que afetam seus sites e vitrines do Adobe Commerce:

- [Habilitar o 2FA para acesso de administrador](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
Autenticação de dois fatores é amplamente usada e é comum gerar códigos de acesso para sites diferentes no mesmo aplicativo. Isso garante que somente você possa fazer logon em sua conta de usuário. Se você perder a senha ou um bot adivinhar, a autenticação de dois fatores adiciona uma camada de proteção.
- [Ativar o MFA para acesso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Quando o MFA é ativado em um projeto, todas as contas da infraestrutura em nuvem da Adobe Commerce com acesso SSH devem seguir um fluxo de trabalho de autenticação que requer um código de autenticação de dois fatores (2FA) ou um token de API e um certificado SSH para acessar o ambiente.
- Atualize para a versão mais recente do Adobe Commerce.
O Adobe lança patches de segurança e funcionais para cada Adobe Commerce de versão compatível.
- Configure e use um [URL de administrador não padrão](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
O Adobe recomenda usar um URL de administrador exclusivo e personalizado em vez do padrão `admin` ou um termo comum como *backend*. Embora essa alteração de configuração não proteja diretamente seu site de um determinado ator incorreto, ela pode reduzir a exposição a scripts que tentam obter acesso não autorizado.
- Evite que os valores de configuração sejam editados ou atualizados no Administrador usando o  [`bin/magento config:set` comando CLI com o `lock env` opção de configuração](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Essa opção bloqueia o valor de configuração para que ele não possa ser editado no Admin ou impede alterações em uma configuração que já está bloqueada. Ao usar essa opção, as alterações de configuração são gravadas no `<Commerce base dir>/app/etc/env.php` arquivo.
- Configure e execute o [Ferramenta Adobe Commerce Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html).
A verificação de segurança aprimorada permite monitorar cada um dos sites da Adobe Commerce, incluindo o PWA, para conhecer os riscos de segurança e malware, além de receber atualizações de patch e notificações de segurança.
- [Revisar e atualizar o acesso do usuário administrador](https://docs.magento.com/user-guide/system/permissions-users-all.html) e [configurações de segurança](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Recomendamos remover quaisquer contas antigas, não utilizadas ou suspeitas e rotular senhas para todos os usuários administradores.
   - Revise e atualize as Configurações avançadas de segurança para seu projeto. A configuração de segurança do Administrador oferece a capacidade de adicionar uma chave secreta a URLs, exigir senhas que diferenciem maiúsculas de minúsculas e limitar a duração das sessões de Administração, incluindo a duração das senhas, e o número de tentativas de logon que podem ser feitas antes que a conta de usuário do Administrador seja bloqueada. Para aumentar a segurança, você pode configurar a duração da inatividade do teclado antes da sessão atual expirar e exigir que o nome de usuário e a senha diferenciem maiúsculas de minúsculas.
- Auditar a Adobe Commerce em [usuários do projeto na nuvem](https://devdocs.magento.com/cloud/project/user-admin.html).
Recomendamos remover qualquer conta antiga, não usada ou suspeita e solicitar que os usuários alterem suas senhas.
- Auditoria [Chaves SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) para o Adobe Commerce na infraestrutura em nuvem.
Recomendamos revisar, excluir e girar chaves SSH.
- Implemente a Lista de Controle de Acesso (ACL) para Admin.
Você pode usar uma lista de ACL do Fastly Edge em combinação com um [Snippet do código VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) para filtrar solicitações recebidas e permitir acesso por endereço IP ao Administrador.

## Analisar um incidente

O primeiro passo da análise de incidentes é reunir o máximo possível de fatos, o mais rápido possível. A coleta de informações sobre o incidente pode ajudar você a determinar a causa potencial do incidente. A Adobe Commerce fornece as ferramentas abaixo para auxiliar na análise de incidentes.

- [Auditoria de logs de ação do administrador](https://docs.magento.com/user-guide/system/action-log-report.html).
O Relatório de logs de ação exibe um registro detalhado de todas as ações de administrador que estão habilitadas para o registro. Cada registro tem o registro de data e hora e registra o endereço IP e o nome do usuário. Os detalhes do log incluem dados do usuário administrador e alterações relacionadas que foram feitas durante a ação.
- Analise eventos com a [Ferramenta Observação para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
A ferramenta Observação para Adobe Commerce permite analisar problemas complexos para ajudar a identificar causas raiz. Em vez de rastrear dados diferentes, você pode gastar seu tempo correlacionando eventos e erros para obter insights mais profundos sobre as causas dos gargalos de desempenho.
A ferramenta tem como objetivo fornecer uma visão clara de alguns dos possíveis problemas do site para ajudar a identificar a causa raiz e manter o desempenho ideal dos sites. Clique no link para a documentação da ferramenta Observação para Adobe Commerce acima para acessar a documentação da ferramenta. Há uma seção na documentação que detalha todas as informações que podem ser encontradas no **Segurança** guia .
- Analisar logs com [Novos Logs Relic](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Os projetos do Adobe Commerce on cloud Infrastructure Pro incluem [Novos Logs Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) serviço. O serviço é pré-configurado para agregar todos os dados de log dos ambientes de preparo e produção para exibi-los em um painel de gerenciamento de log centralizado.
Você pode usar o serviço Novos Registros de Relação para concluir as seguintes tarefas:
   - Use [Novas consultas Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para pesquisar dados de log agregados.
   - Visualize dados de log pelo aplicativo New Relic Logs .

## Informações adicionais

- [Estrutura de análise de causa raiz](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
