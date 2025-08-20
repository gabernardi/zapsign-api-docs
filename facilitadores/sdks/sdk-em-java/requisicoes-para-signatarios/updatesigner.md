---
description: Atualizar signatário
---

# updateSigner

### Visão geral

Parâmetros:&#x20;

* String - token do signatário
* [Signer](../classes-usadas/body/signer.md)

Retorno:

* [Signer ](../classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para atualizar esse signatário precisamos:

* definir seu token api.
* definir o token do signatário.
* definir os novos valores do signatário.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.signer.Signer;
import signers.SignerRequest;

import services.JsonConverter;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Salve o token de seu signatário

```
String signerToken= "TOKEN DO SIGNATÁRIO";
```

Crie seu signatário com a classe [Signer](../classes-usadas/body/signer.md):

```
Signer signer = Signer.builder()
                .name("New Name")
                .email("newEmail@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();
```

Chame o método updateSigner e receba como resposta a classe [Signer ](../classes-usadas/response/signer-response.md)ou uma mensagem de erro:

```
try {
    Signer signerResponse = new SignerRequest(apiToken).updateSigner(signerToken, signer);
    String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
    System.out.println(jsonDocResponse);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

```
import body.signer.Signer;
import services.JsonConverter;
import signers.SignerRequest;

public class UpdateSigner {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String signerToken= "TOKEN DO SIGNATÁRIO";

        Signer signer = Signer.builder()
                .name("New Name")
                .email("newEmail@test.com")
                .lock_email(true)
                .lock_phone(true)
                .phone_country("55")
                .phone_number("99999999999")
                .auth_mode("assinaturaTela")
                .send_automatic_email(false)
                .send_automatic_whatsapp(false)
                .build();

        try {
            Signer signerResponse = new SignerRequest(apiToken).updateSigner(signerToken, signer);
            String jsonDocResponse = new JsonConverter().signerToJson(signerResponse);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
```
