# Obter token de acesso

Para **obter o Token de Acesso**, **faça uma requisição ao endpoint de autenticação com as credenciais do seu usuário ZapSign.** Este endpoint retornará tanto o Token de Acesso quanto o Token de Atualização.

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/auth/token/{{ID_organização}}`

{% code title="Request Body" %}
```json
{
    "username": "dev@exemplo.com.br",
    "password": "Senhaforte123"
}
```
{% endcode %}

{% hint style="info" %}
Você  pode obter o ID da sua organização navegando até **configurações>integrações>api token>ID da organização.**
{% endhint %}

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>



{% tabs %}
{% tab title="200: OK Autenticação realizada com sucesso" %}
{% code overflow="wrap" %}
```json
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTcxMDE3ODM0NCwianRpIjoiYjhmZjMwNDJmNjRkNDJmM2FlMzczZmRiNDQ3YTQ2NGEiLCJ1c2Vyb",
    "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```
{% endcode %}
{% endtab %}

{% tab title="401: Unauthorized Credenciais Inválidas" %}
{% code overflow="wrap" %}
```json
{
    "detail": "No active account found with the given credentials"
}
```
{% endcode %}
{% endtab %}

{% tab title="400: Bad Request Tentativas de login excedidas" %}
```javascript
{
    "message": "Rate limit exceeded"
}
```
{% endtab %}
{% endtabs %}



## Uso do Token&#x20;

Após obter seu Token, você poderá autenticar-se nos endpoints da ZapSign, incluindo o seu token no cabeçalho "Authorization" da sua requisição, utilizando o prefixo "Bearer". Exemplo:

```javascript
  'headers': {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNzA5ODIwMTQxLCJqdGkiOiIxMGM4YmVhOTkxNDM0ZGU5OWQxNmViMGE2ZTA3MTU1YyIsInVzZXJfaWQiOjEsInR5cGUiOiJwdWJsaWMifQ.GhMKXDyiidHrWCSmU3I9e6-zDm61mBmDqEavir4IW0c'
  },
```

Após uma hora, você precisará se autenticar novamente, saiba como no capítulo ["Atualize seu token de acesso"](atualize-seu-token-de-acesso.md).
