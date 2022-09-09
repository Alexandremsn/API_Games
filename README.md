# API_Games
Uso de uma API para importação de uma base de dados, realização de seu tratamento, exportação para banco de dados MySQL, e criação de um Dashboard em Tableau

Para este projeto usamos a API RAWG, acessível no link: http://rawg.io
Esta API, possui um banco de dados de vários jogos, com seus dados, avaliações, status dos jogos fornecidos por jogadores e diversas outras informações.
Focaremos na varíavel avaliação e gênero, para verificarmos correlações e variações, se a preferência do público se alterou nos últimos 20 anos. Podemos também realizar inferências sobre os status dos jogos e número de votos o jogo recebeu.

<img src=images/001.png>

Usamos uma das APIS chamada Game List, que fornece dados gerais sobre jogos, na imagem vemos os parâmetros que podem ser usados nesta API, 
mais para frente veremos que os parâmetros page e page_size serão utilizados.

<img src=images/002.png>

Também usamos o parâmetro Dates, pois no nosso projeto usaremos o filtro entre 01-01-2000 até 31-21-2020, assim gerando dados completos dos últimos 20 anos.

<img src=images/003.png>

Esta ultima parte dos parâmetros não utilizamos.

<img src=images/004.png>

Após verificar a primeira requisição para ter uma ideia do formado, verificamos dois problemas, todos os dados estavam em uma única célula e que a API só fornecia 40 registros por requisição, assim para solucionar o primeiro problema dividimos cada conjunto de dados de cada jogo em uma linha e criamos um laço for para fazer múltiplas requisições e armazenar todos os dados em um dataframe ainda não normalizado.

<img src=images/005.png>

Após aplicar um segundo laço desempacotamos cada linha e adicionados em um dataframe normalizado e tivemos este resultado, que já está mais amigável.

<img src=images/006.png>

Depois verificamos que o único dado que vamos utilizar que ainda precisaria ser desempacotado seria a coluna com o gênero do jogo, assim criamos uma função para realizar o desempacotamento e guardar este dado em uma lista. Depois selecionamos todas as colunas que utilizaremos, e finalmente verificamos que o código rodou com sucesso.

<img src=images/007.png>

Na parte final do código, criamos uma tabela com id_jogo e gênero, pois os jogos possuem mais de um gênero ao mesmo tempo, assim, podemos usar futuramente um join para fazer a relações entre as tabelas e acessar cada gênero individualmente. Exportamos as tabelas em  .CSV para uso em alguma validação, depois por fim exportamos para um banco de dados MySQL.

<img src=images/008.png>

Testamos com uma query simples para verificar se as tabelas foram carregadas, e podemos ver as tabelas carregadas corretamente.

<img src=images/009.png>

Para a segunda tabela também tivemos sucesso.

<img src=images/010.png>

Na sequência construiremos visuais com criação de linha do tempo, filtros por gênero, e ao longo desta construção verificaremos se conseguimos verificar outras relações que agreguem valor e sejam uteis na construção de outros visuais.

Inciando a construção do Dashboard
Foi feito o plano de fundo e definido a posição dos visuais

<img src=images/011.png>

No tableau importamos as tabelas e criamos o vínculo entre elas pela variável id

<img src=images/012.png>

Assim começamos montando as medidas que darão o somatório de cada status possível informado pelos usuários.

<img src=images/013.png>

Criamos o owned e configuramos a fonte e fundo do visual

<img src=images/014.png>

Depois repetimos os processos para os outros status e aplicamos no dashboard

<img src=images/015.png>

Criamos o gráfico com a evolução da avaliação por ano estratificada por gênero 

<img src=images/016.png>

Criamos os filtros e configuramos para aplicar a filtragem a todos os dados da mesma base 
Posicionamos 

<img src=images/017.png>

Depois criamos uma tabela que detalha os mais bem avaliados dentro do filtro aplicado 

<img src=images/018.png>

criamos o último gráfico com a evolução de avaliações por tempo estratificada por gênero 

<img src=images/019.png>

Depois criamos um gráficos com o percentual de avaliações por gênero

<img src=images/020.png>

E ficamos com este resultado final
Link:   


<img src=images/021.png>
