## ⚽🤖 Chatbot de Inteligência Artificial no Futebol (Azure AI Foundry) ⚽🧠

### Visão Geral do Projeto

Este projeto consiste no desenvolvimento de um chatbot interativo capaz de responder perguntas com base no conteúdo de **quatro artigos científicos em formato PDF** sobre a aplicação de Inteligência Artificial (IA) no futebol. Desenvolvido utilizando o **Azure AI Foundry**, o chatbot emprega o **Azure AI Search** para indexação e busca vetorial, impulsionado pelos modelos de ponta **GPT-4o** para geração de respostas e **`text-embedding-3-large`** (disponível através da Azure OpenAI Service) para a criação de representações semânticas. O sistema é capaz de compreender, processar e fornecer respostas contextuais fundamentadas nesses documentos específicos, aproveitando a infraestrutura e os serviços robustos do Azure.

### Cenário

Imagine que você é um analista de desempenho em um clube de futebol ou um pesquisador acadêmico estudando as últimas tendências da IA no esporte. Você possui **quatro artigos científicos cruciais em PDF** que detalham as aplicações mais recentes de IA para análise de jogadores, táticas de jogo, previsão de resultados e detecção de talentos. No entanto, encontrar informações específicas e conectar ideias entre esses documentos essenciais se torna um desafio.

Diante dessa necessidade, este projeto, construído no **Azure AI Foundry**, visa criar um sistema de busca inteligente que interpreta esses quatro PDFs sobre IA no futebol, organiza as informações utilizando o **Azure AI Search** e gera respostas relevantes para suas perguntas com o poder do **GPT-4o**, facilitando sua pesquisa e análise focada em um ambiente de desenvolvimento otimizado para IA.

### Objetivos

* ✅ **Carregar 4 arquivos PDF sobre IA no Futebol:** Permitir o upload e processamento dos quatro artigos científicos fornecidos dentro do ambiente Azure.
* ✅ **Implementar um sistema de busca vetorial com Azure AI Search e text-embedding-3:** Processar o conteúdo dos quatro PDFs carregados, gerar embeddings semânticos de alta qualidade utilizando o modelo **`text-embedding-3-large`** (acessível via Azure OpenAI Service) e indexá-los de forma eficiente no **Azure AI Search** para permitir a recuperação de informações relevantes através de similaridade vetorial.
* ✅ **Utilizar Inteligência Artificial (GPT-4o) para gerar respostas:** Empregar o modelo de linguagem avançado **GPT-4o** da Azure OpenAI Service para gerar respostas contextuais e informativas com base nos trechos dos quatro artigos mais relevantes encontrados pelo **Azure AI Search**.
* ✅ **Desenvolver um chat interativo:** Criar uma interface de interação (possivelmente hospedada como um Azure Web App ou Azure Function com uma interface web) onde seja possível realizar perguntas sobre IA no futebol e obter respostas fundamentadas no conteúdo dos quatro PDFs carregados, com toda a lógica orquestrada no **Azure AI Foundry**.

### Tecnologias Utilizadas

* **Plataforma de Desenvolvimento:** **Azure AI Foundry**
* **Serviço de Busca Vetorial:** **Azure AI Search**
* **Geração de Embeddings:** **`text-embedding-3-large`** (via **Azure OpenAI Service**)
* **Modelo de Linguagem (LLM):** **`gpt-4o`** (via **Azure OpenAI Service**)
* **Armazenamento de Documentos (Opcional):** **Azure Blob Storage** (para armazenar os PDFs)
* **Serviço de Computação:** **Azure Functions** ou **Azure App Service** (para hospedar a lógica do chatbot e a interface, se aplicável)
* **Interface de Chat (Opcional):** **Azure Web Apps** ou interfaces construídas com frameworks como `streamlit` ou `gradio` hospedadas no Azure.

### Arquitetura do Projeto no Azure AI Foundry

1.  **Ingestão de Documentos:**
    * Utilizar os recursos do Azure AI Foundry para ingerir os quatro arquivos PDF (possivelmente armazenados no Azure Blob Storage).
2.  **Extração de Texto:**
    * Implementar um processo (podendo usar Azure Functions ou recursos do AI Foundry) para extrair o texto bruto de cada um dos quatro documentos. O Azure AI Document Intelligence (antigo Form Recognizer) poderia ser utilizado para uma extração mais robusta.
3.  **Divisão do Texto (Chunking):**
    * Dividir o texto extraído de cada artigo em partes menores (chunks) para otimizar a geração de embeddings e a busca vetorial dentro do Azure AI Search.
4.  **Geração de Embeddings com text-embedding-3:**
    * Utilizar a Azure OpenAI Service dentro do Azure AI Foundry para gerar embeddings para cada chunk de texto, empregando o modelo **`text-embedding-3-large`**.
