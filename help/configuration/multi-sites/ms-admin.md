---
title: Configurar vários sites, lojas e visualizações de loja no Administrador
description: Configure sites, lojas e visualizações de loja adicionais no Administrador do Commerce.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: f7c82844fd6d006e4ebbcf56f6e10338f67d0bdd
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# Configurar várias exibições no Administrador

Esta tarefa requer que você crie uma categoria raiz (e categorias adicionais, se desejado) para cada loja. As tarefas discutidas neste tópico fornecem uma maneira de configurar várias lojas. Para obter informações adicionais, consulte os seguintes recursos no Guia do usuário do Commerce:

- [Categorias](https://docs.magento.com/user-guide/catalog/categories.html)
- [Adicionar sites](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Armazenar URLs](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Conteúdo](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Apenas para fins de exemplo, usamos um site francês com o código do site `french` neste tópico. Para obter tutoriais passo a passo, consulte [Tutorial: configurar vários sites com o Apache](ms-apache.md) e [Tutorial: configurar vários sites com o nginx](ms-nginx.md)

## Etapa 1: criar categorias raiz

A criação de uma categoria raiz é opcional, mas mostramos como fazer isso neste tutorial caso você queira que cada site tenha uma categoria raiz exclusiva. Você pode criar categorias adicionais, se desejar.

Para criar uma categoria raiz:

1. Faça logon no Admin como um usuário autorizado a criar categorias.
1. Clique em **Catálogo** > **Categorias**.
1. Clique em **Adicionar categoria raiz**.
1. No **Nome da categoria** insira um nome exclusivo para identificar esta categoria.
1. Certifique-se de que Ativar categoria esteja definido como **Sim**.

   Para obter informações sobre as outras opções desta página, consulte [Categorias de raiz](https://docs.magento.com/user-guide/catalog/category-root.html).

   A figura a seguir mostra um exemplo.

   ![Criar e habilitar uma categoria raiz](../../assets/configuration/add-root-category.png)

1. Clique em **Salvar**.
1. Repita essas tarefas quantas vezes forem necessárias para criar categorias raiz para suas lojas.

## Etapa 2: criar sites

Para criar um site:

1. Faça logon no Administrador como um usuário autorizado a criar sites, lojas e visualizações de loja.
1. Clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. No _Lojas_ clique em **Criar Site**.

   - **Nome**—Digite um nome para identificar o site.
   - **Código**—Digite um código exclusivo; por exemplo, se você tiver uma loja na França, poderá digitar `french`
   - **Ordem de classificação**—Informe uma ordem de classificação numérica opcional.

   A figura a seguir mostra um exemplo.

   ![Adicionar um site](../../assets/configuration/multi-site-website.png)

1. Clique em **Salvar Site**.
1. Repita essas tarefas quantas vezes forem necessárias para criar seus sites.

## Etapa 3: Criar armazenamentos

Para criar uma loja:

1. No _Admin_ clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. No _Lojas_ clique em **Criar armazenamento**.

   - **Site**—Clique no nome do site ao qual associar esta loja.
   - **Nome**—Digite um nome para identificar o armazenamento.
   - **Código**—Digite um código exclusivo para identificar o armazenamento.
   - **Categoria raiz**—Clique no nome da categoria raiz desse armazenamento.

   A figura a seguir mostra um exemplo.

   ![Adicionar uma loja](../../assets/configuration/multi-site-store.png)

1. Clique em **Salvar armazenamento**.
1. Repita essas tarefas quantas vezes forem necessárias para criar seus armazenamentos.

## Etapa 4: criar exibições de loja

Para criar uma exibição de loja:

1. No _Admin_ clique em **Lojas** > **Configurações** > **Todas as lojas**.
1. Na página Lojas, clique em **Criar visualização de loja**.

   - **Loja**—Clique no nome do armazenamento ao qual associar essa exibição de armazenamento.
   - **Nome**—Digite um nome para identificar esta exibição de loja.
   - **Código**—Digite um nome exclusivo para identificar essa exibição de loja.
   - **Status**— Select **Ativado**.

   A figura a seguir mostra um exemplo.

   ![Adicionar uma loja](../../assets/configuration/multi-site-storeview.png)

1. Clique em **Salvar visualização da loja**.
1. Repita essas tarefas quantas vezes forem necessárias para criar suas visualizações de loja.

## Etapa 5: alterar o URL base do site

Para acessar um site usando um URL exclusivo como `http://french.magento.mg`, você deve alterar a URL base de cada site no Administrador.

Para alterar o URL base do site:

1. No _Admin_ clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. No **Exibição da loja** na parte superior da página, clique no nome de um de seus sites, como mostra a figura a seguir.

   ![Selecionar um escopo](../../assets/configuration/multi-site-scope.png)

1. No painel direito, expanda **URLs base**.
1. No _URLs base_ seção, limpar **Usar valor do sistema**.
1. Insira o `http://french.magento.mg` URL no **URL base** e **URL base do link** campos.

1. Repita a etapa anterior no _URLs de base (Seguro)_ seção.

   >[!INFO]
   >
   >Se você estiver configurando um URL de base para implantação do Adobe Commerce na infraestrutura em nuvem, substitua o primeiro período por três traços. Por exemplo, se o URL base for `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, insira `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Se você estiver configurando um URL de base para testes locais, use um ponto.

1. Clique em **Salvar configuração**.

1. Repita essas tarefas para outros sites.

## Etapa 6: adicionar o código de armazenamento ao URL base

O Commerce oferece a opção de adicionar o código da loja ao URL base do site, o que simplifica o processo de configuração de várias lojas. Com essa opção, não é necessário criar diretórios no sistema de arquivos do Commerce para armazenar `index.php` e `.htaccess`.

Isso evita `index.php` e `.htaccess` de ficar fora de sincronia com a base de código do Commerce em atualizações futuras.

Consulte a [Guia do usuário do Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Para adicionar o código da loja ao URL base:

1. No _Admin_ clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.
1. No **Exibição da loja** na parte superior da página, clique em **Configuração padrão** como mostra a figura a seguir.

   ![Selecionar o escopo de configuração padrão](../../assets/configuration/multi-site-default.png)

1. No painel direito, expanda **Opções De Url**.
1. Limpe a **Usar valor do sistema** caixa de seleção ao lado de _Adicionar código da loja a URLs_.
1. No _Adicionar código da loja a URLs_ clique em **Sim**.

   ![Adicionar o código da loja à URL de base da loja](../../assets/configuration/multi-site-add-store-url.png)

1. Clique em **Salvar configuração**.
1. Se solicitado, limpe o cache. (**Sistema** > **Gerenciamento de cache**).

## Etapa 7: alterar o URL de base da exibição de loja padrão

Você deve executar esta etapa por último porque perderá o acesso ao Administrador; seu acesso retorna após configurar hosts virtuais, conforme discutido nos tópicos específicos do servidor Web.

Para alterar o URL de base da exibição de loja padrão:

1. No _Admin_ clique em **Lojas** > **Configurações** > **Configuração** > **Geral** > **Web**.

1. No _Exibição da loja_ na parte superior da página, clique em **Configuração padrão**.

   ![Selecionar o escopo de configuração padrão](../../assets/configuration/multi-site-default.png)

1. No painel direito, expanda **URLs base**.
1. No _URLs base_ seção, limpar **Usar valor do sistema**.
1. Insira o `http://magento.mg` URL no **URL base** e **URL base do link** campos.

1. Repita a etapa anterior no **URLs de base (Seguro)** seção.

   >[!INFO]
   >
   >Se você estiver configurando um URL de base para o Adobe Commerce na infraestrutura em nuvem, substitua o primeiro período por três traços. Por exemplo, se o URL base for `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, insira `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Clique em **Salvar configuração**.

>[!INFO]
>
>O código de exibição do site, da loja e da loja pode incluir somente letras (a-z ou A-Z), números (0-9) e sublinhados (_). Além disso, o primeiro caractere deve ser uma letra. Se forem usadas maiúsculas e minúsculas ou camelcase, internamente, a correspondência não diferencia maiúsculas de minúsculas para acomodar a substituição das definições de configuração por meio de variáveis de ambiente. Consulte [Usar variáveis de ambiente para substituir as definições de configuração](../reference/override-config-settings.md#environment-variables).