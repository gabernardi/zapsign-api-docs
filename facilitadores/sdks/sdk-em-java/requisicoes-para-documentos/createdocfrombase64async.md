---
description: Criar documento via pdf de um base64 Assincrono
---

# createDocFromBase64Async

### Visão geral

Parâmetros:&#x20;

* [DocFromPdfBase64](../classes-usadas/body/docfrompdfbase64.md)

Retorno:

* [DocAsyncResponse ](../classes-usadas/response/docasyncresponse.md)- caso sucesso
* Exception - caso falha

Para criar esse documento precisamos:

* definir seu token api.
* definir o base64 do pdf.
* definir os signatários.
* definir o documento.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.doc.DocFromPdfBase64;
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

Salve seu base64:

```
String base64 = "JVBERi0xLjYKJcOkw7zDtsOfCjIgMCBvYmoKPDwvTG..."
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

Defina seu documento com a classe [DocFromPdfBase64](../classes-usadas/body/docfrompdfbase64.md):

```
DocFromPdfBase64 docFromPdfBase64 = DocFromPdfBase64.docFromPdfBase64Builder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .base64_pdf(base64)
                .build();

```

Chame o método createDocFromPdfBase64 e receba como resposta a classe [docAsyncResponse  ](../classes-usadas/response/docasyncresponse.md)ou uma mensagem de erro:

```
try {
    DocAsyncResponse docAsyncResponse = new DocRequests(apiToken).createDocFromPdfBase64Async(docFromPdfBase64);
    String jsonDocResponse = new JsonConverter().docAsyncResponseToJson(docAsyncResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.doc.DocFromPdfBase64;
import body.signer.Signer;
import docs.DocRequests;
import response.DocResponse;
import services.JsonConverter;

import java.io.IOException;
import java.util.ArrayList;
public class CreateDocFromBase64PdfAssync {
    public static void main(String[] args) throws IOException, InterruptedException  {
        String apiToken = "SEU TOKEN";
        String base64 = "JVBERi0xLjYKJcOkw7zDtsOfCjIgMCBvYmoKPDwvTG..."

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

        DocFromPdfBase64 docFromPdfBase64 = DocFromPdfBase64.docFromPdfBase64Builder()
                .sandbox(false)
                .name("My Contract")
                .brand_primary_color("#000000")
                .lang("pt-br")
                .signers(signers)
                .base64_pdf(base64)
                .build();


        try {
            DocAsyncResponse docAsyncResponse = new DocRequests(apiToken).createDocFromPdfBase64Async(docFromPdfBase64);
            String jsonDocResponse = new JsonConverter().docAsyncResponseToJson(docAsyncResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
