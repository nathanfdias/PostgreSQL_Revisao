CREATE TABLE aluno(
    id SERIAL,
        nome VARCHAR(255),
        cpf CHAR(11),
        observação TEXT,
        idade INTEGER,
        dinheiro NUMERIC(10,2),
        altura REAL,
        ativo BOOLEAN,
        data_nascimento DATE,
        hora_aula TIME,
        matriculado_em TIMESTAMP
);

SELECT * FROM aluno;

INSERT INTO aluno (
    nome,
    cpf,
    observação,
    idade,
    dinheiro,
    altura,
    ativo,
    data_nascimento,
    hora_aula,
    matriculado_em
) VALUES (
    'Diogo',
    '12345678901',
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla ac dui et nisl vestibulum consequat. Integer vitae magna egestas, finibus libero dapibus, maximus magna. Fusce suscipit mi ut dui vestibulum, non vehicula felis fringilla. Vestibulum eget massa blandit, viverra quam non, convallis libero. Morbi ut nunc ligula. Duis tristique purus augue, nec sodales sem scelerisque dignissim. Sed vel rutrum mi. Nunc accumsan magna quis tempus rhoncus. Duis volutpat nulla a aliquet feugiat. Vestibulum rhoncus mi diam, eu consectetur sapien eleifend in. Donec sed facilisis velit. Duis tempus finibus venenatis. Mauris neque nisl, pulvinar eu volutpat eu, laoreet in massa. Quisque vestibulum eros ac tortor facilisis vulputate. Sed iaculis purus non sem tempus mollis. Curabitur felis lectus, aliquam id nunc ut, congue accumsan tellus.',
    35,
    100.50,
    1.81,
    TRUE,
    '1984-08-27',
    '17:30:00',
    '2020-02-08 12:32:45'
);

INSERT INTO aluno (
    nome,
    cpf,
    observação,
    idade,
    dinheiro,
    altura,
    ativo,
    data_nascimento,
    hora_aula,
    matriculado_em
) VALUES (
    'Diogo',
    '12345678901',
    'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla ac dui et nisl vestibulum consequat. Integer vitae magna egestas, finibus libero dapibus, maximus magna. Fusce suscipit mi ut dui vestibulum, non vehicula felis fringilla. Vestibulum eget massa blandit, viverra quam non, convallis libero. Morbi ut nunc ligula. Duis tristique purus augue, nec sodales sem scelerisque dignissim. Sed vel rutrum mi. Nunc accumsan magna quis tempus rhoncus. Duis volutpat nulla a aliquet feugiat. Vestibulum rhoncus mi diam, eu consectetur sapien eleifend in. Donec sed facilisis velit. Duis tempus finibus venenatis. Mauris neque nisl, pulvinar eu volutpat eu, laoreet in massa. Quisque vestibulum eros ac tortor facilisis vulputate. Sed iaculis purus non sem tempus mollis. Curabitur felis lectus, aliquam id nunc ut, congue accumsan tellus.',
    35,
    100.50,
    1.81,
    TRUE,
    '1984-08-27',
    '17:30:00',
    '2020-02-08 12:32:45'
);

UPDATE aluno
    SET nome = 'Nico',
    cpf = '10987654321',
    observação = 'Teste',
    idade = 38,
    dinheiro = 15.23,
    altura = 1.90,
    ativo = FALSE,
    data_nascimento = '1980-01-15',
    hora_aula = '13:00:00',
    matriculado_em = '2020-01-02 15:00:00'
WHERE id = 1;    

SELECT *
    FROM aluno 
    WHERE nome = 'Nico';
	
DELETE *
    FROM aluno 
    WHERE nome = 'Nico';
	
	SELECT nome AS "Nome do Aluno",
       idade,
       matriculado_em AS quando_se_matriculou
    FROM aluno;
	
INSERT INTO aluno (nome) VALUES ('Vinícius Dias');
INSERT INTO aluno (nome) VALUES ('Nico Steppat');
INSERT INTO aluno (nome) VALUES ('João Roberto');
INSERT INTO aluno (nome) VALUES ('Diego');	


SELECT * FROM aluno WHERE nome = 'Diogo';
SELECT * 
    FROM aluno
 WHERE nome LIKE 'Di_go';
 
 SELECT * FROM aluno WHERE nome <> 'Diogo';

