# novo-repo
lista-de-tarefas
lista-de-tarefas/
├── index.html
├── style.css
├── script.js
└── README.md


📁 lista-de-tarefas
   📄 index.html
   📄 style.css
   📄 script.js
   📄 README.md

index.html
meu-projeto/
└── index.html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Minha Lista de Tarefas</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background: #f2f4f8;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }

        .container {
            background: white;
            width: 90%;
            max-width: 500px;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 10px;
        }

        p {
            text-align: center;
            color: #777;
            margin-bottom: 20px;
        }

        .input-area {
            display: flex;
            gap: 10px;
        }

        input {
            flex: 1;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 16px;
        }

        button {
            border: none;
            background: #4f46e5;
            color: white;
            padding: 12px 18px;
            border-radius: 8px;
            cursor: pointer;
        }

        button:hover {
            background: #3730a3;
        }

        ul {
            list-style: none;
            margin-top: 20px;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #f8f8f8;
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 8px;
        }

        .concluida {
            text-decoration: line-through;
            color: #999;
        }

        .excluir {
            background: #ef4444;
            padding: 7px 10px;
        }

        .excluir:hover {
            background: #dc2626;
        }

        #contador {
            margin-top: 20px;
            text-align: center;
            color: #555;
        }
    </style>
</head>

<body>

    <div class="container">

        <h1>📝 Minha Lista</h1>

        <p>Organize suas tarefas</p>

        <div class="input-area">
            <input 
                type="text" 
                id="tarefaInput" 
                placeholder="Digite uma tarefa..."
            >

            <button onclick="adicionarTarefa()">
                Adicionar
            </button>
        </div>

        <ul id="lista"></ul>

        <div id="contador">
            0 tarefas
        </div>

    </div>

    <script>

        function adicionarTarefa() {

            const input = document.getElementById("tarefaInput");
            const texto = input.value.trim();

            if (texto === "") {
                alert("Digite uma tarefa!");
                return;
            }

            const lista = document.getElementById("lista");

            const tarefa = document.createElement("li");

            const textoTarefa = document.createElement("span");

            textoTarefa.textContent = texto;

            textoTarefa.onclick = function() {
                textoTarefa.classList.toggle("concluida");
                atualizarContador();
            };

            const botaoExcluir = document.createElement("button");

            botaoExcluir.textContent = "Excluir";

            botaoExcluir.classList.add("excluir");

            botaoExcluir.onclick = function() {
                tarefa.remove();
                atualizarContador();
            };

            tarefa.appendChild(textoTarefa);
            tarefa.appendChild(botaoExcluir);

            lista.appendChild(tarefa);

            input.value = "";

            atualizarContador();
        }

        function atualizarContador() {

            const tarefas = document.querySelectorAll("#lista li");

            const concluidas = document.querySelectorAll(".concluida");

            const pendentes = tarefas.length - concluidas.length;

            document.getElementById("contador").textContent =
                pendentes + " tarefas pendentes";
        }

        document.getElementById("tarefaInput").addEventListener("keydown", function(event) {

            if (event.key === "Enter") {
                adicionarTarefa();
            }

        });

    </script>

</body>
</html>
