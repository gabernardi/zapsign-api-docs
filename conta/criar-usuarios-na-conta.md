# Criar usuários na conta

Esse endpoint permite a criação de novos usuários vinculados à organização via API. \
\
Ao utilizar essa funcionalidade, é possível adicionar novos membros à organização, configurando os níveis de permissões adequadas e garantindo que todos os dados necessários, como contato, e-mail, nome e etc. sejam devidamente registrados para o novo usuário.

{% hint style="danger" %}
**IMPORTANTE:** Antes da criação do novo usuário ser concluída, será validado o número de usuários disponíveis dentro da organização. Caso o limite tenha sido atingido, não será possível realizar a criação do novo usuário.
{% endhint %}

{% hint style="info" %}
O método de requisição é POST. Caso use PATCH ou PUT, não terá o efeito desejado.
{% endhint %}

## Criar novos usuários

<mark style="color:green;">`POST`</mark>`https://api.zapsign.com.br/api/v1/users/create-user`

### **Headers**

<table><thead><tr><th width="159">Name</th><th width="154">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

### **Request Body**

<table><thead><tr><th width="159">Name</th><th width="158">Type</th><th>Description</th></tr></thead><tbody><tr><td>email</td><td>string</td><td>E-mail do usuário. String de até 255 caracteres e deve ser um e-mail válido. (Campo obrigatório)</td></tr><tr><td>role</td><td>string</td><td>Nível de permissão do usuário dentro da organização. Valores possíveis: "member" (Membro), "admin" (Administrador), "self_docs_limited" (Acesso limitado aos próprios documentos). Default: "self_docs_limited".</td></tr><tr><td>first_name</td><td>string</td><td>Primeiro nome do usuário. String de até 255 caracteres.</td></tr><tr><td>last_name</td><td>string</td><td>Último nome do usuário. String de até 255 caracteres.</td></tr><tr><td>phone_country</td><td>string</td><td>Código do país do usuário. (Ex: 55). </td></tr><tr><td>phone_number</td><td>string</td><td>Número do telefone do usuário. (Ex: 11999999999).</td></tr></tbody></table>

{% hint style="warning" %}
O parâmetro **email** é obrigatório para a criação do novo usuário. Caso valor não seja fornecido no corpo da requisição, não será possível adicionar usuário à organização.
{% endhint %}

{% hint style="info" %}
**Aviso**: Não é possível criar um novo usuário com permissão de 'proprietário'.
{% endhint %}

### Request

```json
{
    "email":"loremipsum@email.com",
    "role":"admin",
    "first_name":"Lorem",
    "last_name":"Ipsum",
    "phone_country":"55",
    "phone_number":"11999999999"
}
```

### Response

{% tabs %}
{% tab title="200: OK" %}
```javascript
{
    "message": "Usuário criado com sucesso."
}
```
{% endtab %}
{% endtabs %}
