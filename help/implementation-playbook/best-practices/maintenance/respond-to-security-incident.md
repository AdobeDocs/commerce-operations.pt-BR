---
title: Responder a um incidente de segurança
description: Lidar com incidentes de segurança seguindo as práticas recomendadas para responder e corrigir problemas de segurança que afetam a disponibilidade e o desempenho do site.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Práticas recomendadas para responder a um incidente de segurança

O artigo a seguir resume as práticas recomendadas para responder a um incidente de segurança e corrigir problemas que afetam a disponibilidade, a confiabilidade e o desempenho do site da Adobe Commerce.

Seguir essas práticas recomendadas pode ajudar a impedir acessos não autorizados e ataques de malware. Se ocorrer um incidente de segurança, essas práticas recomendadas ajudarão você a se preparar para uma resposta imediata, realizar uma análise de causa básica e gerenciar o processo de correção para restaurar as operações normais.

>[!TIP]
>
>O Adobe descobriu que a maioria dos incidentes de segurança ocorre quando os agentes da ameaça aproveitam as vulnerabilidades existentes e sem patch, senhas ruins e configurações fracas de propriedade e permissão na configuração do aplicativo e da infraestrutura do Commerce. Minimize a ocorrência de incidentes de segurança revisando e seguindo as práticas recomendadas de segurança do Adobe ao instalar, configurar e atualizar as instalações do Adobe Commerce. Consulte [Proteger o site e a infraestrutura do Commerce](../launch/security-best-practices.md).


## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Responder a um incidente

Se você suspeitar que seu projeto do Adobe Commerce na infraestrutura em nuvem seja afetado por um incidente de segurança, as primeiras etapas críticas são:

- Auditoria de acesso a todas as contas de usuários administradores
- Habilitar controles avançados de autenticação multifator (MFA)
- Preservar registros críticos
- Revise as atualizações de segurança para sua versão do Adobe Commerce.

Mais recomendações são detalhadas abaixo.

## Tomar medidas imediatas em caso de ataque

No caso infeliz de um compromisso do site, aqui estão algumas recomendações importantes a serem seguidas:

- Envolva o integrador de sistemas e o pessoal de segurança apropriado para conduzir esforços de investigação e correção.

- Determine o escopo do ataque:
   - As informações de cartão de crédito foram acessadas?
   - Que informações foram roubadas?
   - Quanto tempo decorreu desde o compromisso?
   - As informações eram criptografadas?

- Tente encontrar o vetor de ataque para determinar quando e como o site foi comprometido, revisando os arquivos de log do servidor e as alterações nos arquivos.

   - Em determinadas circunstâncias, pode ser aconselhável limpar e reinstalar tudo ou, no caso de hospedagem virtual, criar uma nova instância. Malware pode ser escondido em um local insuspeito apenas esperando para restaurar a si mesmo.

   - Remova todos os arquivos desnecessários. Em seguida, reinstale os arquivos necessários de uma fonte conhecida e limpa. Por exemplo, você pode reinstalar usando arquivos do sistema de controle de versão ou dos arquivos de distribuição originais do Adobe.

   - Redefina todas as credenciais, incluindo o banco de dados, o acesso a arquivos, as integrações de pagamento e envio, os serviços da Web e o logon de Administrador. Além disso, redefina todas as chaves e contas de integração e API que podem ser usadas para atacar o sistema.

## Analisar um incidente

A primeira etapa da análise de incidentes é coletar o máximo de fatos possível, o mais rápido possível. Reunir informações sobre o incidente pode ajudar a determinar a possível causa do incidente. A Adobe Commerce fornece as ferramentas abaixo para ajudar na análise de incidentes.

- [Auditoria de Logs de Ações do Administrador](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html?lang=pt-BR).

  O Relatório de logs de ação exibe um registro detalhado de todas as ações administrativas que estão ativadas para fazer logon. Cada registro recebe o carimbo de data e hora e registra o endereço IP e o nome do usuário. Os detalhes do log incluem dados do usuário administrador e alterações relacionadas que foram feitas durante a ação.

