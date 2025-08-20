---
description: Criar documento via Modelo Assíncrono
---

# createDocFromTemplateAsync

### Visão geral

Parâmetros:&#x20;

* [DocFromTemplate](../classes-usadas/body/docfromtemplate.md)

Retorno:

* [DocAsyncResponse ](../classes-usadas/response/docasyncresponse.md)- caso sucesso
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
import response.DocAsyncResponse;

import services.JsonConverter;
import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Adicione suas variáveis em uma lista de classe [DeParaTemplate](../classes-usadas/body/deparatemplate.md):

```
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

```

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

Chame o método createDocFromTemplateAsync e receba como resposta a classe [docAsyncResponse ](../classes-usadas/response/docasyncresponse.md)ou uma mensagem de erro:

```
try {
    DocAsyncResponse docAsyncResponse = new DocRequests(apiToken).createDocFromTemplateAsync(docFromTemplate);
    String jsonDocResponse = new JsonConverter().docAsyncResponseToJson(docAsyncResponse);
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
            DocAsyncResponse docAsyncResponse = new DocRequests(apiToken).createDocFromTemplateAsync(docFromTemplate);
            String jsonDocResponse = new JsonConverter().docAsyncResponseToJson(docAsyncResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
