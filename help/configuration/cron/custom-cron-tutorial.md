---
title: Configurar um trabalho cron personalizado e um grupo cron (tutorial)
description: Use este tutorial passo a passo para criar um trabalho cron personalizado.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# Configurar um trabalho cron personalizado

Este tutorial passo a passo mostra como criar um trabalho cron personalizado e, opcionalmente, um grupo cron em um módulo de amostra. Você pode usar um módulo que já tem ou pode usar um módulo de amostra de nosso [`magento2-samples` repositório][samples].

A execução do trabalho cron resulta na adição de uma linha ao `cron_schedule` tabela com o nome do trabalho cron, `custom_cron`.

Também mostramos como, opcionalmente, criar um grupo cron, que pode ser usado para executar trabalhos cron personalizados com configurações diferentes dos padrões do aplicativo Commerce.

Neste tutorial, assumimos o seguinte:

- O aplicativo Commerce está instalado em `/var/www/html/magento2`
- Seu nome de usuário e senha do banco de dados do Commerce são `magento`
- Você executa todas as ações como [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md)

## Etapa 1: Obter um módulo de amostra

Para configurar um trabalho cron personalizado, você precisa de um módulo de amostra. Sugerimos que `magento-module-minimal` módulo.

Se você já tiver um módulo de amostra, poderá usá-lo; pule esta etapa e a próxima etapa e continue com a Etapa 3: Crie uma classe para executar o cron.

**Para obter um módulo de amostra**:

1. Faça logon no seu servidor do Commerce como, ou alterne para, a variável [proprietário do sistema de arquivos](../../installation/prerequisites/file-system/overview.md).
1. Altere para um diretório que não esteja na raiz do aplicativo Commerce (por exemplo, seu diretório inicial).
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

1. Verifique os arquivos copiados corretamente:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Você deve ver o seguinte resultado:

   ```terminal
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

1. Atualize o banco de dados e o schema do Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

## Etapa 2: Verificar o módulo de amostra

Antes de continuar, verifique se o módulo de amostra está registrado e ativado.

1. Execute o seguinte comando:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Certifique-se de que o módulo esteja ativado.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Se a saída indicar que a variável `Module does not exist`, revisão [Etapa 1](#step-1-get-a-sample-module) cuidadosamente. Verifique se o código está no diretório correto. A ortografia e o caso são importantes; se algo for diferente, o módulo não será carregado. Além disso, não se esqueça de executar `magento setup:upgrade`.

## Etapa 3: Criar uma classe para executar o cron

Esta etapa mostra uma classe simples para criar um trabalho cron. A classe só grava uma linha no `cron_schedule` tabela que confirma se foi configurada com êxito.

Para criar uma classe:

1. Crie um diretório para a classe e altere para esse diretório:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Criado um arquivo com o nome `Test.php` nesse diretório, com o seguinte conteúdo:

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

O `crontab.xml` O arquivo define um agendamento para executar seu código cron personalizado.

Criar `crontab.xml` como se segue no `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` diretório:

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

O `crontab.xml` executa o `Magento/SampleMinimal/Cron/Test.php` classe uma vez por minuto, resultando em uma linha sendo adicionada à `cron_schedule` tabela.

Para tornar o cronograma do cron configurável no Admin, use o caminho de configuração do campo de configuração do sistema.

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

Em que `system/config/path` é um caminho de configuração do sistema definido em `etc/adminhtml/system.xml` de um módulo.

## Etapa 5: Compilar e limpar cache

Compile o código com este comando:

```bash
bin/magento setup:di:compile
```

E limpe o cache com este comando:

```bash
bin/magento cache:clean
```

## Etapa 6: Verificar a tarefa de cron

Esta etapa mostra como verificar o trabalho cron personalizado com êxito usando uma consulta SQL no `cron_schedule` tabela de banco de dados.

Para verificar o cron:

1. Execute trabalhos do Commerce cron:

   ```bash
   bin/magento cron:run
   ```

1. Insira o `magento cron:run` duas ou três vezes.

   Na primeira vez que você insere o comando, ele enfileira tarefas; posteriormente, são executados os postos de trabalho do cron. Você deve inserir o comando _pelo menos_ duas vezes.

1. Executar a consulta SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` como se segue:

   1. Enter `mysql -u magento -p`
   1. Na `mysql>` prompt, digite `use magento;`
   1. Enter `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      O resultado deve ser semelhante ao seguinte:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Opcional) Verifique se as mensagens são gravadas no log de sistema do Commerce:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Você deve ver uma ou mais entradas como as seguintes:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Essas mensagens vêm do `execute` método em `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Se o comando SQL e o log do sistema não contiverem entradas, execute o `magento cron:run` mais algumas vezes e aguarde. Pode levar algum tempo para que o banco de dados seja atualizado.

## Etapa 7 (opcional): Configurar um grupo cron personalizado

Esta etapa mostra como configurar opcionalmente um grupo cron personalizado. Você deve configurar um grupo de cron personalizado se quiser que seu trabalho de cron personalizado seja executado em um agendamento diferente de outros trabalhos de cron (normalmente, uma vez por minuto) ou se quiser que vários trabalhos de cron personalizados sejam executados com configurações diferentes.

Para configurar um grupo cron personalizado:

1. Abrir `crontab.xml` em um editor de texto.
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

Para obter uma descrição do que significam as opções, consulte [Personalização de referência de crons](custom-cron-reference.md).

## Etapa 8: Verificar seu grupo cron personalizado

Essa _opcional_ mostra como verificar seu grupo cron personalizado usando o Administrador.

Para verificar seu grupo cron personalizado:

1. Execute trabalhos do Commerce cron para o seu grupo personalizado:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Execute o comando pelo menos duas vezes.

1. Limpe o cache:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Faça logon em Admin como administrador.
1. Clique em **Lojas** > **Configurações** > **Configuração** > **Avançado** > **Sistema**.
1. No painel direito, expanda **Cron**.

   Seu grupo cron é exibido da seguinte maneira:

   ![Seu grupo cron personalizado](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
