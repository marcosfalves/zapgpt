# zapgpt
Aplicação em GO para executar serverless (AWS lambda) integrando whatsapp com chatgpt.

Criado durante o evento Full Cycle Learning Experience

Link da live: https://www.youtube.com/watch?v=87iV8v2CRvU

## Pré requisitos
- [Conta na AWS](https://aws.amazon.com/)
- [Conta na OpenAI](https://openai.com/)
- [Conta na Twilio](https://www.twilio.com/)
- [NodeJS](https://github.com/nodesource/distributions)

---
### Passos para o deploy na AWS
- Instalar o serverless
    ```sh
    npm install -g serverless
    ```
- Configurar as credenciais da AWS
    - Criar uma policy com as credenciais [desse arquivo](https://gist.github.com/marcosfalves/72691df15b23b560d9d1771526219da6).
    - Criar um usuário na AWS e atribuir a policy criada.
    - Criar Access keys para esse usuário.
    - [Configurar Access Key da AWS para o serverless utilizar.](https://www.serverless.com/framework/docs/providers/aws/guide/credentials/)
- Criar arquivo .env
    - Duplicar `.env.example` e renomear para `.env`
    - Obter o token da OpenAI e definir na variável `OPENAI_API_KEY` 
- Executar o build
    ```sh
    make build
    ```
- Executar o deploy
    ```sh
    serverless deploy
    ```
- Após o deploy ser finalizado com sucesso será gerado uma URL da função no seu console.

---
### Configurar webhook na Twilio

- Acessar a conta da Twilio e procurar pelo serviço `Send WhatsApp message`.
- Seguir as instruções para a criação de um ambiente Sandbox.
- Na aba `Sandbox Configuration` colar a URL da função da AWS e definir o método POST.