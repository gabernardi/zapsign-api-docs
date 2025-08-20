# Reprocessamento de Documentos e Webhooks

Em cenários de **falhas na integração,** erros de validação ou necessidade de atualizações no sistema receptor, **o reprocessamento de webhooks pode ser crucial** para garantir a **entrega correta de informações** e manter a consistência dos dados entre sistemas integrados.

Nesta seção:\
\
[Reprocessamento de webhooks via interface web;](reprocessamento-de-documentos-e-webhooks.md#reprocessando-via-web)\
[Reprocessamento de webhooks e documentos via API ;](reprocessamento-de-documentos-e-webhooks.md#metodo-http)

***

#### Reprocessando via web

Para reprocessar documentos assinados via web, você deve encontrar seu documento na aba de documentos, clicar na engrenagem e em reprocessar webhooks

<figure><img src="https://github.com/AmandaAmani/documenta-ocurso/blob/main/reprocessamento%20webhook%20web1.gif?raw=true" alt="tela de documentos da ZapSign. Usuário navega com o cursor até o documento, depois clica na engrenagem e em &#x22;reprocessar webhooks&#x22;."><figcaption><p>Reprocessamento Webhook via interface web</p></figcaption></figure>

***

### Reprocessando documentos e webhooks via API <a href="#metodo-http" id="metodo-http"></a>

Em casos onde o documento assinado precisa ser regenerado — como quando há problemas de integridade no arquivo ou falha no envio de webhooks — **você pode utilizar o endpoint de reprocessamento.** Esse recurso é útil, por exemplo, quando o documento final foi corrompido ou o webhook associado não foi devidamente enviado.

<mark style="background-color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_principal_token}}/reprocess-doc/`

.

#### Headers <a href="#headers" id="headers"></a>

<table data-header-hidden><thead><tr><th></th><th width="146"></th><th></th></tr></thead><tbody><tr><td>Name</td><td>Type</td><td>Description</td></tr><tr><td>Authorization*</td><td>string</td><td>Api token a frente do texto "Bearer".Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</td></tr></tbody></table>

#### Request Body <a href="#request-body" id="request-body"></a>

```json
{
    "send_webhook": true,
    "resign_doc": false
}

```

| Name          | Tipo    | Descrição                                                                                           |
| ------------- | ------- | --------------------------------------------------------------------------------------------------- |
| send\_webhook | boolean | Para ativar o reenvio do webhook do documento selecionado. Default: false                           |
| resign\_doc   | boolean | Para reprocessar o documento assinado, criando um novo pdf do documento selecionado. Default: false |

​

#### Respostas  <a href="#observacoes" id="observacoes"></a>

{% tabs %}
{% tab title="200-OK" %}
Documento reprocessado com sucesso. Lembrete: este endpoint é assíncrono, então aguarde os PDF finais ficarem prontos via webhooks ou confira-os daqui alguns minutos.
{% endtab %}

{% tab title="404- Not found" %}
"detail": "Não encontrado."\
\
Cheque se o token do doc está correto na url.&#x20;
{% endtab %}
{% endtabs %}

​

{% hint style="warning" %}
Como o processo é assíncrono, monitore os webhooks ou verifique manualmente o status do documento após alguns minutos
{% endhint %}

