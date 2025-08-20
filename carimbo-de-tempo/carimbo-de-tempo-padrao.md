# Carimbo de Tempo padrão

Use este endpoint se não é necessário preservar a assinatura original do signatário, provando a existência do documento em uma data específica, sem mostrar nomes pessoais.

{% hint style="warning" %}
**Importante:** Essa nova assinatura não invalida ou remove o conteúdo assinado anteriormente, mas ao consultar no ITI, será o carimbo da ZapSign que aparecerá nas informações de assinatura.
{% endhint %}

{% embed url="https://www.postman.com/zapsign/zapsign-workspace/folder/lap0whq/api?action=share&creator=29042971&ctx=documentation" %}
Link para o endpoint já configurado no Postman
{% endembed %}

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/timestamp/`

**Headers**

| Name          | Value                          |
| ------------- | ------------------------------ |
| Content-Type  | `application/json`             |
| Authorization | `API_TOKEN_DA_SUA_ORGANIZAÇÃO` |

**Body**

Este campo **é uma string.** Basta adicionar a url pública do seu documento (pdf ou docx) de até 10mb. Alternativamente, você pode converter seu arquivo para um base64 e inserir neste parâmetro.&#x20;

```json

{
    "url":  <Adicione_sua_url_ou_base64>
}

```

**Respostas possíveis**

{% tabs %}
{% tab title="200 Sucess" %}
```json
{
    "url": "https://zapsign.s3.amazonaws.com/pdf/62c2b027-d8fc-4392-xas75-f3c46c3cfc7a/d33336-4182-8c8b-ded5287e4c0f.pdf"
}
```
{% endtab %}

{% tab title="402 Payment Required" %}
```json
{
  "error": "Payment Required"
}
```
{% endtab %}
{% endtabs %}

![Carimbo de Tempo padrão ](https://github.com/AmandaAmani/documenta-ocurso/blob/main/timestamp%20padrao%20total.gif?raw=true)

{% hint style="info" %}
[Fale com um especialista](https://api.whatsapp.com/send?phone=551140401991\&text=Ol%C3%A1,%20sou%20amanda@zapsign.com.br%20e%20gostaria%20de%20falar%20com%20vendas%20para%20comprar%20Carimbo%20de%20tempo) para adicionar a funcionalidade ao seu plano!
{% endhint %}

Alternativamente, você pode utilizar o carimbo de tempo que mantém a assinatura do signatário visível no validador. Saiba mais no artigo a seguir!
