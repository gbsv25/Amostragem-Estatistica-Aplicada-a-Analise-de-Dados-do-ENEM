## Amostragem Estatística Aplicada à Análise de Dados do ENEM
Este projeto apresenta diferentes métodos de amostragem estatística aplicados a uma base de dados do ENEM na cidade de Campinas. 
A escolha da técnica apropriada depende dos objetivos da análise e da estrutura da população. 
Abaixo, detalhamos cada método utilizado, sua implementação no código e sua importância na análise.

1️ Amostragem Aleatória Simples (AAS)

🛠 Implementação no Código
•	Utilizada a função sample () do Pandas para selecionar uma amostra aleatória de alunos de Campinas.

•	Métodos aplicados:
o	sample(frac=0.20): Seleciona aleatoriamente 20% dos registros da população.
o	sample (3000): Seleciona exatamente 3.000 registros de maneira aleatória.

    🔍 Porque fazer esta análise?
•	Permite capturar tendências gerais dos alunos sem interferência externa.
•	Pode não garantir a representatividade de grupos menores, caso a população original seja desbalanceada.

2️ Amostragem Sistemática

🛠 Implementação no Código
•	Um ponto de partida aleatório foi definido com np.random.choice(10, 1), garantindo que a seleção inicie em um ponto variável.
•	Um intervalo fixo de 100 posições foi aplicado com np.arange(inicio, 13198, 100), garantindo que um aluno seja selecionado a cada 100 registros.
•	A seleção foi feita com enem_campinas.iloc[amostra2, :], retornando apenas os registros escolhidos sistematicamente.

    🔍 Porque fazer esta análise? 
•	Reduz o impacto de padrões estruturais nos dados, garantindo melhor distribuição da amostra.
•	Mas, Pode não ser ideal se os dados possuírem padrões cíclicos, pois poderia introduzir viés.

3️ Amostragem Estratificada

🛠 Implementação no Código
•	A população foi dividida por grupos homogêneos (estratos) com base na variável RACA.
•	Dentro de cada grupo, 15% dos alunos foram selecionados com sample(frac=0.15).
•	A amostra final foi formada pela junção de todos os estratos com pd.concat([branca, parda, preta, amarela, nd]).
 
    🔍 Relevância desta Análise
•	Garante representatividade proporcional de cada grupo na amostra.
•	Este tipo de Análise é essencial para análises comparativas entre grupos, como estudos de desigualdade educacional.

4️ Amostragem por Conglomerados

🛠 Implementação no Código
•	Primeiramente, os alunos foram agrupados com base no código da escola (CO_ESCOLA).
•	Um subconjunto de 15% das escolas públicas foi selecionado aleatoriamente usando np.random.choice(a=[0,1], size=len(amostras), replace=True, p=[0.85, 0.15]).
•	Todos os alunos das escolas selecionadas foram incluídos na amostra final.

   🔍 Relevância para a Análise
•	Captura características institucionais que podem impactar o desempenho dos alunos.
•	Reduz custos computacionais ao trabalhar com grupos menores em vez de toda a população.
•	Pode gerar viés caso os conglomerados escolhidos tenham características muito homogêneas.

📌 Conclusão
Cada método de amostragem tem sua aplicação específica e impacto na análise dos dados. A escolha do método adequado depende do objetivo da pesquisa e da estrutura da base de dados:

✅ Amostragem Aleatória Simples ---> Aplicada para capturar tendências gerais sem interferência externa. 

✅ Amostragem Sistemática ---> aplicada para garantir uma distribuição uniforme ao longo do conjunto de dados. 

✅ Amostragem Estratificada ---> Assegurar representatividade de grupos menores e comparações precisas. 

✅ Amostragem por Conglomerados ---> Considera agrupamentos naturais da população e reduzir custo computacional.

## Este projeto demonstra a aplicação prática de diferentes técnicas estatísticas para garantir análises robustas e mais confiáveis. 
