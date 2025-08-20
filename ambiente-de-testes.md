---
description: >-
  Nesta seção, explicaremos como utilizar os endpoints da API corretamente e
  configurar o ambiente de sandbox para realizar testes sem validade jurídica.
---

# Ambiente de testes

A ZapSign oferece **dois ambientes globais para utilização da API.** Apenas o [ambiente de produção](https://app.zapsign.com.br/acesso/entrar) exige um plano API para ser utilizado.&#x20;

{% hint style="warning" %}
**Lembre-se:** Os **endpoints** fornecidos **são para integração** com a **API** e **não** são acessáveis diretamente pelo navegador da web. Para acessar a interface via navegador ou criar uma conta, visite: [https://sandbox.app.zapsign.com.br/acesso/entrar](https://sandbox.app.zapsign.com.br/acesso/entrar)&#x20;
{% endhint %}

<table><thead><tr><th width="132">Ambiente</th><th width="348">                       Endpoint</th><th>Validade Jurídica</th></tr></thead><tbody><tr><td>Sandbox</td><td>https://sandbox.api.zapsign.com.br/api/v1/</td><td>Não possui validade jurídica</td></tr><tr><td>Produção</td><td>https://api.zapsign.com.br/api/v1/</td><td>Possui validade jurídica</td></tr></tbody></table>

\
Por padrão, as contas são criadas na infraestrutura global, porém oferecemos **a opção de servidores no Brasil para empresas que necessitam dessa configuração.**

<table><thead><tr><th>Ambiente BR</th><th width="295.4000244140625">Endpoint BR</th><th>Validade Jurídica</th></tr></thead><tbody><tr><td>Produção br</td><td>https://br.api.zapsign.com.br/api/v1</td><td>Possui validade jurídica</td></tr></tbody></table>

{% hint style="warning" %}
Caso sua empresa precise de servidores no Brasil, essa opção está disponível apenas para planos com suporte a infraestrutura dedicada. [**Entre em contato para mais informações**](https://zapsign.com.br/fale-com-vendas?hsCtaTracking=82bfa395-a9c4-41b1-a59d-343d8e6ab197%7Ce3a28023-c1e4-4b3b-a03f-cb7f53a0511f)**.**
{% endhint %}

O **ambiente de sandbox** reproduz exatamente o ambiente de produção, porém sem validade jurídica. Para obter seu token, o caminho será o mesmo: [**Configurações > Integrações > API ZAPSIGN**](https://sandbox.app.zapsign.com.br/conta/configuracoes/integration?tab=api-zapsign). Depois, copie seu token e configure na sua ferramenta de testes.

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption><p>Tela onde é possível copiar seu api token.</p></figcaption></figure>



Com seu api token e o endpoint do ambiente sandbox, já é possível disparar seus documentos de testes!\


<figure><img src="https://github.com/AmandaAmani/documenta-ocurso/blob/main/sandbox%20api.gif?raw=true" alt="Usuáriofazendo requisição com endpoint de sandbox"><figcaption><p>Requisição feita com endpoint de sandbox</p></figcaption></figure>

{% hint style="info" %}
Não é necessário incluir o parâmetro `sandbox=true` nas suas requisições para utilizar o ambiente de testes (sandbox). Basta utilizar as URLs específicas para o ambiente sandbox ou utilizar os ambientes pré-definidos da seção ["Todas as requisições prontas".](todas-as-requisicoes-prontas.md)&#x20;
{% endhint %}



