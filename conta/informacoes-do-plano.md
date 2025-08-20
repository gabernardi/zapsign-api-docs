# Informações do Plano

Para facilitar o gerenciamento do seu plano, você pode consultar informações detalhadas sobre seu status e créditos disponíveis diretamente pela API. Este endpoint fornece dados essenciais sobre o plano atual, permitindo que você tenha mais autonomia para acompanhar seu status e gerenciar seu uso.\
\
\
Endpoint: <mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/info-plan/`

#### Headers

<table><thead><tr><th>Name</th><th width="189">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

![Informações do Plano](https://github.com/AmandaAmani/documenta-ocurso/blob/main/info%20plan.gif?raw=true)

\
\
Este endpoint retorna informações sobre o plano, incluindo:

* **Nome do plano** (`name`)
* **Número de créditos** da conta (`number_of_credits`)
* **Status** do plano (`status`): pode ser `paid`, `pending_payment`, `unpaid` ou `canceled`
* **Período** (`period`): mensal (`monthly`) ou anual (`annual`)
* **Data de encerramento** do período atual (`current_period_end`)

### Respostas

{% tabs %}
{% tab title="200- plano encontrado" %}
<pre><code>{
<strong>    "name": "Test Plan",
</strong>    "number_of_credits": "100",
    "status": "paid",
    "period": "annual",
    "current_period_end": "dd-mm-yyyy"
}
</code></pre>
{% endtab %}

{% tab title="404- Plano nao encontrado" %}
Unable to find information about this plan
{% endtab %}
{% endtabs %}

