---
description: Uma visão geral do desenvolvimento de aplicativos com os SDKs Java da Zapsign.
---

# SDK em Java

O repositório desse SDK pode ser encontrado [aqui](https://github.com/ZapSign/zapsign-sdkJava). Nele é possível ver todo código necessário usado.

Em seu projeto Maven - Java, adicione a [dependência da ZapSign](https://mvnrepository.com/artifact/br.com.zapsign/zapsign_sdk) em seu arquivo .pom:

<pre><code>&#x3C;!-- https://mvnrepository.com/artifact/br.com.zapsign/zapsign_sdk -->
&#x3C;dependency>
    &#x3C;groupId>br.com.zapsign&#x3C;/groupId>
    &#x3C;artifactId>zapsign_sdk&#x3C;/artifactId>
<strong>    &#x3C;version>1.0-3&#x3C;/version>
</strong>&#x3C;/dependency>
</code></pre>

Agora apenas atualize suas dependências e realize suas requisições.

### Requisições

As requisições feitas pelo SDK são separadas em duas partes:

* [Requisições para documentos](requisicoes-para-documentos/)
* [Requisições para signatários](requisicoes-para-signatarios/)

