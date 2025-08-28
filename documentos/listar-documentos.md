# Listar documentos

{% hint style="warning" %}
Esse endpoint possui um cache com expiração de 60 minutos.
{% endhint %}

## Listar documentos

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/docs/?page=1`

Esse endpoint permite que você liste todos os documentos da sua conta.

#### Query Parameters

| Name | Type   | Description                                                                                                                                                                                                                                  |
| ---- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| page | number | Page vai de 1 a N (qualquer número inteiro positivo). Por default, este endpoint retorna a lista de documentos na sua conta ordenada em páginas com 25 documentos cada. Assim, para ir para a próxima página, mude o "page=N" na requisição. |

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

{% tabs %}
{% tab title="200 Documentos listados." %}
```javascript
[
    {
        "open_id": 1,
        "token": "7d23fcfa-d37e-44c6-a3c1-677a66383910",
        "status": "pending",
        "name": "Documento teste",
        "original_file": "https://zapsign.s3.amazonaws.com/pdf/0431xxx8-2145-463f-ab2d-540eb77aa3fd/fe998382-cae7-4dd7-8028-cbc679d800d3.pdf",
        "signed_file": null,
        "created_at": "2020-04-16T02:43:31.500058Z",
        "last_update_at": "2020-04-16T02:43:31.500122Z"
    },
    {
        "open_id": 2,
        "token": "6b9da26c-b5d1-497e-9516-6a82fbadaa20",
        "status": "pending",
        "name": "Documento teste 2",
        "original_file": "https://zapsign.s3.amazonaws.com/pdf/3ebxxxc67-df04-412f-99e9-d1338377f7e2/9e16a4cb-7176-4a2f-8cf9-eb9289f7a8e7.pdf",
        "signed_file": null,
        "created_at": "2020-04-16T02:44:13.713004Z",
        "last_update_at": "2020-04-16T02:44:13.713060Z"
    },
    {
        "open_id": 3,
        "token": "12f7e1e0-71d0-4581-a49c-9f9ce6e3cae1",
        "status": "signed",
        "name": "Documento teste 3",
        "original_file": "https://zapsign.s3.amazonaws.com/pdf/5xxx1fa0-eaa6-4d5e-ab6a-46cb942f07ef/1aaacad4-ef56-40a6-bd23-3eb9e309a6cf.pdf",
        "signed_file": "https://zapsign.s3.amazonaws.com/pdf/8xxxccca0-eaa6-4d5e-ab6a-46cb942f07ef/1aaacad4-ef56-40a6-bd23-3eb9e309a6cf.pdf",
        "created_at": "2020-04-16T02:51:01.918228Z",
        "last_update_at": "2020-04-16T02:51:01.918333Z"
    }
]
```
{% endtab %}
{% endtabs %}

### Filtrando documentos de uma pasta

Caso você deseje filtrar apenas documentos de uma determinada pasta, acrescente ao GET o parâmetro opcional "folder\_path". Por exemplo:

**Todos documentos da conta (sem filtro de pasta):**\
https://api.zapsign.com.br/api/v1/docs/?page=1

**Filtrando somente documentos Sem pasta (ou seja, na raiz "/"):**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&folder\_path=/**

**Filtrando somente documentos na pasta "/api/pasta2/":**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&folder\_path=/api/pasta2/**

### Filtrando documentos excluídos ou não excluídos

Caso você deseje filtrar apenas documentos excluídos ou não excluídos, acrescente ao GET o parâmetro opcional "deleted". Por exemplo:

**Apenas documentos não excluídos:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&deleted=false**

**Apenas documentos excluídos:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&deleted=true**

### Filtrando por signatários

Caso você queira filtrar por signatário, acrescente ao GET o parâmetro opcional "signer\_email". Por exemplo:

**Por e-mail do signatário:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&signer\_email=email@zapsign.com.br**

### Filtrando documentos por status

Caso você deseje filtrar documentos assinados, em curso ou recusados, acrescente ao GET o parâmetro opcional "status". Por exemplo:

**Apenas documentos assinados:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&status=signed**

**Apenas documentos em curso:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&status=pending**

**Apenas documentos recusados:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**\&status=refused**

### Filtrando documentos por data de criação

Caso você deseje filtrar documentos por data de criação, acrescente ao GET os parâmetros opcionais "created\_from" e "created\_to", com o formato YYYY-MM-DD. Por exemplo:

**Apenas documentos criados em janeiro de 2024:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**&**&#x63;reated\_fro&#x6D;**=2024-01-01\&created\_to=2024-01-30**

### Ordenando a resposta da requisição

Caso você deseje ordenar a resposta da listagem dos documentos por data de criação, acrescente ao GET o parâmetro opcional "sort\_order". Por exemplo:

**Ordenando documentos em ordem ascendente:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**&**&#x73;ort\_orde&#x72;**=asc**

**Ordenando documentos em ordem descendente:**\
https://api.zapsign.com.br/api/v1/docs/?page=&#x31;**&**&#x73;ort\_orde&#x72;**=desc**





{% hint style="info" %}
**Dica:** em vez de consultar os documentos várias vezes ao dia, utilize nossos [webhooks](https://docs.zapsign.com.br/webhooks/como-funciona). Além de ser uma economia da capacidade computacional dos nossos e seus servidores, você também conseguirá dar um feedback em tempo real ao seu usuário, e não a cada N minutos.
{% endhint %}

### Exemplo de resposta

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que este endpoint seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```javascript
{
    "count": 336,
    "next": "https://api.zapsign.com.br/api/v1/docs/?api_token=xxxx&page=4",
    "previous": "https://api.zapsign.com.br/api/v1/docs/?api_token=xxxx&page=2",
    "results": [
        {
            "open_id": 201,
            "token": "373xxxx-5f7e-4218-917e-9b6f6f7b2aa1",
            "status": "signed",
            "name": "Contrato X.pdf",
            "original_file": "https://zapsign.s3.amazonaws.com/docs/f8d1e963-f4ce-471b-xxxxxfd6e43f6/60eexxxxxc1-9410-81a769ea53b5.pdf",
            "signed_file": "https://zapsign.s3.amazonaws.com/pdf/582a15yyyyy42-f105291252e1.pdf",
            "created_at": "2020-04-02T13:52:21.948145Z",
            "last_update_at": "2020-04-02T16:10:30.780585Z",
            "created_through": "web"
        },
        ...
    ]
}
```
