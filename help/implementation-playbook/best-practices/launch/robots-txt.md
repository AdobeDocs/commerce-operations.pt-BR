---
title: Práticas recomendadas para configurar crawlers da Web
description: Saiba como transmitir instruções sobre o site do Adobe Commerce para rastreadores da Web usando os arquivos "robots.txt" e "sitemap.xml".
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Práticas recomendadas para configurar crawlers da Web

Este artigo fornece práticas recomendadas para usar arquivos do `robots.txt` e do `sitemap.xml` no Adobe Commerce, incluindo configuração e segurança. Esses arquivos instruem os rastreadores da Web (geralmente robôs de mecanismo de pesquisa) a rastrear páginas em um site. A configuração desses arquivos pode melhorar o desempenho do site e a otimização do mecanismo de pesquisa.

>[!NOTE]
>
>Essas práticas recomendadas se aplicam aos projetos que usam somente a loja nativa do Adobe Commerce. Eles não se aplicam a projetos da Adobe Commerce que usam outras soluções da loja (por exemplo, Adobe Experience Manager, headless).

## Produtos e versões afetados

[Todas as versões ](../../../release/versions.md) com suporte de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Adobe Commerce na infraestrutura em nuvem

Um projeto padrão do Adobe Commerce contém uma hierarquia que inclui uma única visualização de site, loja e loja. Para implementações mais complexas, você pode criar sites adicionais, lojas e visualizações de loja para uma loja _com vários sites_.

### Lojas de um único site

Siga estas práticas recomendadas ao configurar os arquivos `robots.txt` e `sitemap.xml` para vitrines de site único:

- Verifique se o projeto está usando o [`ece-tools`](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) versão 2002.0.12 ou posterior.
- Use o aplicativo Administrador para adicionar conteúdo ao arquivo `robots.txt`.

  >[!TIP]
  >
  >Exiba o arquivo `robots.txt` gerado automaticamente para seu armazenamento em `<domain.your.project>/robots.txt`.

- Use o aplicativo de Administração para gerar um arquivo `sitemap.xml`.

  >[!IMPORTANT]
  >
  >Devido ao sistema de arquivos somente leitura no Adobe Commerce em projetos de infraestrutura em nuvem, você deve especificar o caminho `pub/media` antes de gerar o arquivo.

- Use um trecho Fastly VCL personalizado para redirecionar da raiz do site para o local `pub/media/` para ambos os arquivos:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Teste o redirecionamento visualizando os arquivos em um navegador da Web. Por exemplo, `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Verifique se você está usando o caminho raiz para o qual você configurou o redirecionamento e não um caminho diferente.

>[!INFO]
>
>Consulte [Adicionar o mapa do site e os robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/robots-sitemap) para obter instruções detalhadas.


### Lojas de vários sites

Você pode configurar e executar várias lojas com uma única implementação do Adobe Commerce na infraestrutura em nuvem. Consulte [Configurar vários sites ou lojas](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites).

As mesmas práticas recomendadas para configurar os arquivos `robots.txt` e `sitemap.xml` para [vitrines de site único](#single-site-storefronts) aplicam-se a vitrines de vários sites com duas diferenças importantes:

- Verifique se os nomes de arquivo `robots.txt` e `sitemap.xml` contêm os nomes dos sites correspondentes. Por exemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Use um trecho Fastly VCL personalizado modificado para redirecionar da raiz de seus sites para o local `pub/media` para ambos os arquivos em seus sites:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce no local

Use o aplicativo de Administração para configurar os arquivos `robots.txt` e `sitemap.xml` para impedir que os bots verifiquem e indexem conteúdo desnecessário (consulte [Robôs do Mecanismo de Pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Para implantações locais, onde você grava os arquivos depende de como você instalou o Adobe Commerce. Grave os arquivos em `/path/to/commerce/pub/media/` ou `/path/to/commerce/media`, o que for certo para a sua instalação.

## Segurança

Não exponha o caminho de Administrador no arquivo `robots.txt`. Ter o caminho de administrador exposto é uma vulnerabilidade para hackers no site e perda potencial de dados. Remova o caminho Admin do arquivo `robots.txt`.

Para obter as etapas para editar o arquivo `robots.txt` e remover todas as entradas do caminho de Administrador, consulte [Guia do Usuário de Marketing > SEO e Pesquisa > Robôs do Mecanismo de Pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se precisar de ajuda, [envie um tíquete de Suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informações adicionais

- [Compreendendo sites, lojas e exibições de loja](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Adicionando sites](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Use o Fastly para bloquear o tráfego mal-intencionado nos sites do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-blocking)
- [robots.txt fornece um erro 404 no Adobe Commerce na infraestrutura de nuvem 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
