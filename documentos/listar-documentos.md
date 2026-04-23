# Listar documentos

{% hint style="warning" %}
Esse endpoint possui um cache com expiração de 60 minutos.
{% endhint %}

Este endpoint permite listar todos os documentos da sua conta. Por padrão, os resultados são retornados de forma paginada.

<mark style="color:blue;">`GET`</mark> `https://api.zapsign.com.br/api/v1/docs/?page=1`

Esse endpoint permite que você liste todos os documentos da sua conta.

***

#### Parâmetros de URL (Query Params)

| **Parâmetro**     | **Tipo**  | **Descrição**                                                                          |
| ----------------- | --------- | -------------------------------------------------------------------------------------- |
| `page`            | `integer` | Número da página para navegação (ex: `?page=2`).                                       |
| `status`          | `string`  | Filtra por status: `pending` (em curso), `signed` (assinado) ou `refused` (recusado).  |
| `folder_path`     | `string`  | Filtra documentos em uma pasta específica. Use `/` para a raiz.                        |
| `deleted`         | `boolean` | `true` para listar apenas excluídos; `false` para ativos.                              |
| `signer_email`    | `string`  | Filtra documentos que possuam um signatário com este e-mail.                           |
| `created_from`    | `string`  | Data inicial (formato `YYYY-MM-DD`).                                                   |
| `created_to`      | `string`  | Data final (formato `YYYY-MM-DD`).                                                     |
| `sort_order`      | `string`  | Ordenação por data de criação: `asc` (antigos) ou `desc` (novos).                      |
| `include_signers` | `boolean` | (Novo) Use `true`, `1` ou `yes` para incluir o array de signatários em cada documento. |

***

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

***

#### Detalhes do parâmetro `include_signers`

Ao ativar este parâmetro, a API retornará o campo `signers` dentro de cada documento, contendo informações detalhadas:

* Campos incluídos: Nome, e-mail, telefone, modo de autenticação (`auth_mode`), flag de certificado digital, timestamps de interação, URL de assinatura e ordem de assinatura (caso a ordem esteja ativa).
* Status do Signatário: Exposto via um enum estável:
  * `nao_abriu`
  * `abriu`
  * `assinou`
  * `recusou`
  * `expirou`
  *   `cancelado`

      _(Nota: Status do documento têm precedência sobre o status individual quando aplicável)._

***

#### Observações importantes

* Consistência JSON: Strings vazias são normalizadas para `null` no retorno da API.
* Performance Otimizada: O endpoint utiliza `prefetch_related` para evitar problemas de N+1 queries ao solicitar os signatários, garantindo respostas rápidas mesmo em listagens volumosas.
* Links Temporários: Os campos `original_file` e `signed_file` retornam links que expiram em 60 minutos.
* Cache: Há um cache de 60 segundos para este endpoint. Se você acabou de criar um documento, ele pode levar até um minuto para aparecer nesta lista.

***

#### Exemplo de Resposta (JSON)

exemplo com `include_signers = True`

```json
{
    "count": 120,
    "next": "https://api.zapsign.com.br/api/v1/docs/?page=2",
    "previous": null,
    "results": [
        {
            "token": "4f9e-a1b2-c3d4",
            "name": "Contrato de Prestação de Serviços",
            "status": "pending",
            "original_file": "https://s3.amazonaws.com/...",
            "signed_file": null,
            "created_at": "2024-03-25T14:30:00Z",
            "folder_path": "/",
            "signers": [
                {
                    "name": "João Silva",
                    "email": "joao@email.com",
                    "status": "abriu",
                    "auth_mode": "assinatura_tela",
                    "signing_url": "https://zapsign.com.br/sign/...",
                    "has_certificate": false,
                    "order": 1
                }
            ]
        }
    ]
}


```

exemplo sem `include_signers`&#x20;

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

{% hint style="info" %}
**Dica:** em vez de consultar os documentos várias vezes ao dia, utilize nossos [webhooks](https://docs.zapsign.com.br/webhooks/como-funciona). Além de ser uma economia da capacidade computacional dos nossos e seus servidores, você também conseguirá dar um feedback em tempo real ao seu usuário, e não a cada N minutos.
{% endhint %}

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que este endpoint seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}
