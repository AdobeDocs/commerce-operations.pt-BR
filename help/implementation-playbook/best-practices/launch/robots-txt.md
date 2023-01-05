---
title: Práticas recomendadas para configurar arquivos `robots.txt` e `sitemap.xml`
description: Saiba como enviar instruções sobre o site do Adobe Commerce para rastreadores da Web.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---


# Práticas recomendadas para configurar `robots.txt` e `sitemap.xml` arquivos

Este artigo fornece as práticas recomendadas para usar o `robots.txt` e `sitemap.xml` arquivos no Adobe Commerce, incluindo configuração e segurança. Esses arquivos instruem robôs da Web (normalmente robôs de mecanismos de pesquisa) como rastrear páginas em um site. A configuração desses arquivos pode melhorar o desempenho do site e a otimização do mecanismo de pesquisa.

>[!NOTE]
>
>Essas práticas recomendadas se aplicam apenas a projetos que usam a vitrine nativa do Adobe Commerce. Eles não se aplicam a projetos da Adobe Commerce que usam outras soluções de vitrine (por exemplo, Adobe Experience Manager, sem periféricos).

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura de nuvem
- Adobe Commerce no local

## Adobe Commerce na infraestrutura de nuvem

Um projeto padrão do Adobe Commerce contém uma hierarquia que inclui um único site, loja e exibição de loja. Para implementações mais complexas, você pode criar sites, lojas e visualizações de loja adicionais para um _vários sites_ loja.

### Lojas de site único

Siga estas práticas recomendadas ao configurar o `robots.txt` e `sitemap.xml` arquivos para vitrines de site único:

- Certifique-se de que o projeto esteja usando [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) versão 2002.0.12 ou posterior.
- Use o aplicativo Admin para adicionar conteúdo ao `robots.txt` arquivo.

   >[!TIP]
   >
   >Visualizar o gerado automaticamente `robots.txt` arquivo para sua loja em `<domain.your.project>/robots.txt`.

- Use o aplicativo Admin para gerar um `sitemap.xml` arquivo.

   >[!IMPORTANT]
   >
   >Devido ao sistema de arquivos somente leitura no Adobe Commerce em projetos de infraestrutura em nuvem, você deve especificar a variável `pub/media` antes de gerar o arquivo.

- Use um trecho de VCL Fastly personalizado para redirecionar da raiz do site para o `pub/media/` local para ambos os arquivos:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Teste o redirecionamento exibindo os arquivos em um navegador da Web. Por exemplo, `<domain.your.project>/robots.txt` e `<domain.your.project>/sitemap.xml`. Verifique se você está usando o caminho raiz para o qual você configurou o redirecionamento e não um caminho diferente.

>[!INFO]
>
>Consulte [Adicionar o mapa do site e os robôs do mecanismo de pesquisa](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) para obter instruções detalhadas.


### Lojas de vários sites

Você pode configurar e executar várias lojas com uma única implementação do Adobe Commerce na infraestrutura em nuvem. Consulte [Configurar vários sites da Web ou lojas](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

As mesmas práticas recomendadas para configurar o `robots.txt` e `sitemap.xml` arquivos para [vitrines de site único](#single-site-storefronts) se aplica a vitrines de vários sites com duas diferenças importantes:

- Certifique-se de que a variável `robots.txt` e `sitemap.xml` os nomes de arquivo contêm os nomes dos sites correspondentes. Por exemplo:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Use um trecho de VCL Fastly personalizado ligeiramente modificado para redirecionar da raiz de seus sites para o `pub/media` local para ambos os arquivos em seus sites:

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

Use o aplicativo Admin para configurar a variável `robots.txt` e `sitemap.xml` arquivos para impedir que bots digitalizem e indexem conteúdo desnecessário (consulte [Robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>Para implantações locais, onde você grava os arquivos depende de como você instalou o Adobe Commerce. Escreva os arquivos para `/path/to/commerce/pub/media/` ou `/path/to/commerce/media`, o que for mais adequado para a sua instalação.

## Segurança

Não exponha seu caminho de Administrador em `robots.txt` arquivo. Ter o Caminho de administrador exposto é uma vulnerabilidade para hackeamento de site e possível perda de dados. Remova o caminho de Administrador do `robots.txt` arquivo.

Para ver as etapas para editar o `robots.txt` e remova todas as entradas do caminho de Admin, consulte [Guia do usuário de marketing > SEO e Pesquisa > Robôs do mecanismo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Se precisar de ajuda, [enviar um tíquete de suporte da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Informações adicionais

- [Como entender sites, lojas e visualizações de loja](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Adição de sites](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Use com rapidez para bloquear o tráfego mal-intencionado nos sites do Adobe Commerce](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt fornece um erro 404 no Adobe Commerce na infraestrutura de nuvem 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
