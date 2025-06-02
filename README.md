# miss-o_matheus
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Missão Matheus</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #fff0f5;
      padding: 20px;
    }
    h1 {
      color: #d63384;
    }
    #tabuleiro {
      display: grid;
      grid-template-columns: repeat(5, 60px);
      gap: 10px;
      justify-content: center;
      margin-bottom: 20px;
    }
    .casa {
      width: 60px;
      height: 60px;
      background: #ffe6f0;
      border: 2px solid #d63384;
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: bold;
      border-radius: 10px;
    }
    .jogador {
      background: #d63384;
      color: white;
    }
    #desafio, #final {
      margin-top: 20px;
      font-size: 1.2em;
    }
    button {
      padding: 10px 20px;
      font-size: 16px;
      background: #d63384;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
    }
    #final a {
      display: inline-block;
      margin-top: 15px;
      padding: 10px 20px;
      background: #28a745;
      color: white;
      text-decoration: none;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <h1>Missão Matheus 🎲</h1>
  <div id="tabuleiro"></div>
  <button onclick="jogarDado()">Jogar dado 🎲</button>
  <div id="desafio"></div>
  <div id="final"></div>

  <script>
    const totalCasas = 20;
    let posicao = 0;
    const desafios = {
      3: "Pule de um pé só e grave um vídeo mandando pra Gabs!",
      5: "Crie uma dança especial e dê o nome de 'Dança do Amor'",
      7: "Faça um desenho da Gabs com o que tiver por perto",
      9: "Imite o que acha que a Gabs diria se estivesse brava",
      11: "Tire uma selfie com algo que lembre ela",
      13: "Ache um objeto com a letra G",
      15: "Pense em uma palavra fofa e faça mímica para a Gabs adivinhar",
      17: "5 minutos para agradá-la de alguma forma (só avança se me fizer sorrir)"
    };

    function desenharTabuleiro() {
      const tabuleiro = document.getElementById("tabuleiro");
      tabuleiro.innerHTML = "";
      for (let i = 1; i <= totalCasas; i++) {
        const casa = document.createElement("div");
        casa.className = "casa" + (i === posicao ? " jogador" : "");
        casa.textContent = i;
        tabuleiro.appendChild(casa);
      }
    }

    function jogarDado() {
      if (posicao >= totalCasas) return;

      const dado = Math.floor(Math.random() * 6) + 1;
      posicao += dado;
      if (posicao > totalCasas) posicao = totalCasas;

      desenharTabuleiro();
      document.getElementById("desafio").innerText = desafios[posicao] || "";

      if (posicao === totalCasas) {
        document.getElementById("final").innerHTML = `
          <p>Parabéns! Você completou todos os desafios e se mostrou digno para namorar a Gabs!<br>Agora, clique e descubra sua recompensa final:</p>
          <a href="https://gabspedralina.github.io/gabs_matheus/" target="_blank">Acesse seu presente especial 💖</a>
        `;
      }
    }

    desenharTabuleiro();
  </script>
</body>
</html>
