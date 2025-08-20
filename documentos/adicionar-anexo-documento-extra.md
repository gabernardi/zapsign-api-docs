# Adicionar anexo (documento extra)

### Adicionar documento extra

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_principal_token}}/upload-extra-doc/`

Esse endpoint permite que você anexe um documento extra ao documento principal. É possível anexar até 14 documentos (um por vez, isto é, uma requisição para cada anexo), totalizando 15 documentos que o signatário pode assinar de uma vez só.&#x20;

#### Headers

<table><thead><tr><th width="143.05328369140625">Name</th><th width="122.446044921875">Type</th><th>Description</th></tr></thead><tbody><tr><td>Authorization<mark style="color:red;">*</mark></td><td>string</td><td><p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p></td></tr></tbody></table>

#### Request Body

<table><thead><tr><th width="176.64349365234375">Name</th><th width="117.02978515625">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Título do documento extra. String de até 255 caracteres</td></tr><tr><td>url_pdf</td><td>string</td><td>Defina o PDF a ser assinado, a partir de uma URL pública com o arquivo. Aceitamos por enquanto apenas um arquivo no formato PDF, de até 10Mb. </td></tr><tr><td>base64_pdf</td><td>string</td><td><p><strong>Alternativa ao url_pdf:</strong> Defina o PDF a ser assinado, a partir de um base64. Você deve converter o arquivo para uma string em base64 e nos enviar neste parâmetro.</p><p>Ex:</p><p>{</p><p>... 	"base64_pdf":"JVBERi0xLjcNCiWhs8XXDQoxIDA...",</p><p>}</p></td></tr></tbody></table>

{% tabs %}
{% tab title="200 Documento extra adicionado com sucesso." %}
```json
{
    "open_id": 17,
    //utilize esse token caso queira posicionar assinaturas neste documento extra
    "token": "50c7d90e-ead6-46b5-99d6-33d2d3b9a31f", 
    "name": "Anexo ao Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/48025712-b429-4216-8a33-d90c575d0b7f/0e2d0a87-a0f6-4a49-a05f-7a439fd7308e.pdf",
    "signed_file": null
},
```
{% endtab %}
{% endtabs %}

Não há outros parâmetros a serem enviados na requisição, pois todos eles serão herdados do documento principal.

{% hint style="info" %}
**Obs:** não confunda a adição de anexos com a [assinatura em lote via API](https://docs.zapsign.com.br/signatarios/assinar-em-lote-via-api), já que nesta última a assinatura é feita programaticamente pelo seu sistema via código. Os casos de uso são distintos.
{% endhint %}

### Exemplo de requisição

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-b41b0068-b7e4-47aa-a828-e65084fcdb4b?ctx=documentation" %}

### Exemplo de retorno

{% hint style="warning" %}
**Atenção**: os links retornados em **original\_file** e **signed\_file** são temporários e duram **60 minutos**. Caso seu sistema necessite salvar estes links é recomendado que sejam baixados em uma CDN própria ou que o endpoint de [Detalhar documento](detalhar-documento.md) seja consultado sempre para garantir que seu usuário sempre receberá um link válido.
{% endhint %}

```javascript
{
    "open_id": 17,
    //utilize esse token caso queira posicionar assinaturas neste documento extra
    "token": "50c7d90e-ead6-46b5-99d6-33d2d3b9a31f", 
    "name": "Anexo ao Contrato de Admissão João",
    "original_file": "https://zapsign.s3.amazonaws.com/aaa/48025712-b429-4216-8a33-d90c575d0b7f/0e2d0a87-a0f6-4a49-a05f-7a439fd7308e.pdf",
    "signed_file": null
},
```

### Perguntas frequentes

#### O que é um anexo/documento extra?

Caso você utilize a plataforma web da ZapSign, irá perceber que é possível subir vários PDFs de uma vez para serem assinados pelos mesmos signatários:

![Exemplo na plataforma web de um envelope com 3 PDFs.](<../.gitbook/assets/image (49).png>)

Assim, quando o signatário vai assinar o documento, ele se depara com a lista de todos eles, para assinar de uma vez só:

![](<../.gitbook/assets/image (60).png>)

**O documento principal será o número 1** e os **documentos extras aparecerão para o signatário como documentos de número 2, 3, etc.** Ao fazer um GET no documento principal, os documentos extras aparecerão no parâmetro "extra\_docs".



**O documento extra consome crédito de API?** \
Sim. Cada documento extra conta igual a um documento principal. Assim, caso você adicione 14 documentos extras a um documento principal, isso contará como "15 créditos" de API, e não um só.&#x20;

**Eu consigo posicionar assinaturas no documento extra?** \
Sim! Basta encaminhar o token do documento extra no endpoint de posicionar assinaturas.

**Adicionei um anexo sem querer. Tem como remover/desfazer o engano?**\
Não. Por enquanto não é possível remover um anexo, depois de adicionado.
