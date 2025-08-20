# Deletar webhook

Existem várias situações em que você pode precisar remover um webhook, como ao desativar integrações antigas ou reconfigurar endpoints. Para facilitar, você pode deletar um webhook diretamente pelo painel de controle, acessando **Configurações>Integrações>Api ZapSign>** [**Webhooks**](https://app.zapsign.com.br/conta/configuracoes/integration?tab=api-zapsign) e excluindo a url dos seus eventos.\


![Deletando webhooks via interface web.](https://github.com/AmandaAmani/documenta-ocurso/blob/main/deletando%20webhook.gif?raw=true)

***

Alternativamente, você pode deletar o webhook com este endpoint:

## Deletar webhook via api

<mark style="color:red;">`DELETE`</mark> `https://api.zapsign.com.br/api/v1/user/company/webhook/delete/`

#### Headers

<table><thead><tr><th width="292">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

```
{
    "id": "{{webhook_id}}"
}

```

| Name                                 | Type   | Description                  |
| ------------------------------------ | ------ | ---------------------------- |
| id<mark style="color:red;">\*</mark> | string | Id do webhook a ser deletado |

{% tabs %}
{% tab title="200: OK " %}
Webhook deletado com sucesso
{% endtab %}
{% endtabs %}

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-3c2b30d8-1ee5-4afa-b37a-8693355812c7?ctx=documentation" %}