5.  **Indexação no Azure AI Search:**
    * Criar um índice no **Azure AI Search** e carregar os embeddings juntamente com os respectivos chunks de texto e informações de origem (nome do arquivo, número da página).
6.  **Chat Interativo:**
    * Desenvolver uma interface (hospedada no Azure) que permita ao usuário inserir perguntas sobre o conteúdo dos quatro artigos de IA no futebol.
    * Ao receber uma pergunta:
        * Gerar o embedding da pergunta utilizando o modelo **`text-embedding-3-large`** através da Azure OpenAI Service.
        * Realizar uma busca de similaridade vetorial no índice do **Azure AI Search** para encontrar os chunks de texto mais relevantes dos quatro artigos.
        * Enviar a pergunta e os chunks relevantes para o modelo de linguagem **`gpt-4o`** da Azure OpenAI Service com um prompt adequado para gerar uma resposta informativa e contextualizada, baseada no conteúdo dos quatro PDFs indexados no Azure AI Search.
        * Exibir a resposta gerada ao usuário.

### Como Executar o Projeto (Ambiente Azure)

1.  **Configurar o Azure AI Foundry:**
    * Certifique-se de ter acesso e configurado o ambiente Azure AI Foundry.
2.  **Provisionar os Serviços Azure:**
    * Crie instâncias do Azure AI Search e Azure OpenAI Service dentro do seu ambiente Azure.
3.  **Implementar a Lógica do Chatbot:**
    * Desenvolva o código (em Python ou outra linguagem suportada pelo Azure Functions/App Service) para orquestrar o fluxo de trabalho: carregamento, extração, embedding, indexação, busca e geração de respostas, utilizando as SDKs da Azure.
4.  **Implantar no Azure:**
    * Faça o deploy da sua lógica de chatbot para o Azure Functions ou Azure App Service. Se estiver usando uma interface web, implante-a no Azure Web Apps.
5.  **Carregar os 4 PDFs:**
    * Utilize a interface do seu chatbot (ou carregue diretamente no Azure Blob Storage, se configurado) para fornecer os quatro arquivos PDF sobre IA no futebol.
6.  **Começar a Conversar:**
    * Interaja com a interface do chatbot, fazendo perguntas sobre o conteúdo dos quatro artigos. As respostas serão geradas pelo **GPT-4o** com base nas informações recuperadas pelo **Azure AI Search** utilizando embeddings do **`text-embedding-3-large`**.

### Possíveis Melhorias e Extensões

* **Melhoria na divisão de texto (chunking) para Azure AI Search:** Explorar as funcionalidades de chunking e segmentação oferecidas pelo Azure AI Search.
* **Otimização da busca vetorial no Azure AI Search:** Ajustar os parâmetros de busca e explorar recursos como filtros e facetas do Azure AI Search.
* **Adição de funcionalidade de citação:** Integrar metadados dos documentos indexados no Azure AI Search para citar as fontes nas respostas.
* **Interface de usuário mais avançada:** Desenvolver uma interface web mais rica e intuitiva utilizando os serviços de front-end do Azure ou frameworks hospedados no Azure.
* **Implementação de um sistema de feedback:** Integrar um mecanismo de feedback para avaliar as respostas do chatbot e melhorar o sistema.
* **Utilização de outros serviços do Azure AI Foundry:** Explorar outras ferramentas e serviços oferecidos pela plataforma para otimizar o fluxo de trabalho de IA.

### Contribuição

Contribuições para este projeto são bem-vindas! Se você tiver ideias de melhorias, correções de bugs ou novas funcionalidades dentro do ambiente Azure, sinta-se à vontade para abrir uma issue ou enviar um pull request.

### Prints do passo a passo

![1](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/1-irparaAzureAIFoundry.png)

![2](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/2-criandoprojetonoAIFoundry.png)

![3](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/3-projcriadonoAIFoundry.png)

![4](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/4-implantandomodelo.png)

![5](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/5-implantargpt4o.png)

![6](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/6-implantarEmbeddingLarge.png)

![7](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/7-abrirchatplayground.png)

![8](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/8-pensonalizarmsgdosistema.png)

![9](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/9-addfontededados.png)

![10](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/10-carregarpastacompdfs.png)

![11](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/11-arquivoscarregados.png)

![12](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/12-criandorecursodepesquisa.png)

![13](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/13-criandorecursopesquisabasico.png)

![14](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/14-conectaraoservpesquisa.png)

![15](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/15-addconexaosearch.png)

![16](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/16-criarindicedevetor.png)

![17](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/17-ingestaodedocs.png)

![18](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/18-testeretornandorefPDF.png)

![[19 - Por fim, apagar recursos!!]](https://github.com/IvoJucaBezerra/chatbotBaseadoPdf-AzureAIFoundry/blob/main/images/19-apagarrecursosnofim.png)
