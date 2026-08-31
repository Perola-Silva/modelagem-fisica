# Microblog

```sql
CREATE TABLE usuario(
id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
nome VARCHAR(100) NOT NULL,
email VARCHAR(100) UNIQUE NOT NULL,
senha VARCHAR(255) NOT NULL,
tipo ENUM ( 'admin' ,  'editor' ) NOT NULL
);
```

```sql
CREATE TABLE categorias(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);
```