## Gabi Presbítero

Estudante de Análise e Desenvolvimento de Sistemas na UNIT, no Recife.

Os projetos aqui seguem todos a mesma regra: um problema que existe fora do exercício, dado
público de verdade, e um README que explica o porquê, não só o como.

### Projetos

**[conciliacao-bancaria](https://github.com/gabriellapresbitero/conciliacao-bancaria)** · Java 21<br><br>
Cruza o extrato do banco (OFX ou CSV) com os lançamentos do sistema da empresa e mostra o que
bate, o que não bate e **por quê**. Nos dados de exemplo, concilia 71,4% dos lançamentos
sozinho e explica cada centavo dos 28,6% restantes: pagamento em lote, cartão que cai separado,
aluguel pago com multa que não fecha por R$ 31,20. A etapa de agrupamento é um problema de soma
de subconjuntos, resolvido com backtracking limitado. Dinheiro em `BigDecimal`, nunca em
`double`. Leitor de OFX escrito do zero, porque OFX 1.x não é XML válido.

**[deduplicacao-cadastros](https://github.com/gabriellapresbitero/deduplicacao-cadastros)** · Python<br><br>
Acha a mesma pessoa cadastrada três vezes, com erro de digitação e formato diferente em cada
canal, e junta tudo num único registro mestre. Comparar todos com todos seria inviável, então a
blocagem derruba 1,25 milhão de comparações para cerca de 2 mil (0,17%) antes de pontuar os
pares. Valida dígito verificador de CPF, devolve o nono dígito a celular cadastrado antes de
2016, e recupera o zero à esquerda que o Excel apaga.

**[auditoria-cota-parlamentar](https://github.com/gabriellapresbitero/auditoria-cota-parlamentar)** · Python · SQL<br><br>
Lê as despesas reembolsadas aos deputados federais pela CEAP e faz a triagem das que merecem
conferência. As regras moram em SQL: `ROW_NUMBER()` para nota duplicada, CTE para fornecedor
que recebeu R$ 50 mil ou mais de um único deputado, e uma função Python registrada no SQLite
para validar dígito de CNPJ. São centenas de milhares de notas por ano, e isso diz por onde
começar.

**[alerta-dengue-recife](https://github.com/gabriellapresbitero/alerta-dengue-recife)** · Python · SQLite · Power BI<br><br>
Detecta surtos de dengue na Região Metropolitana do Recife comparando cada semana com a mesma
semana dos anos anteriores, a técnica do canal endêmico usada pelas secretarias de saúde. 300
casos em abril e 300 casos em outubro não querem dizer a mesma coisa. O alerta vermelho só sai
depois de duas semanas seguidas acima da zona de epidemia, pra não disparar com ruído.

**[reposicao-estoque](https://github.com/gabriellapresbitero/reposicao-estoque)** · Java<br><br>
Ponto de pedido com estoque de segurança e curva ABC, calculados em cima do histórico real de
vendas. Responde, produto por produto: preciso comprar, quanto, e onde tem dinheiro parado na
prateleira. O nível de serviço é escolhido, não chutado: 95% significa Z = 1,645 e 5% de chance
de faltar produto durante a espera do fornecedor.

Os cinco têm teste automatizado e CI rodando a cada push.
