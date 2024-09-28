<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SARGENTÔMETRO - Turma Inconfidentes</title>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&family=Oswald:wght@500;700&display=swap" rel="stylesheet">
    
    <!-- Font Awesome para Ícones -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* Reset básico */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* Fonte e fundo */
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: #fff;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            text-align: center;
            position: relative;
            padding: 20px;
        }

        /* Cabeçalho com a imagem */
        .header {
            margin-bottom: 20px;
        }

        .header img {
            max-width: 200px;
            height: auto;
            border-radius: 10px;
            /* Remova o box-shadow se estiver afetando a transparência */
            box-shadow: none;
            /* Garanta que a imagem preserve a transparência */
            background: transparent;
        }

        h1 {
            font-family: 'Oswald', sans-serif;
            font-size: 3.5em;
            margin-bottom: 10px;
            letter-spacing: 2px;
        }

        p {
            font-size: 1.2em;
            margin-bottom: 40px;
        }

        #contador {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .item {
            background: rgba(255, 255, 255, 0.1);
            padding: 20px 30px;
            border-radius: 10px;
            min-width: 120px;
            transition: transform 0.3s, background 0.3s;
        }

        .item:hover {
            transform: scale(1.05);
            background: rgba(255, 255, 255, 0.2);
        }

        .numero {
            font-family: 'Oswald', sans-serif;
            font-size: 2.5em;
            margin-bottom: 10px;
            display: inline-block;
        }

        .texto {
            font-size: 1em;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }

        .texto i {
            color: #ff6347;
        }

        /* Mensagem final */
        #mensagem-final {
            font-size: 2em;
            margin-top: 40px;
            display: none;
        }

        /* Responsividade */
        @media (max-width: 600px) {
            h1 {
                font-size: 2.5em;
            }

            .numero {
                font-size: 2em;
            }

            .item {
                padding: 15px 20px;
                min-width: 100px;
            }

            .header img {
                max-width: 150px;
            }
        }
    </style>
</head>
<body>

    <div class="header">
        <img src="Inconfidentes.png" alt="Turma Inconfidentes">
    </div>

    <div>
        <h1>SARGENTÔMETRO</h1>
        <p>Contagem regressiva para a formatura da Turma Inconfidentes<br>Curso de Formação de Sargentos - CBMMG</p>

        <div id="contador">
            <div class="item">
                <span class="numero" id="dias">0</span>
                <div class="texto"><i class="fa-solid fa-calendar-day"></i> Dias</div>
            </div>
            <div class="item">
                <span class="numero" id="horas">0</span>
                <div class="texto"><i class="fa-solid fa-clock"></i> Horas</div>
            </div>
            <div class="item">
                <span class="numero" id="minutos">0</span>
                <div class="texto"><i class="fa-solid fa-stopwatch"></i> Minutos</div>
            </div>
            <div class="item">
                <span class="numero" id="segundos">0</span>
                <div class="texto"><i class="fa-solid fa-hourglass-half"></i> Segundos</div>
            </div>
        </div>

        <div id="mensagem-final">🎓 Formados! 🎉</div>
    </div>

    <script>
        // Definindo a data de término da contagem
        const dataDeTermino = new Date("Dec 6, 2024 00:00:00").getTime();

        // Atualiza a contagem regressiva a cada 1 segundo
        const x = setInterval(function() {

            // Obtém a data e hora atuais
            const agora = new Date().getTime();

            // Calcula a diferença entre agora e a data de término
            const diferenca = dataDeTermino - agora;

            // Cálculo do tempo restante em dias, horas, minutos e segundos
            const dias = Math.floor(diferenca / (1000 * 60 * 60 * 24));
            const horas = Math.floor((diferenca % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutos = Math.floor((diferenca % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((diferenca % (1000 * 60)) / 1000);

            // Exibe o resultado nos elementos correspondentes
            document.getElementById("dias").innerHTML = dias;
            document.getElementById("horas").innerHTML = horas;
            document.getElementById("minutos").innerHTML = minutos;
            document.getElementById("segundos").innerHTML = segundos;

            // Se a contagem terminar, exibe uma mensagem
            if (diferenca < 0) {
                clearInterval(x);
                document.getElementById("contador").style.display = "none";
                document.getElementById("mensagem-final").style.display = "block";
            }
        }, 1000);
    </script>

</body>
</html>
