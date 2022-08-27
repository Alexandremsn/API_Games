# API_Games
Uso de uma api para importação de uma base de dados realização de seu tratamento, exportação para banco de dados MySQL, e criação de um Dashboard em Tableau

Para este projeto usamos a API RAWG, acessível no link: http://rawg.io
Esta API, possui um banco de dados de vários jogos, com seus dados, avaliações, status do jogos fornecidos por jogadores e diversas outras informações.
Vamos focar na varível avaliação e genero, para verificarmos correlações e variações, se a preferência do público se alterou nos últimos 20 anos. podemos também ralizar inferências sobre os status dos jogos e número de votos o jogo recebeu.

<img src=images/001.png>

Usamos uma das API chamada Game List, que fornece dados gerais sobre jogos, na imagem vemos os parâmetros que podem ser usados nesta API, 
mais para frente veremos que os parâmetros page e page_size serão utilizados.

<img src=images/002.png>

Também usamos o parâmetro Dates, pois no nosso projeto vamos usar o filtro entre 01-01-2000 até 31-21-2020, assim gerando dados completos dos últimos 20 anos.

<img src=images/003.png>

Esta ulitma parte dos parâmetros não vamos utilizar.

<img src=images/004.png>

Após verificar a primeira requisição para ter uma ideia do formado, verificamos dois problemas, todos os dados estavam em uma única célula e que a API só fornecia 40 registros por requsição, assim para solucionar o primero problema dividimos cada conjunto de dados de cada jogo em uma linha e criamos um laço for para fazer múltiplas requisições e armazenar todos os dados em um dataframe ainda não normalizado.

<img src=images/005.png>

Após aplicar um segundo laço nós desempacotamos cada linha e adicionados em um dataframe normalizado e tivemos este resultado, que já está mais amigável.

<img src=images/006.png>

Depois verificamos que o único dado que vamos utilzar que ainda presisaria ser desempacotado seria a coluna com o genero do jogo, assim criamos uma função para realizar o desempacotamento e guardar este dado em uma lista. depois selecionamos todas as colunas que vamos utilizar, e finalmente verificamos que o código rodou com sucesso.

<img src=images/007.png>

Na parte final do código, criamos uma tabela com id_jogo e genero, pois os jogos possuiem mais de um gênero ao mesmo tempo assim, podemos usar futuramente um join para fazer a relações entre as tabelas e acessar cada genero individualmente. Exportamos as tabelas em .CSV para uso em alguma validação, deopis por fim exportamos para um banco de dados MySQL.

<img src=images/008.png>



<img src=images/009.png>


<img src=images/010.png>
