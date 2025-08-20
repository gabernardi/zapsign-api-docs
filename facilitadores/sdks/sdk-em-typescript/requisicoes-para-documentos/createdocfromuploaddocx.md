---
description: Criar documento via Upload docx
---

# createDocFromUploadDocx

### Visão geral

Parâmetros:&#x20;

* [DocFromDocx](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfromdocx)

Retorno:

* [DocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api;
* definir os signatários;
* definir o documento;
* chamar o método.

Salve seu[ Api Token](https://docs.zapsign.com.br/):

```typescript
const apiToken: string = "SEU TOKEN";
```

Crie seus signatários com a classe [Signer](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/signer):

<pre class="language-typescript"><code class="lang-typescript"><strong>const signer1: Signer = new SignerBuilder()
</strong>                .withName("My First Signer")
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
</code></pre>

Defina seu documento com a classe [DocFromDocx](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfromdocx):

```typescript
const docFromDocx: DocFromDocx = DocFromDocxBuilder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .url_docx("https://zapsign.s3.amazonaws.com/2022/1/docs/d7660fd2-fe74-4691-bec8-5c42c0ae2b3f/39a35070-8987-476d-86e3-75d91f588a5a.docx")
                .build();
```

Chame o método createDocFromUploadPdf e receba como resposta a classe [DocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docresponse) ou uma mensagem de erro:

```typescript
async function exempleCreateDocFromUploadDocx() {
    try {
        docResponse: DocResponse = await new DocRequests(apiToken).createDocFromUploadDocx(docFromPdf);
        jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
        console.log(jsonDocResponse);
    } catch(Err) {
        console.log(Err);
    }
}
```

### Exemplo completo:

```typescript
import { SignerBuilder } from 'sdk-node-typescript-zapsign/src/body/signer/builders/SignerBuilder';
import { Signer } from "sdk-node-typescript-zapsign/src/body/signer/Signer";
import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { DocFromDocxBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/DocFromDocxBuilder";

apiToken: string = "SEU TOKEN";

signer1: Signer = new SignerBuilder()
                .withName("My First Signer")
                .build();

signer2: Signer = new SignerBuilder()
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

const docFromDocx: DocFromDocx = new DocFroDocxBuilder()
                                .withSandbox(false)
                                .withName("My Contract")
                                .withBrandLogo("#000000")
                                .withLang("pt-br")
                                .withSigners(signers)
                                .withUrlPdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                                .build();
                                
async function exempleCreateDocFromUploadDocx() {
    try {
        docResponse: DocResponse = await new DocRequests(apiToken).createDocFromUploadDocx(docFromPdf);
        jsonDocResponse: string = new JsonConverter().docResponseToJson(docResponse);
        console.log(jsonDocResponse);
    } catch(Err) {
        console.log(Err);
    }
}
```

