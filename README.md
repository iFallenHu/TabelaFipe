![thumbnail-Desafio Java](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256605554-7d1ab66a-2a1c-48e8-825e-2b233c2c1aaa.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211118Z&X-Amz-Expires=300&X-Amz-Signature=8aba0c70cfc4c304b37a769e33bad01733b34b59fe0219ee17581ba6689fd8a2&X-Amz-SignedHeaders=host)


# Desafio


Vamos implementar uma aplicação para consultar o valor médio de veículos (carros, motos ou caminhões) de acordo com a tabela FIPE, que pode ser acessada através [desse site](https://veiculos.fipe.org.br/).

- A consulta aos valores dos veículos pelo site tem o seguinte fluxo:
- Primeiramente é necessário escolher o tipo do veículo: carro, moto ou caminhão.

![image](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256605928-c64bc1d1-2957-4bca-9965-0ce2bf9a6207.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211207Z&X-Amz-Expires=300&X-Amz-Signature=563920a27f6689c241eaed6310428fa98b87a56d75f1ec569edd9b75d44691fe&X-Amz-SignedHeaders=host)


- Depois disso, é necessário preencher a MARCA, MODELO e ANO para consulta.

![image](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256606256-6d85805f-d6b6-40e8-a65d-17cb13a740ed.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211236Z&X-Amz-Expires=300&X-Amz-Signature=e10aad7da79193fd843421b0a8e31a49f787afed95a66a4c21263789d564f97c&X-Amz-SignedHeaders=host)


- Por fim, é exibida a avaliação apenas daquele ano escolhido.

  ![image](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256606353-94910321-15ed-49fe-bffc-25e1c4ab52dc.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211300Z&X-Amz-Expires=300&X-Amz-Signature=a19ac966e3574981728d642daad53762f2ee496c38c63c32c2c74935b8d6c9c1&X-Amz-SignedHeaders=host)



## 🔨 Objetivos do projeto

- O objetivo do projeto é ter um fluxo similar ao que é feito no site, porém com algumas melhorias.
- Criaremos um projeto Spring com linha de comando, utilizando a classe Scanner para fazer interações com o usuário via terminal.
- Solicitaremos que o usuário digite o tipo de veículo desejado (carro, caminhão ou moto).
- Feito isso, listaremos todas as marcas daquele tipo de veículo, solicitando que o usuário escolha uma marca pelo código.
- Após essa escolha, listaremos todos os modelos de veículos daquela marca.
- Solicitaremos que o usuário digite um trecho do modelo que ele quer visualizar, por exemplo **PALIO**.
- Listaremos apenas os modelos que tiverem a palavra **PALIO** no nome.
- Usuário escolherá um modelo específico pelo código e, diferente do site, já listaremos as avaliações para **TODOS** os anos disponíveis daquele modelo, retornando uma lista de forma similar à imagem abaixo:

![image](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256607052-3d0ac772-3eff-4bad-a1fd-e7c2f34a39bc.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211325Z&X-Amz-Expires=300&X-Amz-Signature=9d0fd9bd4afbac6d8d6fa5208208056307cbfce2bb8ad8f1362a1e48ef10bf13&X-Amz-SignedHeaders=host)



## Observações:

- Para realização do desafio faremos o consumo de uma API, documentada [nesse link](https://deividfortuna.github.io/fipe/).

- De acordo com o escolhido (carro, moto, ou caminhão) vamos fazer uma chamada a um dos endpoints abaixo para buscar as marcas:

https://parallelum.com.br/fipe/api/v1/carros/marcas

https://parallelum.com.br/fipe/api/v1/motos/marcas

https://parallelum.com.br/fipe/api/v1/caminhoes/marcas

- O retorno dessa requisição será uma lista com código e marca desejada. Caso o usuário queira por exemplo fazer uma consulta a modelos de carros da Fiat, que possui o código 21, terá que fazer uma nova requisição para o endpoint:

https://parallelum.com.br/fipe/api/v1/carros/marcas/21/modelos

- Feito isso, irá escolher um código de modelo, por exemplo esse **Palio Weekend Stile 1.6 mpi 16V 4p**, representado pelo código 560. Então deverá fazer uma terceira requisição para o endpoint:

https://parallelum.com.br/fipe/api/v1/carros/marcas/21/modelos/560/anos

- Para saber a avaliação para cada ano disponível, teremos que fazer requisições pelo código por ano, onde obteremos um retorno similar ao que é mostrado abaixo:

https://parallelum.com.br/fipe/api/v1/carros/marcas/21/modelos/560/anos/2003-1

![image](https://github-production-user-asset-6210df.s3.amazonaws.com/66698429/256607443-0bed6f40-3112-442e-a6c5-33acd8301c6c.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250125%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250125T211344Z&X-Amz-Expires=300&X-Amz-Signature=99e6162e1226d70c2b14ae23c6f999231921ea4c6973b483295c84a4015ac148&X-Amz-SignedHeaders=host)



- Para podermos exibir em nossa aplicação as avaliações de todos os anos para esse modelo, será necessário trabalhar com as coleções e estruturas de repetição para poder exibir já todos as avaliações de todos os anos para o nosso usuário.
- Utilize a biblioteca Jackson para a desserialização dos dados.
- Modele as classes de acordo com o necessário para representar as marcas, modelos e dados dos veículos.
- Relembre os conceitos vistos no curso para filtrar os modelos por um trecho do nome. 

