---
title: Segurança da infraestrutura em nuvem
description: Saiba mais sobre como mantemos a Adobe Commerce na infraestrutura de nuvem segura.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Segurança

A arquitetura do plano Adobe Commerce Pro foi criada para oferecer um ambiente altamente seguro. Cada cliente é implantado em seu próprio ambiente de servidor isolado, separado de outros clientes. Os detalhes de segurança do ambiente de produção estão descritos abaixo.

## Navegadores da Web

A maior parte do tráfego que entra e sai do ambiente de nuvem vem vem dos navegadores da Web dos consumidores. O tráfego do consumidor pode ser protegido usando HTTPS para todas as páginas no site (usando uma certificação SSL compartilhada ou o certificado SSL do próprio cliente para uma taxa adicional). As páginas de check-out e conta são sempre servidas usando HTTPS. A prática recomendada é distribuir todas as páginas em HTTPS.

## Rede de entrega de conteúdo (CDN)

Fornece rapidamente uma proteção de CDN e negação de serviço distribuída (DDoS). O Fastly CDN ajuda a isolar o acesso direto aos servidores de origem. O DNS público aponta apenas para a Rede Fastly. A solução de DDoS com rapidez protege contra ataques de Camada 3 e Camada 4 com alto interruptor, bem como contra ataques de Camada 7 mais complexos. Os ataques de camada 7 podem ser bloqueados usando regras personalizadas com base em todas as solicitações HTTP/HTTPS e com base nos critérios do cliente e da solicitação, incluindo cabeçalhos, cookies, caminho da solicitação e IP do cliente, ou indicadores como localização geográfica.

## Firewall de aplicações Web (WAF)

O Fastly Web Application Firewall (WAF) é usado para fornecer proteção adicional. A WAF baseada em nuvem da Fastly usa regras de terceiros de fontes comerciais e de código aberto, como o conjunto de regras principal da OWASP. Além disso, regras específicas do Adobe Commerce são empregadas. Os clientes estão protegidos contra ataques-chave de camada de aplicativo, incluindo ataques de injeção e entradas mal-intencionadas, script entre sites, exfiltração de dados, violações de protocolo HTTP e outras 10 ameaças principais da OWASP.

As regras de WAF são atualizadas pela Adobe Commerce caso novas vulnerabilidades sejam detectadas, permitindo que a Managed Services &quot;corrija virtualmente&quot; problemas de segurança antes dos patches de software. A WAF Fastly não fornece serviços limitadores de taxa ou de detecção de bot. Se desejar, os clientes podem licenciar um serviço de detecção de bot de terceiros compatível com o Fastly.

## Nuvem privada virtual (VPC)

O ambiente de produção do plano Adobe Commerce Pro é configurado como uma Nuvem privada virtual (VPC), de modo que os servidores de produção sejam isolados e tenham capacidade limitada de se conectar dentro e fora do ambiente de nuvem. Somente conexões seguras com os servidores de nuvem são permitidas. Protocolos seguros como SFTP ou rsync podem ser usados para transferências de arquivos.

Os clientes podem usar os túneis SSH para proteger as comunicações com o aplicativo. O acesso ao AWS PrivateLink pode ser fornecido com uma taxa adicional. Todas as conexões com esses servidores são controladas usando Grupos de segurança da AWS, um firewall virtual que limita as conexões com o ambiente. Os recursos técnicos dos clientes podem acessar esses servidores usando SSH.

## Criptografia

O Amazon Elastic Block Store (EBS) é usado para armazenamento. Todos os volumes EBS são criptografados usando o algoritmo AES-265. Isso significa que os dados serão criptografados em repouso. O sistema também criptografa dados em trânsito entre a CDN e a origem e entre os servidores de origem. As senhas do cliente são armazenadas como hashes. As credenciais confidenciais, incluindo as do gateway de pagamento, são criptografadas usando o algoritmo SHA-256.

