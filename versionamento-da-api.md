# Versionamento da API

Estamos constantemente aprimorando nossa API com novos recursos e melhorias. No entanto, garantimos que seu aplicativo não será afetado por essas mudanças. Se fizermos alterações significativas em um endpoint, lançaremos uma nova versão da API.

**Versão atual da API: V1**

Consideramos as seguintes alterações como **compatíveis com versões anteriores:**

* Adicionar novos endpoints na API;
* Adicionar novos parâmetros opcionais na requisição;
* Tornar um parâmetro obrigatório da requisição em opcional;
* Adicionar novas propriedades às respostas API existentes;
* Adicionar novos eventos a webhooks (isso significa que seu endpoint de webhook deve lidar com tipos de eventos desconhecidos, por exemplo ignorando-os com um retorno status 200).\
  \
  **Informaremos por email sempre que alguma alteração for feita.**
