<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CRÉDITO PARA INVESTIMENTOS</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://i.imgur.com/m1HgDnr.png') no-repeat center center fixed;
            background-size: cover;
            text-align: center;
            padding: 20px;
            margin: 0;
            text-transform: uppercase; /* Adicionada a transformação para maiúsculas */
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            margin: auto;
        }

        h2 {
            color: #000;
        }

        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
            text-align: left;
        }

        select, input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }

        button {
            background-color: #28a745;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 15px;
            width: 100%;
            font-size: 18px;
        }

        button:hover {
            background-color: #218838;
        }

        a {
            color: inherit;
            text-decoration: none;
            font-weight: normal;
        }

        @media (max-width: 600px) {
            .container {
                width: 90%;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <h2>CRÉDITO PARA INVESTIMENTO</h2>
    <form id="creditoForm">
        <label for="nome">Seu Nome</label>
        <input type="text" id="nome" name="nome" required>

        <label for="telefone">Seu Telefone</label>
        <input type="tel" id="telefone" name="telefone" required>

        <label for="cidade">Cidade</label>
        <input type="text" id="cidade" name="cidade" required>

        <label for="investimento">Área de Investimento</label>
        <select id="investimento" name="investimento" required>
            <option value="" disabled selected>Selecione uma opção</option>
            <option value="Crédito Rural">Crédito Rural</option>
            <option value="Crédito Veicular">Crédito Veicular</option>
            <option value="Crédito Imobiliário">Crédito Imobiliário</option>
            <option value="Crédito para Construção">Crédito para Construção</option>
            <option value="Crédito para Reforma">Crédito para Reforma</option>
            <option value="Crédito Comercial (Loja/Ponto Comercial)">Crédito Comercial (Loja/Ponto Comercial)</option>
            <option value="Crédito para Máquinas e Equipamentos">Crédito para Máquinas e Equipamentos</option>
            <option value="Crédito Agropecuário">Crédito Agropecuário</option>
        </select>

        <label for="valor">Valor do Investimento</label>
        <select id="valor" name="valor" onchange="atualizarParcelas()" required>
            <option value="" disabled selected>Selecione um valor</option>
            <option value="100000">R$ 100.000</option>
            <option value="150000">R$ 150.000</option>
            <option value="200000">R$ 200.000</option>
            <option value="250000">R$ 250.000</option>
            <option value="350000">R$ 350.000</option>
            <option value="400000">R$ 400.000</option>
            <option value="500000">R$ 500.000</option>
            <option value="600000">R$ 600.000</option>
            <option value="750000">R$ 750.000</option>
            <option value="800000">R$ 800.000</option>
            <option value="1000000">R$ 1.000.000</option>
        </select>

        <label for="parcela">Valor da Parcela</label>
        <select id="parcela" name="parcela" required>
            <option value="" disabled selected>Selecione o valor do investimento primeiro</option>
        </select>

        <button type="button" onclick="enviarWhatsApp()">Solicitar Crédito via WhatsApp</button>
    </form>
</div>

<script>
    function atualizarParcelas() {
        var valor = document.getElementById("valor").value;
        var parcela = document.getElementById("parcela");

        parcela.innerHTML = '<option value="" disabled selected>Selecione uma opção</option>';

        var opcoesParcelas = {
            "100000": [590, 690, 800, 900, 1000],
            "150000": [890, 950, 1200, 1500, 1900],
            "200000": [1100, 1300, 1500, 1800, 2200],
            "250000": [1500, 2000, 2500, 3000, 3500],
            "350000": [2000, 2500, 3000, 3500, 4000],
            "400000": [2200, 2700, 3200, 3800, 4500],
            "500000": [3000, 4000, 5000, 6000, 7000],
            "600000": [3500, 4500, 5500, 6500, 7500],
            "750000": [5000, 6000, 7000, 8000, 9000],
            "800000": [5500, 7000, 8500, 10000, 11500],
            "1000000": [7000, 10000, 15000, 20000, 25000]
        };

        if (valor in opcoesParcelas) {
            opcoesParcelas[valor].forEach(function(p) {
                var option = document.createElement("option");
                option.value = p;
                option.text = "R$ " + p.toLocaleString();
                parcela.appendChild(option);
            });
        }
    }

    function enviarWhatsApp() {
        var nome = document.getElementById("nome").value.trim();
        var telefone = document.getElementById("telefone").value.trim();
        var cidade = document.getElementById("cidade").value.trim();
        var investimento = document.getElementById("investimento").value;
        var valor = document.getElementById("valor").value;
        var parcela = document.getElementById("parcela").value;

        if (!nome || !telefone || !cidade || !investimento || !valor || !parcela) {
            alert("Por favor, preencha todos os campos antes de enviar.");
            return;
        }

        var mensagem = `OI, MEU NOME É *${nome}*.\nTENHO INTERESSE EM PEGAR UM CRÉDITO PARA INVESTIMENTO.\n\n` +
            `📍 *CIDADE:* ${cidade}\n📞 *TELEFONE:* ${telefone}\n` +
            `🏡 *ÁREA DE INVESTIMENTO:* ${investimento}\n💰 *VALOR DO INVESTIMENTO:* R$ ${parseInt(valor).toLocaleString()}\n` +
            `💳 *VALOR DA PARCELA:* R$ ${parseInt(parcela).toLocaleString()}`;

        var url = `https://api.whatsapp.com/send?phone=5598992220513&text=${encodeURIComponent(mensagem)}`;
        window.open(url, "_blank");
    }
</script>

</body>
</html>
