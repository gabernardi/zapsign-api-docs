---
description: Criar documento via Modelo
---

# createDocFromTemplate

### Visão geral

Parâmetros:&#x20;

* [DocFromTemplate](../classes-usadas/body/docfromtemplate.md)

Retorno:

* [DocResponse ](../classes-usadas/response/docresponse.md)- caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api.
* definir os signatários.
* definir o documento.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.doc.DeParaTemplate;
import body.doc.DocFromTemplate;
import docs.DocRequests;
import response.DocResponse;

import services.JsonConverter;
import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Adicione suas variáveis em uma lista de classe [DeParaTemplate](../classes-usadas/body/deparatemplate.md):

<pre><code><strong>DeParaTemplate deParaTemplateName = DeParaTemplate.deParaTemplateBuilder()
</strong>        .de("{{NOME COMPLETO}}")
        .para("Full Name")
        .build();

DeParaTemplate deParaTemplateCpf= DeParaTemplate.deParaTemplateBuilder()
        .de("{{NÚMERO DO CPF}}")
        .para("Social Security Number")
        .build();

DeParaTemplate deParaTemplateEnd = DeParaTemplate.deParaTemplateBuilder()
        .de("{{ENDEREÇO COMPLETO}}")
        .para("Full address")
        .build();

ArrayList&#x3C;DeParaTemplate> deParaTemplates = new ArrayList&#x3C;>();
deParaTemplates.add(deParaTemplateName);
deParaTemplates.add(deParaTemplateCpf);
deParaTemplates.add(deParaTemplateEnd);

</code></pre>

Defina seu documento com a classe [DocFromTemplate](../classes-usadas/body/docfromtemplate.md):

```
DocFromTemplate docFromTemplate = DocFromTemplate.docFromTemplateBuilder()
                .sandbox(false)
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signer_name("My Signer for template")
                .template_id("75a3a92b-36d5-451f-95cd-5af9a927a392")
                .data(deParaTemplates)
                .build();

```

Chame o método createDocFromTemplate e receba como resposta a classe [DocResponse ](../classes-usadas/response/docresponse.md)ou uma mensagem de erro:

```
try {
    DocResponse docResponse = new DocRequests(apiToken).createDocFromTemplate(docFromTemplate);
    String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.doc.DeParaTemplate;
import body.doc.DocFromTemplate;
import docs.DocRequests;
import response.DocResponse;
import services.JsonConverter;

import java.util.ArrayList;

public class CreateDocFromTemplate {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";

        DeParaTemplate deParaTemplateName = DeParaTemplate.deParaTemplateBuilder()
                .de("{{NOME COMPLETO}}")
                .para("Full Name")
                .build();

        DeParaTemplate deParaTemplateCpf= DeParaTemplate.deParaTemplateBuilder()
                .de("{{NÚMERO DO CPF}}")
                .para("Social Security Number")
                .build();

        DeParaTemplate deParaTemplateEnd = DeParaTemplate.deParaTemplateBuilder()
                .de("{{ENDEREÇO COMPLETO}}")
                .para("Full address")
                .build();

        ArrayList<DeParaTemplate> deParaTemplates = new ArrayList<>();
        deParaTemplates.add(deParaTemplateName);
        deParaTemplates.add(deParaTemplateCpf);
        deParaTemplates.add(deParaTemplateEnd);

        DocFromTemplate docFromTemplate = DocFromTemplate.docFromTemplateBuilder()
                .sandbox(false)
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signer_name("My Signer for template")
                .template_id("75a3a92b-36d5-451f-95cd-5af9a927a392")
                .data(deParaTemplates)
                .build();

        try {
            DocResponse docResponse = new DocRequests(apiToken).createDocFromTemplate(docFromTemplate);
            String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}

```
