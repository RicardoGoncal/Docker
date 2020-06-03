<h1> Relatório Top N - Home Page Sicredi </h1>

<h2> Objetivo do relatório </h2>
<p>
    Este relatório tem como objetivo apresentar algumas demonstrações de como alguns<br />
    datasources realizam a ordenação de valores pelo grafana utilizando métricas.
</p>

<h3> Grafana e Zabbix plugin </h3>
<p>
    Ao trabalhar com esse datasource podemos ver que existem muitas maneiras de realizar<br />
    uma consulta em sua base de dados. Porém para esse documento, foco em sua ordenação de<br />
    dados, principalmente se tratando de métricas.
</p>
<p>
    Após realizar um painel com os 10 maiores valores de CPU, foi analisado que deveria ser<br />
    ordenado de acordo com o mair uso, porém isso não ocorreu. Mas porquê não ocorreu?<br />
    Através desta pergunta varias modificações foram realizadas no painel, mas foi visto que<br />
    o plugin em si não tem um suporte para escolha de qual campo podemos aplicar a ordenação.<br />
    Sua ordenação aparentemente se dá pelo item que está sendo escolhido na aplicação do Zabbix<br />
    tornado problematica uma escolha por qualquer outra coluna se os dados forem tratados como<br />
    métricas.
</p>
<p>
    A imagem abaixo faz uma pequena demonstração de como o painel ficou, além de apresentar uma<br />
    tabela com as opções que são possiveis. Além dela temos mais algumas que executam diferentes<br />
    funções, como: soma, filtros, agrupamento, sortseries, top, groupby....<br />
    Dentro da imagem podemos perceber o método de SortSeries que foi utilizado como tentativa<br />
    de ordenar os valores, porém o resultado é a ordenação do nome dos hosts.<br />
</p>
<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn3.jpg" height="300" width="600">
<p>
    Com base nessa imagem e estudo com os colegas de equipe, é concluido que realmente no<br />
    momento não se consiga essa ordenação em algumas situações.
</p>

<h3> Grafana e InfluxDB </h3>
<p>
    Como forma de garantir mais informações e que realmente não é possivel executar a ordenação,<br />
    escolhendo uma certa coluna, realizei uma demonstração com outro DataSource, o InfluxDB.<br />
    Essa DEMO tem como objetivo exibir o resultado de uma simples query que contem informações<br />
    de temperatura e um TimeStamp fixo como exemplo.
</p>
<p>
    As imagens abaixo mostram como são feitas as querys, e também o erro que é exibido em caso de<br />
    ordenação por uma coluna sem ser a de tempo. O plugin deixa bem claro que somente uma ordem<br />
    pelo tempo, ou seja, pelo seu TimeStamp, é possível.
</p>
<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn2.JPG" height="300" width="600">

<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn1.JPG" height="300" width="600">
<p>
    Com base nesse segundo estudo demonstrado, somos capazes de absorver mais uma integração<br />
    que não foi possivel a combinação de ordenação de valores se tratando de métricas, mesmo<br />
    que por código em SQL.
</p>

<h3> Grafana e MySQL </h3>
<p>
    Esta ultima DEMO consiste na utilização do MySQL como DataSource de pesquisa. Foi realizado<br />
    também uma base de dados simples contendo um TimeStamp e informações de temperatura.<br />
    O MySQL como plugin dentro do Grafana reage de uma maneira diferente, possibilitando<br />
    uma mescla maior de manipulação de informações. 
</p>
<p>
    A imagem abaixo demonstra uma query realizada em cima dos dados simulados. Foi utilizado a<br />
    função de editar o código, algo que nos outros acima não era possivel. Se olharmos no campo<br />
    'Format as' é claro que está em sendo produzida uma query em cima da Serie temporal, mas<br />
    devido a flexibiidade do MySQL ainda sim o resultado saiu em ordenação pelos valores. <br />
    Logo através de uma query produzida manualemente foi possível colocar os campos desejados<br />
    sempre acompanhado do TimeStamp, "algo que em todos os é meio que obrigatório", realizando<br />
    o agrupamento de valores para não ocorrer erro, e se olhar ao final da linha de código<br />
    temos um ORDER BY 2 DESC( trata-se da ordenção pelo valor pedido na seleção) que realiza<br />
    a ordenação pela coluna AVG(TEMP_celsius).
</p>
<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn4.jpg" height="300" width="600">

<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn5.jpg" height="300" width="600">

<h2> Considerações finais </h2> 
<p>
    Com a realização das 3 demonstrações com diferentes DataSources, podemos observar que cada um<br />
    possui suas caracteristicas de manipulação através de plugins no Grafana. Logo é possivel<br />
    ter uma noção de desenvolvimento dentro de cada ambiente, sendo necessarias se possiveis<br />
    adaptações para casos que fogem da perspectiva desejada.
</p>