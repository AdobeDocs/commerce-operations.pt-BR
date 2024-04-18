---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Comunicação segura com o servidor da Web

Este tópico discute um exemplo de proteção da comunicação entre o servidor da Web e o mecanismo de pesquisa (Elasticsearch ou OpenSearch) usando uma combinação de criptografia TLS (Transport Layer Security) e [Autenticação básica HTTP](https://datatracker.ietf.org/doc/html/rfc2617). Opcionalmente, também é possível configurar outros tipos de autenticação; fornecemos referências para essas informações.

(Um termo mais antigo, SSL (Secure Sockets Layer), é frequentemente usado alternadamente com TLS. Neste tópico, nos referimos a *TLS*.)

>[!WARNING]
>
>A menos que seja indicado de outra forma, todos os comandos neste tópico devem ser inseridos como usuários com `root` privilégios.

## Recommendations

Recomendamos o seguinte:

* Seu servidor da Web usa TLS.

  O TLS está fora do escopo desse tópico; no entanto, recomendamos que você use um certificado real na produção e não um certificado autoassinado.

* Seu mecanismo de pesquisa é executado no mesmo host que um servidor da Web. A execução do mecanismo de pesquisa e do servidor Web em hosts diferentes está além do escopo deste tópico.

  A vantagem de colocar o mecanismo de busca e o servidor Web no mesmo host é que isso torna impossível a interceptação de comunicações criptografadas. O servidor Web do mecanismo de pesquisa não precisa ser o mesmo que o servidor Web do Adobe Commerce; por exemplo, o Adobe Commerce pode executar o Apache e o Elasticsearch/OpenSearch pode executar o nginx.

  Se o mecanismo de pesquisa for exposto à Web pública, você deverá configurar a autenticação. Se a instância do mecanismo de pesquisa estiver protegida na rede, isso pode não ser necessário. Trabalhe com seu provedor de hospedagem para determinar quais medidas de segurança você deve implementar para proteger sua instância.

## Mais informações sobre TLS

Consulte um dos seguintes recursos:

* Apache

   * [Instruções sobre criptografia forte do Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Como criar um certificado SSL no Apache para Ubuntu 14.04 (tutorial DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configuração de um servidor Web seguro por SSL com CentOS (CentOS wiki)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminação SSL do Nginx](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Como criar um certificado SSL no Nginx para Ubuntu 14.04 (tutorial DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Instalação do certificado SSL do Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
