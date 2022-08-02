---
title: Configurar vários sites, lojas e visualizações de loja no Administrador
description: Configure sites, lojas e visualizações de loja adicionais no Administrador de comércio.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1016'
ht-degree: 0%

---


# Configurar várias exibições no Administrador

Essa tarefa requer que você crie uma categoria raiz (e categorias adicionais, se desejar) para cada loja. As tarefas discutidas neste tópico fornecem uma maneira de configurar várias lojas. Para obter mais informações, consulte os seguintes recursos no Guia do usuário do Commerce:

- [Categorias](https://docs.magento.com/user-guide/catalog/categories.html)
- [Adicionar Sites](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Armazenar URLs](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Conteúdo](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Por exemplo, usamos apenas um site em francês com código de site `french` neste tópico. Para obter tutoriais passo a passo, consulte [Tutorial: Configurar vários sites com o Apache](ms-apache.md) e [Tutorial: Configurar vários sites com o nginx](ms-nginx.md)

## Etapa 1: Criar categorias raiz

A criação de uma categoria raiz é opcional, mas mostramos como fazer isso neste tutorial no [evento](https://glossary.magento.com/event) você deseja que cada site tenha uma categoria raiz exclusiva. É possível criar categorias adicionais, se desejar.

Para criar uma categoria raiz:

1. Faça logon em Admin como um usuário autorizado a criar categorias.
1. Clique em **Catálogo** > **Categorias**.
1. Clique em **Adicionar categoria raiz**.
1. No **Nome da categoria** , insira um nome exclusivo para identificar essa categoria.
1. Certifique-se de que Ativar categoria esteja definido como **Sim**.

   Para obter informações sobre as outras opções nesta página, consulte [Categorias de raiz](https://docs.magento.com/user-guide/catalog/category-root.html).

   A figura a seguir mostra um exemplo.

   ![Criar e ativar uma categoria raiz](../../assets/configuration/add-root-category.png)

1. Clique em **Salvar**.
1. Repita essas tarefas quantas vezes forem necessárias para criar categorias raiz para suas lojas.

## Etapa 2: Criar sites

Para criar um site:

1. Faça logon em Admin como um usuário autorizado a criar sites, lojas e armazenar visualizações.
1. Clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. No _Lojas_ página, clique em **Criar Site**.

   - **Nome**—Digite um nome para identificar o site.
   - **Código**—Digite um código exclusivo; por exemplo, se você tiver uma loja em francês, poderá inserir `french`
   - **Ordem de classificação**—Digite uma ordem de classificação numérica opcional.

   A figura a seguir mostra um exemplo.

   ![Adicionar um site](../../assets/configuration/multi-site-website.png)

1. Clique em **Salvar Site**.
1. Repita essas tarefas quantas vezes forem necessárias para criar seus sites.

## Etapa 3: Criar armazenamentos

Para criar uma loja:

1. No _Administrador_ painel, clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. No _Lojas_ página, clique em **Criar Loja**.

   - **Site**—Clique no nome do site ao qual associar esta loja.
   - **Nome**—Digite um nome para identificar o armazenamento.
   - **Código**—Insira um código exclusivo para identificar o armazenamento.
   - **Categoria raiz**—Clique no nome da categoria raiz para este armazenamento.

   A figura a seguir mostra um exemplo.

   ![Adicionar uma loja](../../assets/configuration/multi-site-store.png)

1. Clique em **Salvar armazenamento**.
1. Repita essas tarefas quantas vezes forem necessárias para criar suas lojas.

## Etapa 4: Criar visualizações de loja

Para criar uma exibição de loja:

1. No _Administrador_ painel, clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. Na página Lojas , clique em **Criar exibição de loja**.

   - **Loja**—Clique no nome da loja à qual associar esta vista de loja.
   - **Nome**—Digite um nome para identificar essa exibição de loja.
   - **Código**—Digite um nome exclusivo para identificar essa exibição de loja.
   - **Status**—Select **Ativado**.

   A figura a seguir mostra um exemplo.

   ![Adicionar uma loja](../../assets/configuration/multi-site-storeview.png)

1. Clique em **Salvar Exibição da Loja**.
1. Repita essas tarefas quantas vezes forem necessárias para criar suas exibições de loja.

## Etapa 5: Alterar o URL de base do site

Para acessar um site usando um URL exclusivo como `http://french.magento.mg`, é necessário alterar o URL básico de cada site no Administrador.

Para alterar o URL de base do site:

1. No _Administrador_ painel, clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. No **Exibição da loja** na parte superior da página, clique no nome de um de seus sites, conforme a figura a seguir mostra.

   ![Selecionar um escopo](../../assets/configuration/multi-site-scope.png)

1. No painel direito, expanda **URLs básicos**.
1. No _URLs básicos_ seção, limpar **Usar valor do sistema**.
1. Insira o `http://french.magento.mg` O URL na **URL básica** e **URL do link básico** campos.

1. Repita as etapas anteriores na _URLs básicos (seguros)_ seção.

   >[!INFO]
   >
   >Se você estiver configurando um URL básico para implantação do Adobe Commerce na infraestrutura de nuvem, é necessário substituir o primeiro período por três traços. Por exemplo, se o URL de base for `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, insira `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Se você estiver configurando um URL básico para testes locais, use um ponto.

1. Clique em **Salvar configuração**.

1. Repita essas tarefas para outros sites.

## Etapa 6: Adicionar o código de armazenamento ao URL base

O Commerce oferece a opção de adicionar o código da loja ao URL de base do site, o que simplifica o processo de configuração de várias lojas. Com essa opção, não é necessário criar diretórios no sistema de arquivos do Commerce para armazenar `index.php` e `.htaccess`.

Isso evita `index.php` e `.htaccess` de sair de sincronia com a base de código do Commerce em atualizações futuras.

Consulte a [Guia do usuário do Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Para adicionar o código de armazenamento ao URL de base:

1. No _Administrador_ painel, clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. No **Exibição da loja** na parte superior da página, clique em **Configuração padrão** como mostra a figura a seguir.

   ![Selecione o escopo de configuração padrão](../../assets/configuration/multi-site-default.png)

1. No painel direito, expanda **Opções De Url**.
1. Limpe o **Usar valor do sistema** caixa de seleção ao lado de _Adicionar código de armazenamento aos URLs_.
1. No _Adicionar código de armazenamento aos URLs_ listar, clique em **Sim**.

   ![Adicionar o código de armazenamento ao URL de base da loja](../../assets/configuration/multi-site-add-store-url.png)

1. Clique em **Salvar configuração**.
1. Se solicitado, libere o cache. (**Sistema** > **Gerenciamento de cache**).

## Etapa 7: Alterar o URL de base da exibição de loja padrão

Você deve executar essa etapa por último, pois perderá o acesso ao Administrador; seu acesso retorna depois de configurar hosts virtuais, como discutido nos tópicos específicos do servidor da Web.

Para alterar o URL de base da exibição de loja padrão:

1. No _Administrador_ painel, clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.

1. No _Exibição da loja_ na parte superior da página, clique em **Configuração padrão**.

   ![Selecione o escopo de configuração padrão](../../assets/configuration/multi-site-default.png)

1. No painel direito, expanda **URLs básicos**.
1. No _URLs básicos_ seção, limpar **Usar valor do sistema**.
1. Insira o `http://magento.mg` O URL na **URL básica** e **URL do link básico** campos.

1. Repita as etapas anteriores na **URLs básicos (seguros)** seção.

   >[!INFO]
   >
   >Se você estiver configurando um URL básico para Adobe Commerce na infraestrutura de nuvem, é necessário substituir o primeiro período por três traços. Por exemplo, se o URL de base for `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, insira `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Clique em **Salvar configuração**.
