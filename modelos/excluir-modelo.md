---
description: Exclui um modelo da conta.
---

# Excluir modelo

{% hint style="danger" %}
**A exclusão do modelo é irreversível**. Caso deseje utilizar o modelo novamente, o mesmo deverá ser recriado.
{% endhint %}

{% hint style="info" %}
O método de requisição é DELETE. Caso use GET ou POST, não tera o efeito desejado.
{% endhint %}

## Detalhar modelo

<mark style="color:red;">`DELETE`</mark>`https://api.zapsign.com.br/api/v1/templates/{{template_token}}/`&#x20;

{% hint style="success" %}
No endpoint acima, substitua `{{template_token}}` pelo token exclusivo do modelo que deseja detalhar.&#x20;
{% endhint %}

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    "message": "Modelo excluído com sucesso."
}
```
{% endtab %}
{% endtabs %}