SELECT * 
    FROM aluno
 WHERE nome LIKE 'D%';
 
 SELECT * 
    FROM aluno
 WHERE nome NOT LIKE 'D%';
 
 SELECT * 
    FROM aluno
 WHERE nome LIKE '% %';
 
 SELECT * 
    FROM aluno
 WHERE nome LIKE '%i%a%';
 
 SELECT *
    FROM aluno
 WHERE cpf IS NULL;
 
 SELECT *
    FROM aluno
 WHERE idade BETWEEN 20 AND 40;
 
 SELECT *
    FROM aluno
  WHERE nome LIKE 'D%'
    AND cpf IS NOT NULL;
	
SELECT *
    FROM aluno
  WHERE nome LIKE 'Diogo'
    OR nome LIKE 'Rodrigo';
	
CREATE TABLE curso (
    id INTEGER NOT NULL,
        nome VARCHAR(255) NOT NULL
);	

DROP TABLE curso;

CREATE TABLE curso (
    id INTEGER PRIMARY KEY,
        nome VARCHAR(255) NOT NULL
);

INSERT INTO curso (id, nome) VALUES (1, 'HTML');
INSERT INTO curso (id, nome) VALUES (2, 'Javascript');

SELECT * FROM curso;
SELECT * FROM aluno;

DROP TABLE aluno;

CREATE TABLE aluno (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(255) NOT NULL
);

INSERT INTO aluno (nome) VALUES ('Diogo');
INSERT INTO aluno (nome) VALUES ('Vinícius');

CREATE TABLE aluno_curso (
    aluno_id INTEGER,
    curso_id INTEGER,
    PRIMARY KEY (aluno_id, curso_id)
);

DROP TABLE aluno_curso;

CREATE TABLE aluno_curso (
    aluno_id INTEGER,
        curso_id INTEGER,
        PRIMARY KEY (aluno_id, curso_id),

        FOREIGN KEY (aluno_id)
         REFERENCES aluno (id),

        FOREIGN KEY (curso_id)
         REFERENCES curso (id)
	);

);

INSERT INTO aluno_curso (aluno_id, curso_id) VALUES (1,1);
INSERT INTO aluno_curso (aluno_id, curso_id) VALUES (2,1);

SELECT * FROM aluno WHERE id = 1;
SELECT * FROM curso WHERE id = 1;

SELECT *
  FROM aluno
  JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
  
  
 SELECT aluno.nome as aluno,
       curso.nome as curso
  FROM aluno
  JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
  JOIN curso ON curso.id = aluno_curso.curso_id 
  
  SELECT aluno.nome as "Nome do Aluno",
       curso.nome as "Nome do Curso"
  FROM aluno
  JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
  JOIN curso ON curso.id = aluno_curso.curso_id
  
  SELECT aluno.nome as "Nome do Aluno",
        curso.nome as "Nome do Curso"
    FROM aluno
LEFT JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
LEFT JOIN curso ON curso.id = aluno_curso.curso_id

--RIGHT & FULL JOIN
--CROSS Relaciona todoas os campos das duas tabelas

CREATE TABLE aluno_curso (
    aluno_id INTEGER,
    curso_id INTEGER,
    PRIMARY KEY (aluno_id, curso_id),

    FOREIGN KEY (aluno_id),
     REFERENCES aluno (id),
     ON DELETE CASCADE

    FOREIGN KEY (curso_id),
     REFERENCES curso (id)

);


CREATE TABLE aluno_curso (
    aluno_id INTEGER,
        curso_id INTEGER,
        PRIMARY KEY (aluno_id, curso_id),

        FOREIGN KEY (aluno_id),
         REFERENCES aluno (id),
         ON DELETE CASCADE
         ON  UPDATE CASCADE

        FOREIGN KEY (curso_id),
         REFERENCES curso (id)
);

CREATE TABLE funcionarios(
    id SERIAL PRIMARY KEY,
    matricula VARCHAR(10),
    nome VARCHAR(255),
    sobrenome VARCHAR(255)
);

INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M001', 'Diogo', 'Mascarenhas');
INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M002', 'Vinícius', 'Dias');
INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M003', 'Nico', 'Steppat');
INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M004', 'João', 'Roberto');
INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M005', 'Diogo', 'Mascarenhas');
INSERT INTO funcionarios (matricula, nome, sobrenome) VALUES ('M006', 'Alberto', 'Martins');

SELECT * 
    FROM funcionarios
    ORDER BY nome;
	
SELECT * 
    FROM funcionarios
    ORDER BY nome DESC;
	
SELECT *
    FROM funcionarios
    ORDER BY 3, 4, 2;	
	
