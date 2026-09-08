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

## INSERT na tabela usuários

```sql
-- Usuarios
INSERT INTO `usuarios`(`nome`, `email`, `senha`, `tipo`) VALUES (
    'Ana Silva',
    'ana@email.com',
    '123abc',
    'editor');

INSERT INTO `usuarios`(`nome`, `email`, `senha`, `tipo`) VALUES (
    'Bruno Souza',
    'bruno@email.com',
    'abc456',
    'admin');

INSERT INTO `usuarios`(`nome`, `email`, `senha`, `tipo`) VALUES (
    'Carla Mendes',
    'carla@email.com',
    '789xyz',
    'editor');

```

## INSERT na tabela categorias

```sql
-- Categorias
INSERT INTO `categorias`(`nome`) VALUES ('Tecnologia');
INSERT INTO `categorias`(`nome`) VALUES ('Educação');
INSERT INTO `categorias`(`nome`) VALUES ('Entretenimento');
```

## INSERT na tabela noticias

```sql
-- Noticias
INSERT INTO `noticias`(`titulo`, `resumo`, `texto`, `imagem`, `data`, `destaque`, `usuario_id`, `categoria_id`) VALUES (
    'Inteligência artificial ganha espaço no dia a dia',
    
    'Ferramentas de inteligência artificial em atividades cotidianas.',
    
    'A inteligência artificial vem se tornando cada vez mais presente na rotina das pessoas. Ferramentas de IA podem ajudar em pesquisas, estudos, organização de tarefas e criação de conteúdos. Com o avanço da tecnologia, novos recursos devem continuar surgindo e facilitando diversas atividades.',
    
    'inteligencia-artificial.jpg',
    '2026-09-07 14:30:00',
    'sim',
    '2', -- Bruno
    '1' -- Tecnologia
);

INSERT INTO `noticias`(`titulo`, `resumo`, `texto`, `imagem`, `data`, `destaque`, `usuario_id`, `categoria_id`) VALUES (
	'Tecnologia ajuda a transformar as salas de aula',
    'Recursos digitais estão sendo utilizados para tornar o aprendizado mais interativo.',
    'O uso de computadores, tablets e plataformas digitais está crescendo nas escolas. Essas ferramentas permitem que os estudantes tenham acesso a diferentes conteúdos e atividades. Para os professores, a tecnologia também pode ser uma forma de complementar as aulas e estimular a participação dos alunos.',
    'tecnologia-educacao.jpg',
    '2026-09-01 12:36:53',
    'sim',
    '1', -- Ana
    '2' -- Educação
);

INSERT INTO `noticias`(`titulo`, `resumo`, `texto`, `imagem`, `data`, `destaque`, `usuario_id`, `categoria_id`) VALUES (
	'Jogos eletrônicos continuam conquistando novos jogadores',
    'O mercado de games continua crescendo e atraindo pessoas de diferentes idades.',
    'Os jogos eletrônicos fazem parte do entretenimento de milhões de pessoas. Atualmente, é possível jogar em computadores, consoles e celulares. Além dos grandes lançamentos, jogos independentes também vêm ganhando destaque entre os jogadores.',
    'jogos-eletronicos.jpg',
    '2026-08-01 22:36:53',
    'nao',
    '3', -- Carla
    '3' -- Entreternimento
);

INSERT INTO `noticias`(`titulo`, `resumo`, `texto`, `imagem`, `data`, `destaque`, `usuario_id`, `categoria_id`) VALUES (
	'Filmes e séries ganham cada vez mais espaço no streaming',
    'Plataformas de streaming continuam investindo em novos filmes e séries para atrair o público.',
    'Os serviços de streaming mudaram a forma como muitas pessoas assistem a filmes e séries. Com diferentes opções de gêneros e produções, o público pode escolher o que assistir diretamente pela internet. As plataformas também estão investindo em produções próprias para conquistar novos espectadores.',
    'filmes-streaming.jpg',
    '2026-05-11 09:01:03',
    'nao',
    '3', -- Carla
    '3' -- Entertenimento
);
```
