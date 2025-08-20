# Grupo de signatários

A funcionalidade de **Grupo de Signatários** permite organizar os signatários de um documento em grupos específicos, definindo uma ordem estruturada de assinatura. Com essa funcionalidade, é possível estabelecer que todos os signatários do **Grupo A** assinem primeiro, e somente após a conclusão, os signatários do **Grupo B** poderão assinar, e assim por diante. Isso é especialmente útil em processos onde o fluxo de assinatura deve seguir uma hierarquia ou sequência definida.

#### Exemplo de uso

Imagine que você está gerenciando um processo de assinatura de contrato. Você quer garantir que Pedro e Maria assinem o documento antes que ele seja enviado para Carlos e Alice. Para isso, você pode criar dois grupos de signatários:

* **Grupo 1**: Pedro, Maria
* **Grupo 2**: Carlos, Alice

### **Como funciona**

A criação de grupos de signatários é feita diretamente no momento da criação do documento, utilizando o mesmo endpoint da API. Isso simplifica o processo, permitindo definir a ordem de assinatura entre grupos de forma mais eficiente, sem a necessidade de chamadas adicionais.

Para ver instruções completas e exemplos de como configurar os grupos no payload, consulte o subtópico: [➡️ Definir grupos de signatários](definir-grupos-de-signatarios.md)

{% hint style="warning" %}
**Edição de grupos:**\
Após a criação dos grupos e a definição dos signatários, **não será possível editar os signatários dentro de cada grupo**. Certifique-se de revisar cuidadosamente antes de finalizar a configuração.
{% endhint %}

### **Requisitos para usar a funcionalidade**

Para que essa funcionalidade funcione corretamente, é necessário ativar a configuração "Bloquear assinatura fora da ordem definida para signatários": Essa opção está disponível em [**Configurações > Organização > Preferências**](https://app.zapsign.com.br/conta/configuracoes?tab=preferences). Se essa configuração não estiver habilitada, os signatários poderão assinar sem seguir a ordem definida pelos grupos.

<img src="../../.gitbook/assets/image (1).png" alt="" data-size="original">

**Benefícios dessa funcionalidade**

* **Controle do fluxo de assinatura:** Garante que os documentos sejam assinados na ordem desejada.
* **Flexibilidade na alocação de signatários:** Os grupos podem conter um ou mais signatários conforme necessário.
* **Aprimoramento de processos hierárquicos:** Ideal para contratos ou documentos que exigem aprovação sequencial.

Com essa nova funcionalidade, o ZapSign facilita a gestão de documentos eletrônicos, oferecendo maior controle e estrutura nos fluxos de assinatura.

