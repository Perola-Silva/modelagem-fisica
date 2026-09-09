# SQL SELECT - Exemplos de consultas ao banco Fly By Night

O comando `SELECT` é usado para **consultar dados armazenados nas tabelas do banco de dados**

## SELECT básico

Consultar todos os dados de uma tabela:

```sql
SELECT * FROM produtos;
```

## SELECT para apenas determidas colunas

```sql
SELECT nome, preco FROM produtos;
```

## Alterando nome de exibição das colunas

Usamos o comando `AS` **para criar um apelido (alias)**.

```sql
SELECT 
    nome AS produto, 
    preco AS 'Preço em R$' 
FROM produtos;
```

## Filtrando registros com WHERE

O `WHERE` permite determinar **Quais registros devem aparecer** no resultado. Na prática, são condições para execução do `SELECT`

### Comparação de igualdade

```sql
SELECT * FROM produtos WHERE quantidade = 0;
```

### Comparação de maior

```sql
SELECT nome, preco FROM produtos WHERE preco > 1000;
```

### Comparação de menor ou igual

```sql
SELECT nome, preco FROM produtos WHERE preco <= 1000;
```

### Comparação de diferença

Normalmente se usa o operador `<>` em vez do `!=`.

```sql
SELECT * FROM produtos WHERE fornecedor_id <> 1;
```

---

## Combinando condições

Usamos o `WHERE` e operadores lógicos e relacionais

### Operador AND (E)

Exibir os produtos que custem menos de 500 reais e quantidade acima de 20.

```sql
SELECT nome, preco, quantidade FROM produtos 
WHERE preco < 500 AND quantidade > 20;
```

### Operador OR (OU)

Exibir os produtos que custem mais de 3000 ou com quantidade zerada.

```sql
SELECT nome, preco, quantidade FROM produtos 
WHERE preco > 3000 OR quantidade = 0;
```

### Operador NOT (NÃO)

Exibir os produtos que **não possuem um preço acima de 1000**

```sql
SELECT nome, preco, quantidade FROM produtos 
WHERE NOT preco > 1000;
```

### BETWEEN

Exibir produtos com preço **entre 100 e 500**.

```sql
SELECT nome, preco FROM produtos 
WHERE preco BETWEEN 100 AND 500;
```

### IN 

Exibir produtos que tenha o fornecedor ID 1, 4 ou 8.

```sql
SELECT * FROM produtos
WHERE fornecedor_id IN (1, 4, 8); -- Lista de valores
```

Sem usar o `IN`, teriamos que fazer a lógica ccom múltiplos `OR`:

```sql
SELECT * FROM produtos
WHERE 
fornecedor_id = 1 OR 
fornecedor_id = 4 OR 
fornecedor_id = 8;
```