---
title: Visão geral da instalação local
description: Saiba mais sobre o processo de instalação local do Adobe Commerce. Descubra os requisitos do servidor, as etapas de configuração e as práticas recomendadas de implantação.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 062267b8b06e41d89f704144e640fc1254952532
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Visão geral da instalação local

Esta página fornece uma visão geral da instalação do Adobe Commerce em sua própria infraestrutura. O processo de instalação envolve a configuração do ambiente do servidor, a obtenção do software e das credenciais necessárias e a execução do comando de instalação.

Você pode instalar o software Adobe Commerce no local em aproximadamente 30 a 60 minutos. No entanto, o tempo necessário para configurar o ambiente do servidor antes da instalação varia de acordo com a sua experiência e as tecnologias selecionadas.

>[!TIP]
>
>Você deve ter conhecimento técnico intermediário e acesso ao servidor para prosseguir com êxito.

A instalação cria um armazenamento do Adobe Commerce totalmente funcional com uma [vitrine voltada para o cliente](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/storefront/storefront) e um [painel administrativo](https://experienceleague.adobe.com/pt-br/docs/commerce-admin/start/admin/admin). Você deve ter suas credenciais de banco de dados, informações de domínio e chaves de autenticação prontas antes de iniciar o processo.

## Responsabilidades do comerciante

Com o Adobe Commerce no local, você hospeda e gerencia sua própria infraestrutura, incluindo servidores, ambientes de hospedagem e manutenção do sistema. A Adobe fornece suporte específico para o aplicativo principal do Commerce, incluindo:

- Acesso a atualizações e correções de produtos
- Patches de segurança para lidar com vulnerabilidades
- Documentação abrangente para ajudá-lo a gerenciar e otimizar sua solução de auto-hospedagem

Você tem controle total sobre seu ambiente, permitindo maior personalização e flexibilidade, mas é responsável por garantir o desempenho, a segurança e a escalabilidade da infraestrutura. Por exemplo, você é responsável pelo seguinte:

- O design, a implementação, a configuração, a manutenção, a solução de problemas e os testes de desempenho de todos os sistemas Adobe Commerce no local.
   - Servidores, sistema operacional, bancos de dados, [!DNL PHP], pesquisa, armazenamento em cache, cache de página inteira e rede de entrega de conteúdo. Temas comuns podem incluir (mas não limitados a) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] e qualquer [!DNL CDN] usado.
- Planejamento de capacidade, dimensionamento automático, clustering, backups, recuperação de desastres
- Todos os dados do produto e do cliente, projeto, configuração e instalação, manutenção de aplicativos e bancos de dados, implantação de código, atualizações de versão e aplicativo de patch
- Monitoramento e alerta via APM/logging/alerting (por exemplo, [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Patch de segurança para sistema operacional, [!DNL PHP], banco de dados, proteção e atualizações de middleware

## Fluxo de trabalho (WRK)

O diagrama a seguir ilustra as principais etapas envolvidas na instalação do Adobe Commerce para ambientes locais:

![Como funciona a instalação](../assets/installation/on-premises-install.drawio.svg)

### Configurar o ambiente do servidor

Instale e configure o PHP, o servidor Web, o banco de dados e o mecanismo de pesquisa de acordo com os [pré-requisitos](prerequisites/overview.md).

### Obter chaves de autenticação

Gere novas [chaves de autenticação](prerequisites/authentication-keys.md) (ou copie as chaves existentes) do Commerce Marketplace para acessar os pacotes do Adobe Commerce Composer.

### Obtenha o software Adobe Commerce

Baixe usando o [Composer](prerequisites/commerce.md) (recomendado) ou clone do GitHub para contribuições de desenvolvimento.

Se você deseja contribuir com a base de código do Magento Open Source ou personalizar o aplicativo, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) o repositório do GitHub. Este método requer familiaridade com o GitHub e o Composer.

### Instalar o aplicativo

Execute o comando de instalação com a configuração específica. Consulte o [início rápido](composer.md) para obter exemplos completos.

>[!NOTE]
>
>Se as etapas falharem porque o software de pré-requisito não está configurado corretamente, verifique os [pré-requisitos](prerequisites/overview.md).

### Verificar a instalação

[Teste](next-steps/verify.md) sua vitrine e o painel de administração para garantir que tudo funcione corretamente.

## Problemas comuns de instalação

- **Erros de permissão**: verifique a propriedade e as permissões adequadas do sistema de arquivos
- **Falhas de conexão do banco de dados**: verifique as credenciais do banco de dados e a conectividade da rede
- **Erros de chave de autenticação**: confirme se suas chaves do Commerce Marketplace são válidas e estão ativas
- **Limites de memória**: garantir alocação suficiente de memória do PHP (mínimo de 2 GB recomendado)
