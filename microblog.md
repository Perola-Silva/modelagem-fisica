# Microblog

```sql
CREATE DATABASE microblog CHARACTER SET utf8mb4;
```

```sql
CREATE TABLE usuarios(
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    senha VARCHAR(255) NOT NULL,
    tipo ENUM ('admin','editor') NOT NULL
);
```

```sql
CREATE TABLE categorias(
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);
```

```sql
CREATE TABLE noticias(
	id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    titulo VARCHAR(100) NOT NULL,
    resumo VARCHAR(100) NOT NULL,
    texto TEXT NOT NULL,
    imagem VARCHAR(100),
    data TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    destaque ENUM ('nao','sim') NOT NULL,
    usuario_id INT NOT NULL, 
    categoria_id INT NOT NULL,
    
    FOREIGN KEY(usuario_id) REFERENCES usuario(id) ON DELETE SET NULL,
    FOREIGN KEY(categoria_id) REFERENCES categorias(id) ON DELETE SET NULL
);
```
