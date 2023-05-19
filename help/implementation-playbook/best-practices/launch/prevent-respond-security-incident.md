---
title: Prevenir e responder a um incidente de segurança
description: Saiba mais sobre as práticas recomendadas para evitar e responder a incidentes de segurança em seu projeto do Adobe Commerce na infraestrutura em nuvem.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Práticas recomendadas para ajudar a impedir e responder a um incidente de segurança

A segurança do Adobe Commerce funciona sob um [Responsabilidade compartilhada](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modelo. É fundamental entender por que o Adobe e suas equipes técnicas são responsáveis. Abaixo, resumimos [Práticas recomendadas de segurança](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) para garantir que o projeto tenha os melhores controles de segurança em vigor e a melhor maneira de responder a um incidente de segurança.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem

## Responder a um incidente

Há muitas considerações sobre a resposta a um incidente de segurança. Se você suspeitar que encontrou um incidente de segurança recente para seu projeto Adobe Commerce na infraestrutura em nuvem, é importante auditar todo o acesso da conta de usuário administrador, habilitar controles avançados de autenticação multifator (MFA), preservar logs críticos e revisar atualizações de segurança para sua versão do Adobe Commerce.

Mais recomendações são detalhadas abaixo. Eles podem ajudar a impedir o acesso não autorizado e iniciar o processo para análise adicional de incidentes.

## Como evitar incidentes de segurança

Siga estas práticas recomendadas de segurança para impedir proativamente incidentes de segurança que afetam seus sites e vitrines da Adobe Commerce:

- [Habilitar 2FA para acesso de administrador](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
A autenticação de dois fatores é amplamente usada, e é comum gerar códigos de acesso para sites diferentes no mesmo aplicativo. Isso garante que somente você possa fazer logon na sua conta de usuário. Se você perder sua senha ou um bot adivinhar, a autenticação de dois fatores adicionará uma camada de proteção.
- [Habilitar MFA para acesso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Quando o MFA é habilitado em um projeto, todas as contas do Adobe Commerce na infraestrutura em nuvem com acesso SSH devem seguir um fluxo de trabalho de autenticação que exija um código de autenticação de dois fatores (2FA) ou um token de API e um certificado SSH para acessar o ambiente.
- Atualize para a versão mais recente do Adobe Commerce.
O Adobe lança patches de segurança e funcionais para cada versão suportada do Adobe Commerce.
- Configurar e usar um [URL do administrador não padrão](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
O Adobe recomenda que você use um URL de administrador exclusivo e personalizado em vez do URL padrão `admin` ou um termo comum, como *back-end*. Embora essa alteração de configuração não proteja diretamente seu site de um determinado fator ruim, ela pode reduzir a exposição a scripts que tentam obter acesso não autorizado.
- Evite que os valores de configuração sejam editados ou atualizados no Administrador usando o  [`bin/magento config:set` Comando da CLI com o `lock env` opção de configuração](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Essa opção bloqueia o valor de configuração para que ele não possa ser editado no Admin ou impede alterações em uma configuração que já está bloqueada. Quando você usa essa opção, as alterações de configuração são gravadas no `<Commerce base dir>/app/etc/env.php` arquivo.
- Configure e execute o [Ferramenta de verificação de segurança da Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html).
A varredura de segurança aprimorada permite monitorar cada um dos sites da Adobe Commerce, incluindo o PWA, quanto a riscos de segurança conhecidos e malware, e receber atualizações de patches e notificações de segurança.
- [Revisar e atualizar o acesso de usuário administrador](https://docs.magento.com/user-guide/system/permissions-users-all.html) e [configurações de segurança](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Recomendamos a remoção de contas antigas, não utilizadas ou suspeitas e a rotação de senhas para todos os usuários administradores.
   - Revise e atualize as Configurações avançadas de segurança do seu projeto. A configuração de segurança do Administrador oferece a capacidade de adicionar uma chave secreta aos URLs, exigir que as senhas diferenciem maiúsculas de minúsculas e limitar a duração das sessões de Administrador, incluindo o tempo de vida das senhas, e o número de tentativas de logon que podem ser feitas antes que a conta de usuário Administrador seja bloqueada. Para aumentar a segurança, você pode configurar o comprimento da inatividade do teclado antes que a sessão atual expire e exigir que o nome de usuário e a senha diferenciem maiúsculas de minúsculas.
- Auditoria do Adobe Commerce em [usuários de projeto na nuvem](https://devdocs.magento.com/cloud/project/user-admin.html).
Recomendamos remover contas antigas, não usadas ou suspeitas e solicitar que os usuários alterem suas senhas.
- Auditoria [Chaves SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) para Adobe Commerce na infraestrutura em nuvem.
Recomendamos revisar, excluir e girar as chaves SSH.
- Implemente a Lista de controle de acesso (ACL) para o administrador.
Você pode usar uma lista ACL de borda do Fastly em combinação com uma [Trecho de código VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) para filtrar solicitações recebidas e permitir o acesso do endereço IP ao administrador.

## Analisar um incidente

A primeira etapa da análise de incidentes é coletar o máximo de fatos possível, o mais rápido possível. Reunir informações sobre o incidente pode ajudar você a determinar a possível causa do incidente. A Adobe Commerce fornece as ferramentas abaixo para ajudar na análise de incidentes.

- [Auditoria de Logs de Ações do Administrador](https://docs.magento.com/user-guide/system/action-log-report.html).
O Relatório de logs de ação exibe um registro detalhado de todas as ações administrativas que estão ativadas para fazer logon. Cada registro recebe o carimbo de data e hora e registra o endereço IP e o nome do usuário. Os detalhes do log incluem dados do usuário administrador e alterações relacionadas que foram feitas durante a ação.
- Analisar eventos com o [Observação para a ferramenta Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
A ferramenta Observation for Adobe Commerce permite analisar problemas complexos para ajudar a identificar as causas raiz. Em vez de rastrear dados díspares, você pode gastar seu tempo correlacionando eventos e erros para obter insights mais profundos sobre as causas dos gargalos de desempenho.
A ferramenta tem como objetivo fornecer uma visão clara de alguns dos possíveis problemas do site para ajudar você a identificar a causa raiz e manter o desempenho ideal dos sites. Clique no link para a documentação da ferramenta Observation for Adobe Commerce acima para acessar a documentação da ferramenta. Há uma seção na documentação que detalha todas as informações que podem ser encontradas no **Segurança** guia.
- Analisar logs com [Logs do New Relic](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Os projetos Pro do Adobe Commerce em infraestrutura em nuvem incluem o [Logs do New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) serviço. O serviço é pré-configurado para agregar todos os dados de log dos ambientes de preparo e produção para exibi-los em um painel de gerenciamento de log centralizado.
Você pode usar o serviço Logs do New Relic para concluir as seguintes tarefas:
   - Uso [consultas do New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para pesquisar dados de log agregados.
   - Visualizar dados de log por meio do aplicativo New Relic Logs.

## Informações adicionais

- [Estrutura de análise de causa básica](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