O aplicativo Adobe Commerce não é compatível com criptografia ou criptografia em nível de coluna ou linha quando os dados não estão parados ou não estão em trânsito entre servidores. O cliente pode gerenciar chaves de criptografia no aplicativo. As chaves usadas pelo sistema são armazenadas no AWS Key Management System e devem ser gerenciadas pela Managed Services para fornecer partes do serviço.

## Ensaio de penetração

A Managed Services realiza testes de penetração regulares no sistema de nuvem Adobe Commerce com o aplicativo pronto para uso. Os clientes são responsáveis por qualquer teste de penetração de seu aplicativo personalizado.

## Gateway de pagamento

A Adobe Commerce requer integrações de gateway de pagamento em que os dados do cartão de crédito são passados diretamente do navegador do consumidor para o gateway de pagamento. Os dados do cartão nunca estão disponíveis em nenhum dos ambientes Adobe Commerce Pro plan Managed Services. As ações nas transações pelo aplicativo de comércio eletrônico são concluídas usando uma referência à transação do gateway.

## aplicativo Adobe Commerce

O Adobe testa regularmente o código do aplicativo principal em busca de vulnerabilidades de segurança. Os patches para defeitos e problemas de segurança são fornecidos aos clientes. A Equipe de segurança do produto valida os produtos da Adobe Commerce seguindo as diretrizes de segurança do aplicativo OWASP. Várias ferramentas de avaliação de vulnerabilidade de segurança e fornecedores externos são usadas para testar e verificar a conformidade. As ferramentas de segurança incluem:

- Verificação estática e dinâmica de código vertical
- Varredura de código-fonte RIPS
- Serviços de varredura de vulnerabilidade da Trustwave e da Lógica de Alerta
- Burp Suite Pro
- OWASPIAP
- eSqlMap

