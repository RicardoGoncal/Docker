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
    como tentativa de ordenar, porém o resultado é a ordenação do nome dos host e<br />
    não os valores.
</p>

<img src="https://github.com/RicardoGoncal/Docker/blob/master/topn3.jpg" height="300" width="700">
