# Códigos do front-end de consultas
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Clínica</title>
</head>

<body>
    <header>
        <h1>Provisório</h1>
    </header>
    <main>
        <section>
            <form>
                <h2>Agendar consulta</h2>
                <input type="text" name="paciente" placeholder="Nome do paciente" required>
                <input type="text" name="medico" placeholder="Nome do médico" required>
                <input type="date" name="data" required>
                <button type="submit">Agendar</button>
            </form>
        </section>
        <section>
            <table>
                <thead>
                    <th>Id</th>
                    <th>Paciente</th>
                    <th>Medico</th>
                    <th>Data</th>
                </thead>
                <tbody>
                </tbody>
            </table>
        </section>
    </main>
    <footer>
        <h2>by wellifabio</h2>
    </footer>
</body>
<script src="index.js"></script>

</html>
```
```css
* {
    margin: 0;
    padding: 0;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

:root {
    --p1: #000;
    --p2: #666;
    --p3: #ccc;
    --p4: #fff;
    --pt: rgba(0, 0, 0, 0.3);
}

body {
    width: 100vw;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}

header,
footer {
    width: 100%;
    height: 10vh;
    background-color: var(--p1);
    color: var(--p4);
    display: flex;
    justify-content: center;
    align-items: center;
}

main {
    width: 100%;
    height: 80vh;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
}

table {
    width: 100%;
    max-height: 100%;
    border-collapse: collapse;
}

th {
    background-color: var(--p3);
    color: var(--p1);
    padding: 10px;
}

td {
    border-bottom: solid 1px var(--p3);
    padding: 10px;
}

section{
    width: 40%;
    display: flex;
    flex-direction: column;
    align-items: center;
    overflow-y: auto;
}

form{
    width: 70%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

input, button{
    width: 100%;
    margin: 5px;
    padding: 10px;
    border-radius: 5px;
}

button{
    cursor: pointer;
}

@media screen and (max-width: 600px) {
    main{
        flex-direction: column;
    }
    section{
        width: 80%;
    }
}
```

```js
const uri = 'http://localhost:4000';

//Obtendo o título do servidor
const titulo = document.querySelector('header h1'); //DOM
fetch(uri)
    .then(resp => resp.json())
    .then(resp => titulo.innerHTML = resp.titulo);

//Obtendo as consultas do servidor e exibindo na tabela
const corpo = document.querySelector('table tbody'); //DOM
fetch(uri + '/consultas')
    .then(resp => resp.json())
    .then(resp => {
        resp.forEach(c => {
            const linha = document.createElement('tr')
            linha.innerHTML = `
                <td>${c.consulta_id}</td>
                <td>${c.nome_paciente}</td>
                <td>${c.nome_medico}</td>
                <td>${c.data_hora}</td>
            `;
            corpo.appendChild(linha);
        });
    });

//Enviando uma nova consulta para o servidor
const form = document.querySelector('form'); //DOM
form.addEventListener('submit', (e) => {
    e.preventDefault();
    const body = {
        paciente: form.paciente.value,
        medico: form.medico.value,
        data: form.data.value
    };

    const options = {
        method: 'POST',
        headers: { 'Content-Type': 'application/json', 'User-Agent': 'insomnia/10.3.1' },
        body: JSON.stringify(body)
    };

    fetch(uri + '/consultas', options)
        .then(resp => resp.status)
        .then(resp => resp === 201 ? window.location.reload() : alert(resp))
        .catch(err => console.error(err));
});
```
