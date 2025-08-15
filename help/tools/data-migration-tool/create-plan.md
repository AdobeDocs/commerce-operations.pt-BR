---
title: Criar um plano de migração de dados
description: Siga estas etapas para criar um plano de migração de dados e garantir um upgrade bem-sucedido do Magento 1 para o Magento 2.
exl-id: a14237f3-c5fe-4f5f-86eb-ed4c39507bff
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Criar um plano de migração de dados

Para migrar com sucesso e evitar problemas, é necessário planejar e testar minuciosamente a migração.

## Antes de começar: considere atualizar

A migração é um momento perfeito para fazer alterações sérias e preparar seu site para o próximo nível de crescimento. Considere se o novo site precisa ser projetado com mais hardware ou uma topologia mais avançada com melhores níveis de cache.

## Etapa 1: revisar extensões no site atual

* Quais extensões você instalou?

* Você identificou se precisa de todas essas extensões no novo site? Pode haver arquivos antigos que você pode remover com segurança.

* Você determinou se existem versões Magento 2 de suas extensões? Visite o [Commerce Marketplace] para encontrar as versões mais recentes ou contate seu provedor de extensão.

* Quais ativos de banco de dados de suas extensões você deseja migrar?

## Etapa 2: criar e preparar seu armazenamento para migração

* Configure um sistema de hardware Magento 2 usando topologia e design que corresponda pelo menos ao seu sistema Magento 1 existente

* Instale o Magento 2.x (com todos os módulos desta versão) e o [!DNL Data Migration Tool] em um sistema que atenda aos [requisitos de sistema](../../installation/system-requirements.md)

* Faça ajustes personalizados no código [!DNL Data Migration Tool] caso não precise migrar alguns dados (como Páginas do CMS, Regras de vendas) ou queira converter a personalização do Magento durante a migração. Leia a [!DNL Data Migration Tool]Especificação Técnica[ do ](technical-specification.md) para entender melhor como a migração funciona de dentro

## Etapa 3: simulação

Antes de iniciar a migração no ambiente de produção, seria melhor passar por todas as etapas de migração no ambiente de teste.

Nesses testes de migração, siga estas etapas:

* Copiar o armazenamento do Magento 1 para um servidor de preparo

* Migrar totalmente o armazenamento replicado do Magento 1 para o Magento 2

* Teste minuciosamente seu novo armazenamento

## Etapa 4: iniciar a migração

1. Verifique se o [!DNL Data Migration Tool] tem acesso de rede para se conectar aos bancos de dados Magento 1 e Magento 2. Abra as portas correspondentes no firewall.

1. Interrompa todas as atividades no Painel de administração do Magento 1.x (exceto gerenciamento de pedidos), como remessa, criação de faturas e avisos de crédito. A lista de atividades permitidas pode ser estendida ajustando as configurações do modo Delta no [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Você não deve retomar essas atividades até que sua loja do Magento 2 entre em funcionamento.

1. Recomendamos interromper todos os trabalhos do Magento 1.x cron.

   Ainda assim, se alguns trabalhos forem necessários para execução durante a migração, certifique-se de que eles não criem novas entidades de banco de dados ou alterem as existentes de forma que tais entidades não possam ser processadas pelo modo Delta.

   Por exemplo, o trabalho cron `enterprise_salesarchive_archive_orders` move pedidos antigos para o arquivo morto. A execução desse trabalho durante a migração é segura porque o modo Delta reconhece esse trabalho e processa corretamente as ordens arquivadas.

1. Use o [!DNL Data Migration Tool] para migrar configurações e sites.

1. Copie os arquivos de mídia do Magento 1.x para o Magento 2.x.

   Você deve copiar esses arquivos manualmente do diretório `magento1-root/media` para `magento2-root/pub/media`.

1. Use o [!DNL Data Migration Tool] para copiar seus dados em massa do banco de dados Magento 1 para o banco de dados Magento 2.

   Se algumas de suas extensões tiverem dados que você deseja migrar, talvez seja necessário instalar essas extensões adaptadas para o Magento 2. Caso as extensões tenham uma estrutura diferente no banco de dados do Magento 2, use os arquivos de mapeamento fornecidos com o [!DNL Data Migration Tool].

1. Reindexe todos os indexadores do Magento 2.x. Para obter detalhes, consulte o [Gerenciar indexadores](../../configuration/cli/manage-indexers.md) no _Guia de configuração_.

## Etapa 5: Fazer alterações nos dados migrados (se necessário)

Às vezes, você pode querer que seu Magento 2 armazene com diferentes estruturas de catálogo, regras de vendas e páginas do CMS após a migração.

É importante ter cuidado ao trabalhar com alterações manuais de dados. Erros criam erros na etapa de migração de dados incremental a seguir.

Por exemplo, um produto excluído do Magento 2: aquele que foi comprado na loja do Magento 1 em tempo real e que não está mais disponível na loja do Magento 2. A transferência de dados sobre essa compra pode causar um erro ao executar o [!DNL Data Migration Tool] no modo Delta.

## Etapa 6: atualizar dados incrementais

Depois de migrar os dados, você deve capturar de forma incremental as atualizações de dados que foram adicionadas ao armazenamento do Magento 1 (como novos pedidos, revisões e alterações nos perfis do cliente) e transferir essas atualizações para o armazenamento do Magento 2 usando o modo Delta.

* Inicie a migração incremental; as atualizações são executadas continuamente. Você pode parar de transferir atualizações a qualquer momento pressionando `Ctrl+C`.

* Teste o site do Magento 2 durante esse período para detectar problemas o mais rápido possível. Se você encontrar problemas, pressione `Ctrl+C` para interromper a migração incremental e iniciá-la novamente após resolvê-los.

>[!NOTE]
>
>Avisos de verificação de volume podem ser exibidos caso você realize testes no site do Magento 2 e execute o processo de migração ao mesmo tempo. Isso acontece porque no Magento 2 você cria entidades que não existem na instância do Magento 1.

## Etapa 7: ativação

Agora que seu site do Magento 2 está atualizado com o Magento 1 e está funcionando normalmente, faça o seguinte para mudar para o novo site:

1. Coloque seu sistema Magento 1 no modo de manutenção (INICIALIZAÇÃO).

1. Pressione Control+C na janela de comando da ferramenta de migração para interromper atualizações incrementais.

1. Inicie seus trabalhos cron do Magento 2.

1. No sistema Magento 2, reindexe o indexador de ações. Para obter mais informações, consulte o [Guia de configuração].

1. Usando uma ferramenta de sua escolha, acesse páginas em seu sistema Magento 2 para armazenar páginas em cache antes dos clientes que usam sua loja.

1. Faça qualquer verificação final no site do Magento 2.

1. Altere o DNS, os balanceadores de carga e assim por diante para apontar para o novo hardware de produção (DOWNTIME ENDS).

1. A loja do Magento 2 está pronta para uso. Você e seus clientes podem retomar todas as atividades.

<!-- LINK ADDRESSES -->

[Commerce Marketplace]: https://marketplace.magento.com
