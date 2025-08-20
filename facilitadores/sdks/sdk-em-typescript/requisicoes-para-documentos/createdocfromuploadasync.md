---
description: Criar documento via Upload pdf Assíncrono
---

# createDocFromUploadAsync

### Visão geral

Parâmetros:&#x20;

* [DocFromPdf](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfrompdf)

Retorno:

* [DocAsyncResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docasyncresponse) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api;
* definir os signatários;
* definir o documento;
* chamar o método.

Salve seu[ Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>

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

Defina seu documento com a classe [DocFromPdf](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfrompdf):

```typescript
const docFromPdf: DocFromPdf = new DocFromPdfBuilder()
                                .withSandbox(false)
                                .withName("My Contract")
                                .withPrimaryColor("#000000")
                                .withLang("pt-br")
                                .withSigners(signers)
                                .withUrlPdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                                .build();
```

Chame o método createDocFromUploadAsync e receba como resposta a classe [docAsyncResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docasyncresponse)  ou uma mensagem de erro:

```typescript
async function exempleCreateDocFromUploadAsync() {
    try {
        docResponse: DocResponse = await new DocRequests(apiToken).createDocFromUploadAsync(docFromPdf);
        jsonDocResponse: string = new JsonConverter().docAsyncResponseToJson(docResponse);
        console.log(jsonDocResponse);
    } catch(Err) {
        console.log(Err);
    }
}
```

### Exemplo completo:

```typescript
import { Signer } from "sdk-node-typescript-zapsign/src/body/signer/Signer";
import { SignerBuilder } from 'sdk-node-typescript-zapsign/src/body/signer/builders/SignerBuilder';
import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { DocFromPdfBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/DocFromPdfBuilder";
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

const docFromPdf: DocFromPdf = new DocFromPdfBuilder()
                                .withSandbox(false)
                                .withName("My Contract")
                                .withPrimaryColor("#000000")
                                .withLang("pt-br")
                                .withSigners(signers)
                                .withUrlPdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                                .build();
                                
async function exempleCreateDocFromUploadAsync() {
    try {
        docResponse: DocResponse = await new DocRequests(apiToken).createDocFromUploadAsync(docFromPdf);
        jsonDocResponse: string = new JsonConverter().docAsyncResponseToJson(docResponse);
        console.log(jsonDocResponse);
    } catch(Err) {
        console.log(Err);
    }
}
```
