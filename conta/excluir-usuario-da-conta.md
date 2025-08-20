# Excluir usuário da conta

Remove o vínculo de um usuário da conta da organização.

{% hint style="danger" %}
**IMPORTANTE:** Ao remover um usuário da organização, ele perderá o acesso a todos os recursos, como documentos e modelos. Contudo, **os documentos criados por ele** permanecerão na organização e continuarão acessíveis aos demais membros.
{% endhint %}

{% hint style="info" %}
O método de requisição é DELETE. Caso use GET ou POST, não terá o efeito desejado.
{% endhint %}

## Remover usuário

<mark style="color:red;">`DELETE`</mark>`https://api.zapsign.com.br/api/v1/users/{{user_email}}/`&#x20;

{% hint style="success" %}
No endpoint acima, substitua `{{user_email}}` pelo e-mail do usuário que deseja remover da organização.
{% endhint %}

#### Headers

<table><thead><tr><th width="163">Name</th><th width="148">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

{% tabs %}
{% tab title="200: OK " %}
```json
{
    "message": "Usuário excluído da organização com sucesso."
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Aviso**: Não é possível remover usuários com permissão de proprietário da organização.
{% endhint %}