A base de código completa é digitalizada com essas ferramentas quinzenalmente. Os clientes são notificados de patches de segurança por meio de emails diretos, notificações no aplicativo e no [Central de segurança](https://magento.com/security).

Os clientes devem garantir que esses patches sejam aplicados ao seu aplicativo personalizado dentro de 30 dias do lançamento, de acordo com as diretrizes do PCI. O Adobe também fornece uma [Ferramenta de Verificação de Segurança](https://docs.magento.com/user-guide/magento/security-scan.html) que permite que os comerciantes monitorem regularmente seus sites e recebam atualizações sobre riscos de segurança conhecidos, malware e acesso não autorizado. A Ferramenta de Verificação de Segurança é um serviço gratuito e pode ser executado em qualquer versão do Adobe Commerce.

Para incentivar os pesquisadores de segurança a identificar e relatar vulnerabilidades, a Adobe Commerce tem uma [programa de recompensa de erros](https://hackerone.com/magento) além dos ensaios internos. Além disso, se desejado, o cliente recebe o código-fonte completo do aplicativo para sua própria revisão.

## Sistema de arquivos somente leitura

Todo o código executável é implantado em uma imagem do sistema de arquivos somente leitura, o que reduz drasticamente as superfícies disponíveis para ataque. O processo de implantação cria uma imagem Squash-FS. Essa abordagem reduz drasticamente as oportunidades de injetar código PHP ou JavaScript no sistema ou modificar os arquivos do aplicativo Adobe Commerce.

## Implantação remota

A única maneira de obter o código executável no ambiente de produção do Managed Services é executá-lo por meio de um processo de provisionamento. Isso envolve enviar o código-fonte do repositório de origem para um repositório remoto que inicia um processo de implantação. O acesso a esse target de implantação é controlado, portanto, você tem controle total sobre quem pode acessar o target de implantação. Todas as implantações do código de aplicativo no ambiente de não produção são controladas pelo cliente.

## Registro

Todas as atividades do AWS estão conectadas no AWS CloudTrail. Linux, servidor de aplicativos e registros de banco de dados são armazenados nos servidores de produção e armazenados em backups. Todas as alterações no código-fonte são registradas em um repositório Git. O histórico de implantação está disponível na Adobe Commerce [Interface da Web do projeto](https://devdocs.magento.com/cloud/project/projects.html#login). Todo o acesso de suporte é registrado e as sessões de suporte são registradas.

## Dados sensíveis

Os dados confidenciais podem abranger informações pessoais de consumidores ou dados confidenciais de clientes da Managed Services. A proteção de dados confidenciais de clientes e consumidores é uma obrigação fundamental para a Adobe Commerce Managed Services. A Managed Services e seus clientes têm obrigações legais em relação a informações de identificação pessoal. Além dos recursos de segurança da arquitetura, há outros controles para limitar a distribuição e o acesso a dados confidenciais.

Os clientes são proprietários de seus dados e têm controle sobre onde esses dados serão localizados. O cliente especifica o local onde as instâncias de produção e desenvolvimento residem. Eles também especificam qual local será usado para o ambiente Magento Business Intelligence (MBI) em conjunto com Commerce e se esse aplicativo MBI tem acesso ou não a informações de identificação pessoal. As instâncias de produção podem estar localizadas na maioria das regiões do AWS, enquanto os ambientes de desenvolvimento e MBI podem se integrar nos Estados Unidos ou na União Europeia no momento.

Os dados confidenciais podem passar pela rede do servidor CDN Fastly, mas não são armazenados na rede Fastly. Todos os parceiros incluídos na oferta da Adobe Commerce Managed Services têm obrigações contratuais para garantir a proteção de dados confidenciais. A Managed Services não moverá dados confidenciais de clientes ou consumidores dos locais especificados pelo cliente.

Como parte do fornecimento dos serviços incluídos na oferta Adobe Commerce Managed Services, a equipe da Managed Services requer acesso a sistemas de produção que contenham dados confidenciais. Esses funcionários são treinados em suas obrigações de proteger dados confidenciais de clientes e consumidores. O acesso a esses sistemas é limitado aos funcionários que precisam de acesso. Esses funcionários só têm acesso pelo tempo necessário para fornecer esses serviços.

## Regulamento Geral sobre a Proteção de Dados (GDPR)

O GDPR é um quadro jurídico que estabelece diretrizes para a coleta e o processamento de informações pessoais de indivíduos na União Europeia (UE). Essas regulamentações se aplicam independentemente de onde o site se baseia e os visitantes da UE têm acesso a ele.

Essencialmente, os visitantes devem ser notificados dos dados que o site coleta e consentir explicitamente na coleta de informações. Os sites devem notificar os visitantes se os dados pessoais mantidos pelo site forem violados.

O comerciante ou empresa que opera o site também deve ter um responsável pela proteção de dados dedicado que supervisione a segurança de dados do site, e esse indivíduo (ou equipe de gerenciamento de site) deve estar disponível para contato caso um visitante solicite que seus dados sejam apagados.

O GDPR também exige que qualquer informação pessoal identificável (como nomes, raça e data de nascimento) coletada seja anonimizada ou pseudônimo.

>[!NOTE]
>
> Esta página é apenas uma visão geral do que deve ser considerado para o GDPR. Para obter mais informações, consulte seu consultor jurídico ou consulte o[texto oficial](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Backups

Os backups são executados a cada hora nas últimas 24 horas de operação. Após o período de 24 horas, os backups são retidos no seguinte agendamento, usando o serviço AWS EBS Snapshot:

| Período | Política de retenção de backup |
|----------------|-------------------------|
| Dias 1 a 3 | Cada backup |
| Dias 4 a 6 | Um backup por dia |
| Semanas 2 a 6 | Um backup por semana |
| Semanas 8 a 12 | Um backup quinsemanal |
| Semanas 12 a 22 | Um backup por mês |

Isso cria um backup independente em armazenamento redundante. Como os volumes EBS são criptografados, os backups também são criptografados. Além disso, a Managed Services realiza backups sob demanda de acordo com solicitações do cliente.

Sua abordagem de backup e recuperação da Adobe Commerce Managed Services usa uma arquitetura de alta disponibilidade combinada com backups completos do sistema. Cada projeto é replicado (todos os dados, código e ativos) em três zonas de disponibilidade separadas da AWS; cada zona com um data center separado.
