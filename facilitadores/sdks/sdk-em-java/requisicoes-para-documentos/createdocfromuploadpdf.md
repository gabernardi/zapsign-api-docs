---
description: Criar documento via Upload pdf
---

# createDocFromUploadPdf

### Visão geral

Parâmetros:&#x20;

* [DocFromPdf](../classes-usadas/body/docfrompdf.md)

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
import body.doc.DocFromPdf;
import body.signer.Signer;
import docs.DocRequests;
import response.DocResponse;

import services.JsonConverter;
import java.io.IOException;
import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Crie seus signatários com a classe [Signer](../classes-usadas/body/signer.md):

```
Signer signer1 = Signer.builder()
                .name("My First Signer")
                .build();

Signer signer2 = Signer.builder()
                .name("My Second Signer")
                .email("test@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();
                
ArrayList<Signer> signers = new ArrayList<>();
        signers.add(signer1);
        signers.add(signer2);
```

Defina seu documento com a classe [DocFromPdf](../classes-usadas/body/docfrompdf.md):

```
DocFromPdf docFromPdf = DocFromPdf.docFromPdfBuilder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .url_pdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                .build();

```

Chame o método createDocFromUploadPdf e receba como resposta a classe [DocResponse ](../classes-usadas/response/docresponse.md)ou uma mensagem de erro:

```
try {
    DocResponse docResponse = new DocRequests(apiToken).createDocFromUploadPdf(docFromPdf);
    String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.doc.DocFromPdf;
import body.signer.Signer;
import docs.DocRequests;
import response.DocResponse;
import services.JsonConverter;

import java.io.IOException;
import java.util.ArrayList;
public class CreateDocFromUploadPdf {
    public static void main(String[] args) throws IOException, InterruptedException  {
        String apiToken = "SEU TOKEN";

        Signer signer1 = Signer.builder()
                .name("My First Signer")
                .build();

        Signer signer2 = Signer.builder()
                .name("My Second Signer")
                .email("test@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();

        ArrayList<Signer> signers = new ArrayList<>();
        signers.add(signer1);
        signers.add(signer2);

        DocFromPdf docFromPdf = DocFromPdf.docFromPdfBuilder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .url_pdf("https://zapsign.s3.amazonaws.com/2022/1/pdf/63d19807-cbfa-4b51-8571-215ad0f4eb98/ca42e7be-c932-482c-b70b-92ad7aea04be.pdf")
                .build();

        try {
            DocResponse docResponse = new DocRequests(apiToken).createDocFromUploadPdf(docFromPdf);
            String jsonDocResponse = new JsonConverter().docResponseToJson(docResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
