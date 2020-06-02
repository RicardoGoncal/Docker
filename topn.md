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
    Mas porque? Através desta pergunta varias modificações foram realizadas, mas visto que<br />
    o plugin em si não tem um suporte para escolha de qual campo podemos aplicar a ordenação.
</p>