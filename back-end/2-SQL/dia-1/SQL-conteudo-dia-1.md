### O que é SQL?

**SQL**  (_Structured Query Language_) é a linguagem mais usada para criar, pesquisar, extrair e também manipular dados dentro de um  _banco de dados relacional_. Para que isso seja possível, existem comandos como o  `SELECT`,  `UPDATE`,  `DELETE`,  `INSERT`  e  `WHERE`, entre outros, que você aprenderá ao longo do curso.

### Como essas informações (tabelas) são armazenadas?

Todas as pesquisas realizadas dentro de um banco de dados são feitas em tabelas. Tabelas possuem linhas e colunas. Linhas representam um exemplo, ou instância, daquilo que se deseja representar, ao passo que colunas descrevem algum aspecto da entidade representada.

Por exemplo, a imagem a seguir apresenta uma tabela com dados sobre pessoas. Cada linha na tabela representa uma pessoa específica. As colunas descrevem uma característica que queremos armazenar sobre as pessoas; nesse caso, são nome, sobrenome e email.
![](https://assets.app.betrybe.com/back-end/sql/images/columns-8d5054734054be358f6a1f56f1585f0e.png)

---
### _Constraints_  (restrições), chaves primárias e chaves estrangeiras

Uma das grandes vantagens de armazenar seus dados em um banco de dados é possibilitar a criação de regras e restrições (_constraints_, em inglês), que ditam exatamente como os dados podem ou não ser manipulados em suas tabelas.
Como as  _constraints_  são aplicadas às  **colunas**  das tabelas, é possível assegurar que os dados inseridos nelas serão consistentes  **conforme as regras definidas**. Veja alguns tipos de  _constraints_:

-   **NOT NULL**  - Garante que aquele campo  **não pode conter valores nulos**, ou seja, se não houver um valor padrão (`DEFAULT`) definido, será sempre necessário passar um valor para esse campo durante a inserção ou alteração de dados.
-   **UNIQUE**  - Garante que o valor inserido na coluna da tabela é  **único**, isto é, não pode haver outro valor igual para esta coluna registrado nesta tabela.
-   **PRIMARY KEY**  - Garante que o valor seja a  _chave primária_  da tabela, ou seja, que a coluna que possui essa  _constraint (restrição)_  aplicada seja  **o identificador único da tabela**. Ela também é, por definição,  **não nula**  (mesmo efeito da  _constraint NOT NULL_) e  **única**  (mesmo efeito da  _constraint UNIQUE_).
-   **FOREIGN KEY**  - Garante que o valor seja uma  _chave estrangeira_  da tabela, ou seja, faça referência à chave primária (valor em uma coluna com a  _constraint PRIMARY KEY_)  **de outra tabela**, permitindo um relacionamento entre tabelas.
-   **DEFAULT**  - Garante que, caso nenhum valor seja inserido na coluna (ou caso a pessoa usuária insira um valor nulo), a  _constraint (restrição)_  **colocará o valor padrão passado para ela**.

Assim, durante a criação de uma tabela, ao se pensar em suas colunas, podemos avaliar quais  _constraints_  podemos aplicar àquela informação. Por exemplo, imagine uma tabela que liste os sabores de sorvete de uma sorveteria. Nessa tabela, temos três colunas: um código identificador, o nome do sabor do sorvete e o código identificador de quem fornece. Vamos ver cada coluna e pensar em quais  _constraints_  podemos adicionar a elas:

-   **Código identificador (id)**  - Para o id do sorvete, precisamos que ele  _identifique e represente_  o sabor do sorvete na tabela, então podemos adicionar como  _constraint (restrição)_  a  **PRIMARY KEY**.
-   **Nome**  - Aqui, queremos que os valores sejam únicos, afinal, não temos a necessidade de cadastrar um novo sabor de sorvete que já conste na tabela. Além disso, queremos que, ao cadastrar, o valor não seja nulo. Então, como  _constraints_, podemos adicionar  **UNIQUE**  e  **NOT NULL**.
-   **Código identificador de quem fornece (id)**  - Suponha que já possuímos uma tabela onde listamos todas as empresas fornecedoras, e que nessa tabela, os valores estão sendo representados por uma  _primary key_. Então, podemos atribuir como  _constraint (restrição)_  a  **FOREIGN KEY**.




