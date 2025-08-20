---
description: Posicionar assinaturas
---

# placeSignatures

### Visão geral

Parâmetros:&#x20;

* String - token do documento
* [RubricaList](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/rubricalist)

Retorno:

* int- caso sucesso
* Exception - caso falha

Para posicionar as rubricas nesse documento precisamos:

* definir seu token api.
* token do documento.
* definir as rúbricas.
* chamar o método.

### Uso:

Salve seu [Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve token do documento original:

<pre class="language-typescript"><code class="lang-typescript"><strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";
</strong></code></pre>



Defina suas rúbricas em uma classe [RubricaList ](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/rubricalist)que contenha arrays de classe [Rubrica](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/rubrica):

```typescript
const rubrica1: RubricaBuilder = rubricaBuilder()
                .withPage(0)
                .withtRelativePositionBottom(52.50)
                .withRelativePositionLeft(75.71)
                .withRelativeSizeX(19.55)
                .withRelativePositionSizeY(9.42)
                .withType("signature")
                .withSignerToken("TOKEN SIGNER")
                .build();
                
const rubrica2: RubricaBuilder = rubricaBuilder()
                .withPage(0)
                .withtRelativePositionBottom(13.50)
                .withRelativePositionLeft(20.71)
                .withRelativeSizeX(19.55)
                .withRelativePositionSizeY(9.42)
                .withType("signature")
                .withSignerToken("TOKEN SIGNER")
                .build();
                
let rubricas = RubricaBuilder[];
rubricas.push(rubrica1, rubrica2);

const rubricasArray = new RubricaArray(rubricas);
```



Chame o método placeSignatures e receba como resposta um inteiro contendo o status code da resposta ou uma mensagem de erro:

```typescript
async function exempleAddExtraDoc() {
        try {
                statusCode: number = await new DocRequests(apiToken).placeSignatures(docToken, rubricasArray);
                console.log(statusCode);
        } catch(Err) {
            console.log(Err);
        }
    }
}
```



### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { RubricaBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/RubricaBuilder";
import { RubricasArray } from "sdk-node-typescript-zapsign/src/body/doc/RubricasArray";

<strong>const apiToken: string = "SEU TOKEN";
</strong><strong>
</strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";

const rubrica1: RubricaBuilder = RubricaBuilder()
                .withPage(0)
                .withtRelativePositionBottom(52.50)
                .withRelativePositionLeft(75.71)
                .withRelativeSizeX(19.55)
                .withRelativePositionSizeY(9.42)
                .withType("signature")
                .withSignerToken("TOKEN SIGNER")
                .build();
                
const rubrica2: RubricaBuilder = rubricaBuilder()
                .withPage(0)
                .withtRelativePositionBottom(13.50)
                .withRelativePositionLeft(20.71)
                .withRelativeSizeX(19.55)
                .withRelativePositionSizeY(9.42)
                .withType("signature")
                .withSignerToken("TOKEN SIGNER")
                .build();
                
let rubricas = RubricaBuilder[];
rubricas.push(rubrica1, rubrica2);

const rubricasArray = new RubricasArray(rubricas);

async function exempleAddExtraDoc() {
        try {
                statusCode: number = await new DocRequests(apiToken).placeSignatures(docToken, rubricasArray);
                console.log(statusCode);
        } catch(Err) {
            console.log(Err);
        }
    }
}
</code></pre>

