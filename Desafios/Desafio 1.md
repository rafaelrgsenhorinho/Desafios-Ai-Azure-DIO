## Primeiro passo: Criar recurso do Azure Machine Learning
Entre os serviços disponiveis, procurei por Azure Machine Learning para criar o meu primeiro recurso.

## Segundo passo: Configurar o recurso criado
Preenchi os dados necessários nessa página, como nome do grupo, nome da área de trabalho, região dos serviços... Após isso, submeti clicando em "Review and Submit", para criar.

Após o recurso ser criado,, abri ele e cliquei no botão "Launch studio" para acessar a página do recurso.

## Terceiro passo: Criar Automated ML Job
No estúdio, na página do workspace criado anteriormente, acessei a opção do menu "Automated ML", e na abrindo a página, "New Automated ML Job".

Em "Basic settings", preenchi "Job name", "New experiment name" e dei uma descrição no campo "Description". Após segui em "Next".

No passo "Task type & data", selecionei o tipo com "Regression" e em seguida, cliquei para criar um "data asset". Em "Data type", preenchi com o nome e descrição dos dados e no "type" inseri "Tabular". Cliquei em "Next", em seguida escolhi a opção "files from the web", e depois em "next".

Em "Web URL", informei a URL https://aka.ms/bike-rentals, e segui com "next". Em "Settings", mudei apenas o "Column headers" para "Only the first file". Depois só segui avançando até o "review" e depois em "create".

Em "Task settings", selecionei o "Target column" como rentals" e o restante preenchi de acordo com a numeração disponibilizada na documentação.

Após concluido e enviado para treinamento, demore alguns minutos para ficar concluido, em torno de 8-9 minutos.

## Quarto passo: Criar model e Metricas

Após criado, na barra lateral, selecionei "Models" e precisei criar um registro na opção "Register" depois "From a job output". Selecionei o meu Job criado, inseri nome, descrição e versão, enquanto o restante deixei no padrão.

Para acessar as Metricas, entrei na pagina "Models", selecionei o modelo, e depois no link da opção "Created by job". A aba de Metricas ficará logo acima, como "Metrics".

## Quinto passo: Teste

Po fim, para testar o modelo, na pagina "Endpoints", foi necessário criar um endpoint, selecionando o modelo criado, depois de criar e acessar, ele requisitará de alguns minutos para ser criado de fato, e assim que for concluido, ficará uma aba de "Test" para utilizar de um código JSON, para fazer o teste.

O código JSON que utilizei foi:

{
  "input_data": {
    "data": [
       {
         "day": 1,
         "mnth": 1,   
         "year": 2022,
         "season": 2,
         "holiday": 0,
         "weekday": 1,
         "workingday": 1,
         "weathersit": 2, 
         "temp": 0.3, 
         "atemp": 0.3,
         "hum": 0.3,
         "windspeed": 0.3 
       }
     ]
  }
}

Por fim o meu retorno foi: [345.50199572426015]