---
description: >-
  Postman e Insomnia são ferramentas que facilitam o desenvolvimento, testes e
  documentação de APIs. Nós da ZapSign deixamos todas as bibliotecas de
  requisições prontas para ambas as ferramentas.
---

# Todas as requisições prontas!

Utilizando o Postman

Você pode economizar muito tempo utilizando as requisições já prontas do Postman.

{% embed url="https://elements.getpostman.com/redirect?entityId=27495556-787b914f-ebeb-426a-9808-7fb0bd0d47fd&entityType=collection" %}
Link para o workspace contendo todas as requisições publicas
{% endembed %}

Abra o link, selecione o ambiente que deseja testar (no canto superior direito) e crie um fork para acessar todos os endpoints no seu próprio WorkSpace.

![Ambientes pré existentes](<.gitbook/assets/image (39).png>)

Após selecionar o ambiente, basta configurar suas variaveis clicando no item "Environments" no menu esquerdo:

<figure><img src=".gitbook/assets/image (42).png" alt=""><figcaption><p>Variaveis de ambiente disponiveis</p></figcaption></figure>

Com o Postman configurado, você já pode utilizar todos os endpoints. A única variável obrigatória é a [api\_token](https://app.zapsign.com.br/conta/configuracoes/integration?tab=api-zapsign), seu token de autenticação. Todas as outras podem ser preenchidas conforme sua necessidade.

{% hint style="info" %}
**Dica:** no menu lateral direito, o simbolo de código \</> permite que você exporte todas as requisições na sua linguagem de preferência.\
![](<.gitbook/assets/image (17).png>)
{% endhint %}

### Utilizando o Insomnia

Para o [Insomnia](https://insomnia.rest/), deixamos todos os endpoints preparados neste arquivo. Após importar o arquivo, você precisará escolher o ambiente e inserir seu Api Token antes de fazer um disparo da request.

{% file src=".gitbook/assets/Insomnia_2023-03-27 (1).json" %}
Insomnia ZapSign API.json
{% endfile %}

<figure><img src="https://github.com/AmandaAmani/documenta-ocurso/blob/main/%20cortado%20insonia.gif?raw=true" alt="Usuário importando arquivo para Insomnia"><figcaption><p>Importação de arquivo com todas as requisições para o Insomnia.</p></figcaption></figure>

{% hint style="info" %}
**Dica:** dentro do Insomnia, aperte **Shift+Ctrl+G** ao visualizar uma requisição e o **código será gerado automaticamente** em qualquer linguagem de programação que você queira.
{% endhint %}
