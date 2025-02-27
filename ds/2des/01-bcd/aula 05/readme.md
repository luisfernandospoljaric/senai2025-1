Link meet: https://meet.google.com/ojg-iegh-sun
<div align = "center">
<img src ="https://github.com/user-attachments/assets/4b69c7d1-bdd6-47cf-8d84-02dd8b92abeb"/>
</div>

# Aula 05 - Criando Banco através do MER

## Criar Script

Vamos criar um banco de dados sobre uma academia, neste caso vamos usar o Diagrama a seguir para que possamos realizar o script do banco de dados

![alt text](lousa.jpg)

### Agora vamos popular o banco de dados com as informações

```sql
DROP DATABASE academia;
CREATE DATABASE academia;
USE academia;

CREATE TABLE Cliente(
id_clientes INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
nome VARCHAR(50) NOT NULL,
idade INT NOT NULL
);
CREATE TABLE Treinos (
id_treinos int PRIMARY KEY AUTO_INCREMENT NOT NULL,
nome VARCHAR(50) NOT NULL,
tipo VARCHAR (50) NOT NULL,
duracao INT NOT NULL,
data_adicionado DATE NOT NULL 

);
CREATE TABLE Inscricoes(
id_clientes INT NOT NULL,
id_treinos INT NOT NULL,
PRIMARY KEY(id_clientes,id_treinos),
FOREIGN KEY id_clientes REFERENCES Clientes(id_clientes),
FOREIGN KEY id_treinos REFERENCES Treinos(id_treinos),


INSERT INTO Clientes (nome, idade) VALUES
('Ana Silva', 28),
('Pedro Oliveira', 35),
('Mariana Souza', 42),
('Lucas Lima', 23),
('Carla Santos', 31);

-- Dados para Treinos
INSERT INTO Treinos (nome, tipo, duracao, data_adicionado ) VALUES
('Treino Cardio 1', 'Cardio', 45, '2024-01-15'),
('Treino Cardio 2', 'Cardio', 60, '2024-02-20'),
('Treino Força 1', 'Força', 50, '2024-03-10'),
('Treino Força 2', 'Força', 70, '2024-04-05'),
('Treino Yoga', 'Flexibilidade', 40, '2024-05-01');

-- Dados para Inscricoes
INSERT INTO Inscricoes (id_clientes, id_treinos) VALUES
(1, 1),
(1, 3),
(2, 2),
(2, 4),
(3, 5),
(4, 1),
(4, 2),
(4, 3),
(5, 4);
```

## Perguntas utilizando select

 1. Listar todos os clientes da academia

2. Encontrar todos os clientes com mais de 30 anos

3. Listar todos os treinos disponíveis

4. Encontrar todos os clientes que estão inscritos em qualquer treino com ID 5

5. Listar todos os treinos aos quais um cliente específico (ID 2) está inscrito

6. Encontrar o número total de treinos em que um cliente específico (ID 3) está inscrito

7. Listar todos os clientes que não estão inscritos em nenhum treino

8. Encontrar os treinos que têm duração superior a 60 minutos

9. Listar os clientes que frequentam treinos do tipo "Cardio"

10. Encontrar o cliente com o maior número de inscrições
