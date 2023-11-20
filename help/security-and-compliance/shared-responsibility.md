---
title: Responsabilidade compartilhada
description: Saiba mais sobre as responsabilidades de segurança de cada parte envolvida em seu projeto Adobe Commerce na infraestrutura em nuvem.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Modelo de segurança de responsabilidade compartilhada

O Adobe Commerce na infraestrutura em nuvem é uma oferta de plataforma como serviço (PaaS) que depende de um modelo de segurança de responsabilidade compartilhada. Adobe, o comerciante, o provedor de serviços em nuvem e o provedor de rede de entrega de conteúdo (CDN) têm responsabilidade distinta pela manutenção da segurança do Adobe Commerce no aplicativo de infraestrutura em nuvem e no código e nas extensões específicos do comerciante.

Essa abordagem permite que os comerciantes projetem e implementem uma solução altamente flexível, personalizável e dimensionável que melhor se adapte às suas necessidades de negócios, minimizando, ao mesmo tempo, as responsabilidades e os custos operacionais.

Em geral, o Adobe é responsável por desenvolver e manter código seguro de aplicativos principais, manter a segurança da plataforma, garantir a conformidade da plataforma com SOC 2 e PCI e sua compatibilidade com componentes de tecnologia compatíveis com PCI (por exemplo, PHP, Redis) e responder a problemas de segurança relacionados à plataforma principal. A Adobe também é responsável por trabalhar com provedores de serviços em nuvem e parceiros CDN para resolver problemas que possam surgir.

Os comerciantes são responsáveis por manter código personalizado seguro e integrações com aplicativos de terceiros, garantir o desenvolvimento seguro do aplicativo, obter certificação PCI, se solicitado pelo processador de pagamento do comerciante, e reagir e responder a incidentes de segurança.

## responsabilidades do Adobe

O Adobe é responsável pela segurança e disponibilidade do ambiente Adobe Commerce na infraestrutura em nuvem e do código da solução Adobe Commerce na infraestrutura em nuvem. Além disso, a Adobe é responsável pelas atividades e mecanismos necessários para manter a segurança da solução Adobe Commerce na infraestrutura em nuvem, incluindo:

- Aplicação de segurança no nível do servidor e patches para aplicativos compatíveis com o Adobe Commerce na infraestrutura em nuvem, como armazenamento de dados em nuvem e recursos de pesquisa
- Realização de testes de penetração e verificação do Adobe Commerce principal no código de infraestrutura em nuvem
- Realização de revisões/auditorias semestrais da solução de gerenciamento de identidade e acesso (IAM) e do gerenciamento de permissões dos provedores de serviços de nuvem pública (requisito de conformidade com o PCI)
- Realização de revisões/auditorias semestrais de usuários autorizados, inclusive funcionários e contratados da Adobe (requisito de conformidade com o PCI)
- Realização anual de testes e documentação dos recursos de backup e restauração
- Configuração de firewalls de servidor e perímetro
- Conectar e configurar o repositório do Adobe Commerce na infraestrutura em nuvem
- Definir, testar, implementar e documentar planos de recuperação de desastres (DR) para as áreas dentro do escopo de responsabilidade da Adobe
- Definição de regras do WAF (Web Application Firewall, firewall de aplicativo Web) da plataforma global
- Fortalecimento do sistema operacional (SO)
- Implementar e manter a integração das soluções de rede de distribuição de conteúdo (CDN) e de gerenciamento de desempenho de aplicativos (APM) com o Adobe Commerce na infraestrutura em nuvem
- Emitir atualizações de segurança periódicas e outras atualizações para o Adobe Commerce principal no código de infraestrutura em nuvem (a aplicação de patches é responsabilidade do comerciante)
- Gerenciamento de suporte ao comerciante e controles de acesso de suporte (por exemplo, Zendesk)
- Monitoramento, registro e correção de incidentes de segurança relacionados ao Adobe Commerce na infraestrutura da plataforma de infraestrutura em nuvem
- Monitoramento de operações de plataforma e fornecimento de suporte 24 horas por dia, 7 dias por semana para o Adobe Commerce em comerciantes de infraestrutura em nuvem
- Provisionamento dos ambientes de produção e de preparo
- Avaliação de possíveis ameaças à segurança das operações e da infraestrutura da plataforma
- Dimensionamento de computação, armazenamento, grade e outros recursos, conforme descrito no contrato de nível de serviço (SLA) com o comerciante
- Configuração de DNS (Adobe Commerce somente na infraestrutura da plataforma de infraestrutura em nuvem)
- Teste da plataforma para verificar vulnerabilidades de segurança

