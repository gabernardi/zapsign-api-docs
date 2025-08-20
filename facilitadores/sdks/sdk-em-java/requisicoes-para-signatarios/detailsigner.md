---
description: Detalhar signatário
---

# detailSigner

### Visão geral

Parâmetros:&#x20;

* String - token do signatário

Retorno:

* [Signer ](../classes-usadas/response/signer-response.md)- caso sucesso
* Exception - caso falha

Para obter esse signatário precisamos:

* definir seu token api.
* definir o token do signatário.
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

Chame o método detailSigner e receba como resposta a classe [Signer ](../classes-usadas/response/signer-response.md)ou uma mensagem de erro:

```
try {
    Signer signer = new SignerRequest(apiToken).detailSigner(signerToken);
    String jsonDocResponse = new JsonConverter().signerToJson(signer);
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

public class DetailSigner {
    public static void main(String[] args) throws Exception {
        String apiToken = "SEU TOKEN";
        String signerToken= "TOKEN DO SIGNATÁRIO";

        try {
            Signer signer = new SignerRequest(apiToken).detailSigner(signerToken);
            String jsonDocResponse = new JsonConverter().signerToJson(signer);
            System.out.println(jsonDocResponse);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}

```
