---
description: Adicionar anexo (documento extra)
---

# addExtraDoc

### Visão geral

Parâmetros:&#x20;

* [ExtraDoc](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/extradoc)

Retorno:

* [ExtraDocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/extradocresponse) - caso sucesso
* Exception - caso falha

Para adicionar esse documento extra precisamos:

* definir seu token api.
* token do documento original.
* definir o documento extra.
* chamar o método.

### Uso:

Salve seu [Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>



Salve token do documento original:

<pre class="language-typescript"><code class="lang-typescript"><strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";
</strong></code></pre>



Defina seu documento extra com a classe [ExtraDoc:](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/extradoc)

```typescript
const extraDoc: ExtraDocBuilder = ExtraDocBuilder()
                .withName("Extra Doc Name")
                .withUrlPdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                .build();
```



Chame o método addExtraDoc e receba como resposta a classe[ ExtraDocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/extradocresponse) ou uma mensagem de erro:

<pre class="language-typescript"><code class="lang-typescript">async function exempleAddExtraDoc() {
            try {
                        docResponse: DocResponse = await new DocRequests(apiToken).addExtraDoc(docToken, extraDoc);
                        jsonDocResponse: string = new JsonConverter().extraDocToJson(docResponse);
                        console.log(jsonDocResponse);
                } catch(Err) {
                    console.log(Err);
                }
<strong>            }
</strong><strong>}
</strong></code></pre>

### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { ExtraDocBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/ExtraDocBuilder";
<strong>
</strong><strong>const apiToken: string = "SEU TOKEN";
</strong><strong>
</strong>const docToken: string = "TOKEN DOCUMENTO ORIGINAL";

const extraDoc: ExtraDocBuilder = ExtraDocBuilder()
                .withName("Extra Doc Name")
                .withUrlPdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                .build();
                
async function exempleAddExtraDoc() {
            try {
                        docResponse: DocResponse = await new DocRequests(apiToken).addExtraDoc(docToken, extraDoc);
                        jsonDocResponse: string = new JsonConverter().extraDocToJson(docResponse);
                        console.log(jsonDocResponse);
                } catch(Err) {
                        console.log(Err);
                }
}
</code></pre>
