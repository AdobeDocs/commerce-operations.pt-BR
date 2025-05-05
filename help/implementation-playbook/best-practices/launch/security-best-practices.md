---
title: Proteger o site e a infraestrutura da Commerce
description: Mantenha a segurança implementando práticas recomendadas de segurança ao instalar, configurar e atualizar instalações do Adobe Commerce.
feature: Best Practices
exl-id: 50d8a464-6496-4e9a-b642-0c6d0eb51ba0
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '2000'
ht-degree: 0%

---

# Proteger o site e a infraestrutura da Commerce

Estabelecer e manter um ambiente seguro para projetos Adobe Commerce implantados em infraestrutura em nuvem é uma responsabilidade compartilhada entre clientes Adobe Commerce, parceiros de soluções e Adobe. O objetivo deste guia é fornecer práticas recomendadas para o lado do cliente na equação.

Embora não seja possível eliminar todos os riscos de segurança, a aplicação dessas práticas recomendadas fortalece a postura de segurança das instalações do Commerce. Um local e uma infraestrutura seguros tornam o alvo menos atraente para ataques mal-intencionados, garantem a segurança da solução e das informações confidenciais dos clientes e ajudam a minimizar os incidentes relacionados à segurança que podem causar interrupções no local e investigações dispendiosas.

