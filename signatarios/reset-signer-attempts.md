# Resetar tentativas de validação

Se um signatário falhar no processo de validação três vezes, o documento será bloqueado e ele não poderá continuar com a assinatura. Este endpoint permite resetar as tentativas de validação de um signatário específico, possibilitando que ele reinicie o processo de validação.

{% hint style="warning" %}
**Importante:** Ao resetar as tentativas, caso o signatário inicie novamente o processo de validação, haverá um custo adicional de créditos conforme o método selecionado ([veja os preços aqui](https://app.zapsign.com.br/conta/configuracoes/plans?tab=credits)). O signatário terá três (3) novas tentativas para validar sua identidade e, se falhar novamente, o processo será bloqueado mais uma vez.
{% endhint %}

<mark style="color:blue;">**PUT**</mark> `https://api.zapsign.com.br/api/v1/reset-auth-attempts/{{signer_token}}/`

#### Parametros

<table><thead><tr><th width="162">Name</th><th width="128">Type</th><th>Description</th></tr></thead><tbody><tr><td>signer_token</td><td>string</td><td>Token único do signatário (obtido ao criar o documento).</td></tr></tbody></table>

#### Exemplo response

{% tabs %}
{% tab title="200 - sucesso" %}
```json
{
    "success": "As tentativas do signatário foram resetadas com sucesso."
}
```
{% endtab %}

{% tab title="400 - erro" %}
```json
{
    "error": "Signatário tem tentativas"
}
```
{% endtab %}
{% endtabs %}

### **Nota importante**

Este endpoint de reset de tentativas só se aplica aos métodos de autenticação que possuem reintentos, especificamente quando o parâmetro `selfie_validation_type` corresponde a um dos seguintes valores:

* `liveness-document-match`
* `identity-verification`
* `identity-verification-global`
* `face-match-and-datavalid`

Para outros métodos de autenticação que não requerem captura de selfie ou validação biométrica, este endpoint não tem efeito.
