---
title: Obtenha o software Adobe Commerce
description: Saiba como baixar o software Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 0659c19e24e90ca4e3a7ac1c04914bda82b766dd
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Obtenha o software Adobe Commerce

Você está entre os 240.000 comerciantes em todo o mundo que confiam em nosso software de comércio eletrônico. Coletamos algumas informações para ajudar você a começar a instalação.

## Como obter o software

Verifique a disponibilidade e a compatibilidade das extensões criadas pela Adobe e dos Serviços da Commerce para Adobe Commerce e Magento Open Source em nossa [página de disponibilidade do produto](https://experienceleague.adobe.com/pt-br/docs/commerce-operations/release/product-availability).

>[!NOTE]
>
>As bases de código do Adobe Commerce agora são distribuídas exclusivamente pelo Composer devido a alterações de política. Use o Composer para baixar qualquer uma das versões do Adobe Commerce listadas, pois a base de código não está mais disponível na seção Downloads.
>
>Para obter mais informações, consulte [Não é possível acessar o extrato de cobrança e baixar a base de código na Adobe Commerce na infraestrutura em nuvem](https://experienceleague.adobe.com/pt-br/docs/experience-cloud-kcs/kbarticles/ka-26611)

Consulte a tabela a seguir para começar a instalar o Adobe Commerce.

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
        <td><ol><li>Cria um <em>projeto</em> do Composer que contém a lista de componentes a serem usados.</li>
            <li>Usa o Composer para atualizar dependências de pacote; usa <code>composer create-project</code> para obter o metapackage do Composer.</li>
            <li>Instala o aplicativo usando a <a href="../advanced.md">linha de comando</a>.</li>
        <li>Atualiza o aplicativo e as extensões usando a <a href="../../upgrade/implementation/perform-upgrade.md">linha de comando</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obter o metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Desenvolvedor colaborador</p></td>
        <td><p>Contribui para a base de código do Magento Open Source, arquiva bugs e personaliza o aplicativo. Altamente técnico, tem seu próprio servidor de desenvolvimento, entende o Composer e o GitHub.</p>
            <p>Você <em>não pode</em> usar o aplicativo em um ambiente de produção.</p>
      <p>Você deve atualizar usando os <a href="../../upgrade/developer/git-installs.md">comandos do Composer e do Git</a>.</p></td>
        <td><ol><li>Clona o repositório GitHub.</li>
            <li>Usa o Composer para atualizar as dependências do pacote.</li>
            <li>Instala o aplicativo usando a <a href="../advanced.md">linha de comando</a>.</li>
            <li>Atualiza o aplicativo usando os <a href="../../upgrade/developer/git-installs.md">comandos do Composer e do Git</a>.</li>
            <li>Personaliza o código no diretório <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonar o repositório GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Informações úteis

Use os links no lado esquerdo da página para navegar pelos tópicos em cada parte da instalação do.

## Permissões de servidor necessárias

Sistemas UNIX requerem privilégios `root` para instalar e configurar software como um servidor Web, PHP. Se precisar instalar este software, verifique se você tem acesso de `root`.

*não* instale o aplicativo no docroot do servidor Web como o usuário `root` porque talvez o servidor Web não possa interagir com esses arquivos.

Você precisa de `root` privilégios para criar o [proprietário do sistema de arquivos](file-system/overview.md) e adicionar esse proprietário ao grupo do servidor Web. Você usa o proprietário do sistema de arquivos para executar comandos `bin/magento` a partir da linha de comando e para configurar trabalhos cron, que agendem tarefas para você.
