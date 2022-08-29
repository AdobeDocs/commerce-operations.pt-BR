---
title: Criar um plano de migração de dados
description: Siga estas etapas para criar um plano de migração de dados para garantir uma atualização bem-sucedida do Magento 1 para o Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 0%

---


# Criar um plano de migração de dados

Para migrar com sucesso e evitar problemas, é necessário planejar e testar completamente sua migração.

## Antes de começar: Considere a atualização

A migração é um momento perfeito para fazer mudanças sérias e preparar seu site para o próximo nível de crescimento. Considere se o novo site precisa ser projetado com mais hardware ou uma topologia mais avançada com melhores níveis de armazenamento em cache.

## Etapa 1: Revisar extensões no seu site atual

* Quais extensões você instalou?

* Você identificou se precisa de todas essas extensões no novo site? Pode haver velhos que você possa remover com segurança.

* Você determinou se as versões do Magento 2 das extensões existem? Visita [Commerce Marketplace] para encontrar as versões mais recentes ou entrar em contato com seu provedor de extensão.

* Quais ativos de banco de dados das extensões você deseja migrar?

## Etapa 2: Crie e prepare sua loja para migração

* Configure um sistema de hardware Magento 2 usando topologia e design que pelo menos correspondam ao seu sistema Magento 1 existente

* Instale o Magento 2.x (com todos os módulos desta versão) e a [!DNL Data Migration Tool] em um sistema que atenda à [Requisitos do sistema Magento]

* Faça os ajustes personalizados na [!DNL Data Migration Tool] caso não precise migrar alguns dados (como Páginas CMS, Regras de vendas) ou queira converter a personalização do Magento durante a migração. Leia o [!DNL Data Migration Tool]&#39;s [Especificação técnica](technical-specification.md) para entender melhor como a migração funciona de dentro

## Etapa 3: Execução seca

Antes de iniciar a migração no ambiente de produção, seria melhor passar por todas as etapas de migração no ambiente de teste.

Em tais testes de migração, siga estas etapas:

* Copiar sua loja do Magento 1 para um servidor de preparo

* Migrar totalmente o armazenamento do Magento 1 replicado para o Magento 2

* Teste completamente sua nova loja

## Etapa 4: Inicie sua migração

1. Certifique-se de que a variável [!DNL Data Migration Tool] O tem acesso de rede para se conectar aos bancos de dados Magento 1 e Magento 2. Abra as portas correspondentes no firewall.

1. Pare todas as atividades no Painel de administração do Magento 1.x (exceto para o gerenciamento de pedidos), como remessa, criação de faturas e avisos de crédito. A lista de atividades permitidas pode ser estendida ajustando as configurações do modo Delta no [!DNL Data Migration Tool].

   >[!NOTE]
   >
   >Você não deve retomar essas atividades até que a loja do Magento 2 entre em funcionamento.

1. Recomendamos interromper todos os trabalhos do Magento 1.x cron.

   Ainda assim, se for necessário executar algumas tarefas durante a migração, certifique-se de que elas não criem novas entidades de banco de dados ou alterem as existentes da maneira que essas entidades não possam ser processadas pelo modo Delta.

   Por exemplo, a variável `enterprise_salesarchive_archive_orders` o trabalho cron move pedidos antigos para arquivamento. A execução deste trabalho durante a migração é segura porque o modo Delta reconhece este trabalho e processa corretamente os pedidos arquivados.

1. Use o [!DNL Data Migration Tool] para migrar configurações e sites.

1. Copie os arquivos de mídia do Magento 1.x para o Magento 2.x.

   Você deve copiar esses arquivos manualmente do `magento1-root/media` direcionar para `magento2-root/pub/media`.

1. Use o [!DNL Data Migration Tool] para copiar seus dados do banco de dados do Magento 1 para o banco de dados do Magento 2 em massa.

   Se algumas de suas extensões tiverem dados que você deseja migrar, talvez seja necessário instalar essas extensões adaptadas para o Magento 2. Caso as extensões tenham uma estrutura diferente no banco de dados do Magento 2, use os arquivos de mapeamento fornecidos com o [!DNL Data Migration Tool].

1. Reindexe todos os indexadores Magento 2.x. Para obter detalhes, consulte o [Guia de configuração].

## Etapa 5: Faça alterações nos dados migrados (se necessário)

Às vezes, você pode querer ter seu Magento 2 armazenado com estrutura de catálogo, regras de vendas e páginas CMS diferentes após a migração.

É importante ter cuidado ao trabalhar com alterações manuais de dados. Erros criam erros na etapa de migração de dados incremental a seguir.

Por exemplo, um produto excluído do Magento 2: aquele que foi comprado em sua loja de Magento 1 ativa e que não está mais disponível em sua loja de Magento 2. A transferência de dados sobre essa compra pode causar um erro ao executar o [!DNL Data Migration Tool] no modo Delta.

## Etapa 6: Atualizar dados incrementais

Depois de migrar os dados, você deve capturar de forma incremental as atualizações de dados que foram adicionadas ao armazenamento do Magento 1 (como novos pedidos, revisões e alterações nos perfis do cliente) e transferir essas atualizações para o armazenamento do Magento 2 usando o modo Delta.

* Iniciar a migração incremental; as atualizações são executadas continuamente. Você pode interromper a transferência de atualizações a qualquer momento pressionando `Ctrl+C`.

* Teste seu site de Magento 2 durante esse período para capturar qualquer problema o mais rápido possível. Se encontrar problemas, prima `Ctrl+C` para interromper a migração incremental e reiniciá-la depois de resolver os problemas.

>[!NOTE]
>
>Avisos de verificação de volume podem aparecer caso você realize testes do site do Magento 2 e execute o processo de migração ao mesmo tempo. Isso ocorre porque no Magento 2 você cria entidades que não existem na instância do Magento 1.

## Etapa 7: Ativa

Agora que seu site de Magento 2 está atualizado com o Magento 1 e está funcionando normalmente, faça o seguinte para recortar para o novo site:

1. Coloque seu sistema de Magento 1 no modo de manutenção (INÍCIO DO DOWNTIME).

1. Pressione Control+C na janela de comando da ferramenta de migração para interromper atualizações incrementais.

1. Inicie os trabalhos do Magento 2 cron.

1. No seu sistema Magento 2, reindexe o indexador de estoque. Para obter mais informações, consulte o [Guia de configuração].

1. Usando uma ferramenta de sua escolha, clique em páginas no sistema Magento 2 para armazenar em cache páginas antes de clientes que usam sua loja.

1. Execute qualquer verificação final do site Magento 2.

1. Altere o DNS, balanceadores de carga e assim por diante para apontar para o novo hardware de produção (DOWNTIME ENDS).

1. Agora a loja de Magento 2 está pronta para ser usada. Você e seus clientes podem retomar todas as atividades.

<!-- LINK ADDRESSES -->
[Requisitos do sistema Magento]: https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html
[Commerce Marketplace]: https://marketplace.magento.com
[Guia de configuração]: https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html
