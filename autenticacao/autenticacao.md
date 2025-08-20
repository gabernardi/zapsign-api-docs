---
description: >-
  O token estático é um token fixo e predefinido, utilizado para autenticação
  contínua na API. Ele é simples de implementar e ideal para cenários onde a
  segurança não exige tokens temporários.
---

# Token estático (Api Token)

Para utilizá-lo basta inserir seu api\_token no header **"Authorization"** da requisição, com o prefixo **"Bearer "**. Por exemplo:

```javascript
  'headers': {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer c7f35c84-7893-4087-b4fb-d1f06c23'
  },
```

{% hint style="info" %}
Para saber mais, consulte o capítulo "[Como começar"](../como-comecar.md#e-como-obter-meu-api-token).
{% endhint %}

<figure><img src="https://github.com/AmandaAmani/documenta-ocurso/blob/main/integra%C3%A7%C3%A3o%20sem%20url.gif?raw=true" alt="usuário copiando seu api token e inserindo no postman para fazer uma requisição."><figcaption><p>Copie seu token estático e autentique sua ferramenta.</p></figcaption></figure>