- Analise eventos com a [ferramenta Observation for Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  A ferramenta Observation for Adobe Commerce permite analisar problemas complexos para ajudar a identificar as causas raiz. Em vez de rastrear dados díspares, você pode gastar seu tempo correlacionando eventos e erros para obter insights mais profundos sobre as causas dos gargalos de desempenho.

  Use a guia **Segurança** da ferramenta para obter uma visão clara dos possíveis problemas de segurança e ajudar a identificar as causas raiz e manter os sites com desempenho ideal.

- Analisar logs com [Logs do New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html?lang=pt-BR)

  Os projetos Pro do Adobe Commerce na infraestrutura em nuvem incluem o serviço [Logs do New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html?lang=pt-BR). O serviço é pré-configurado para agregar todos os dados de log dos ambientes de preparo e produção para exibi-los em um painel de gerenciamento de log centralizado, onde você pode pesquisar e visualizar dados agregados.

  Para outros projetos da Commerce, você pode configurar e usar o serviço [Logs do New Relic](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) para concluir as seguintes tarefas:
   - Use [consultas New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para pesquisar dados de log agregados.
   - Visualizar dados de log por meio do aplicativo New Relic Logs.

## Contas de auditoria, código e banco de dados

Revise as contas de administrador e usuário do Commerce, o código do aplicativo e a configuração e os logs do banco de dados para identificar e limpar códigos suspeitos e garantir a segurança do acesso à conta, ao site e ao banco de dados. Em seguida, reimplante conforme necessário.

Continue a monitorar de perto o local após o incidente, pois muitos locais serão comprometidos novamente em horas. Garanta a análise contínua de registros e o monitoramento da integridade de arquivos para detectar rapidamente qualquer sinal de novo comprometimento.

### Auditoria de contas de usuário Admin

- [Revisar acesso de usuário Administrador](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html?lang=pt-BR)—Remova contas antigas, não utilizadas ou suspeitas e alterne senhas para todos os usuários Administradores.

- [Revisar configurações de segurança do administrador](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=pt-BR) — Verifique se as configurações de segurança do administrador seguem as práticas recomendadas de segurança.

- [Revisar contas de usuário do Adobe Commerce em projetos de infraestrutura em nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=pt-BR)—Remover contas antigas, não utilizadas ou suspeitas e girar senhas para todos os usuários administradores de projetos em nuvem. Verifique se as configurações de segurança da conta estão definidas corretamente.

- [Auditoria de chaves SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html?lang=pt-BR) para Adobe Commerce na infraestrutura em nuvem — revisão, exclusão e rotação de chaves SSH.

### Código de auditoria

- Do Administrador, examine a [configuração do Cabeçalho e Rodapé de HTML](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html?lang=pt-BR) em todos os níveis de escopo, incluindo `website` e `store view`. Remova qualquer código JavaScript desconhecido das configurações de scripts e folhas de estilos e de HTML diversos. Reter somente código reconhecido, como trechos de rastreamento.

- Compare a base de código de produção atual com a base de código armazenada no Sistema de controle de versão (VCS).

- Coloque qualquer código suspeito em quarentena.

- Certifique-se de que não haja vestígios de código suspeito reimplantando a base de código no ambiente de produção.

### Auditoria de configuração e logs de banco de dados

- Revise todos os procedimentos armazenados para modificações.

- Verifique se o banco de dados está acessível somente pela instância do Commerce.

- Verifique se não há mais malware verificando o site com ferramentas de verificação de malware publicamente disponíveis.

- Proteja o painel Administrador alterando seu nome e verificando se as URLs do site `app/etc/local.xml` e `var` não estão acessíveis publicamente.

- Continue a monitorar de perto o local após o incidente, pois muitos locais serão comprometidos novamente em horas. Garanta a análise contínua de registros e o monitoramento da integridade de arquivos para detectar rapidamente qualquer sinal de novo comprometimento.

## Remover avisos do Google

Se o site tiver sido sinalizado pelo Google como contendo código mal-intencionado, solicite uma revisão depois que o site for limpo. As análises de sites infectados com malware levam alguns dias. Depois que o Google determinar que o site está limpo, os avisos dos resultados de pesquisa e dos navegadores deverão desaparecer em 72 horas. Consulte [Solicitar uma revisão](https://web.dev/articles/request-a-review).

## Revisar lista de verificação de resultados de malware

Se as ferramentas de verificação de malware disponíveis publicamente confirmarem um ataque de malware, investigue o incidente. Trabalhe com o integrador de soluções para limpar o site e seguir o processo de correção recomendado.

## Realizar análises adicionais

Ao lidar com ataques sofisticados, o melhor curso de ação é trabalhar com um desenvolvedor experiente, um especialista terceirizado ou um integrador de soluções para reparar totalmente o site e analisar as práticas de segurança. Trabalhar com profissionais de segurança experientes garante que medidas abrangentes e avançadas sejam tomadas para garantir a segurança de sua empresa e de seus clientes.

## Informações adicionais

- [Estrutura de Análise de Causa Raiz](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
