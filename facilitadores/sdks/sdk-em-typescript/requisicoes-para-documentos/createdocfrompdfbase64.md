---
description: Criar documento via pdf de um base64
---

# createDocFromPdfBase64

### Visão geral

Parâmetros:&#x20;

* [DocFromPdf](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfrompdfbase64)

Retorno:

* [DocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api;
* definir os signatários;
* definir o documento;
* chamar o método.

### Uso:

Salve seu[ Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>

Salve seu base64:

```typescript
const base64: string = "JVBERi0xLjYKJcOkw7zDtsOfCjIgMCBvYmoKPDwvTG..."
```

Salve seu base64:

```typescript
const base64: string = "JVBERi0xLjYKJcOkw7zDtsOfCjIgMCBvYmoKPDwvTG..."ty
```



Crie seus signatários com a classe [Signer](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/signer):

```typescript
const signer1: Signer = new SignerBuilder()
                .withName("My First Signer")
                .build();

const signer2: Signer = new SignerBuilder()
                .withName("My Second Signer")
                .withEmail("test@test.com")
                .withLockEmail(true)
                .withLockPhone(true)
                .withPhoneCountry("55")
                .withPhoneNumber("99999999999")
                .withAuthMode("assinaturaTela")
                .withSendAutomaticEmail(false)
                .withSendAutomaticWhatsapp(false)
                .build();
                
let signers: Signer[] = [];
                
signers.push(signer1, signer2);
```

Defina seu documento com a classe [DocFromPdfBase64](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfrompdfbase64):

```typescript
const docFromPdfBase64 = DocFromPdfBase64Builder()
    .withSandbox(false)
    .withName("My Contract")
    .withBrandPrimaryColor("#000000")
    .withBase64Pdf(base64)
    .build();
```

Chame o método createDocFromPdfBase64 e receba como resposta a classe [DocResponse ](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse)ou uma mensagem de erro:

<pre class="language-typescript"><code class="lang-typescript">try {
<strong>    docResponse = new DocRequests(apiToken).createDocFromPdfBase64(docFromPdfBase64);
</strong>    jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
    console.log(jsonDocResponse);
} catch {
     console.log(Err);
}
</code></pre>

### Exemplo completo:

```typescript
import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";

const apiToken: string = "SEU TOKEN";

const base64: string = "JVBERi0xLjYKJcOkw7zDtsOfCjIgMCBvYmoKP...";

const signer1: Signer = new SignerBuilder()
                .withName("My First Signer")
                .build();

const signer2: Signer = new SignerBuilder()
                .withName("My Second Signer")
                .withEmail("test@test.com")
                .withLockEmail(true)
                .withLockPhone(true)
                .withPhoneCountry("55")
                .withPhoneNumber("99999999999")
                .withAuthMode("assinaturaTela")
                .withSendAutomaticEmail(false)
                .withSendAutomaticWhatsapp(false)
                .build();
                
let signers: Signer[] = [];
                
signers.push(signer1, signer2);

const docFromPdfBase64 = DocFromPdfBase64Builder()
    .withSandbox(false)
    .withName("My Contract")
    .withBrandPrimaryColor("#000000")
    .build();

async function exempleDocFRomPdfBase64() {
    try {
                docResponse: DocResponse = await new DocRequests(apiToken).createDocFromPdfBase64(docFromPdfBase64);
                jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
                console.log(jsonDocResponse);
    } catch(Err) {
                console.log(Err);
    }
  }
}
```
