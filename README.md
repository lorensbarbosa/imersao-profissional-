# imersao-profissional-
projeto de imersao profissional controle de estoque 
<!DOCTYPE html>

<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Sistema de Estoque</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

```
<div class="container">
    <h1>Controle de Estoque</h1>

    <input type="text" id="produto" placeholder="Nome do Produto">
    <input type="number" id="quantidade" placeholder="Quantidade">

    <button onclick="adicionarProduto()">Adicionar</button>

    <table>
        <thead>
            <tr>
                <th>Produto</th>
                <th>Quantidade</th>
                <th>Ação</th>
            </tr>
        </thead>
        <tbody id="tabelaProdutos"></tbody>
    </table>
</div>

<script src="script.js"></script>
```

</body>
</html>
body{
font-family: Arial, sans-serif;
background-color: #f4f4f4;
}

.container{
width: 70%;
margin: auto;
background: white;
padding: 20px;
margin-top: 30px;
border-radius: 10px;
}

h1{
text-align: center;
}

input{
padding: 10px;
margin: 5px;
}

button{
padding: 10px;
cursor: pointer;
}

table{
width: 100%;
margin-top: 20px;
border-collapse: collapse;
}

th, td{
border: 1px solid #ddd;
padding: 10px;
text-align: center;
}

th{
background-color: #007BFF;
color: white;
}
let produtos = [];

function adicionarProduto() {

```
const nome = document.getElementById("produto").value;
const quantidade = document.getElementById("quantidade").value;

if(nome === "" || quantidade === ""){
    alert("Preencha todos os campos!");
    return;
}

produtos.push({
    nome: nome,
    quantidade: quantidade
});

atualizarTabela();

document.getElementById("produto").value = "";
document.getElementById("quantidade").value = "";
```

}

function atualizarTabela(){

```
const tabela = document.getElementById("tabelaProdutos");
tabela.innerHTML = "";

produtos.forEach((produto, indice) => {

    tabela.innerHTML += `
    <tr>
        <td>${produto.nome}</td>
        <td>${produto.quantidade}</td>
        <td>
            <button onclick="removerProduto(${indice})">
                Excluir
            </button>
        </td>
    </tr>`;
});
```

}

function removerProduto(indice){
produtos.splice(indice,1);
atualizarTabela();
}


