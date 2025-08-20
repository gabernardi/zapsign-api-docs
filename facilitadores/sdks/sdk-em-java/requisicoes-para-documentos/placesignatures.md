---
description: Posicionar assinaturas
---

# placeSignatures

### Visão geral

Parâmetros:&#x20;

* String - token do documento
* [RubricaList](../classes-usadas/body/rubricalist.md)

Retorno:

* int- caso sucesso
* Exception - caso falha

Para posicionar as rubricas nesse documento precisamos:

* definir seu token api.
* token do documento.
* definir as rúbricas.
* chamar o método.

### Uso:

Importe os componentes relevantes:

```
import body.doc.Rubrica;
import body.doc.RubricaList;
import docs.DocRequests;

import java.util.ArrayList;
```

Salve seu [Api Token](../../../../):

```
String apiToken = "SEU TOKEN";
```

Salve o token do documento original:

```
String docToken = "TOKEN DOCUMENTO";
```

Defina suas rúbricas em uma classe [RubricaList ](../classes-usadas/body/rubricalist.md)que contenha arrays de classe [Rubrica](../classes-usadas/body/rubrica.md):

```
Rubrica rubrica1 = Rubrica.builder()
                .page(0)
                .relative_position_bottom(52.50)
                .relative_position_left(75.71)
                .relative_size_x(19.55)
                .relative_size_y(9.42)
                .type("signature")
                .signer_token("TOKEN SIGNER")
                .build();

Rubrica rubrica2 = Rubrica.builder()
        .page(0)
        .relative_position_bottom(13.50)
        .relative_position_left(20.71)
        .relative_size_x(19.55)
        .relative_size_y(9.42)
        .type("visto")
        .signer_token("TOKEN SIGNER")
        .build();

ArrayList<Rubrica> _rubricas = new ArrayList<>();
_rubricas.add(rubrica1);
_rubricas.add(rubrica2);

RubricaList rubricaList = RubricaList.builder()
                .rubricas(_rubricas)
                .build();
```

Chame o método placeSignatures e receba como resposta um inteiro contendo o status code da resposta ou uma mensagem de erro:

```
try {
    int statusCode = new DocRequests(apiToken).placeSignatures(docToken, rubricaList);
    System.out.println(statusCode);
}
catch(Exception exceptionError) {
    System.out.println(exceptionError.getMessage());
}
```

### Exemplo completo:

<pre><code>import body.doc.Rubrica;
import body.doc.RubricaList;
import docs.DocRequests;

import java.util.ArrayList;

public class PlaceSignatures {
    public static void main(String[] args) throws Exception {
<strong>        String apiToken = "SEU TOKEN";
</strong>
        String docToken = "TOKEN DOCUMENTO";

        Rubrica rubrica1 = Rubrica.builder()
                .page(0)
                .relative_position_bottom(52.50)
                .relative_position_left(75.71)
                .relative_size_x(19.55)
                .relative_size_y(9.42)
                .type("signature")
                .signer_token("TOKEN SIGNER")
                .build();

        Rubrica rubrica2 = Rubrica.builder()
                .page(0)
                .relative_position_bottom(13.50)
                .relative_position_left(20.71)
                .relative_size_x(19.55)
                .relative_size_y(9.42)
                .type("visto")
                .signer_token("TOKEN SIGNER")
                .build();

        ArrayList&#x3C;Rubrica> _rubricas = new ArrayList&#x3C;>();
        _rubricas.add(rubrica1);
        _rubricas.add(rubrica2);

        RubricaList rubricaList = RubricaList.builder()
                .rubricas(_rubricas)
                .build();

        try {
            int statusCode = new DocRequests(apiToken).placeSignatures(docToken, rubricaList);
            System.out.println(statusCode);
        }
        catch(Exception exceptionError) {
            System.out.println(exceptionError.getMessage());
        }
    }
}
</code></pre>