Embora a Adobe mantenha a certificação PCI para a infraestrutura e os serviços usados na operação da solução Adobe Commerce em infraestrutura em nuvem, os comerciantes são responsáveis pela conformidade do código personalizado, dos processos de sistema e de rede e da organização.

O Adobe também garante a disponibilidade da infraestrutura do comerciante, conforme acordado no SLA aplicável.

## Responsabilidades do comerciante

O comerciante é responsável por seguir as práticas recomendadas de segurança para a instância específica e personalizada do Adobe Commerce na solução de infraestrutura em nuvem e por:

- Adicionar o Adobe Commerce necessário nos arquivos de configuração da infraestrutura em nuvem ao repositório
- Aplicar patches de segurança e outros à solução personalizada Adobe Commerce on cloud infrastructure imediatamente após o lançamento pelo Adobe
- Aplicação de patches de segurança e outros a todas as extensões e códigos personalizados, imediatamente após o lançamento pelo fornecedor
- Criação, implantação e teste de arquivos personalizados de VCL do Varnish
- Projetar, criar temas, instalar, integrar e proteger a solução personalizada do Adobe Commerce na infraestrutura em nuvem, incluindo todas as extensões e códigos personalizados
- Conceder e revogar o acesso do usuário à instância do comerciante do Adobe Commerce na configuração, no aplicativo e na plataforma da infraestrutura em nuvem
- Lidar com problemas de segurança relacionados à rede interna, aos servidores, à infraestrutura e a qualquer aplicativo personalizado do comerciante criado na plataforma Adobe Commerce de infraestrutura em nuvem
- Instalação da ferramenta de integração de linha de comando (CLI) do Adobe Commerce na infraestrutura em nuvem
- Manutenção do nível exigido de conformidade com o PCI do aplicativo personalizado e outros processos internos, conforme definido pelas diretrizes do PCI-DSS

  >[!NOTE]
  >
  >A conformidade com o PCI do comerciante se baseia nas certificações de PCI da Adobe Commerce na infraestrutura em nuvem e no provedor de hospedagem em nuvem para minimizar as áreas que devem ser analisadas.

- Execução de verificações e correção de problemas do PCI ASV no Adobe Commerce principal no código e na plataforma da infraestrutura em nuvem
- Monitoramento de todas as atividades do aplicativo que possam revelar uma possível ameaça à segurança, incluindo testes de penetração, verificações de vulnerabilidade e registros
- Monitoramento e resposta a incidentes de segurança, incluindo análises jurídicas, correções e relatórios relacionados ao Adobe Commerce do comerciante sobre a solução de infraestrutura em nuvem e contas de usuário
- Obtenção de um provedor de DNS e configuração e manutenção de registros de DNS específicos do comerciante
- Execução de testes de desempenho no aplicativo personalizado
- Proteção do acesso às contas da plataforma, do acesso às instâncias e do aplicativo
- Teste e controle de qualidade do aplicativo personalizado
- Manutenção da segurança de quaisquer sistemas ou redes que o comerciante conecte à Adobe Commerce no aplicativo de infraestrutura em nuvem

## Responsabilidades do provedor de serviços em nuvem

O Adobe depende de provedores de serviços de nuvem bem estabelecidos para hospedar a infraestrutura do servidor de nuvem do Adobe Commerce na infraestrutura em nuvem. Esses provedores são responsáveis pela segurança da rede, incluindo roteamento, switching e segurança de perímetro da rede através de sistemas de firewall e sistemas de detecção de intrusão (IDS). Os provedores de serviços em nuvem também são responsáveis pela segurança física dos data centers que hospedam a solução Adobe Commerce on cloud infrastructure e pela segurança ambiental dos data centers.

Os provedores de serviços em nuvem também são responsáveis por:

- Manutenção das certificações PCI DSS, SOC 2 e ISO 27001 para seus serviços em nuvem
- Proteção do hipervisor
- Proteção do data center, incluindo acesso físico e de rede

## Responsabilidades do provedor de CDN

A solução Adobe Commerce na infraestrutura em nuvem usa provedores de CDN para acelerar o tempo de carregamento de página, armazenar em cache o conteúdo e remover instantaneamente o conteúdo desatualizado. Esses provedores também são responsáveis por problemas de segurança diretamente relacionados ou que afetem sua CDN, e por definir e manter regras WAF da CDN.

