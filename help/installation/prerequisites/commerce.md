---
title: Obtenha o software Adobe Commerce
description: Saiba como baixar o software Adobe Commerce e Magento Open Source.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Obtenha o software Adobe Commerce

Você está entre os 240.000 comerciantes em todo o mundo que confiam em nosso software de comércio eletrônico. Coletamos algumas informações para ajudar você a começar a instalação.

## Como obter o software

Verifique a disponibilidade de novos recursos e versões interessantes e saiba como obtê-los em nossos [página de disponibilidade do produto](https://devdocs.magento.com/release/availability.html).

Consulte a tabela a seguir para começar a instalar o Adobe Commerce ou o Magento Open Source.

<table>
    <tbody>
        <tr>
            <th>Necessidades do usuário</th>
            <th>Descrição</th>
            <th>Etapas de instalação e atualização de alto nível</th>
            <th>Link de introdução</th>
        </tr>
    <tr>
        <td><p>Integrador, empacotador</p></td>
        <td><p>Quer controle total sobre todos os componentes instalados, tem acesso ao servidor de aplicativos, é altamente técnico, pode reempacotar o Magento Open Source com outros componentes.</p>
        </td>
        <td><ol><li>Cria um compositor <em>projeto</em> que contém a lista de componentes a serem usados.</li>
            <li>Usa o Composer para atualizar as dependências do pacote; usa <code>composer create-project</code> para obter o metapackage do Composer.</li>
            <li>Instala o aplicativo usando o <a href="../advanced.md">linha de comando</a>.</li>
        <li>Atualiza o aplicativo e as extensões usando o  <a href="../../upgrade/implementation/perform-upgrade.md">linha de comando</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obter o metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Desenvolvedor colaborador</p></td>
        <td><p>Contribui para a base de código do Magento Open Source, para a criação de bugs de arquivos e para a personalização do aplicativo. Altamente técnico, tem seu próprio servidor de desenvolvimento, entende o Composer e o GitHub.</p>
            <p>Você <em>não é possível</em> usar o aplicativo em um ambiente de produção.</p>
      <p>Você deve atualizar usando <a href="../../upgrade/developer/git-installs.md">Comandos do Composer e do Git</a>.</p></td>
        <td><ol><li>Clona o repositório GitHub.</li>
            <li>Usa o Composer para atualizar as dependências do pacote.</li>
            <li>Instala o aplicativo usando <a href="../advanced.md">linha de comando</a>.</li>
            <li>Atualiza o aplicativo usando <a href="../../upgrade/developer/git-installs.md">Comandos do Composer e do Git</a>.</li>
            <li>Personaliza o código no <code>app/code</code> diretório.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonar o repositório GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informações úteis

Use os links no lado esquerdo da página para navegar pelos tópicos em cada parte da instalação do.

## Permissões de servidor necessárias

Os sistemas UNIX exigem `root` privilégios para instalar e configurar software como um servidor web, PHP. Se precisar instalar este software, verifique se `root` acesso.

Fazer *não* instale o aplicativo no docroot do servidor web como o `root` usuário porque talvez o servidor Web não possa interagir com esses arquivos.

Você precisa `root` privilégios para criar a [proprietário do sistema de arquivos](file-system/overview.md) e adicionar esse proprietário ao grupo do servidor Web. Use o proprietário do sistema de arquivos para executar `bin/magento` comandos da linha de comando e para configurar trabalhos cron, que programam tarefas para você.
