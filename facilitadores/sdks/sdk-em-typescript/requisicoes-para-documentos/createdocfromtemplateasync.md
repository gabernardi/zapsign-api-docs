---
description: Criar documento via Modelo Assíncrono
---

# createDocFromTemplateAsync

### Visão geral

Parâmetros:&#x20;

* [DocFromTemplate](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfromtemplate)

Retorno:

* [DocAsyncResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docasyncresponse) - caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token ap;
* definir os signatários;
* definir o documento;
* chamar o método.

### Uso:

Salve seu [Api Token](https://docs.zapsign.com.br/):

<pre class="language-typescript"><code class="lang-typescript"><strong>const apiToken: string = "SEU TOKEN";
</strong></code></pre>

Adicione suas variáveis em uma lista de classe [DeParaTemplate](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/deparatemplate):

<pre class="language-typescript"><code class="lang-typescript"><strong>const deParaTemplateName: DeParaTemplateBuilder = deParaTemplateBuilder()
</strong>        .de("{{NOME COMPLETO}}")
        .para("{{Full Name}}")
        .build();
        
const deParaTemplateCpf: DeParaTemplateBuilder = deParaTemplateBuilder()
        .de("{{NÚMERO DO CPF}}")
        .para("{{Social Security Number}}")
        .build();
        
const deParaTemplateEndereco: DeParaTemplateBuilder = deParaTemplateBuilder()
        .de("{{ENDEREÇO COMPLETO}}")
        .para("{{Full address}}")
        .build();
        
let deParaTemplates: DeParaTemplatesBuilder[] = [];

deParaTemplates.push(deParaTemplateName, deParaTemplateCpf, deParaTemplateEndereco);
</code></pre>

Defina seu documento com a classe[ DocFromTemplate](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/body/docfromtemplate):

```typescript
const docFromTemplate: DocFomTemplateBuilder = new DocFromTemplateBuilder()
        .withSandbox(false)
        .withPrimaryColor("#000000")
        .withSignerName("My Signer for Template")
        .withTemplateId("SEU TEMPLATE ID")
        .withData(deParaTemplates)
        .build();
```

Chame o método createDocFromTemplate e receba como resposta a classe [DocResponse](https://docs.zapsign.com.br/facilitadores/sdks/sdk-em-typescript/classes-usadas/response/docasyncresponse) ou uma mensagem de erro:

```typescript
async function exempleCreateDocFromTemplateAsync() {
        try {
        docResponse: DocResponse = await new DocRequests(apiToken).createDocFromTemplateAsync(docFromTemplate);
        jsonDocResponse: string = new JsonConverter().docAsyncResponseToJson(docResponse);
        console.log(jsonDocResponse);
    } catch(Err) {
        console.log(Err);
    }
}
```

### Exemplo completo:

<pre class="language-typescript"><code class="lang-typescript">import { DeParaTemplateBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/DeParaTemplateBuilder";
import DocRequests from "sdk-node-typescript-zapsign/src/docs/DocRequests";
import { JsonConverter } from "sdk-node-typescript-zapsign/src/services/JsonConverter";
import { DocFromTemplateBuilder } from "sdk-node-typescript-zapsign/src/body/doc/builders/DocFromTemplateBuilder";
<strong>const apiToken: string = "SEU TOKEN";
</strong><strong>
</strong>const deParaTemplateName: DeParaTemplateBuilder = deParaTemplateBuilder()
        .de("{{NOME COMPLETO}}")
        .para("{{Full Name}}")
        .build();
        
const deParaTemplateCpf: DeParaTemplateBuilder = deParaTemplateBuilder()
        .de("{{NÚMERO DO CPF}}")
        .para("{{Social Security Number}}")
        .build();
        
const deParaTemplateEndereco: DeParaTemplateBuilder = deParaTemplateBuilder()
        .de("{{ENDEREÇO COMPLETO}}")
        .para("{{Full address}}")
        .build();
        
let deParaTemplates: DeParaTemplatesBuilder[] = [];

deParaTemplates.push(deParaTemplateName, deParaTemplateCpf, deParaTemplateEndereco);

const docFromTemplate: DocFomTemplateBuilder = new DocFromTemplateBuilder()
        .withSandbox(false)
        .withPrimaryColor("#000000")
        .withSignerName("My Signer for Template")
        .withTemplateId("SEU TEMPLATE ID")
        .withData(deParaTemplates)
        .build();

async function exempleCreateDocFromTemplateAsync() {
        try {
                docResponse: DocResponse = await new DocRequests(apiToken).createDocFromTemplateAsync(docFromTemplate);
                jsonDocResponse: string = new JsonConverter().docAsyncResponseToJson(docResponse);
                console.log(jsonDocResponse);
            } catch(Err) {
                console.log(Err);
            }
}
</code></pre>
