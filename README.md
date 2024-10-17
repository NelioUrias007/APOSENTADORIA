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
            justify-content: flex-start; /* Alterado para flex-start para acomodar o carômetro */
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
            margin-bottom: 60px; /* Espaço para o carômetro */
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

        /* Carômetro */
        #carometro {
            width: 100%;
            max-width: 1200px;
            margin: 40px 0;
        }

        #carometro h2 {
            font-family: 'Oswald', sans-serif;
            font-size: 2.5em;
            margin-bottom: 20px;
        }

        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .grid-item {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            transition: transform 0.3s, background 0.3s;
        }

        .grid-item:hover {
            transform: scale(1.05);
            background: rgba(255, 255, 255, 0.2);
        }

        .grid-item img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            margin-bottom: 10px;
        }

        .grid-item .nome {
            font-family: 'Oswald', sans-serif;
            font-size: 1.2em;
            margin-bottom: 5px;
        }

        .grid-item .descricao {
            font-size: 0.9em;
        }

        /* Responsividade */
        @media (max-width: 768px) {
            h1 {
                font-size: 3em;
            }

            #carometro h2 {
                font-size: 2em;
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

            .grid-item img {
                height: 150px;
            }
        }

        @media (max-width: 600px) {
            h1 {
                font-size: 2.5em;
            }

            #carometro h2 {
                font-size: 1.8em;
            }

            .numero {
                font-size: 1.8em;
            }

            .item {
                padding: 15px 20px;
                min-width: 100px;
            }

            .header img {
                max-width: 150px;
            }

            .grid-item img {
                height: 120px;
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
        <p>Contagem regressiva para o último Bola de Fogo<br>CFS - 2024<br>Turma Inconfidentes</p>

        <div id="contador">
            <div class="item">
                <span class="numero" id="dias">0</span>
                <div class="texto"><i class="fa-solid fa-calendar-day" aria-hidden="true"></i> Dias</div>
            </div>
            <div class="item">
                <span class="numero" id="horas">0</span>
                <div class="texto"><i class="fa-solid fa-clock" aria-hidden="true"></i> Horas</div>
            </div>
            <div class="item">
                <span class="numero" id="minutos">0</span>
                <div class="texto"><i class="fa-solid fa-stopwatch" aria-hidden="true"></i> Minutos</div>
            </div>
            <div class="item">
                <span class="numero" id="segundos">0</span>
                <div class="texto"><i class="fa-solid fa-hourglass-half" aria-hidden="true"></i> Segundos</div>
            </div>
        </div>

        <!-- Carômetro da Turma de Sargentos -->
        <section id="carometro">
            <h2>LATÔMETRO</h2>
            <div class="grid-container">
                <!-- Início dos 31 itens do Carômetro -->
                
                <!-- Exemplo de Item 1 -->
                <div class="grid-item">
                    <img src="sargento1.jpg" alt="Sargento 1">
                    <div class="nome">Sd Breno</div>
                    <div class="descricao">Saruê</div>
					<div class="descricao">Paquito</div>
                </div>
                
                <!-- Exemplo de Item 2 -->
                <div class="grid-item">
                    <img src="sargento2.jpg" alt="Sargento 2">
                    <div class="nome">Sd Nogueira</div>
                    <div class="descricao">Pãozinho</div>
                </div>
                
                <!-- Exemplo de Item 3 -->
                <div class="grid-item">
                    <img src="sargento3.jpg" alt="Sargento 3">
                    <div class="nome">Sd Samuel Almeida</div>
                    <div class="descricao">Cara fina</div>
                </div>
                
				<!-- Exemplo de Item 4 -->
                <div class="grid-item">
                    <img src="sargento4.jpg" alt="Sargento 3">
                    <div class="nome">Sd Moisés Henrique</div>
                    <div class="descricao">Momô</div>
                </div>
				
				<!-- Exemplo de Item 5 -->
                <div class="grid-item">
                    <img src="sargento5.jpg" alt="Sargento 3">
                    <div class="nome">Sd Thaís Cardoso</div>
                    <div class="descricao">Fofa</div>
                </div>
				
				<!-- Exemplo de Item 6 -->
                <div class="grid-item">
                    <img src="sargento6.jpg" alt="Sargento 3">
                    <div class="nome">Cb Euler</div>
					<div class="descricao">Zero meia</div>
                    <div class="descricao">Cabelinho de mola</div>
                </div>
				
				<!-- Exemplo de Item 7 -->
                <div class="grid-item">
                    <img src="sargento7.jpg" alt="Sargento 3">
                    <div class="nome">Sd Almir</div>
                    <div class="descricao">Riquinho</div>
                </div>
				
				<!-- Exemplo de Item 8 -->
                <div class="grid-item">
                    <img src="sargento8.jpg" alt="Sargento 3">
                    <div class="nome">Sd Pedro Freire</div>
                    <div class="descricao">Thammy Gretchen</div>
                </div>
				
				<!-- Exemplo de Item 9 -->
                <div class="grid-item">
                    <img src="sargento9.jpg" alt="Sargento 3">
                    <div class="nome">Sd Fernanda</div>
                    <div class="descricao">Araguari</div>
                </div>
				
				<!-- Exemplo de Item 10 -->
                <div class="grid-item">
                    <img src="sargento10.jpg" alt="Sargento 3">
                    <div class="nome">Sd Karla Mota</div>
                    <div class="descricao">Karlatirica</div>
                </div>
				
				<!-- Exemplo de Item 11 -->
                <div class="grid-item">
                    <img src="sargento11.jpg" alt="Sargento 3">
                    <div class="nome">Sd Dreison</div>
                    <div class="descricao">Drayson</div>
                </div>
				
				<!-- Exemplo de Item 12 -->
                <div class="grid-item">
                    <img src="sargento12.jpg" alt="Sargento 3">
                    <div class="nome">Cb Paulo Magalhães</div>
                    <div class="descricao">Magal</div>
                </div>
				
				<!-- Exemplo de Item 13-->
                <div class="grid-item">
                    <img src="sargento13.jpg" alt="Sargento 3">
                    <div class="nome">Cb Paulo Rodrigues</div>
                    <div class="descricao">Caveirão</div>
                </div>
				
				<!-- Exemplo de Item 14 -->
                <div class="grid-item">
                    <img src="sargento14.jpg" alt="Sargento 3">
                    <div class="nome">Cb Thales</div>
                    <div class="descricao">Filho do Gepeto</div>
                </div>
				
				<!-- Exemplo de Item 15 -->
                <div class="grid-item">
                    <img src="sargento15.jpg" alt="Sargento 3">
                    <div class="nome">Sd Jobson</div>
                    <div class="descricao">Majobson</div>
                </div>
				
				<!-- Exemplo de Item 16 -->
                <div class="grid-item">
                    <img src="sargento16.jpg" alt="Sargento 3">
                    <div class="nome">Sd Lima</div>
                    <div class="descricao">Peixinho</div>
                </div>
				
				<!-- Exemplo de Item 17 -->
                <div class="grid-item">
                    <img src="sargento17.jpg" alt="Sargento 3">
                    <div class="nome">Cb Nelio</div>
                    <div class="descricao">Moreno</div>
					<div class="descricao">Último Romântico</div>
                </div>
				
				<!-- Exemplo de Item 18 -->
                <div class="grid-item">
                    <img src="sargento18.jpg" alt="Sargento 3">
                    <div class="nome">Cb Diego Bruno</div>
                    <div class="descricao">Cara de Trakinas</div>
                </div>
				
				<!-- Exemplo de Item 19 -->
                <div class="grid-item">
                    <img src="sargento19.jpg" alt="Sargento 3">
                    <div class="nome">Cb Sâmara</div>
                    <div class="descricao">Onça</div>
					<div class="descricao">Samarina</div>
                </div>
				
				<!-- Exemplo de Item 20 -->
                <div class="grid-item">
                    <img src="sargento20.jpg" alt="Sargento 3">
                    <div class="nome">Sd Renilson</div>
                    <div class="descricao">Pastor</div>
                </div>
				
				<!-- Exemplo de Item 21 -->
                <div class="grid-item">
                    <img src="sargento21.jpg" alt="Sargento 3">
                    <div class="nome">Sd Oliveira</div>
                    <div class="descricao">Zero Um</div>
                </div>
				
				<!-- Exemplo de Item 22 -->
                <div class="grid-item">
                    <img src="sargento22.jpg" alt="Sargento 3">
                    <div class="nome">Sd Sara</div>
                    <div class="descricao">Sarinha</div>
					<div class="descricao">Perfeita</div>
                </div>
				
				<!-- Exemplo de Item 23 -->
                <div class="grid-item">
                    <img src="sargento23.jpg" alt="Sargento 3">
                    <div class="nome">Sd Castro</div>
                    <div class="descricao">Ligeirinho</div>
                </div>
				
				<!-- Exemplo de Item 24 -->
                <div class="grid-item">
                    <img src="sargento24.jpg" alt="Sargento 3">
                    <div class="nome">Cb Erickson</div>
                    <div class="descricao">Papai</div>
                </div>

				<!-- Exemplo de Item 25 -->
                <div class="grid-item">
                    <img src="sargento25.jpg" alt="Sargento 3">
                    <div class="nome">Sd Vinte</div>
                    <div class="descricao">Ms. Pum</div>
                </div>

				<!-- Exemplo de Item 26 -->
                <div class="grid-item">
                    <img src="sargento26.jpg" alt="Sargento 3">
                    <div class="nome">Cb Marcus Vinicius</div>
                    <div class="descricao">Tião</div>
                </div>

				<!-- Exemplo de Item 27 -->
                <div class="grid-item">
                    <img src="sargento27.jpg" alt="Sargento 3">
                    <div class="nome">Sd Sérgio</div>
                    <div class="descricao">Gru</div>
                </div>

				<!-- Exemplo de Item 28 -->
                <div class="grid-item">
                    <img src="sargento28.jpg" alt="Sargento 3">
                    <div class="nome">Sd Maedsson</div>
                    <div class="descricao">Sub</div>
                </div>

				<!-- Exemplo de Item 29 -->
                <div class="grid-item">
                    <img src="sargento29.jpg" alt="Sargento 3">
                    <div class="nome">Sd Leão</div>
                    <div class="descricao">Lion</div>
                </div>

				<!-- Exemplo de Item 30 -->
                <div class="grid-item">
                    <img src="sargento30.jpg" alt="Sargento 3">
                    <div class="nome">Cb Kétia</div>
                    <div class="descricao">Caboquetia</div>
                </div>


                <!-- Item 31 -->
                <div class="grid-item">
                    <img src="sargento31.jpg" alt="Sargento 31">
                    <div class="nome">Sd Drummond</div>
                    <div class="descricao">Draimon</div>
                </div>

                <!-- Fim dos 31 itens do Carômetro -->
            </div>
        </section>

        <div id="mensagem-final">🎓 Enfim, Sargentos! 🎉</div>
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
