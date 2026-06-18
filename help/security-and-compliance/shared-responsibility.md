---
title: Responsabilidade Compartilhada Segurança e Modelo Operacional
description: Saiba mais sobre as responsabilidades de segurança de cada parte envolvida em seu projeto Adobe Commerce na infraestrutura em nuvem.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 7dcd7f79417df28402a29e1e52d99eb288e8c6b9
workflow-type: tm+mt
source-wordcount: '3253'
ht-degree: 0%

---

# Segurança de responsabilidade compartilhada e modelo operacional

O Adobe Commerce na infraestrutura em nuvem é uma oferta de plataforma como serviço (PaaS) que depende de um modelo operacional e de segurança de responsabilidade compartilhada. O Adobe, o comerciante, o provedor de serviços em nuvem e o provedor de rede de entrega de conteúdo (CDN) compartilham essas responsabilidades. Cada parte tem uma responsabilidade distinta pela segurança e operação do aplicativo Adobe Commerce e do código e extensões específicos do comerciante implantados na infraestrutura em nuvem.

Esse modelo compartilhado permite que os comerciantes projetem e implementem uma solução flexível, personalizável e dimensionável que atenda aos requisitos de negócios, minimizando as responsabilidades e os custos operacionais.

>[!VIDEO](https://video.tv.adobe.com/v/3458392/?learn=on&enablevpops)

A Adobe é responsável pelo seguinte:

* Desenvolvimento e manutenção de um código de aplicativo principal seguro
* Manutenção da segurança da plataforma
* Assegurar que a plataforma é compatível com SOC 2 e PCI e com componentes de tecnologia compatíveis com PCI (por exemplo, PHP, Redis)
* Resposta a problemas de segurança relacionados à plataforma principal
* Trabalhar com provedores de serviços de nuvem e parceiros CDN para resolver problemas que ocorram

Os comerciantes são responsáveis pelo seguinte:

* Manutenção da segurança para código personalizado e integrações com aplicativos de terceiros
* Garantia de desenvolvimento seguro de aplicativos
* Obter a certificação PCI, se solicitado pelo processador de pagamento do comerciante
* Reagir e responder a incidentes de segurança
* Manutenção de todas as dependências de terceiros, serviços de plataforma e extensões dos Serviços da Adobe Commerce em versões que têm suporte ativo. A Adobe não fornece suporte ou assistência de segurança para implantações que executam versões de dependências não compatíveis. Consulte [Requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=pt-BR) e a [Matriz de disponibilidade do produto](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/product-availability) para obter as versões com suporte.

>[!NOTE]
>
>Consulte também:
>
>* [Política de ciclo de vida do software](../release/lifecycle-policy.md) — datas de fim de suporte, suporte estendido e disposições transitórias somente de segurança
>* [Política de imposição de atualização de versão da nuvem](../release/version-upgrade-enforcement-policy.md) — datas de imposição e ações necessárias

{{supported-versions-only}}

## Responsabilidades do Adobe

A Adobe é responsável pela segurança e disponibilidade do ambiente Adobe Commerce na infraestrutura em nuvem e pelo código da solução principal. A Adobe também realiza as atividades que mantêm a segurança da solução Adobe Commerce na infraestrutura em nuvem, incluindo:

* Aplicação de segurança no nível do servidor e patches para aplicativos compatíveis com o Adobe Commerce na infraestrutura em nuvem, como armazenamento de dados em nuvem e recursos de pesquisa
* Realização de testes de penetração e verificação do Adobe Commerce principal no código de infraestrutura em nuvem
* Realização de análises e auditorias semestrais das soluções e do gerenciamento de permissões de gerenciamento de identidade e acesso (IAM) dos provedores de serviços de nuvem pública (requisito de conformidade com o PCI)
* Realização de revisões e auditorias semestrais de usuários autorizados, inclusive de funcionários e contratados da Adobe (requisito de conformidade com o PCI)
* Realização anual de testes e documentação dos recursos de backup e restauração
* Configuração de firewalls de servidor e perímetro
* Conectar e configurar o repositório do Adobe Commerce na infraestrutura em nuvem
* Definir, testar, implementar e documentar planos de recuperação de desastres (DR) para as áreas de responsabilidade da Adobe
* Definição de regras de firewall de aplicativo Web da plataforma global (WAF)
* Fortalecimento do sistema operacional (SO)
* Implementar e manter a integração das soluções de rede de distribuição de conteúdo (CDN) e de gerenciamento de desempenho de aplicativos (APM) com o Adobe Commerce na infraestrutura em nuvem
* Emitir atualizações de segurança periódicas e outras atualizações para o Adobe Commerce principal no código de infraestrutura em nuvem (a aplicação de patches é responsabilidade do comerciante)
* Gerenciamento de suporte ao comerciante e controles de acesso de suporte (por exemplo, Suporte da Experience League)
* Monitoramento, registro e correção de incidentes de segurança relacionados ao Adobe Commerce na infraestrutura da plataforma de infraestrutura em nuvem
* Monitoramento de operações de plataforma e fornecimento de suporte 24 horas por dia, 7 dias por semana para o Adobe Commerce em comerciantes de infraestrutura em nuvem
* Provisionamento dos ambientes de produção e de preparo
* Avaliação de possíveis ameaças à segurança das operações e da infraestrutura da plataforma
* Dimensionamento de computação, armazenamento, grade e outros recursos, conforme descrito no contrato de nível de serviço (SLA) com o comerciante
* Configuração de DNS (Adobe Commerce somente na infraestrutura da plataforma de infraestrutura em nuvem)
* Teste da plataforma para verificar vulnerabilidades de segurança

A Adobe mantém a certificação PCI para a infraestrutura e os serviços usados para a solução Adobe Commerce. Os comerciantes são responsáveis pela conformidade de seus códigos personalizados, sistemas, processos de rede e organização.

A Adobe também garante a disponibilidade da infraestrutura do comerciante, conforme acordado na SLA aplicável.

## Responsabilidades do comerciante

O comerciante é responsável por seguir as práticas recomendadas de segurança para a instância personalizada da solução Adobe Commerce na infraestrutura em nuvem:

* Adicionar o Adobe Commerce necessário nos arquivos de configuração da infraestrutura em nuvem ao repositório
* Aplicar patches de segurança e outros à solução personalizada Adobe Commerce on cloud infrastructure imediatamente após o lançamento pela Adobe
* Aplicação de patches de segurança e outros a todas as extensões e códigos personalizados imediatamente após o lançamento pelo fornecedor
* Criação, implantação e teste de arquivos personalizados de VCL do Varnish
* Projetar, criar temas, instalar, integrar e proteger a solução personalizada do Adobe Commerce na infraestrutura em nuvem, incluindo todas as extensões e códigos personalizados
* Conceder e revogar o acesso do usuário à instância do comerciante do Adobe Commerce na configuração, no aplicativo e na plataforma da infraestrutura em nuvem
* Lidar com problemas de segurança relacionados à rede interna, aos servidores, à infraestrutura e a qualquer aplicativo personalizado do comerciante criado na plataforma Adobe Commerce de infraestrutura em nuvem
* Instalação da ferramenta de integração de linha de comando (CLI) do Adobe Commerce na infraestrutura em nuvem
* Manutenção do nível exigido de conformidade com o PCI do aplicativo personalizado e outros processos internos, conforme definido pelas diretrizes do PCI-DSS

  >[!NOTE]
  >
  >Para minimizar as áreas que devem ser analisadas, a conformidade com o PCI para o comerciante é baseada nas certificações PCI da Adobe Commerce e do provedor de hospedagem na nuvem.

* Execução de verificações e correção de problemas do PCI ASV no Adobe Commerce principal no código e na plataforma da infraestrutura em nuvem
* Monitoramento de todas as atividades do aplicativo que possam revelar uma possível ameaça à segurança, incluindo testes de penetração, verificações de vulnerabilidade e registros
* Monitoramento e resposta a incidentes de segurança, incluindo análises jurídicas, correções e relatórios relacionados ao Adobe Commerce do comerciante sobre a solução de infraestrutura em nuvem e contas de usuário
* Obtenção de um provedor de DNS e configuração e manutenção de registros de DNS específicos do comerciante
* Execução de testes de desempenho no aplicativo personalizado
* Proteção do acesso às contas da plataforma, do acesso às instâncias e do aplicativo
* Teste e controle de qualidade do aplicativo personalizado
* Manutenção da segurança de quaisquer sistemas ou redes que o comerciante conecte à Adobe Commerce no aplicativo de infraestrutura em nuvem
* Manutenção de todos os serviços da plataforma, dependências de terceiros e extensões dos Serviços da Adobe Commerce em versões ativamente suportadas pelos respectivos fornecedores ou pela Adobe. Isso inclui:

   * Serviços de infraestrutura como banco de dados, cache, pesquisa, tempo de execução PHP e servidor Web
   * Extensões do Adobe Commerce Services
   * Todas as extensões de terceiros e integrações personalizadas

  A Adobe não fornece suporte para implantações que executam versões não compatíveis. Consulte [Requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=pt-BR) e a [Matriz de disponibilidade do produto](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/product-availability) para obter as versões com suporte.

## Responsabilidades do provedor de serviços em nuvem

A Adobe depende de provedores de serviços em nuvem para hospedar a infraestrutura do servidor em nuvem do Adobe Commerce na infraestrutura em nuvem. Esses provedores são responsáveis pela segurança da rede, incluindo roteamento, switching e segurança de perímetro da rede através de sistemas de firewall e sistemas de detecção de intrusão (IDS). Os provedores de serviços em nuvem também são responsáveis pela segurança física e ambiental dos data centers que hospedam a solução Adobe Commerce na infraestrutura em nuvem.

Os provedores de serviços em nuvem também são responsáveis por:

* Manutenção das certificações PCI DSS, SOC 2 e ISO 27001 para seus serviços em nuvem
* Proteção do hipervisor
* Proteção do data center, incluindo acesso físico e de rede

## Responsabilidades do provedor de CDN

A solução Adobe Commerce na infraestrutura em nuvem usa provedores de CDN para acelerar o tempo de carregamento de página, armazenar em cache o conteúdo e remover instantaneamente o conteúdo desatualizado. Esses provedores também são responsáveis por problemas de segurança que afetem a CDN e por definir e manter regras de WAF da CDN.

## Resumo das responsabilidades de segurança

>[!BEGINSHADEBOX]

A tabela de resumo a seguir usa o modelo RACI para mostrar as responsabilidades de segurança compartilhadas entre a Adobe, o comerciante e o provedor de serviços de nuvem:

**R** — Responsável
**A** — Responsável
**C** — Consultado
**I** — Informado

>[!ENDSHADEBOX]

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
    <td>Aplicando patches aos serviços de suporte <br>(Por exemplo, Nginx ou MySQL.)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definição das regras de origem do WAF</td>
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
    <td>Implantação de regras do Platform WAF</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implantação de regras do WAF CDN</td>
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
    <td>Dimensionamento (PaaS e grade)</td>
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
    <td>Configurando o repositório de origem<sup>1</sup></td>
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
    <td>Teste do aplicativo personalizado</td>
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
    <td>Configuração de aplicativos New Relic APM e de infraestrutura</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalando aplicativos do New Relic APM e de infraestrutura</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Suporte a aplicativos New Relic APM e de infraestrutura</td>
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
    <td>Obter um provedor de DNS (somente Pro)</td>
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
    <td>Auxiliar a Adobe na pesquisa de segurança (software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Auxiliar a Adobe na pesquisa de segurança (verificações/auditorias)</td>
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
    <td>Remediando verificações de PCI do Adobe Commerce na infraestrutura em nuvem<sup>4</sup></td>
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
    <td>Gerenciamento de IAM e permissões para Adobe Commerce na infraestrutura em nuvem</td>
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
    <td>Teste e documentação anuais do plano de DR da Adobe e backup e restauração</td>
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
  <tr>
    <td>Manutenção de todos os serviços da plataforma, dependências de terceiros e extensões do Commerce Services em versões ativamente compatíveis (incluindo, mas não limitado a, serviços de infraestrutura, complementos SaaS Commerce e extensões de terceiros)</td>
    <td>I</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup>1</sup> Somente se o repositório do Adobe Commerce na infraestrutura em nuvem for usado como o repositório principal. O uso de outros repositórios externos é de exclusiva responsabilidade do comerciante.</p>
      <p><sup>2</sup> O Adobe oferece suporte de Nível 1 para problemas com provedores CDN.</p>
      <p><sup>3</sup> O comerciante é responsável por todos os controles Nginx configurados para seus aplicativos.</p>
      <p><sup>4</sup> Para o PCI, os requisitos de teste de penetração são compartilhados entre a Adobe e o comerciante.</p>
    </td>
  </tr>
</tfoot>
</table>

## Resumo das responsabilidades operacionais

>[!BEGINSHADEBOX]

As tabelas de resumo a seguir esclarecem as responsabilidades operacionais da Adobe e dos comerciantes ao desenvolver, implantar, manter e proteger o Adobe Commerce na infraestrutura em nuvem.

>[!ENDSHADEBOX]

### Codificação e desenvolvimento

#### Código Adobe Commerce principal

|     | Adobe | Comerciante |
| --- | --- | --- |
| Publicação de atualizações e patches no Adobe Commerce Core | R |     |
| Disponibilidade e patches do sistema de arquivos | R |  |
| Publicação de atualizações e correções no ECE-Tools | R |     |
| Qualidade do aplicativo principal do Adobe Commerce | R |     |

{style="table-layout:auto"}

#### Repositório de código

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do repo.magento.com | R |     |
| Disponibilidade do Adobe Commerce no servidor Git da nuvem | R |     |
| Outros repositórios de código selecionados pelo comerciante (GitHub, Bitbucket, servidor Git hospedado) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilização de contêineres do Cloud Docker para download | R |   |
| Implantação e configuração do Cloud Docker (opcional) |     | R |
| Qualquer outra configuração de desenvolvimento local |     | R |

{style="table-layout:auto"}

#### CLI do Commerce Cloud

|     | Adobe | Comerciante |
| --- | --- | --- |
| Qualidade contínua e atualização das ferramentas ECE | R |   |
| Instalação da versão mais recente das ferramentas ECE |     | R |

{style="table-layout:auto"}

#### Personalizações

|  | Adobe | Comerciante |
| --- | --- | --- |
| Módulos e código personalizados do Adobe Commerce |     | R |
| Extensões |     | R |
| Integrações personalizadas |     | R |

{style="table-layout:auto"}

#### Implantações

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade da infraestrutura para criar e implantar código | R |   |
| Pipeline de qualidade contínua de configuração de criação e implantação de infraestrutura | R |   |
| Configuração de criação e implantação de conteúdo estático |     | R |
| Criação e execução do processo de governança de implantação: critérios e gerenciamento de alterações |     | R |
| Implantação no ambiente de preparo |     | R |
| Implantação no ambiente de produção |     | R |
| Reversões de produção |     | R |

{style="table-layout:auto"}

#### Sincronização de ambientes

Os comerciantes são responsáveis por sincronizar dados entre ambientes.

#### Patches

|     | Adobe | Comerciante |
| --- | --- | --- |
| Instalação de atualizações e correções no ECE-Tools |     | R |
| Instalação de atualizações e patches no Adobe Commerce Core |     | R |

#### Disponibilidade do site

|  | Adobe | Comerciante |
| --- | --- | --- |
| Aplicativo Adobe Commerce personalizado e sites associados |     | R |

#### Desempenho

|     | Adobe | Comerciante |
| --- | --- | --- |
| Ajuste e otimização de aplicativos principais | R |   |
| Ajuste e otimização de código personalizado |     | R |
| Código Adobe Commerce personalizado |     | R |
| Teste de carga |     | R |
| Teste de desempenho |     | R |

{style="table-layout:auto"}


#### Logs e monitoramento

|     | Adobe | Comerciante |
| --- | --- | --- |
| Rotação de logs | R |   |
| Aplicativo Adobe Commerce personalizado |   | R |
| Disponibilidade de serviços da New Relic:<br>integração de agente e aplicativo de APM, aplicativo de infraestrutura,<br>logon e integração | R |   |
| Configuração de alertas do New Relic |     | R |
| Implantação do agente do New Relic em servidores PaaS | R |   |

{style="table-layout:auto"}

#### Depuração e isolamento de problemas

|     | Adobe | Comerciante |
| --- | --- | --- |
| Depuração e isolamento de problemas | R | R |
| Suporte oportuno ao processo de depuração e isolamento de problemas |     | R |

{style="table-layout:auto"}

### Configuração de aplicativos e serviços

#### aplicativo Commerce

|     | Adobe | Comerciante |
| --- | --- | --- |
| Configuração do aplicativo |     | R |
| Adicionar domínios ao aplicativo do Adobe Commerce (URLs de base) |     | R |
| Configurando PaaS para usar versões de Serviços suportadas pela versão implantada do Adobe Commerce<br><br>Por exemplo, versões diferentes do Commerce são compatíveis com versões específicas do PHP, Redis, etc. |     | R |

{style="table-layout:auto"}

#### Agendamento de tarefas com trabalhos cron

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade de trabalhos cron padrão | R | |
| Qualidade contínua de trabalhos cron personalizados |  | R |

{style="table-layout:auto"}

#### Agente de mensagens para estrutura de fila de mensagens

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço RabbitMQ | R |   |
| Configuração das configurações padrão do RabbitMQ | R |   |
| Qualidade contínua e correção de RabbitMQ | R |   |
| Enviar uma solicitação de serviço para instalar uma versão do RabbitMQ compatível com a versão instalada do Adobe Commerce |   | R |

{style="table-layout:auto"}

#### serviço PHP

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do PHP | R |   |
| Configuração das configurações padrão do PHP | R |     |
| Configuração de definições de PHP personalizadas |     | R |
| Configuração do arquivo YAML para alinhar as versões do PHP compatíveis com a versão do Adobe Commerce instalada |    | R |
| O comerciante precisa manter o PHP em uma versão suportada. As implantações em versões não compatíveis NÃO estão qualificadas para suporte ao Adobe e podem conter vulnerabilidades de segurança sem patch. |     | R |

{style="table-layout:auto"}

#### Serviços de banco de dados

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade dos serviços Galera e MariaDB | R | |
| Manutenção em andamento das configurações padrão do banco de dados<br><br>(indexação e otimização das tabelas principais, otimização das configurações padrão de administração do sistema) | R |   |
| Manutenção contínua de dados de comerciante e configurações modificadas<br><br>(configuração de tabelas normalizadas versus planas, indexação e otimização de tabelas personalizadas e de terceiros, arquivamento ou remoção de dados, definição das configurações de administração do sistema) |     | R |
| Configuração do Galera e do MySQL | R |   |
| Qualidade contínua e patches de Galera e MariaDB | R |   |
| Otimização contínua da infraestrutura | R |   |
| Identificação e correção de consultas lentas |     | R |
| Enviar uma solicitação de serviço para instalar uma versão do MariaDB compatível com a versão instalada do Adobe Commerce |     | R |
| O comerciante deve manter o MariaDB em uma versão compatível. As implantações em versões não compatíveis NÃO estão qualificadas para suporte ao Adobe e podem conter vulnerabilidades de segurança sem patch. |     | R |
| Definição e manutenção de políticas de retenção de dados específicas do comerciante (as políticas de retenção de dados da Adobe são definidas no acordo do comerciante) |     | R |

{style="table-layout:auto"}

#### Serviço CDN

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade e qualidade da CDN | R |   |
| Configuração do serviço Fastly (por meio de extensão ou API) |     | R |
| Qualidade da extensão do Fastly | R |   |
| Qualidade de trechos de VCL da integração Fastly (incluído na extensão Fastly) | R |   |
| Otimização do cache da página |     | R |
| Adicionar domínios a serviços, CDN e infraestrutura | R |   |
| Trechos de VCL personalizados |     | R |
| Regras do WAF e do WAF | R |   |

{style="table-layout:auto"}

#### Serviço de cache

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço Redis | R |   |
| Configuração das configurações padrão de Redis | R |   |
| Qualidade contínua e correção de Redis | R |   |
| Enviar uma solicitação de serviço para instalar uma versão do Redis compatível com a versão do Adobe Commerce instalada |     | R |
| O comerciante deve manter o Redis em uma versão compatível. As implantações em versões não compatíveis NÃO estão qualificadas para suporte ao Adobe e podem conter vulnerabilidades de segurança sem patch. |     | R |

{style="table-layout:auto"}

#### Serviço de pesquisa

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do OpenSearch | R |   |
| Configuração das opções padrão do OpenSearch | R |   |
| Enviar uma solicitação de serviço para instalar uma versão do OpenSearch compatível com a versão do Adobe Commerce instalada |   | R |
| O comerciante deve manter o OpenSearch em uma versão compatível. As implantações em versões sem suporte _não_ estão qualificadas para o suporte da Adobe e podem conter vulnerabilidades de segurança sem patch. |     | R |

{style="table-layout:auto"}

#### Serviço de e-mail

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço de e-mail SendGrid e sua integração | R |   |
| Monitoramento do uso do SendGrid do comerciante em relação aos limites | R |   |
| Usar o serviço somente para emails transacionais de saída. O serviço não oferece suporte ao envio de emails de marketing. |     | R |
| Configuração de serviços de email opcionais de terceiros |     | R |

{style="table-layout:auto"}

#### Serviços de terceiros

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade e qualidade de serviços de terceiros |     | R |

{style="table-layout:auto"}

### Extensões do Commerce Services

#### Serviço de relatório avançado

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço Advanced Reporting | R |   |
| A configuração do Advanced Reporting está em conformidade com os termos e condições do Advanced Reporting |     | R |

{style="table-layout:auto"}

#### Commerce Intelligence

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade dos serviços do Adobe Commerce Business Intelligence | R |   |
| Processos de Sincronização de Dados do MBI | R |   |
| Detecção de problemas de sincronização do MBI | R |   |
| Configurando a Sincronização de Dados do MBI para Adobe Commerce Cloud Pro, Starter, No Local ou não Adobe Commerce<br> (API, Qualidade e formatação de dados, rede de comerciante,<br>Conexões de BD dentro e fora do BD da Adobe Commerce Cloud, acima dos limites de dados) |     | R |
| Configurando a sincronização de dados do MBI para o Adobe Commerce Cloud Pro<br> (configuração do banco de dados do Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

#### Recomendações de produto

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço Product Recommendations | R |   |
| Atualização de módulos do Product Recommendations |   | R |
| Somente a versão mais recente lançada do Product Recommendations é compatível. O comerciante deve atualizar imediatamente após cada versão. |     | R |

{style="table-layout:auto"}

#### Live Search

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do serviço Live Search | R |   |
| Atualizando módulos do Live Search |   | R |
| Somente a versão mais recente lançada do Live Search é compatível. O comerciante deve atualizar imediatamente após cada versão. |     | R |

{style="table-layout:auto"}

#### Qualidade dos dados do evento da loja

A coleção de eventos da loja aumenta a qualidade das Recomendações de produto e do Resultado do Live Search. A responsabilidade depende da implementação da loja:

|     | Adobe | Comerciante |
| --- | --- | --- |
| Tema principal (Luma) | R |   |
| Tema personalizado |  | R |
| Implementação principal do PWA | R |   |
| Implementação personalizada do PWA |  | R |
| Implementação principal do Edge Delivery Services (Commerce Boilerplate) | R |   |
| Implementação personalizada do Edge Delivery Services |   | R |
| Qualquer outra implementação personalizada de loja |  | R |

{style="table-layout:auto"}

#### Payment Services

|     | Adobe | Comerciante |
| --- | --- | --- |
| Serviço de disponibilidade de pagamentos | R |   |
| Atualizando módulos de Pagamentos |   | R |
| Somente a versão mais recente lançada dos Serviços de pagamento é compatível. O comerciante deve atualizar imediatamente após cada versão. |     | R |

{style="table-layout:auto"}

### Serviços de rede

#### Otimização de imagem

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade e qualidade da otimização de imagens | R |   |
| Configuração da otimização de imagem |     | R |

{style="table-layout:auto"}

#### Certificados SSL

|     | Adobe | Comerciante |
| --- | --- | --- |
| Expiração de certificado SSL dedicado | R |   |
| Provisionamento de certificados SSL | R |   |
| Comprar e manter certificados EV ou outros certificados SSL específicos (além dos padrões fornecidos) e fornecê-los à Adobe |     | R |

{style="table-layout:auto"}

#### Firewall de aplicativo web (WAF)

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade e configuração do WAF | R |   |
| Endereçamento de falsos positivos da regra do WAF | R |   |
| Relatórios de falsos positivos da regra do WAF |     | R |
| Ajuste de regra do WAF (NÃO SUPORTADO) |     |     |
| Logs do WAF e da CDN |     | R |

{style="table-layout:auto"}

#### DDoS

|     | Adobe | Comerciante |
| --- | --- | --- |
| Bloqueio pró-ativo de IP |     | R |
| Proteção de bot |     | R |
| Detecção de DDoS — camada 3-4 | R |   |
| Detecção de DDoS — camada 7 |     | R |
| Resposta de DDoS | R |   |

{style="table-layout:auto"}

#### PrivateLink

|     | Adobe | Comerciante |
| --- | --- | --- |
| Configurar e manter conexões PrivateLink (se usadas) com uma VPC da Adobe | R |   |
| Configurar e manter conexões PrivateLink (se usadas) com um VPC de propriedade do comerciante |     | R |
| Disponibilidade de SSH (non-PrivateLink) | R |   |
| Configuração de entrada do PrivateLink para o endpoint do Adobe Commerce Cloud Service | R |   |
| Aceitação da entrada do PrivateLink para o endpoint do Adobe Commerce Cloud Service |     | R |
| Configuração de entrada do PrivateLink para o ponto de acesso de serviço do VPC do comerciante |     | R |
| Aceitação de entrada do PrivateLink para o ponto de acesso de serviço do VPC do comerciante | R |   |
| Configuração de integrações de PrivateLink (endpoint para conta) |     | R |
| Configuração de VPC de propriedade de comerciante para o ponto de extremidade PrivateLink <br><br> (incluindo quaisquer conexões VPN) |     | R |

{style="table-layout:auto"}

### Sistema e infraestrutura

#### Servidor de aplicativos

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do Nginx | R |   |
| Configuração do Nginx | R |   |
| Qualidade contínua e aplicação de patches no Nginx | R |   |

{style="table-layout:auto"}

#### Sistema operacional

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade do sistema operacional | R |   |
| Qualidade e correção contínuas do sistema operacional | R |   |

{style="table-layout:auto"}

#### Backup, alta disponibilidade e failover

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade de snapshot e processo de backup | R |   |
| Agendando backups para ambientes de preparo e produção do Cloud Pro | R |   |
| Agendamento de backups para ambientes de integração Cloud Starter e Pro |     | R |
| Disponibilidade de HA/failover | R |   |

{style="table-layout:auto"}

#### Servidores em nuvem e dimensionamento

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidade de recursos, data center e espaço em disco da CPU | R |   |
| Disponibilidade e execução de capacidade de sobretensão ou upsizing de emergência | R |   |
| Solicitando capacidade de sobretensão |     | R |
| Monitoramento do uso da vCPU em relação aos limites | R |   |

{style="table-layout:auto"}

