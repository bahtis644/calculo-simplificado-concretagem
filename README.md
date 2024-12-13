<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>calculo simplificado concretagem</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 500px;
            margin: 50px auto;
            background: #fff;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
            border-radius: 8px;
        }
        input, select {
            width: 80%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .button {
            background-color: #28a745;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .button:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e9ecef;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Calculadora de Materiais para concretagem</h1>
        <p>Preencha os campos abaixo para calcular a quantidade de materiais necessários para a sua obra.</p>
        <form id="calcForm">
            <label for="area">Área (m²):</label><br>
            <input type="number" id="area" placeholder="Digite a área em m²" required><br>
            <label for="espessura">Espessura da camada (cm):</label><br>
            <input type="number" id="espessura" placeholder="Digite a espessura em cm" required><br>
            <button type="button" class="button" onclick="calcular()">Calcular</button>
        </form>
        <div class="result" id="result"></div>
    </div>

    <script>
        function calcular() {
            // Obter os valores do formulário
            const area = document.getElementById('area').value;
            const espessura = document.getElementById('espessura').value;

            // Verificar se os campos estão preenchidos
            if (!area || !espessura) {
                alert("Por favor, preencha todos os campos.");
                return;
            }

            // Cálculos (exemplo: concreto básico com proporções fixas)
            const volume = area * (espessura / 100); // Conversão para metros cúbicos
            const cimento = volume * 7; // 7 sacos de cimento por m³
            const areia = volume * 0.5; // 0,5 m³ de areia por m³ de concreto
            const brita = volume * 0.75; // 0,75 m³ de brita por m³ de concreto

            // Exibir o resultado
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = `
                <h3>Resultados:</h3>
                <p>Volume total: <strong>${volume.toFixed(2)} m³</strong></p>
                <p>Sacos de cimento (50kg): <strong>${Math.ceil(cimento)}</strong></p>
                <p>Areia necessária: <strong>${areia.toFixed(2)} m³</strong></p>
                <p>Brita necessária: <strong>${brita.toFixed(2)} m³</strong></p>
            `;
        }
    </script>
</body>
</html>
