---
title: Visão geral da instalação local
description: Saiba mais sobre o processo de instalação de implantações locais do Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 7cc77a204d2a3c0773e6a0ab60e57e6e35f12091
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---


# Visão geral da instalação local

Esta página fornece uma visão geral da instalação do Adobe Commerce em sua própria infraestrutura. O processo de instalação envolve a configuração do ambiente do servidor, a obtenção do software e das credenciais necessárias e a execução do comando de instalação.

Você pode instalar o software Adobe Commerce em aproximadamente 30 a 60 minutos. No entanto, o tempo necessário para configurar o ambiente do servidor antes da instalação varia de acordo com a sua experiência e as tecnologias selecionadas.

>[!TIP]
>
>Você deve ter conhecimento técnico intermediário e acesso ao servidor para prosseguir com êxito.

A instalação cria um armazenamento do Adobe Commerce totalmente funcional com uma [vitrine voltada para o cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) e um [painel administrativo](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin). Você deve ter suas credenciais de banco de dados, informações de domínio e chaves de autenticação prontas antes de iniciar o processo.

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
