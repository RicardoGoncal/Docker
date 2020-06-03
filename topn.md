<h1> Relatório Top N - Home Page Sicredi </h1>

<h2> Objetivo do relatório </h2>
<p>
    Este relatório tem como objetivo apresentar algumas demonstrações<br />
    de como alguns datasources realizam a ordenação de valores pelo grafana.
</p>

<h3> Grafana e Zabbix plugin </h3>
<p>
    Ao trabalhar com esse datasource podemos ver que existem muitas maneiras<br />
    de realizar uma consulta em sua base de dados. Porém para esse documento,<br />
    coloco o foco em sua ordenação de dados, principalemente se tratando de métricas.
</p>
<p>
    Para o campo de métricas após realizar um painel com os 10 maiores valores de CPU,<br />
    foi percebido que deveria ser ordenado de acordo com o mair uso, mas isso não ocorreu.<br />
    Mas porque? Através desta pergunta varias modificações foram realizadas, mas foi visto que<br />
    o plugin em si não tem um suporte para escolha de qual campo podemos aplicar a ordenação<br />
    pela coluna desejada, ele entende a ordenação de acordo com alguma configuração do Zabbix<br />
    em seu interior podendo ser por timestamp, aplicação ou até mesmo um item travado dentro<br />
    da aplicação.
</p>
<p>
    A imagem abaixo faz uma pequena demonstração de como o painel ficou, além de apresentar<br />
    uma tabela com as opções que são possiveis. Fora ela temos mais algumas que executam diferentes<br />
    funções, como: soma, filtros, agrupamento, sortseries, top, groupby....<br />
    Dentro da imagem podemos perceber o método de SortSeries que foi utilizado<br />
    como tentativa de ordenar, porém o resultado é a ordenação do nome dos hosts e<br />
    não dos valores.
</p>
<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn3.jpg" height="300" width="600">
<p>
    Com base nessa imagem e estudo com os colegas de equipe, é concluido que realmente no<br />
    momento não se consiga essa ordenação.
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
    ordenação por uma coluna sem ser a de tempo. O plugin deixa bem claro que somente uma<br />
    pelo tempo, ou seja, pelo seu TimeStamp, é possível.
</p>
<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn2.png" height="300" width="600">

<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn1.png" height="300" width="600">