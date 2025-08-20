# Opcional: Posicionar assinaturas

## Posicionamento com âncoras na criação do documento

Ao criar documentos pela API da ZapSign, é possível posicionar automaticamente as assinaturas e rubricas no conteúdo do arquivo PDF ou DOCX utilizando **âncoras de texto**.\
\
Criar documento via Upload: [https://docs.zapsign.com.br/documentos/criar-documento](https://docs.zapsign.com.br/documentos/criar-documento)

## Posicionamento com coordenadas no endpoint posicionar assinaturas

É possível definir a posição exata de cada assinatura ou rubrica utilizando coordenadas manuais.

<mark style="color:green;">`POST`</mark> `https://api.zapsign.com.br/api/v1/docs/{{doc_token}}/place-signatures/`

#### Headers

| Name                                            | Type   | Description                                                                                     |
| ----------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | <p>Api token a frente do texto "Bearer". </p><p>Ex: Bearer c7f35c84-7893-4087-b4fb-d1f06c23</p> |

#### Request Body

| Name                                  | Type    | Description                                                                                         |
| ------------------------------------- | ------- | --------------------------------------------------------------------------------------------------- |
| rubricas\[type]                       | string  | Há dois tipos de rubricas possíveis, a "signature" (assinatura) ou o "visto". Default: "signature". |
| rubricas\[page]                       | integer | Página em que a assinatura será posicionada. Começa em 0.                                           |
| rubricas\[relative\_size\_x]          | number  | (Explicado abaixo)                                                                                  |
| rubricas\[relative\_size\_y]          | number  | (Explicado abaixo)                                                                                  |
| rubricas\[relative\_position\_bottom] | number  | (Explicado abaixo)                                                                                  |
| rubricas\[relative\_position\_left]   | number  | (Explicado abaixo)                                                                                  |
| rubricas\[signer\_token]              | string  | Token do signatário da assinatura que será posicionada                                              |

{% tabs %}
{% tab title="200 Posicionamento concluído com sucesso." %}

{% endtab %}
{% endtabs %}

### Exemplo de requisição:

{% embed url="https://www.postman.com/zapsign/workspace/zapsign-workspace/request/27495556-c5d8b072-37cf-4e5d-a4b7-3b905f1e1140?ctx=documentation" %}

### Antes de começar, veja como a funcionalidade funciona na plataforma web:

Se ainda não conhece, veja abaixo:

![Após subir um novo documento, clique em "Opcional: Posicionar assinaturas"](<../.gitbook/assets/image (69).png>)

![A assinatura do signatário será posicionada nesses campos.](<../.gitbook/assets/image (58).png>)

### Como funciona o posicionamento via API?

E como a ZapSign calcula onde essas assinaturas devem ser posicionadas? De acordo com os cálculos abaixo:

![Temos o eixo x e eixo y começando no canto inferior esquerdo de cada página.](<../.gitbook/assets/image (62).png>)

O posicionamento acima representado, da assinatura de "Fulano Silveira" na metade direita do documento, corresponderia ao JSON:

```javascript
    {
        "page": 0, //primeira página do documento
        "relative_position_bottom": 42.50, //distância de 0 a 100 da extremidade inferior da página
        "relative_position_left": 65.71, //distância de 0 a 100 da extremidade esquerda da página
        "relative_size_x": 19.55, //tamanho de 0 a 100 da assinatura em comparação à largura da página 
        "relative_size_y": 9.42, //tamanho de 0 a 100 da assinatura em comparação à altura da página
        "signer_token": "cf1c0b7a-03d3-468b-97ce-3061e3abcdefg" //token do signatário "Fulano Silveira"
    }
```

Abaixo segue uma explicação detalhada de cada um dos campos.

### **relative\_position\_left e relative\_position\_bottom:&#x20;**_**Posicionando a assinatura no documento**_

É necessário tomar alguns cuidados, para que as assinaturas não fiquem fora do documento. Por exemplo, se o **relative\_position\_left** for de 80, o **relative\_size\_x** não deve ser maior do que 20 (totalizando 100 que é o eixo X). Se essa soma for maior do que 100, a assinatura ficaria em parte para fora do documento.&#x20;

Matematicamente falando, seu objeto deve respeitar os seguintes limites:\
0 <= relative\_size\_y <= 100\
0 <= relative\_size\_x <= 100\
0 <= relative\_position\_bottom <= 100\
0 <= relative\_position\_left <= 100\
\
E também:\
0 <= (relative\_size\_y + relative\_position\_bottom) <= 100\
0 <= (relative\_size\_x + relative\_position\_left) <= 100

### **relative\_size\_x e relative\_size\_y:&#x20;**_**Mantendo a proporção da assinatura**_

* **Caso seu PDF seja uma folha A4 vertical (mais comum)**, recomenda-se utilizar sempre os valores **relative\_size\_x: 19.55** e **relative\_size\_y: 9.42**, como no exemplo acima. Se você quiser aumentar o tamanho da assinatura, multiplique-os pelo mesmo número, para que a razão seja mantida.
  * Obs.: caso se trate de uma rubrica com type "**visto**", recomenda-se **relative\_size\_x: 13.76** e **relative\_size\_y: 9.42**\

* **Caso o PDF seja uma folha A4 horizontal**, recomendam-se os valores de **relative\_size\_x: 15.05** e **relative\_size\_y: 12.13.**
  * Obs.: caso se trate de uma rubrica com type "**visto**", recomenda-se **relative\_size\_x: 10.58** e **relative\_size\_y: 12.13**

### page: _Como **definir** a página em que a assinatura será posicionada_

O parâmetro page equivale a cada página do documento, começando no 0. Se você quiser posicionar a assinatura no mesmo local em todas as páginas, é necessário passar o objeto mais de uma vez. Por exemplo:

```javascript
{
	"rubricas":[
    {
        "page": 0, //primeira página do documento
        "relative_position_bottom": 42.50, 
        "relative_position_left": 65.71, 
        "relative_size_x": 19.55, 
        "relative_size_y": 9.42, 
        "signer_token": "cf1c0b7a-03d3-468b-97ce-3061e3abcdefg"
    },
    {
        "page": 1, //segunda página do documento
        "relative_position_bottom": 42.50, 
        "relative_position_left": 65.71, 
        "relative_size_x": 19.55, 
        "relative_size_y": 9.42, 
        "signer_token": "cf1c0b7a-03d3-468b-97ce-3061e3abcdefg"
    }
  ]
}
```

### Perguntas frequentes

* **Como eu sei se o posicionamento das assinaturas deu certo?** R.: Você só saberá depois que o documento for assinado, conferindo diretamente o PDF. As validações devem ser feitas do seu lado.
* **Caso o posicionamento tenha sido feito errado, tem como eu mudar?** R.: Para sobrescrever o posicionamento das assinaturas anterior, basta fazer um novo POST para essa rota, que todos posicionamentos anteriores serão deletados e substituídos pelos novos.&#x20;
* **Como eu posso cancelar o posicionamento de assinaturas?** R.: Basta fazer um post com o objeto rubricas sendo um array vazio. Ex: {"rubricas":\[ ]}
* **O documento assinado é atualizado sempre que eu mudar o posicionamento das assinaturas?** R.: **Não!!!** O novo posicionamento só será aplicado depois que um novo signatário assinar o documento. Isto é, o documento não será atualizado toda vez que você alterar o posicionamento de assinaturas, mas apenas quando algum signatário assinar.
