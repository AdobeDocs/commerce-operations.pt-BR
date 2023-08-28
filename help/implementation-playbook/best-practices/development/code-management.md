---
title: Práticas recomendadas de gerenciamento de código
description: Saiba mais sobre as práticas recomendadas de gerenciamento de código para a fase de desenvolvimento de projetos do Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 0902997fb0bf862b37a5e29026f462bf8c86c96b
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Práticas recomendadas de gerenciamento de código do Adobe Commerce

Este tópico foi projetado para ajudá-lo a decidir se usará o Git ou o Composer para distribuir código personalizado, considerando o gerenciamento de versões, a complexidade do código e o gerenciamento de dependências.

>[!NOTE]
>
>Essas práticas recomendadas são mais adequadas para migrações e implementações; menos para o desenvolvimento de um único módulo.

## Produtos e versões afetados

[Todas as versões compatíveis](../../../release/versions.md) de:

- Adobe Commerce na infraestrutura em nuvem
- Adobe Commerce no local

Abrange os dois [arquitetura de referência global (GRA)](../../architecture/global-reference/overview.md) e instalações de instância única.

## Definições

{{$include /help/_includes/gra-definitions.md}}

## Quando usar o Git ou o Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Código gerenciado principalmente pelo Git</th>
    <th>Código gerenciado principalmente pelo Composer</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Quando usar para uma configuração de instância única</td>
    <td>
      <ul>
        <li><strong>Abordagem padrão para gerenciar código para uma configuração de instância única</strong></li>
        <li>Quando a base de código não for parte de um GRA de várias marcas no futuro</li>
        <li>Quando todas as marcas são executadas em uma única instância como sites</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Quando a base de código puder ou se tornará parte de uma configuração de várias instâncias no futuro</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Quando usar para uma configuração de várias instâncias</td>
    <td>
      <ul>
        <li>Quando quase todos os módulos estão interligados (não recomendado)</li>
        <li>Quando o código é mantido por uma equipe não familiarizada com o Composer</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Abordagem padrão para gerenciar código para uma configuração de várias instâncias</strong></li>
        <li>Quando o Adobe mantém a base de código ou a equipe de manutenção está familiarizada com o Composer</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Matriz de recursos

| Recurso | Git | Compositor |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Repositório de código principal | Todo o código reside em um único ou em alguns repositórios Git | Todo o código reside nos pacotes em um repositório do Composer<br>Cada pacote do Composer é representado por um repositório Git |
| Local do código | O desenvolvimento acontece no `app/` diretório | O desenvolvimento acontece no `vendor/` diretório |
| Gerenciamento de atualização principal | O núcleo do Adobe Commerce é instalado e atualizado usando o Composer. O resultado é confirmado no Git | O núcleo do Adobe Commerce é instalado e atualizado usando o Composer; o resultado é confirmado no Git |
| Gerenciamento de módulo de terceiros | Os módulos de terceiros são instalados no `vendor/` se estiverem instalados por meio do marketplace ou packagist.org. Caso contrário, eles serão instalados no `app/` | Todos os módulos de terceiros são instalados no `vendor/` diretório |
| Versões | A liberação é caracterizada por `git merge` e `git pull` ou `git checkout` comandos | A liberação é caracterizada por `composer update` e `git pull` ou `git checkout` comandos |
| Número de repositórios Git | Poucos | Muitos |
| Complexidade de desenvolvimento | Simples | Complexo |
| Complexidade da solicitação de pull | Simples | Complexo |
| Complexidade da análise do código | Simples | Simples |
| Complexidade de atualização do ambiente Dev/QA/UAT | Simples | Complexo |
| Suporte a GRA | ![Ícone Sim](../../../assets/yes.svg) | ![Ícone Sim](../../../assets/yes.svg) |
| Os módulos podem instalar bibliotecas externas automaticamente | ![Nenhum ícone](../../../assets/no.svg) | ![Ícone Sim](../../../assets/yes.svg) |
| Flexibilidade na composição do GRA | ![Nenhum ícone](../../../assets/no.svg) | ![Ícone Sim](../../../assets/yes.svg) |
| Gerenciamento de dependência de módulo | ![Ícone Sim](../../../assets/yes.svg) Somente até `module.xml`, funcionalidade limitada | ![Ícone Sim](../../../assets/yes.svg) Gerenciamento completo de dependências por meio de `composer.json` |
| Versão do módulo | ![Ícone Sim](../../../assets/yes.svg) Você pode definir uma versão, mas não pode instalar uma versão específica | ![Ícone Sim](../../../assets/yes.svg) Suporte à versão completa |
| Serviços pagos necessários | Repositório Git | Repositório Git, Private Packagist (± €600 por ano) |
| Possível integração do Bitbucket com o Jira | ![Ícone Sim](../../../assets/yes.svg) | ![Ícone Sim](../../../assets/yes.svg) |
| Alterações no código disponíveis instantaneamente para instalação | ![Ícone Sim](../../../assets/yes.svg) | ![Ícone Sim](../../../assets/yes.svg) |

## Soluções a serem evitadas

1. **Compositor e combinação `app/code` para seus módulos**

   Isso resulta na combinação de todas as desvantagens dos dois estilos de gerenciamento de código no seu projeto. Ele acrescenta complexidade desnecessária, instabilidade e falta de flexibilidade.

   Por exemplo:
   - Explique os fluxos de trabalho do Git e do Composer (em vez de apenas um deles) à equipe de desenvolvimento.
   - Instalar módulos incompatíveis no `app/code` pois não há nada em vigor que impeça isso de acontecer.
   - Mover um módulo do `app/code` Composer (ou vice-versa) é complicado, especialmente com desenvolvimento contínuo.

1. **Gerenciador de pacotes do Satis**

   O Private Packagist custa ± €600 por ano. Este custo é para todo o GRA combinado, não por marca. Não tente evitar esses custos usando a solução gratuita Satis. O Satis não atualiza automaticamente seus pacotes sempre que você envia confirmações para o Git. Além disso, o Satis não tem autorização incorporada. Você deve manter um servidor Web para executar o Satis. Você acaba gastando uma multidão da taxa de assinatura do Private Packagist mantendo o Satis.

1. **Comece com Git e depois vá para o Composer**

   Escolha uma abordagem de gerenciamento de código no início do projeto. Alternar do Git para o Composer ou vice-versa, com desenvolvimento contínuo, é complicado e pode levar à perda de código e/ou perda de histórico de revisão.
