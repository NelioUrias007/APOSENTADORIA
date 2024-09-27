<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SARGENTÔMETRO</title>
    <style>
        body {
            text-align: center;
            font-family: 'Arial', 'Helvetica', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #f06, #4a90e2);
            color: white;
        }
        h1 {
            font-size: 3em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
        }
        #countdown {
            font-size: 2em;
            margin-top: 20px;
            padding: 10px 20px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }
        img {
            max-width: 80%;
            max-height: 50%;
            object-fit: contain;
        }
    </style>
</head>
<body>
    <h1>SARGENTÔMETRO</h1>
    <img src="Inconfidentes.png" alt="Imagem de Inconfidentes" />
    <div id="countdown"></div>

    <script>
        const countDownDate = new Date("Dec 6, 2024 00:00:00").getTime();

        const x = setInterval(function() {
            const now = new Date().getTime();
            const distance = countDownDate - now;

            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((distance % (1000 * 60)) / 1000);

            document.getElementById("countdown").innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;

            if (distance < 0) {
                clearInterval(x);
                document.getElementById("countdown").innerHTML = "O tempo acabou!";
            }
        }, 1000);
    </script>
</body>
</html>
