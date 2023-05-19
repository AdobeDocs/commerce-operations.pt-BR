---
title: Armazenamento remoto para Commerce em infraestrutura em nuvem
description: Consulte orientações sobre como configurar o armazenamento remoto para o Adobe Commerce na infraestrutura em nuvem.
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Configurar o armazenamento remoto para a infraestrutura do Commerce na nuvem

Começando com o `ece-tools` pacote 2002.1.5, você pode usar uma variável de ambiente para habilitar o módulo de Armazenamento remoto; no entanto, o módulo de Armazenamento remoto _limitado_ no Adobe Commerce na infraestrutura em nuvem. O Adobe não pode solucionar problemas completamente com o serviço de adaptador de armazenamento de terceiros.

## Variável de ambiente

A variável `REMOTE_STORAGE` é usada durante a [fase de implantação](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) projeto de infraestrutura em nuvem.

### `REMOTE_STORAGE`

- **Padrão**—_Não definido_
- **Versão**—Commerce 2.4.2 e posterior

Configurar um _adaptador de armazenamento_ para armazenar arquivos de mídia em um contêiner de armazenamento remoto persistente usando um serviço de armazenamento, como o AWS S3. Habilite o módulo de Armazenamento remoto para melhorar o desempenho em projetos na nuvem com configurações complexas de vários servidores que devem compartilhar recursos. Veja a seguir um exemplo de configuração de armazenamento remoto usando o `.magento.env.yaml` arquivo:

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

### Definir a variável com a CLI da nuvem

Defina o `REMOTE_STORAGE` variável como um [variável de nível de ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) para que os arquivos não sejam compartilhados entre os ambientes de Produção, Preparo e Integração. Definir as variáveis no nível do ambiente proporciona a flexibilidade de usar somente o armazenamento remoto em ambientes selecionados, como excluir o uso do armazenamento remoto no ambiente de integração.

**Para adicionar a variável de armazenamento remoto usando a CLI da nuvem**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Isso cria uma `REMOTE_STORAGE` com a configuração JSON especificada. A variável `REMOTE_STORAGE` A variável usa uma cadeia de caracteres JSON para configurar o armazenamento remoto. Veja a seguir um exemplo de configuração JSON:

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

Após criar a configuração e implantar, os logs de implantação devem incluir informações sobre a configuração de armazenamento remoto, por exemplo `INFO: Remote storage driver set to: "aws-s3"`

### Definir variável com a interface da Web do projeto

Como alternativa, você pode usar a Interface da Web do projeto para adicionar a variável ao ambiente apropriado.

**Para adicionar a variável de armazenamento remoto usando a interface da Web do projeto**:

1. No _Interface da Web do Project_, selecione o ambiente à esquerda.

1. Clique em **Configurar ambiente** ícone.

1. No _Configurar ambiente_ clique no link **Variáveis** guia.

1. Clique em **Adicionar variável**.

1. No _Nome_ insira `REMOTE_STORAGE`

1. No _Valor_ adicione a configuração JSON.

1. Selecionar **Valor JSON** e **Sensível**; desmarcar **Herdável por ambientes secundários**.

1. Clique em **Adicionar variável**.

### Usar autenticação opcional

A variável `key` e `secret` são opcionais. Ao criar a variável, você pode ocultar a variável `key` e `secret` selecionando o `sensitive` opção. Com essa configuração, os valores não ficam visíveis na interface da Web. Consulte [Visibilidade da variável](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) no _Guia do Commerce na infraestrutura em nuvem_.

Se quiser usar um método de autenticação diferente, omita o `key` e `secret` na configuração JSON,. Configure o método de autenticação alternativo e verifique se o servidor está autorizado para o bucket do S3.

### Sincronizar o armazenamento remoto

Depois de habilitar o módulo de Armazenamento remoto, sincronize os arquivos de mídia atuais para o local de armazenamento remoto.

**Para iniciar a sincronização**:

1. Use o SSH para fazer logon no ambiente remoto com o armazenamento remoto configurado.

1. Inicie a sincronização.

```bash
bin/magento remote-storage:sync 
```

## Configuração do Fastly

Se você optar por usar a solução de armazenamento remoto com um projeto Adobe Commerce na infraestrutura em nuvem, use o [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) orientação no _Fastly_ documentação para garantir que o Fastly Image Otimization funcione com o AWS S3.

Esteja preparado com seu [Credenciais do Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). Em projetos Pro, use SSH para se conectar ao servidor e obter as credenciais do Fastly no `/mnt/shared/fastly_tokens.txt` arquivo. Os ambientes de preparo e produção têm credenciais exclusivas. Você deve obter as credenciais para cada ambiente.

Continue configurando o armazenamento remoto para projetos na nuvem com as seguintes tarefas:

1. Configurar um [Integração de back-end do Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Criar lógica de VCL para [Autenticação AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Criar lógica de VCL para [solicitações de back-end para o bucket do AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
