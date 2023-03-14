---
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---
# Verifique se a comunicação está segura

Esta seção discute duas maneiras de verificar se a autenticação básica de HTTP está funcionando:

* Uso de um `curl` comando para verificar é necessário digitar um nome de usuário e senha para obter o status do cluster
* Configuração da autenticação básica de HTTP no Admin

## Use um `curl` comando para verificar o status do cluster

Digite o seguinte comando:

```bash
curl -i http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Por exemplo, se você digitar o comando no servidor do mecanismo de pesquisa e seu proxy usar a porta 8080:

```bash
curl -i http://localhost:8080/_cluster/health
```

A seguinte mensagem é exibida para indicar falha na autenticação:

```terminal
HTTP/1.1 401 Unauthorized
Date: Tue, 23 Feb 2016 20:35:29 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
WWW-Authenticate: Basic realm="Restricted"
<html>
<head><title>401 Authorization Required</title></head>
<body bgcolor="white">
  <center><h1>401 Authorization Required</h1></center>
</body>
</html>
```

Agora, tente o seguinte comando:

```bash
curl -i -u <username>:<password> http://<hostname, ip, or localhost>:<proxy port>/_cluster/health
```

Por exemplo:

```bash
curl -i -u magento_elasticsearch:mypassword http://localhost:8080/_cluster/health
```

Desta vez, o comando é bem-sucedido com uma mensagem semelhante à seguinte:

```terminal
HTTP/1.1 200 OK
Date: Tue, 23 Feb 2016 20:38:03 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 389
Connection: keep-alive
{"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
```

## Configurar a autenticação básica de HTTP no Admin

Execute as mesmas tarefas discutidas em [Configuração do mecanismo de pesquisa](../configuration/search/configure-search-engine.md) *exceto* click **[!UICONTROL Yes]** do **[!UICONTROL Enable HTTP Auth]** e digite seu nome de usuário e senha nos campos fornecidos.

Clique em **[!UICONTROL Test Connection]** para verificar se funciona e clique em **[!UICONTROL Save Config]**.

Você deve liberar o cache e reindexar antes de continuar.
