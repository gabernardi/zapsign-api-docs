---
description: >-
  Tokens são fundamentais para utilizar todas as nossas funcionalidades de
  maneira eficiente e segura. Confira os principais tokens utilizados e como
  encontrá-los na plataforma
---

# Tipos de Tokens e Como Localizá-los

**API Token**

* **Descrição:** O API Token é o principal token da conta, usado para autenticação ao integrar com a API. Se você preferir um método de autenticação baseado em JWT, confira o tópico "[Autenticação](autenticacao/#tipos-de-autenticacao-suportados)"
* **Localização:** Vá para [**Configurações** > **Integrações** > **API Zapsign** > **Token de Acesso**.](https://app.zapsign.com.br/conta/configuracoes/integration?tab=api-zapsign)

**User Token**

* **Descrição:** O User Token é um token exclusivo para [assinaturas em lote](signatarios/assinar-em-lote-via-api.md) via API.
* **Localização:** Navegue para [**Configurações** > **Meu Perfil** > **Segurança** > **Assinatura via API**.](https://app.zapsign.com.br/conta/perfil?tab=security)

**Token de Modelo**&#x20;

* **Descrição:** O Template ID identifica um modelo específico criado na plataforma e servirá para vinculá-lo à sua requisição.
* **Localização:** Em **Modelos**, selecione o modelo desejado e clique em **Gerenciar**. Copie o código da URL após "modelos/".
* **Exemplo:** https://app.zapsign.com.br/conta/modelos/<mark style="color:green;">31bfa32c-9427-40ac-9804-187e6f4e73</mark>

**Signer Token**

* **Descrição:** O Signer Token é associado a um signatário específico. Cada signatário tem um link exclusivo para autenticação e identificação. Você pode utilizar para assinar em lote, detalhar signatários, etc.
* **Localização:** Encontre o conjunto de números após "/verificar" na URL.
* **Exemplo**: https://app.zapsign.com.br/verificar/<mark style="color:green;">92b36ec9-a449-4574-8ff0-5cc2c5ab7</mark>

**Doc Token**

* **Descrição:** O Doc Token é único para cada documento criado na plataforma e é usado para identificação e operações específicas, como adicionar documentos e usuários extras, detalhar documentos e posicionar assinaturas.&#x20;
* **Localização:** Em **Documentos Criados**, selecione o documento desejado e clique sobre ele. Copie o código da URL após "documentos/".
* **Exemplo:** https://app.zapsign.com.br/conta/documentos/<mark style="color:green;">1a764cab-b702-4a85-b16d-612688</mark>



{% hint style="info" %}
Ao fazer o disparo de uma requisição, tanto o Doc token quanto o Signer token serão criados automaticamente e podem ser verificados na resposta recebida.
{% endhint %}

