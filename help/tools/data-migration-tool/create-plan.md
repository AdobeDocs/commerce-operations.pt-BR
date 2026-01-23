---
title: Criar um plano de migração de dados
description: Saiba como criar um plano de migração de dados para atualizar do Magento 1 para o Magento 2. Planeje e teste sua migração para evitar problemas.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---

# Criar um plano de migração de dados

Para migrar com sucesso e evitar problemas, é necessário planejar e testar a migração.

## Antes de começar: considere uma atualização

A migração é um bom momento para fazer alterações sérias e preparar seu site para o próximo nível de crescimento. Considere se o novo site precisa ser projetado com hardware adicional ou uma topologia mais avançada com melhores níveis de cache.

## Etapa 1: revisar extensões no site atual

* Quais extensões você instalou?

* Você identificou se precisa de todas essas extensões no novo site? Pode haver arquivos antigos que você pode remover com segurança.

* Você determinou se existem versões Magento 2 de suas extensões? Visite o [Commerce Marketplace](https://commercemarketplace.adobe.com/) para encontrar as versões mais recentes ou contate seu provedor de extensão.

* Quais ativos de banco de dados de suas extensões você deseja migrar?

## Etapa 2: criar e preparar seu armazenamento para migração

* Configure um sistema de hardware Magento 2 usando uma topologia e um design que correspondam pelo menos ao seu sistema Magento 1 existente

* Instale o Magento 2 (com todos os módulos desta versão) e o [!DNL Data Migration Tool] em um sistema que atenda aos [requisitos de sistema](../../installation/system-requirements.md)

* Personalize o código [!DNL Data Migration Tool] para ignorar determinados dados (como páginas do CMS, regras de vendas) ou converter personalizações durante a migração. Leia a [!DNL Data Migration Tool]Especificação técnica[&#x200B; do &#x200B;](technical-specification.md) para saber mais sobre como funciona a migração

## Etapa 3: simulação

Antes de iniciar a migração no ambiente de produção, passe por todas as etapas de migração no ambiente de teste.

Nesses testes de migração, siga estas etapas:

* Copiar o armazenamento do Magento 1 para um servidor de preparo

* Migrar totalmente o armazenamento replicado do Magento 1 para o Magento 2

* Teste minuciosamente seu novo armazenamento

## Etapa 4: iniciar a migração

1. Verifique se o [!DNL Data Migration Tool] tem acesso de rede para se conectar aos bancos de dados Magento 1 e Magento 2. Abra as portas correspondentes no firewall.

1. Interrompa todas as atividades no Painel de administração do Magento 1 (exceto Order Management), como remessa, criação de NFFs e avisos de crédito. A lista de atividades permitidas pode ser estendida ajustando as configurações do modo Delta no [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Não retome essas atividades até que sua loja do Magento 2 entre em funcionamento.

1. Recomendamos interromper todos os trabalhos do Magento 1 cron.

   Se alguns trabalhos precisarem ser executados durante a migração, certifique-se de que eles não criem ou modifiquem entidades de banco de dados de maneiras que o modo Delta não possa ser processado.

   Por exemplo, o trabalho cron `enterprise_salesarchive_archive_orders` move pedidos antigos para o arquivo morto. A execução desse trabalho durante a migração é segura porque o modo Delta reconhece esse trabalho e processa corretamente as ordens arquivadas.

1. Use o [!DNL Data Migration Tool] para migrar configurações e sites.

1. Copie os arquivos de mídia do Magento 1 para o Magento 2.

   Copie esses arquivos manualmente do diretório `magento1-root/media` para `magento2-root/pub/media`.

1. Use o [!DNL Data Migration Tool] para copiar seus dados em massa do banco de dados Magento 1 para o banco de dados Magento 2.

   Se algumas de suas extensões tiverem dados que você deseja migrar, talvez seja necessário instalar essas extensões adaptadas para o Magento 2. Caso as extensões tenham uma estrutura diferente no banco de dados do Magento 2, use os arquivos de mapeamento fornecidos com o [!DNL Data Migration Tool].

1. Reindexe todos os indexadores do Magento 2. Para obter detalhes, consulte [Gerenciar indexadores](../../configuration/cli/manage-indexers.md) no _Guia de configuração_.

## Etapa 5: Fazer alterações nos dados migrados (se necessário)

Às vezes, você pode querer que seu Magento 2 armazene com diferentes estruturas de catálogo, regras de vendas e páginas do CMS após a migração.

É importante ter cuidado ao trabalhar com alterações manuais de dados. Erros criam erros na etapa de migração de dados incremental a seguir.

Por exemplo, um produto excluído do Magento 2: aquele que foi comprado na loja do Magento 1 em tempo real e que não está mais disponível na loja do Magento 2. A transferência de dados sobre essa compra pode causar um erro ao executar o [!DNL Data Migration Tool] no modo Delta.

## Etapa 6: atualizar dados incrementais

Depois de migrar os dados, use o modo Delta para capturar e transferir atualizações incrementais da Magento 1 (como novos pedidos, revisões e alterações no perfil do cliente) para a Magento 2.

* Inicie a migração incremental; as atualizações são executadas continuamente. Você pode parar de transferir atualizações a qualquer momento pressionando `Ctrl+C`.

* Teste o site do Magento 2 durante esse período para detectar problemas o mais rápido possível. Se você encontrar problemas, pressione `Ctrl+C` para interromper a migração incremental e iniciá-la novamente após resolvê-los.

>[!NOTE]
>
>Avisos de verificação de volume podem ser exibidos caso você realize testes no site do Magento 2 e execute o processo de migração ao mesmo tempo. Isso acontece porque no Magento 2 você cria entidades que não existem na instância do Magento 1.

## Etapa 7: ativação

Quando o site do Magento 2 estiver totalmente migrado e funcionando normalmente, conclua a transferência:

1. Coloque seu sistema Magento 1 no modo de manutenção (INICIALIZAÇÃO).

1. Pressione Control+C na janela de comando da ferramenta de migração para interromper atualizações incrementais.

1. Inicie seus trabalhos cron do Magento 2.

1. No sistema Magento 2, reindexe o indexador de ações. Para obter mais informações, consulte [Gerenciar indexadores](../../configuration/cli/manage-indexers.md) no _Guia de configuração_.

1. Usando uma ferramenta de sua escolha, acesse páginas em seu sistema Magento 2 para armazenar páginas em cache antes dos clientes que usam sua loja.

1. Faça qualquer verificação final no site do Magento 2.

1. Altere o DNS, os balanceadores de carga e assim por diante para apontar para o novo hardware de produção (DOWNTIME ENDS).

1. A loja do Magento 2 está pronta para uso. Você e seus clientes podem retomar todas as atividades.
