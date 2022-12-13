---
title: Armazenamento remoto para o Commerce na infraestrutura em nuvem
description: Consulte as orientações sobre como configurar o armazenamento remoto para o Adobe Commerce na infraestrutura em nuvem.
source-git-commit: 2080950852e3c4e6da556733e56f68e0e8005530
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Configurar o armazenamento remoto para o Commerce on Cloud Infrastructure

Começando com o `ece-tools` pacote 2002.1.5, você pode usar uma variável de ambiente para ativar o módulo de Armazenamento remoto; no entanto, o módulo de Armazenamento Remoto tem _limitado_ suporte no Adobe Commerce na infraestrutura em nuvem. O Adobe não pode solucionar totalmente os problemas do serviço do adaptador de armazenamento de terceiros.

## Variável de ambiente

O `REMOTE_STORAGE` é usada durante a [fase de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) de um projeto de infraestrutura em nuvem.

### `REMOTE_STORAGE`

- **Padrão**—_Não definido_
- **Versão**—Comércio 2.4.2 e posterior

Configure um _adaptador de armazenamento_ para armazenar arquivos de mídia em um contêiner de armazenamento persistente e remoto usando um serviço de armazenamento, como o AWS S3. Ative o módulo de Armazenamento Remoto para melhorar o desempenho em projetos do Cloud com configurações complexas de vários servidores que devem compartilhar recursos. Este é um exemplo de configuração de armazenamento remoto usando o `.magento.env.yaml` arquivo:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Definir variável com a CLI da nuvem

Defina as `REMOTE_STORAGE` como uma [variável de nível de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) para que os arquivos não sejam compartilhados entre ambientes de Produção, Armazenamento temporário e Integração. Definir as variáveis no nível do ambiente oferece a flexibilidade de usar somente o armazenamento remoto em ambientes selecionados, como excluir o uso do ambiente de integração do armazenamento remoto.

**Para adicionar a variável de armazenamento remoto usando a CLI da nuvem**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Isso cria uma `REMOTE_STORAGE` com a configuração JSON especificada. O `REMOTE_STORAGE` exige uma string JSON para configurar o armazenamento remoto. Este é um exemplo de configuração JSON:

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Após criar a configuração e implantar, os logs de implantação devem incluir informações sobre a configuração do armazenamento remoto, por exemplo `INFO: Remote storage driver set to: "aws-s3"`

### Definir variável com a interface da Web do projeto

Como alternativa, você pode usar a Interface Web do Projeto para adicionar a variável ao ambiente apropriado.

**Para adicionar a variável de armazenamento remoto usando a Interface Web do Projeto**:

1. No _Interface da Web do projeto_, selecione o ambiente à esquerda.

1. Clique no botão **Configurar ambiente** ícone .

1. No _Configurar ambiente_ , clique no botão **Variáveis** guia .

1. Clique em **Adicionar variável**.

1. No _Nome_ , insira `env:REMOTE_STORAGE`

1. No _Valor_ adicione a configuração JSON.

1. Selecionar **Valor JSON** e **Sensível**; desmarcar **Herdado por ambientes secundários**.

1. Clique em **Adicionar variável**.

### Usar autenticação opcional

O `key` e `secret` são opcionais. Ao criar a variável , é possível ocultar a variável `key` e `secret` selecionando o `sensitive` opção. Com essa configuração, os valores não estão visíveis na interface da Web. Consulte [Visibilidade da variável](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) no _Guia do Commerce on Cloud Infrastructure_.

Se quiser usar um método de autenticação diferente, omita a variável `key` e `secret` na configuração JSON,. Configure o método de autenticação alternativo e verifique se o servidor está autorizado ao bucket S3.

### Sincronizar o armazenamento remoto

Após habilitar o módulo de Armazenamento Remoto, sincronize os arquivos de mídia atuais para o local de armazenamento remoto.

**Para iniciar a sincronização**:

1. Use o SSH para fazer logon no ambiente remoto com o armazenamento remoto configurado.

1. Inicie a sincronização.

```bash
bin/magento remote-storage:sync 
```

## Configuração rápida

Se você optar por usar a solução de armazenamento remoto com um projeto Adobe Commerce em infraestrutura em nuvem, use o [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) orientações na _Rápido_ documentação para garantir que a Otimização de imagem rápida funcione com o AWS S3.

Esteja preparado com seu [Credenciais rápidas](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Em projetos Pro, use o SSH para se conectar ao seu servidor e obter as credenciais do Fastly da `/mnt/shared/fastly_tokens.txt` arquivo. Os ambientes de preparo e produção têm credenciais exclusivas. Você deve obter as credenciais para cada ambiente.

Continue configurando o armazenamento remoto para projetos em nuvem com as seguintes tarefas:

1. Configure um [Integração rápida de backend](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Criar lógica de VCL para [Autenticação AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Criar lógica de VCL para [solicitações de backend para o bucket do AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
