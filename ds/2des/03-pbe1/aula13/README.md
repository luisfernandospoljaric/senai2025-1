## Aula 13 - Verificação Prática Somativa 02

- API - Criação de API (Plataforma de Interface de Aplicação)
- CRUD - Funcionalidades de Cadastro, consulta, alteração e exclusão
- MVC - Padrão de projeto (Modelo, Visão e Controle) (SRC => Controller, Connect + routes.js)
- Testes - Testes unitários da API utilizando software Insomnia

|Contextualização da VPS|
|-|
|Sr. Lucas Oliveira é CEO de uma Holding de auto escola em jaguariuna, com o nome de "vitoriakar", os diretores necessitam de um sistema para gerenciamento de estoque de veículos e cadastro de alunos e professores. Você foi incumbido/a de desenvolver a API REST back-end com as funcionalidades básicas CRUD.|

- Script para a população do banco de dados

```SQL
DROP DATABASE IF EXISTS vitoriakar;
CREATE DATABASE IF NOT EXISTS vitoriakar;
USE vitoriakar;

CREATE TABLE clientes(
    cliente_id int(10) NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome varchar(255) NOT NULL,
    cpf varchar(11) NOT NULL UNIQUE,
    email varchar(255) NOT NULL UNIQUE,
    endereco varchar(255) NOT NULL,
    data_nascimento date NOT NULL,
    data_cadastro date NOT NULL   
);

CREATE TABLE professor(
    professor_id int(10) NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome varchar(255) NOT NULL,
    cpf varchar(11) NOT NULL UNIQUE,
    email varchar(255) NOT NULL UNIQUE,
    endereco varchar(255) NOT NULL,
    data_nascimento date NOT NULL,
    data_cadastro date NOT NULL   
);

CREATE TABLE telefone (
    telefone_id int(10) NOT NULL PRIMARY KEY AUTO_INCREMENT,
    cliente_id int(10),
    professor_id int(10),
    numero varchar(20) NOT NULL,
    tipo enum('residencial', 'comercial', 'celular') NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id),
    FOREIGN KEY (professor_id) REFERENCES professor(professor_id)
);

CREATE TABLE veiculos (
    veiculos_id int(10) NOT NULL PRIMARY KEY AUTO_INCREMENT,
    marca_veiculo VARCHAR(252) NOT NULL,
    modelo_veiculo VARCHAR(252) NOT NULL,
    ano_veiculo date NOT NULL,
    fabricacao_veiculo date NOT NULL,
    cliente_id int(10) NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES clientes(cliente_id)
);

```

|Desafio|
|-|
|A partir do script de criação e população com dados de testes do banco de dados, Desenvolva as seguintes funcionalidades
CRUD de Alunos: Implementar operações CRUD (Create, Read, *Update*, Delete) para os Clientes.
CRUD de Professor: Implementar operações CRUD (Create, Read, *Update*, Delete) para os Professores.
CRUD de Telefones: Implementar operações CRUD (Create, Read, Update, Delete) para os telefones
CRUD de veiculos:  Implementar operações CRUD (Create, Read, *Update*, Delete) para os Carros.|

|Entregas|
|-|
|Repostirório no Git Contendo:
API back-end com os CRUDs no padrão MVC em uma pasta "api"
Arquivo insomnia.json com todas as rotas de teste na pasta "testes"
Data: 04/12/2024, <a href="https://forms.gle/6bygMCBKcNDXuUWd7">FORMS</a>|

|Critério|Fundamentos técnicos, científicos ou capacidades técnicas|Critérios|
|-|-|-|
|![Critico](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/critico.png)|Utilizar interações com base de dados para desenvolvimento de sistemas web|Criou arquivo de conexão com os dados efetivos para conexão local com o BD em MySQL, importou a dependência mysql|
|![Critico](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/critico.png)|Estabelecer envio de notificações entre cliente e servidor por meio de aplicação web|Desenvolveu os arquivos controllers e routes utilizando as dependências express e cors, respondendo as requisições HTTP|
|![Critico](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/critico.png)|Desenvolver API (web services) para integração de dados entre plataformas|O back-end está respondendo com dados no formato JSON na rota get, post, put e delete|
|![Critico](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/critico.png)|Desenvolver sistemas web de acordo com as regras de negócio estabelecidas|Implementou as funcionalidades CRUD|	
|![Desejável](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/desejavel.png)|Publicar a aplicação web|O repositório github está publico e com o projeto completo.|
|![Desejável](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/desejavel.png)|Demonstrar raciocínio lógico na organização das informações (14)|Desenvolveu tudo que foi solicitado conforme modelo|
|![Desejável](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/desejavel.png)|Demonstrar visão sistêmica (16)|Desenvolveu API REST com evidencias no arquivo .json do insomnia|
|![Desejável](https://raw.githubusercontent.com/wellifabio/senai2023/main/outros/assets/desejavel.png)|Seguir método de trabalho (15)|Seguir método de trabalho (15)|