## Gráfico de responsabilidades de segurança

O gráfico a seguir usa o modelo RACI (R — Responsável, A — Responsável, C — Consultado, I — Informado) para descrever visualmente cada parte nas responsabilidades de segurança do ecossistema relacionadas ao modelo de responsabilidade compartilhada da Adobe Commerce na infraestrutura em nuvem:

<table>
<thead>
  <tr>
    <th>Tarefa</th>
    <th>Adobe</th>
    <th>Comerciante</th>
    <th>Provedor de serviços na nuvem</th>
    <th>Provedor de CDN</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Aplicação de Adobe Commerce em patches de infraestrutura em nuvem</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aplicação de patches aos serviços de suporte<br>(por exemplo, Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definindo regras WAF de origem</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definição de regras WAF CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Implantação de regras do WAF da plataforma</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implantação de regras WAF da CDN</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Correção de bugs principais no Adobe Commerce no código de infraestrutura em nuvem</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Lançamento do Adobe Commerce em patches de infraestrutura em nuvem</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Dimensionamento (computação e armazenamento)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Dimensionamento (PaaS/grade)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Garantia de acesso ao código-fonte, incluindo repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalação do Adobe Commerce na ferramenta CLI de infraestrutura em nuvem</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Adicionar arquivos de configuração do Adobe Commerce na infraestrutura em nuvem ao repositório</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Criação de um projeto para o comerciante (interface de integração)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Conectar repositórios ao Adobe Commerce na infraestrutura em nuvem</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configurar repositório de origem<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Criar um usuário para o gerenciador de versões (interface de integração)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implantação de código na produção</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implantação de código em preparo</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Integração de aplicativos e extensões externas</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalação de extensões</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Personalização do Adobe Commerce na infraestrutura em nuvem</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Teste do desempenho do Adobe Commerce personalizado na infraestrutura em nuvem</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Teste de aplicativo personalizado</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definição de temas e design do aplicativo personalizado</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Criação, implantação e teste de VCLs de verniz personalizados</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuração de DNS (somente infraestrutura de plataforma)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Desenvolvimento e correção de bugs na extensão CDN</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Integração da CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Suporte à CDN<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Configuração do APM/infraestrutura do New Relic</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalação do APM/infraestrutura do New Relic</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Suporte a APM/infraestrutura da New Relic</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configurando Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Obtenção do provedor de DNS (somente Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Fortalecimento do SO</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Provisionamento dos ambientes de produção e de preparo</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Acesso ao Zendesk para Adobe Commerce na infraestrutura em nuvem</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Resolução de problemas de segurança do comerciante</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Resolução de problemas de segurança da infraestrutura em nuvem do Adobe Commerce</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Resolução de problemas de segurança da CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Resolução de problemas de segurança APM</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Auxiliar o Adobe com pesquisa de segurança (software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Auxiliar o Adobe na pesquisa de segurança (varreduras/auditorias)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Executando verificações ASV de PCI</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Correção de verificações do Adobe Commerce na infraestrutura em nuvem PCI<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Remediando verificações de PaaS PCI</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gerenciamento de segredos de SO e plataforma</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gerenciamento de chaves de criptografia da infraestrutura em nuvem do Adobe Commerce</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Verificação de Adobe Commerce personalizado em instâncias de infraestrutura em nuvem</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Monitorar logs de segurança</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gerenciamento de IAMs e permissões para Adobe Commerce na infraestrutura em nuvem</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Gerenciamento de controles de acesso de suporte (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Controle do suporte e do acesso dos comerciantes</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Teste e documentação anuais do plano de DR de Adobe e backup e restauração</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Teste e documentação anuais do plano de recuperação de desastres</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Somente se o repositório do Adobe Commerce na infraestrutura em nuvem for usado como o repositório principal. O uso de outros repositórios externos é de exclusiva responsabilidade do comerciante.</p>
      <p><sup><strong>2</strong></sup> O Adobe oferece suporte de Nível 1 para problemas com provedores CDN.</p>
      <p><sup><strong>3</strong></sup> Alguns controles Ngnix são configurados pelo comerciante para suas aplicações e são sua responsabilidade.</p>
      <p><sup><strong>4</strong></sup> Para PCI, os requisitos de teste de penetração são compartilhados entre a Adobe e o comerciante.</p>
    </td>
  </tr>
</tfoot>
</table>