SELECT *
    FROM funcionarios
    ORDER BY 4 DESC, nome DESC, 2 ASC

SELECT 
        aluno.id as aluno_id,
        aluno.nome as "Nome do Aluno",
        curso.id as "curso_id",
        curso.nome as "Nome do Curso"
    FROM aluno
    JOIN aluno_curso ON aluno_curso.aluno_id = aluno.id
    JOIN curso ON curso.id = aluno_curso.curso_id
    ORDER BY curso.nome, aluno.nome
	
SELECT *
  FROM funcionarios
  ORDER BY nome
LIMIT 3;

SELECT *
  FROM funcionarios
  ORDER BY id
 LIMIT 2
OFFSET 2;
--OFFSET de onde starta

-- COUNT - Retorna a quantidade de registros
-- SUM -   Retorna a soma dos registros
-- MAX -   Retorna o maior valor dos registros
-- MIN -   Retorna o menor valor dos registros
-- AVG -   Retorna a média dos registros

SELECT COUNT (id),
       SUM(id),
       MAX(id),
       MIN(id),
       ROUND(AVG(id),0)
  FROM funcionarios;
  
  SELECT DISTINCT
        nome,
        sobrenome
  FROM funcionarios
  ORDER BY nome;
  
  SELECT
       nome,
       sobrenome,
       COUNT(*)
  FROM funcionarios
  GROUP BY nome, sobrenome
  ORDER BY nome;
  
  SELECT curso.nome,
        COUNT(aluno.id)
    FROM aluno
    JOIN aluno_curso ON aluno.id = aluno_curso.aluno_id
    JOIN curso ON curso.id = aluno_curso.curso_id
    GROUP BY 1
    ORDER BY 1
	
SELECT *
    FROM curso
    LEFT JOIN aluno_curso ON aluno.curso_id = curso.id
    LEFT JOIN aluno ON aluno.id = aluno_curso.aluno_id
    --WHERE curso.nome = 'Javascritp'
GROUP BY 1
    HAVING COUNT (aluno.id) = 0
	
	SELECT nome
    FROM funcionarios
    GROUP BY nome
    HAVING COUNT(id) > 1;
	
	SELECT nome,
       COUNT(id)
    FROM funcionarios
    GROUP BY nome
    HAVING COUNT(id) > 1;
	
		SELECT nome,
       COUNT(id)
    FROM funcionarios
    GROUP BY nome
    HAVING COUNT(id) = 1;

CREATE TEMPORARY TABLE a(
	coluna1 VARCHAR(255) NOT NULL CHECK(coluna1 <> ''),
	coluna2 VARCHAR(255) NOT NULL,
	UNIQUE (coluna1, coluna2)
);

INSERT INTO a VALUES('a', 'c');

SELECT * FROM a;

ALTER TABLE a RENAME TO teste;
SELECT * FROM teste;

ALTER TABLE teste RENAME coluna1 TO primeira_coluna
ALTER TABLE teste RENAME coluna2 TO segunda_coluna

-- Bom costume, antes de usar DELETE ou UPDATE,
-- usar SELECT para ter certeza do que será excluido

--OBS: Comandos sql funcionam sobre atomicidade:
-- caso de erro reverte o que foi mudadado

-- Controlando Transações
--START TRANSACTION ou BEGIN: inicia o checkpoint
-- DELETE FROM aluno;
-- Salvar: COMMIT
-- Voltar Checkpoint: ROLLBACK

CREATE SEQUENCE minha_sequence

SELECT NEXTVAL('minha_sequence')
SELECT CURRVAL('minha_sequence')

CREATE TABLE auto(
	id INTEGER PRIMARY KEY DEFAULT NEXTVAL('minha_sequence'),
	nome VARCHAR(30) NOT NULL
);

INSERT INTO auto (nome) VALUES ('Vinicius Dias')
INSERT INTO auto(id, nome) VALUES (2, 'Vinicius Dias')

SELECT * FROM auto;

CREATE TYPE CLASSIFICACAO AS ENUM ('LIVRE', '18_ANOS');

CREATE TABLE filme(
	id SERIAL PRIMARY KEY,
	nome VARCHAR(255) NOT NULL,
	--classificacao VARCHAR(255)CHECK (classificacao IN ('LIVRE', '18_ANOS'))
	--classificacao ENUM ('LIVRE', '18_ANOS')
	classificacao CLASSIFICACAO
);

INSERT INTO filme(nome, classificacao) VALUES ('Um filme qualquer', 'LIVRE')
