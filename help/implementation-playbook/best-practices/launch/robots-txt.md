---
title: Práticas recomendadas para configurar os arquivos "robots.txt" e "sitemap.xml"
description: Saiba como transmitir instruções sobre o site do Adobe Commerce para rastreadores da Web.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Práticas recomendadas para configuração `robots.txt` e `sitemap.xml` arquivos

Este artigo fornece práticas recomendadas para usar o `robots.txt` e `sitemap.xml` arquivos no Adobe Commerce, incluindo configuração e segurança. Esses arquivos instruem os robôs da Web (geralmente robôs de mecanismo de pesquisa) a rastrear páginas em um site. A configuração desses arquivos pode melhorar o desempenho do site e a otimização do mecanismo de pesquisa.

>[!NOTE]
>
>Essas práticas recomendadas se aplicam aos projetos que usam somente a loja nativa do Adobe Commerce. Eles não se aplicam a projetos da Adobe Commerce que usam outras soluções da loja (por exemplo, Adobe Experience Manager, headless).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

## Adobe Commerce na infraestrutura em nuvem

Um projeto padrão do Adobe Commerce contém uma hierarquia que inclui uma única visualização de site, loja e loja. Para implementações mais complexas, é possível criar sites, lojas e visualizações de loja adicionais para uma _vários sites_ vitrine eletrônica.

### Lojas de um único site

Siga estas práticas recomendadas ao configurar o `robots.txt` e `sitemap.xml` arquivos para vitrines de site único:

- Verifique se o projeto está usando [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versão 2002.0.12 ou posterior.
- Use o aplicativo de Administração para adicionar conteúdo ao `robots.txt` arquivo.

   >[!TIP]
   >
   >Visualizar as variáveis geradas `robots.txt` arquivo para sua loja em `<domain.your.project>/robots.txt`.

- Use o aplicativo de Administração para gerar um `sitemap.xml` arquivo.

   >[!IMPORTANT]
   >
   >Devido ao sistema de arquivos somente leitura no Adobe Commerce em projetos de infraestrutura em nuvem, você deve especificar o `pub/media` antes de gerar o arquivo.

- Use um trecho Fastly VCL personalizado para redirecionar da raiz do site para o `pub/media/` local para ambos os arquivos:

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
>Consulte [Adicionar mapa do site e robôs de mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) para obter instruções detalhadas.


### Lojas de vários sites

Você pode configurar e executar várias lojas com uma única implementação do Adobe Commerce na infraestrutura em nuvem. Consulte [Configurar vários sites ou lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

As mesmas práticas recomendadas para configurar o `robots.txt` e `sitemap.xml` arquivos para [vitrines de um único site](#single-site-storefronts) aplica-se a vitrines de vários sites, com duas diferenças importantes:

- Certifique-se de que a variável `robots.txt` e `sitemap.xml` nomes de arquivo contêm os nomes dos sites correspondentes. Por exemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Use um trecho Fastly VCL personalizado modificado para redirecionar da raiz de seus sites para o `pub/media` local para ambos os arquivos em seus sites:

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

Use o aplicativo de Administração para configurar o `robots.txt` e `sitemap.xml` arquivos para impedir que bots verifiquem e indexem conteúdo desnecessário (consulte [Robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Para implantações locais, onde você grava os arquivos depende de como você instalou o Adobe Commerce. Gravar os arquivos em `/path/to/commerce/pub/media/` ou `/path/to/commerce/media`, o que for adequado para a sua instalação.

## Segurança

Não exponha o caminho do Administrador no `robots.txt` arquivo. Ter o caminho de administrador exposto é uma vulnerabilidade para hackers no site e perda potencial de dados. Remova o caminho de Administrador do `robots.txt` arquivo.

Para obter etapas para editar o `robots.txt` e remover todas as entradas do Caminho do administrador, consulte [Guia de usuário de marketing > SEO e pesquisa > Robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se precisar de ajuda, [enviar um tíquete de suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informações adicionais

- [Noções básicas sobre sites, lojas e visualizações de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Adicionar sites](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Use o Fastly para bloquear o tráfego mal-intencionado em seus sites do Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [o robots.txt fornece um erro 404 no Adobe Commerce na infraestrutura em nuvem 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
