## 2. Exercícios de Funções Agregadas

1. Quais são os valores máximo e mínimo das seguintes colunas:
    * total
    * hp
    * ataque
    * defesa
    * ataque_especial
    * defesa_especial
    * velocidade
    * taxa_captura

```sql
SELECT 
    MAX(total), MIN(total)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(hp), MIN(hp)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(ataque), MIN(ataque)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(defesa), MIN(defesa)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(ataque_especial), MIN(ataque_especial)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(defesa_especial), MIN(defesa_especial)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(velocidade), MIN(velocidade)
FROM
    pokemon;
/*--*/
SELECT 
    MAX(taxa_captura), MIN(taxa_captura)
FROM
    pokemon;

```

2. Quantas cores diferentes possuem os pokémons?

```sql
SELECT 
    COUNT(DISTINCT cor) AS 'cores'
FROM
    pokemon;

```

3. Qual é o peso médio dos pokémons?

```sql
SELECT 
    AVG(peso_kg)
FROM
    pokemon;

```

4. Qual é a soma das alturas dos pokémons?

```sql
SELECT 
    SUM(altura_m)
FROM
    pokemon;

```

5. Quantos pokémons estão cadastrados no banco de dados?

```sql
SELECT 
    COUNT(nome)
FROM
    pokemon;

```

6. Qual é o altura média dos pokémons?

```sql
SELECT 
    AVG(altura_m)
FROM
    pokemon;

```

7. Qual é o desvio padrão do valor de HP dos pokémons?
```sql

SELECT 
    STDDEV(hp)
FROM
    pokemon;
```

8. Quantos pokémons possuem tipo2?

```sql
SELECT 
    COUNT(tipo2)
FROM
    pokemon;

```

9. Quantos são os diferentes tipos primários dos pokémons? 

```sql
SELECT 
    COUNT(DISTINCT tipo1)
FROM
    pokemon;

```

10. Qual é a soma dos pesos dos pokémons?

```sql
SELECT 
    SUM(peso_kg)
FROM
    pokemon;


```

11. Qual é a quantidade de Pokémons lendários e não lendários

```sql
SELECT 
    lendario, COUNT(lendario)
FROM
    pokemon
GROUP BY 
	lendario;

```

12. Qual é a quantidade de pokémons para cada uma das diferentes cores ordenadas decrescente?

```sql
SELECT 
    cor, COUNT(cor)
FROM
    pokemon
GROUP BY cor
ORDER BY cor DESC;

```

13. Qual é a média de peso e altura de cada um dos tipos primários dos pokémons? Ordene os resultados decrescente respectivamente por média de peso e altura.
```sql
SELECT 
    tipo1, AVG(peso_kg), AVG(altura_m)
FROM
    pokemon
GROUP BY tipo1
ORDER BY AVG(peso_kg) DESC, AVG(altura_m) DESC;

```

14. Qual é a taxa de captura média por cor de cada um dos pokémons lendários?

```sql
SELECT 
    cor, AVG(taxa_captura) AS 'Média'
FROM
    pokemon
WHERE
    lendario = 1
GROUP BY cor;

```

15. Qual os tipos primários que possuem a taxa de captura média acima de 100

```sql
SELECT 
    tipo1, AVG(taxa_captura) AS 'Média'
FROM
    pokemon
WHERE
    taxa_captura > 100
GROUP BY tipo1;

```

16. Agrupados por cor, quais pokémons não lendários possuem média total abaixo de 400

```sql
SELECT 
    nome
FROM
    pokemon
WHERE
    lendario = 0
        AND (ataque + defesa + defesa_especial + ataque_especial + velocidade) / 5 < 400
GROUP BY cor;

```

17. Qual o valor máximo total em cada uma das gerações?

```sql
SELECT 
    geracao, MAX(total)
FROM
    pokemon
GROUP BY geracao;

```

18. Quantos pokémons lendários existem em cada uma das gerações?

```sql
SELECT 
    geracao, COUNT(lendario)
FROM
    pokemon
WHERE
    lendario = 1
GROUP BY geracao;

```

19. Em cada uma das gerações, quantos pokémons tem tipos primários e secundários e qual a taxa_captura média deles?

```sql
SELECT 
    geracao, COUNT(nome), AVG(taxa_captura)
FROM
    pokemon
WHERE
    tipo1 IS NOT NULL AND tipo2 IS NOT NULL
GROUP BY geracao;

```

20. Qual é a quantidade de cores de cada um dos pokémons lendários em todas as gerações?

```sql
SELECT 
    geracao, COUNT(cor)
FROM
    pokemon
WHERE
    lendario = 1
GROUP BY geracao;

```


## REFERÊNCIAS

* [Webiste Oficial - Pokémon](https://www.pokemon.com/br/guia-para-pais/)
* [Guia de Estilo SQL · SQL Style Guide](https://www.sqlstyle.guide/pt-br/)