>[!NOTE]
>
>Para obter informações sobre as funções e responsabilidades para proteger e manter projetos do Adobe Commerce na infraestrutura em nuvem, consulte [Modelo de Responsabilidade Compartilhada](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/security-and-compliance/shared-responsibility#security-responsibilities-chart)) no _Guia de Segurança e Conformidade do Adobe Commerce_.

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Recomendações prioritárias

A Adobe considera as seguintes recomendações de alta prioridade para todos os clientes. Implemente estas práticas recomendadas de segurança importantes em todas as implantações do Commerce:

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Habilite a autenticação de dois fatores para o Administrador e todas as conexões SSH**

- [Segurança para o administrador do Commerce](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication.html?lang=pt-BR)

- [Conexões SSH seguras](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/multi-factor-authentication.html?lang=pt-BR) (infraestrutura em nuvem)

Quando o MFA é habilitado em um projeto, todas as contas do Adobe Commerce na infraestrutura em nuvem com acesso SSH devem seguir um fluxo de trabalho de autenticação. Esse fluxo de trabalho requer um código de autenticação de dois fatores (2FA) ou um token de API e um certificado SSH para acessar o ambiente.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Proteger o Administrador**

- [Configure uma URL de administrador não padrão](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/store-urls.html?lang=pt-BR#use-a-custom-admin-url) em vez de usar o `admin` padrão ou um termo comum, como `backend`. Essa configuração reduz a exposição a scripts que tentam obter acesso não autorizado ao site.

- [Definir configurações de segurança avançadas](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=pt-BR) — Adicione uma chave secreta às URLs, exija que as senhas diferenciem maiúsculas de minúsculas e limite a duração da sessão do Administrador, o intervalo de tempo de vida da senha e o número de tentativas de logon permitidas antes de bloquear uma conta de usuário Administrador. Para maior segurança, configure o tempo de inatividade do teclado antes que a sessão atual expire e exija que o nome de usuário e a senha diferenciem maiúsculas de minúsculas.

- [Habilite o ReCAPTCHA](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/captcha/security-google-recaptcha.html?lang=pt-BR) para proteger o Administrador de ataques automatizados de força bruta.

- Siga o princípio do privilégio mínimo ao atribuir [Permissões de administrador](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions.html?lang=pt-BR) a funções e funções para contas de usuário administrador.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Atualize para a versão mais recente do Adobe Commerce**

Mantenha seu código atualizado ao [atualizar seu projeto do Commerce para a versão mais recente](#upgrade-to-the-latest-release) do Adobe Commerce, Commerce Services e extensões, incluindo patches de segurança, hotfixes e outros patches fornecidos pelo Adobe.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Valores de configuração confidenciais seguros**

Use o [gerenciamento de configuração](../../../configuration/cli/set-configuration-values.md) para bloquear valores de configuração críticos.

Os comandos da CLI `lock config` e `lock env` configuram variáveis de ambiente para impedir que sejam atualizadas pelo Administrador. O comando grava o valor no arquivo `<Commerce base dir>/app/etc/env.php`. (Para obter informações sobre o Commerce em projetos de infraestrutura em nuvem, consulte [Gerenciamento de Configuração de Armazenamento](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=pt-BR#sensitive-data).)

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Executar verificações de segurança**

Use o [serviço de Verificação de Segurança da Commerce](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=pt-BR) para monitorar todos os sites da Adobe Commerce quanto a riscos de segurança e malware conhecidos, e inscreva-se para receber atualizações de patches e notificações de segurança.

## Garantir a segurança das extensões e do código personalizado

Ao estender o Adobe Commerce adicionando extensões de terceiros do Adobe Commerce Marketplace ou adicionar código personalizado, garanta a segurança dessas personalizações aplicando as seguintes práticas recomendadas:

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Escolha um parceiro ou integrador de soluções (SI) com bom conhecimento em segurança**—Garanta integrações seguras e a entrega segura de código personalizado, selecionando organizações que sigam práticas seguras de desenvolvimento e tenham um sólido histórico de prevenção e solução de problemas de segurança.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Usar extensões seguras**—Identifique as extensões mais apropriadas e seguras para implantações do Commerce consultando o integrador ou desenvolvedor da sua solução e seguindo as [Práticas recomendadas para extensões Adobe](../planning/extensions.md).

- Somente extensões de origem do Adobe Commerce Marketplace ou por meio do integrador de soluções. Se a extensão for obtida por meio de um integrador, certifique-se de que a propriedade da licença de extensão seja transferível, caso o integrador seja alterado.

- Reduza a exposição a riscos limitando o número de extensões e fornecedores.

- Se possível, revise o código da extensão para obter segurança antes de integrar ao aplicativo do Commerce.

- Certifique-se de que os desenvolvedores de extensão PHP sigam as diretrizes, processos e práticas recomendadas de segurança do Adobe Commerce. Especificamente, os desenvolvedores devem evitar o uso de recursos PHP que podem levar à execução remota de código ou criptografia fraca. Consulte [Segurança](https://developer.adobe.com/commerce/php/best-practices/security/) no *Guia de Práticas Recomendadas para Desenvolvedores de Extensão*.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Código de auditoria**—Revise o servidor e o repositório de código-fonte para ver se há sobras de desenvolvimento. Certifique-se de que não haja arquivos de log acessíveis, diretórios .git publicamente visíveis, túneis para executar instruções SQL, dumps de banco de dados, arquivos php info ou quaisquer outros arquivos desprotegidos que não sejam necessários e que possam ser usados em um ataque.

## Atualizar para a versão mais recente

O Adobe lança continuamente componentes atualizados da solução para melhorar a segurança e proteger melhor os clientes contra possíveis comprometimentos. Atualizar para a versão mais recente do aplicativo Adobe Commerce, serviços instalados e extensões e aplicar os patches atuais é a primeira e melhor linha de defesa contra ameaças à segurança.

A Commerce geralmente lança atualizações de segurança trimestralmente, mas se reserva o direito de lançar hotfixes para grandes ameaças à segurança com base na prioridade e em outros fatores.

Consulte os seguintes recursos para obter informações sobre versões disponíveis do Adobe Commerce, ciclos de versão e o processo de atualização e patch:

- [Versões liberadas](../../../release/versions.md)
- [Disponibilidade do produto](../../../release/product-availability.md) (serviços da Adobe Commerce e extensões criadas pelo Adobe)
- [política de ciclo de vida do Adobe Commerce](../../../release/lifecycle-policy.md)
- [Guia de atualização](../../../upgrade/overview.md)
- [Como aplicar patches](../../../upgrade/patches/overview.md)

>[!TIP]
>
>Obtenha as informações de segurança mais recentes e resolva problemas de segurança conhecidos assinando o [Serviço de Notificação de Segurança do Adobe](https://www.adobe.com/subscription/adbeSecurityNotifications.html).

## Desenvolver um plano de recuperação de desastres

Se o seu site Commerce estiver comprometido, controle os danos e restaure rapidamente as operações normais de negócios, desenvolvendo e implementando um plano abrangente de recuperação de desastres.

Se um cliente solicitar a restauração de uma instância do Commerce devido a um desastre, o Adobe poderá fornecer arquivos de backup ao cliente. O cliente e o integrador de soluções, se aplicável, podem executar a restauração.

Como parte de um plano de recuperação de desastres, a Adobe recomenda que os clientes [exportem sua configuração de aplicativo do Adobe Commerce](../../../configuration/cli/export-configuration.md) para facilitar a reimplantação se ela for necessária para fins de continuidade de negócios. O principal motivo para exportar a configuração para o sistema de arquivos é que a configuração do sistema tem prioridade sobre a configuração do banco de dados. Em um sistema de arquivos somente leitura, o aplicativo deve ser reimplantado para alterar configurações confidenciais, fornecendo uma camada extra de proteção.

### Informações adicionais

**Adobe Commerce implantado na infraestrutura em nuvem**

- [Backup e recuperação de desastres](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html?lang=pt-BR#backup-and-disaster-recovery)

- [Armazenar gerenciamento de configuração para o Adobe Commerce na infraestrutura de nuvem](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/store-settings.html?lang=pt-BR)

**Adobe Commerce implantado no local**

- [Exportar definições de configuração](../../../configuration/cli/export-configuration.md)

   - [Importar definições de configuração](../../../configuration/cli/import-configuration.md)

   - [Fazer backup e reverter o sistema de arquivos, a mídia e o banco de dados](../../../installation/tutorials/backup.md)

## Manter um local e uma infraestrutura seguros

Esta seção resume as práticas recomendadas para manter a segurança do local e da infraestrutura de uma instalação do Adobe Commerce. Muitas dessas práticas recomendadas enfocam a proteção da infraestrutura do computador em geral, portanto, algumas das recomendações já podem estar implementadas.

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Bloquear acesso não autorizado**—Trabalhe com seu parceiro de hospedagem para configurar um túnel VPN para bloquear o acesso não autorizado ao site da Commerce e aos dados do cliente. Configure um túnel SSH para bloquear o acesso não autorizado ao aplicativo do Commerce.

![Lista de Verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Usar um Firewall do Aplicativo Web**—Analise o tráfego e descubra padrões suspeitos, como informações de cartão de crédito enviadas para um endereço IP desconhecido usando um Firewall do Aplicativo Web.

As instalações do Adobe Commerce implantadas na infraestrutura em nuvem podem usar os serviços WAF integrados disponíveis com a [integração do Fastly services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html?lang=pt-BR)

![Lista de Verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Definir configurações avançadas de segurança de senha**—Configure senhas fortes e altere-as pelo menos a cada 90 dias, conforme recomendado pelo Padrão de Segurança de Dados PCI na seção 8.2.4. Consulte [Definir configurações de segurança do administrador](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html?lang=pt-BR).

![Lista de verificação](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) **Usar HTTPS** — Se o site do Commerce for recém-implementado, inicie o site inteiro usando HTTPS. Google Além de usar HTTPS como fator de classificação, muitos usuários não consideram comprar de um site, a menos que ele esteja protegido por HTTPS.

## Protect contra malware

Ataques de malware direcionados a sites de comércio eletrônico são muito comuns e os agentes de ameaça desenvolvem continuamente novas maneiras de coletar informações pessoais e de cartões de crédito das transações.

No entanto, a Adobe descobriu que a maioria dos comprometimentos do site não se deve a um hacker inovador. Em vez disso, os agentes de ameaças geralmente tiram proveito das vulnerabilidades existentes e sem patch, senhas ruins e configurações fracas de propriedade e permissão no sistema de arquivos.

Nos ataques mais comuns, um código mal-intencionado é inserido no cabeçalho ou rodapé absoluto de uma loja de clientes. Lá, o código coleta dados de formulário que um cliente insere na loja, incluindo credenciais de logon do cliente e dados de formulário de check-out. Em seguida, esses dados são enviados para outro local para fins mal-intencionados, em vez de para o back-end do Commerce. Além disso, o malware pode comprometer o administrador a executar o código que substitui o formulário de pagamento original por um formulário falso que substitui qualquer proteção definida pelo provedor de pagamento.

As escumadeiras de cartão de crédito do lado do cliente são um tipo de malware que incorpora código no conteúdo do site do comerciante que pode ser executado no navegador de um usuário, como mostrado na figura a seguir.

![Fluxo de dados para ataques de malware direcionados a sites de comércio eletrônico](../../../assets/playbooks/malware-data-flow.svg)

Depois que determinadas ações ocorrem, como um usuário enviar um formulário ou modificar um valor de campo, o skimmer serializa os dados e os envia para endpoints de terceiros. Normalmente, esses endpoints são outros sites comprometidos que atuam como uma retransmissão para enviar os dados ao destino final.


>[!TIP]
>
>Se um site do Commerce for afetado por um ataque de malware, siga as práticas recomendadas da Adobe Commerce para [responder a um incidente de segurança](../maintenance/respond-to-security-incident.md).

### Conhecer os ataques mais comuns

Abaixo está uma lista de categorias comuns de ataques que a Adobe recomenda que todos os clientes da Commerce estejam cientes e tomem medidas para se proteger contra:

- **Desfiguração do site** — Um invasor danifica um site ao alterar a aparência visual dele ou adicionar suas próprias mensagens. Embora o acesso ao site e às contas de usuário tenha sido comprometido, as informações de pagamento geralmente permanecem seguras.

- **Botnets**—O servidor Commerce do cliente se torna parte de uma botnet que envia email de spam. Incluir na lista de bloqueios Embora os dados do usuário normalmente não sejam comprometidos, o nome de domínio do cliente pode ser classificado por filtros de spam, impedindo a entrega de qualquer email do domínio. Como alternativa, o site do cliente se torna parte de uma botnet que causa um ataque de negação de serviço distribuído (DDoS) em outro site. A botnet pode bloquear o tráfego IP de entrada para o servidor do Commerce, impedindo que os clientes possam comprar.

- **Ataques diretos ao servidor**—Os dados estão comprometidos, backdoors e malware estão instalados e as operações do site são afetadas. As informações de pagamento que não estão armazenadas no servidor têm menos probabilidade de serem comprometidas por meio desses ataques.

- **Captura silenciosa de cartão**—Neste ataque mais desastroso, os invasores instalam malware oculto ou software de captura de cartão, ou pior, modificam o processo de finalização para coletar dados de cartão de crédito. Em seguida, os dados são enviados para outro site para venda na web escura. Esses ataques podem passar despercebidos por um longo período de tempo e podem resultar em um grande comprometimento das contas dos clientes e das informações financeiras.

- **Keylogging silencioso** — O ator de ameaças instala código de registro de chaves no servidor do cliente para coletar credenciais de usuário Admin para que eles possam fazer logon e iniciar outros ataques sem serem detectados.

### Protect contra ataques de detecção de senha

Ataques de detecção de senha com força bruta podem resultar em acesso não autorizado do administrador. Protect seu site contra esses ataques seguindo estas práticas recomendadas:

- Identifique e proteja todos os pontos em que a instalação do Commerce pode ser acessada de fora.

  É possível proteger o acesso ao Administrador, que geralmente requer mais proteção, seguindo as [recomendações de prioridade](#priority-recommendations) do Adobe ao configurar o projeto do Commerce.

- Controle o acesso ao site do Commerce configurando uma lista de controle de acesso que permite acesso somente a usuários provenientes de um endereço IP ou rede especificada.

  Você pode usar uma ACL do Fastly Edge com um trecho de código de VCL personalizado para filtrar solicitações recebidas e permitir o acesso pelo endereço IP. Consulte [VCL personalizado para permitir solicitações](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html?lang=pt-BR).


  >[!TIP]
  >
  >Se você empregar uma força de trabalho remota, verifique se os endereços IP dos funcionários remotos estão incluídos na lista de endereços com permissão para acessar o site da Commerce.

### Impedir explorações de clickjacking

O Adobe protege seu armazenamento de ataques de clickjacking, fornecendo o cabeçalho de solicitação HTTP `X-Frame-Options` que você pode incluir em solicitações para sua loja. Consulte [Impedir explorações de clickjacking](../../../configuration/security/xframe-options.md) no *Guia de Configuração do Adobe Commerce*.
