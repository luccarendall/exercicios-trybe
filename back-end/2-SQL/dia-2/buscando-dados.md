### Para os exercícios a seguir, vamos usar a tabela  `sakila.film`:

-   Escreva uma  _query_  que exiba  **todos os filmes**  cadastrados no banco de dados.
> SELECT * FROM sakila.film;
-   Escreva uma  _query_  que exiba apenas o  **nome**  dos filmes, seu  **ano de lançamento**  e sua  **classificação indicativa**.
> SELECT title, release_year, rating FROM sakila.film;
-   **Quantos filmes**  temos cadastrados?
> SELECT COUNT(*) FROM sakila.film;
> // 1000 filmes

### Para os exercícios a seguir, vamos usar a tabela  `sakila.actor`:

-   Escreva uma  _query_  que exiba apenas os  **sobrenomes únicos**  cadastrados.
> SELECT DISTINCT last_name FROM sakila.actor;
-   **Quantos sobrenomes únicos**  temos na tabela?
> SELECT COUNT(DISTINCT last_name) FROM sakila.actor;
> // 121 sobrenomes únicos
- Ordene os valores na tabela  **em ordem crescente**  de sobrenomes e  **em ordem decrescente**  de nome.
> SELECT * FROM sakila.actor
> ORDER BY first_name DESC, last_name ASC;

### Usando a tabela  `language`:

-   Crie uma pesquisa que mostre os  **5 idiomas cadastrados**, mas  **não mostre**  o idioma  `english`.
> SELECT * FROM sakila.language LIMIT 5 OFFSET 1;

### Usando a tabela  `film`:

-   Selecione todos os dados da tabela. Pronto, fez isso?
> SELECT * FROM sakila.film;
-   Agora vamos tentar fazer o seguinte: Crie uma  _query_  para encontrar os  **20 primeiros filmes**, incluindo o  **título**, o  **ano de lançamento**, a  **duração**, a  **classificação indicativa**  e o  **custo de substituição**. 
> SELECT title, release_year, length, rating, replacement_cost FROM sakila.film LIMIT 20; 
- Ordene os resultados pelos filmes com a **maior duração** e depois pelo **menor custo de substituição**.
> SELECT title, release_year, length, rating, replacement_cost FROM sakila.film 
> ORDER BY rental_duration DESC, replacement_cost ASC
> LIMIT 20;
> obs: o LIMIT só entra no final para limitar o retorno
