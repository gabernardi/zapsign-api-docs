---
description: >-
  Após uma hora você precisará atualizar seu token nas suas integrações, para
  isso, utilize o refresh token obtido na chamada anterior.
---

# Atualize seu token de acesso

## Atualizar token de acesso

O Token de Atualização serve para renovar o Token de Acesso. Esse token tem um tempo de expiração de 1 hora.

* **Uso do Token de Atualização:**\
  Quando o Token de Acesso expirar (após 1 hora), utilize o Token de Atualização para solicitar um novo Token de Acesso, que será válido por mais 1 hora.

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/auth/token-refresh/`



```json
Request Body

{
    "refresh": "Token_obtido_na_chamada_do_token_de_acesso"
}

```

| Name                                      | Type   | Description                                                                                  |
| ----------------------------------------- | ------ | -------------------------------------------------------------------------------------------- |
| refresh<mark style="color:red;">\*</mark> | string | O campo `refresh` retornado em[obter-token-de-acesso.md](obter-token-de-acesso.md "mention") |

{% tabs %}
{% tab title="200: OK Atualização realizada com sucesso" %}
{% code overflow="wrap" %}
```json
{
    "access": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```
{% endcode %}
{% endtab %}

{% tab title="401: Unauthorized Token Inválido" %}
{% code overflow="wrap" %}
```json
{
    "detail": "Token is invalid or expired",
    "code": "token_not_valid"
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

