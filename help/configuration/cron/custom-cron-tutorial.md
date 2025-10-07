---
title: Configurar um trabalho cron personalizado e um grupo cron (tutorial)
description: Saiba como criar trabalhos cron personalizados usando este tutorial passo a passo para o Adobe Commerce. Descubra a configuração do módulo e a configuração do grupo cron.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# Configurar um trabalho cron personalizado

Este tutorial passo a passo mostra como criar um trabalho cron personalizado e, opcionalmente, um grupo cron em um módulo de amostra. Você pode usar um módulo que já tem ou pode usar um módulo de exemplo de nosso [`magento2-samples` repositório][samples].

A execução do trabalho cron resulta na adição de uma linha à tabela `cron_schedule` com o nome do trabalho cron, `custom_cron`.

Também mostramos como criar opcionalmente um grupo cron, que você pode usar para executar trabalhos cron personalizados com configurações diferentes dos padrões do aplicativo Commerce.

Neste tutorial, assumimos o seguinte:

- O aplicativo Commerce está instalado em `/var/www/html/magento2`
- Seu nome de usuário e senha do banco de dados do Commerce são `magento`
- Você executa todas as ações como [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md)

## Etapa 1: obter um módulo de amostra

Para configurar um trabalho cron personalizado, você precisa de um módulo de amostra. Sugerimos o módulo `magento-module-minimal`.

Se você já tiver um módulo de amostra, poderá usá-lo; ignore esta etapa e a próxima e continue com a Etapa 3: Criar uma classe para executar o cron.

**Para obter um módulo de exemplo**:

1. Faça logon no servidor Commerce como ou alterne para o [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Mude para um diretório que não esteja na raiz do aplicativo do Commerce (por exemplo, seu diretório inicial).
1. Clonar o [`magento2-samples` repositório][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Se o comando falhar com o erro `Permission denied (publickey).`, você deve [adicionar sua chave pública SSH ao GitHub.com][git-ssh].

1. Crie um diretório para o qual copiar o código de amostra:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Copie o código do módulo de amostra:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Verifique se os arquivos foram copiados corretamente:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Você deve ver o seguinte resultado:

   ```
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Atualize o banco de dados e o esquema do Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

## Etapa 2: verificar o módulo de amostra

Antes de continuar, verifique se o módulo de amostra está registrado e ativado.

1. Execute o seguinte comando:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Certifique-se de que o módulo esteja ativado.

   ```
   Module is enabled
   ```

>[!TIP]
>
>Se a saída indicar que o `Module does not exist`, reveja a [Etapa 1](#step-1-get-a-sample-module) com cuidado. Verifique se o código está no diretório correto. A ortografia e o uso de maiúsculas e minúsculas são importantes; se algo for diferente, o módulo não será carregado. Além disso, não se esqueça de executar `magento setup:upgrade`.

## Etapa 3: criar uma classe para executar o cron

Esta etapa mostra uma classe simples para criar um trabalho cron. A classe grava apenas uma linha na tabela `cron_schedule` que confirma que está configurada com êxito.

Para criar uma classe:

1. Crie um diretório para a classe e altere para esse diretório:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Criado um arquivo chamado `Test.php` nesse diretório com o seguinte conteúdo:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Etapa 4: Criar `crontab.xml`

O arquivo `crontab.xml` define um agendamento para executar seu código cron personalizado.

Crie `crontab.xml` da seguinte maneira no diretório `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc`:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

O `crontab.xml` anterior executa a classe `Magento/SampleMinimal/Cron/Test.php` uma vez por minuto, resultando na adição de uma linha à tabela `cron_schedule`.

Para tornar o cronograma cron configurável no Admin, use o caminho de configuração do campo de configuração do sistema.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Onde, `system/config/path` é um caminho de configuração do sistema definido em `etc/adminhtml/system.xml` de um módulo.

## Etapa 5: Compilar e limpar o cache

Compile o código com este comando:

```bash
bin/magento setup:di:compile
```

E limpe o cache com este comando:

```bash
bin/magento cache:clean
```

## Etapa 6: verificar o trabalho cron

Esta etapa mostra como verificar o trabalho cron personalizado usando uma consulta SQL na tabela de banco de dados `cron_schedule`.

Para verificar o cron:

1. Executar trabalhos cron do Commerce:

   ```bash
   bin/magento cron:run
   ```

1. Digite o comando `magento cron:run` duas ou três vezes.

   Na primeira vez que você insere o comando, ele enfileira trabalhos; subsequentemente, os trabalhos cron são executados. Você deve inserir o comando _pelo menos_ duas vezes.

1. Execute a consulta SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` da seguinte maneira:

   1. Inserir `mysql -u magento -p`
   1. No prompt `mysql>`, digite `use magento;`
   1. Inserir `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      O resultado deve ser semelhante ao seguinte:

      ```
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Opcional) Verifique se as mensagens estão gravadas no log do sistema da Commerce:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Você deve ver uma ou mais entradas como as seguintes:

   ```
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Estas mensagens vêm do método `execute` em `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Se o comando SQL e o log do sistema não contiverem entradas, execute o comando `magento cron:run` mais algumas vezes e aguarde. Pode levar algum tempo para que o banco de dados seja atualizado.

## Etapa 7 (opcional): configurar um grupo cron personalizado

Esta etapa mostra como configurar opcionalmente um grupo cron personalizado. Você deve configurar um grupo cron personalizado se quiser que seu trabalho cron personalizado seja executado em um cronograma diferente de outros trabalhos cron (normalmente, uma vez por minuto) ou se quiser que vários trabalhos cron personalizados sejam executados com configurações diferentes.

Para configurar um grupo cron personalizado:

1. Abra `crontab.xml` em um editor de texto.
1. Alterar `<group id="default">` para `<group id="custom_crongroup">`
1. Saia do editor de texto.
1. Criar `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` com o seguinte conteúdo:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

Para obter uma descrição do que significam as opções, consulte [Personalizando referência de crons](custom-cron-reference.md).

## Etapa 8: verificar seu grupo cron personalizado

Esta etapa _opcional_ mostra como verificar seu grupo cron personalizado usando o Administrador.

Para verificar seu grupo cron personalizado:

1. Execute trabalhos cron do Commerce para seu grupo personalizado:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Execute o comando pelo menos duas vezes.

1. Limpe o cache:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Faça logon no Admin como administrador.
1. Clique em **Lojas** > **Configurações** > **Configuração** > **Avançadas** > **Sistema**.
1. No painel direito, expanda **Cron**.

   Seu grupo cron é exibido da seguinte maneira:

   ![Seu grupo cron personalizado](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
