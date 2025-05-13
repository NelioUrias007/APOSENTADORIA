<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Contador para Aposentadoria da NINI</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #6dd5fa, #ffffff);
      color: #333;
      text-align: center;
      padding-top: 50px;
    }
    h1 {
      font-size: 2.5em;
      margin-bottom: 10px;
    }
    h2 {
      font-size: 1.5em;
      margin-bottom: 10px;
      color: #005f73;
    }
    h3 {
      font-size: 1.2em;
      color: #0077b6;
      margin-bottom: 30px;
    }
    .contador {
      font-size: 2em;
      background: #f0f8ff;
      border: 2px solid #0077b6;
      border-radius: 15px;
      padding: 30px;
      display: inline-block;
      box-shadow: 0 0 20px rgba(0,0,0,0.1);
    }
    .motivacao {
      margin-top: 30px;
      font-style: italic;
      color: #0077b6;
    }
  </style>
</head>
<body>

  <h1>⏳ Contador para a Aposentadoria</h1>
  <h2>NINI</h2>
  <h3>Data estimada: <strong>13 de novembro de 2027</strong></h3>

  <div class="contador" id="contador">
    Calculando...
  </div>

  <div class="motivacao">
    "Cada dia é um passo rumo ao merecido descanso. Continue firme, NINI!"
  </div>

  <script>
    function atualizarContador() {
      const agora = new Date();
      const fim = new Date("2027-11-13T00:00:00");

      if (agora >= fim) {
        document.getElementById("contador").innerHTML = "🎉 Parabéns NINI! Chegou a sua aposentadoria!";
        return;
      }

      let anos = fim.getFullYear() - agora.getFullYear();
      let meses = fim.getMonth() - agora.getMonth();
      let dias = fim.getDate() - agora.getDate();

      if (dias < 0) {
        meses--;
        const mesAnterior = new Date(fim.getFullYear(), fim.getMonth(), 0).getDate();
        dias += mesAnterior;
      }

      if (meses < 0) {
        anos--;
        meses += 12;
      }

      const totalMeses = anos * 12 + meses;

      const proximaDataParcial = new Date(agora);
      proximaDataParcial.setMonth(proximaDataParcial.getMonth() + totalMeses);
      const diff = fim - proximaDataParcial;

      const horas = Math.floor((diff / (1000 * 60 * 60)) % 24);
      const minutos = Math.floor((diff / (1000 * 60)) % 60);
      const segundos = Math.floor((diff / 1000) % 60);

      document.getElementById("contador").innerHTML = 
        `${totalMeses} meses, ${dias} dias, ${horas} horas, ${minutos} minutos e ${segundos} segundos`;
    }

    atualizarContador();
    setInterval(atualizarContador, 1000);
  </script>

</body>
</html>
