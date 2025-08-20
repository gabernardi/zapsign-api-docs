---
description: Adicionar signatário
---

# addSigner

### Visão geral

Parâmetros:&#x20;

* String - token do documento
* [Signer](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signer)

Retorno:

* [Signer](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signer) - caso sucesso
* Exception - caso falha

Para adicionar esse signatário precisamos:

* definir seu token api;
* definir o token do documento;
* criar novo signatário;
* chamar o método.

### Uso:

Salve seu [Api Token](../../../../):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve o token de seu signatário:

```typescript
const signerToken: string = "TOKEN DO SIGNATÁRIO";
```



Crie seu signatário com a classe [Signer](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signer):

```typescript
const signerBuilder = SignerBuilder()
    .withName("New Signer Name")
    .withEmail("newEmail@test.com")
    .withLockEmail(true)
    .withLockPhone(true)
    .withPhoneCountry("55")
    .withPhoneNumber("999999999")
    .withAuthMode("assinaturaTela")
    .withSendAutomaticAemail(false)
    .withSendAutomaticWhatsApp(false)
    .build();
```

Chame o método addSigner e receba como resposta a classe [Signer](https://app.gitbook.com/s/-M4noMoX5ZGb2-RhWjjf-887967055/~/changes/193/facilitadores/sdks/sdk-typescript/classes-usadas/body/signer) ou uma mensagem de erro:

```typescript
async function exempleAddSigner() {
    try {
        signerResponse: string = new SignerRequest(apiToken).addSigner(signerToken, signer);
        jsonDocResponse: string = new JsonConverter().signerToJson(signerResponse);
        console.log(jsonDocResponse);
    }
    catch(Err) {
        console.log(Err);
    }    
}
```



### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import SignerRequest from "sdk-node-typescript-zapsign/src/signer/SignerRequest";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { SignerBuilder } from "sdk-node-typescript-zapsign/src/body/signer/builders/SignerBuilder";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong>const docToken: string = "TOKEN DOCUMENTO";

const signerBuilder = SignerBuilder()
    .withName("New Signer Name")
    .withEmail("newEmail@test.com")
    .withLockEmail(true)
    .withLockPhone(true)
    .withPhoneCountry("55")
    .withPhoneNumber("999999999")
    .withAuthMode("assinaturaTela")
    .withSendAutomaticAemail(false)
    .withSendAutomaticWhatsApp(false)
    .build();
    
async function exempleAddSigner() {
    try {
        signerResponse: string = new SignerRequest(apiToken).addSigner(signerToken, signer);
        jsonDocResponse: string = new JsonConverter().signerToJson(signerResponse);
        console.log(jsonDocResponse);
    }
    catch(Err) {
        console.log(Err);
    }    
}
</code></pre>



