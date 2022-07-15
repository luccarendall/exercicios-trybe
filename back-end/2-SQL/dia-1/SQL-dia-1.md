Agora vamos abrir o  **Workbench**  e fazer uma análise prática do banco de dados  `sakila`, que já deve estar instalado, caso você tenha feito a instalação do  **MySql Workbench**  de forma padrão. Caso o banco  `sakila`  não esteja disponível, volte até a seção  `Restaurando o banco de dados de prática sakila`  e siga as instruções listadas. Com esse banco disponível na sua instalação do  **Workbench**, sua missão agora é tentar finalizar os exercícios a seguir!

**Exercício 1**: Descubra como fazer uma pesquisa em qualquer tabela sem utilizar uma linha de código usando o  **MySql Workbench**.
> SELECT * FROM sakila.actor; para criar uma tabela com base nos dados de atores e pesquisar sem escrever código usamos o input de texto que tem a label "filter rows" para filtrar o resultado das linhas

**Exercício 2**: Descubra como é possível criar uma tabela sem usar código  **SQL**  usando o  **MySql Workbench**.
> Clicando com o botão direito na propriedade e selecionando Create Table

**Exercício 3**: Feito isso, crie uma tabela com as seguintes restrições:

Nome da tabela:  `filme`

Colunas:

-   **_filme_id_**  - primary key, tipo int, incrementa por 1 cada vez que um valor é inserido automaticamente;
-   **_descricao_**  - não permite nulos, tipo texto (varchar(100));
-   **_ano_lancamento_**  - não permite nulos, tipo int;
-   **_nota_**  - permite nulos, tipo int;

> USE sakila
CREATE TABLE filme (
filme_id INT AUTO_INCREMENT PRIMARY KEY,
descricao varchar(100) NOT NULL,
ano_lancamento INT NOT NULL,
nota INT
);
SHOW TABLES;

**Exercício 4**: Analise a tabela  `city`  e encontre a tabela à qual a coluna  `country_id`  faz referência.
> Tabela country

**Exercício 5**: Após resolver o exercício anterior, responda: qual tipo de relacionamento a tabela  `city`  faz com a tabela  `country`?
>N:1
Uma cidade está em um país mas um país tem mais de uma cidade

**Exercício 6**: Qual tipo de relacionamento a tabela  `country`  faz com a tabela  `city`?
>1:N
Uma cidade está em um país mas um país tem mais de uma cidade

**Exercício 7**: Abra tabela por tabela do banco  `sakila`  e encontre no mínimo 3 exemplos de um relacionamentos 1:N ou N:1.
