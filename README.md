# Bootcamp Dio - Microsoft Azure AI Fundamentals - Azure Cognitive Search
Projeto tem como objetivo demonstrar com um passo, como aplicar as técnicas de organização de documentos e conduzimento de pesquisas eficientes através da ingestão de dados, seguindo três passos essenciais: 
 * Ingestão de conhecimento de IA.
 * Criação do índice correspondente.
 * Explorar essas funcionalidades.
  <p>Trata-se de um projeto simples, que tem como objetivo demostrar de modo prático o aproveitamento do conteúdo ministradados nas aulas.Inclusivél foi realizado de acordo com a documentação disponibilizada no portal de documentos de treianmento da Microrosft em:</p>

 [<center> Microsoft Learn</center>](https://aka.ms/ai900-ai-search)

 <p> Ao final, foi possível ter uma visão prática das potencialidades oferecidas por essas ferramentas na mineração de conhecimento.
   Para conseguir alcançar o resultado esperado será feito a combinação dos três serviços a seguir:</>

### Objetivo do emprego dos Serviços do Azure
  <p>Compor uma solução para uma dada rede de cafeteria fictícia que deseja obter de forma centralizada informações referentes a satisfação do cliente em relação aos serviços prestados e a infraestrutura das cafeterias da rede.</p>

## Azure AI Services - Azure AI Search
![alt text](images/AISearch.png)

Clicando no botão Create search service, daremos inicio as principais configurações(Pelo menos no diz respeito a este projeto.)
![alt text](images/image-3.png)

Obs: Não foi selecionada a location Brasil por questão de precificação do serviço que tende a ser mais custosa em termos monetários.
   Para este projeto não se aplica as configurações das outras guias(Scale,Networking e Tags), apesar das mesmas serem de extrema importância em um Projeto Real.
   Neste caso então basta clicar em Create + Review.

![alt text](images/image-5.png)

em seguida é apresentada a tela de review momento para aplicar alguma alteração caso seja necessária clicando em Previous

![alt text](images/image-6.png)

Neste caso como tudo esta configurado de acordo basta clicar em Create e aguardar o fim do Deployment(Provionamento do serviço "Serverless").
![alt text](images/image-8.png)

## Azure AI Service

Em Home -> Create a resource,selecionaremos a categoria Ai + machine learning em seguida a direita em  Azure AI services clicar em create.

![alt text](images/image-11.png)

Como dito anteriormente iremos configurar de acordo com o propósito deste projeto, em um Projeto Real volto a repetir, as demais configurações merecem atenção.Para o projeto atual basta clicar em Review + create.

![alt text](images/image-12.png)

![alt text](images/image-13.png)

Na tela seguinte como em qualquer outro serviço é a oportunidade de revisar e se for o caso realizar alguma alteração clicando em Previous.Se está tudo certo clique em Create.

![alt text](images/image-14.png)

Aguarde o Deployment e o serviço estára provisionado.

![alt text](images/image-15.png)


## Storage Accounts

Iremos criar uma conta de armazenamento do zero.

![alt text](images/image-16.png)

Iniciamos a criação clicando em Create Storage Account.

![alt text](images/image-17.png)

Como em todos os recursos temos algumas configurações padrões por assim dizer ,que devem ser feitas como Subscription, Resource group( a que grupo será alocado o recurso).

![alt text](images/image-18.png)

Outras configurações no entanto devem ser feita com relevância como as a seguir:
  * Perfomance - Para nosso caso fo selecionado a  Standart pois tem um custo menor porém com menos recursos.
    A Premium - Será mais usada para projetos reais onde de fato todos os recursos oferecidos por ela serão necessários.
  * Redundancy - Outro ponto importante para projetos reais, pois diz respeito aos modelos de  replicas dos dados no storage account, para nosso projeto foi selecionado o Locally-redundant storage(LRS) por questões do projeto ser simples para aprendizado e claro reduzir o custo, pois a cada redundancia selecionada implica um valor.

  ![alt text](images/image-19.png)

  Tela de revisão.Mais uma vez pra nosso projeto seguiremos clicando no botão Review + create em seguida em Create.

  ![alt text](images/image-20.png)

  Após o provisionamneto do Storange clicaremos em Go  to Resource, pois neste caso tem algumas configurações adicionais que serão realizadas no storage account criado.

  ![alt text](images/image-21.png)

  ![alt text](images/image-22.png)

  Neste projeto em específico serã realizadas algumas alterações nas Regras de Segurança do Storage account que são padrão ao ser criado.

  ![alt text](images/image-23.png)

  Nas configurações farei alteração no que diz respeito ao acesso no storage account. Desta forma para o projeto em questão a opção Allow Blob anonymous access deixarei como Enabled(Habilitada) em seguida clique no icone disquete e salve a alteração realizada.

  ![alt text](images/image-24.png)

  O próximo passo será trazer para um container que será criado em seguida alguns arquivos.

  ![alt text](images/image-25.png)

  <p>Observe que é possível agora selecionar o nivel de acesso para anonios.
  Outra observação é o nome note que o mesmo se encontra na documentação que estou seguindo neste projeto, observem também mesmo seguindo a documentação o nome foi alterado para seguir as nomenclaturas exigidas:</> 
  
  https://aka.ms/ai900-ai-search

  ![alt text](images/image-26.png)

  clique em create após realizar essas configurações.

  ![alt text](images/image-27.png)

  Agora faremos o Upload dos docs no link abaixo que simulam as revisões dos usuários. É só realizar o download do zip contido no link e descompactar em algum lugar da maquina para em seguida realizar o upload.Observe que o container criado anteriormente deve ser selecionado.

  https://aka.ms/mslearn-coffee-reviews

  ![alt text](images/image-33.png)

  Tudo pronto hora de ver acontecer.
     * Criamos um mecanismo de busca(AI Search).
     * Um Recurso de Inteligência Artificial.
     * Um Storage Account com informações relevantes para realizarmos os testes.

   Vamos então para o serviço AI Search para realizarmos alguns testes(ou seja buscas).

   ![alt text](images/image-29.png)  

   Clico nele, em seguida iremos importar os dados.

   ![alt text](images/image-31.png)

   Ao clicar em importdata será apresentada a seguinte tela, qu evolto a frisar esta presente na documentação as devidas configurações realizadas a seguir:

   ![alt text](images/image-34.png)

   Em Attach Cognitive Services - selecione o serviço de Ai que foi criado anteriormente.

   ![alt text](images/image-35.png)

   Em Add enrichments - Troque o nome de Skillset name para coffee-skillset.
   Deixar selecionado o checkbox - Habilitar OCR e mesclar todo o texto no campo merged_content, pois só assim será possível ver todas as opções de campo enriquecido.

   ![alt text](images/image-36.png)

   ![alt text](images/image-37.png)

![alt text](images/image-39.png)

![alt text](images/image-40.png)

*Consulta que retorna todos os documentos no índice de pesquisa, incluindo uma contagem de todos os documentos no campo @odata.count. Para isto foi acionado o editor de consultas JSON passando para ele o seguinte corpo:
 {
    "search": "*",
    "count": true
}

![alt text](images/image-44.png)

* Filtro por lcalização:
{
 "search": "locations:'Chicago'",
 "count": true
}

![alt text](images/image-43.png)

 * Traz como resultado todos os documentos no índice e filtra revisões com localização em Chicago.

 ![alt text](images/image-42.png)

 * Filtro por analise de sentimento neste caso reaçoes negativas.
 {
 "search": "sentiment:'negative'",
 "count": true
}

![alt text](images/image-41.png)
 


  



   




