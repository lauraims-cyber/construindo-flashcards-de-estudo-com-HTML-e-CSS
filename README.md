# construindo-flashcards-de-estudo-com-HTML-e-CSS<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Card Interativo com Pseudoclasses</title>
    <style>
        /* Configurações Globais de Reset */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f0f2f5;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            gap: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 10px;
        }

        /* Nav para testar o :visited */
        .cabecalho-link {
            color: #0066cc;
            text-decoration: none;
            font-weight: bold;
            transition: color 0.2s;
        }

        /* 5. :visited - Link já visitado muda de cor sutilmente */
        .cabecalho-link:visited {
            color: #551a8b;
        }

        /* O CONTAINER DO CARD (Cria o cenário 3D) */
        .cartao {
            background-color: transparent;
            width: 300px;
            height: 400px;
            perspective: 1000px; /* Necessário para o efeito 3D */
        }

        /* O CARD INTERNO (O esqueleto que vai girar) */
        .cartao-interno {
            position: relative;
            width: 100%;
            height: 100%;
            text-align: center;
            transition: transform 0.6s;
            transform-style: preserve-3d;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            border-radius: 10px;
        }

        /* 1. :hover - Gira o card quando o mouse passa por cima */
        .cartao:hover .cartao-interno {
            transform: rotateY(180deg);
        }

        /* 4. :focus-within - Gira o card quando o botão lá dentro recebe foco (via Tab) */
        .cartao:focus-within .cartao-interno {
            transform: rotateY(180deg);
        }

        /* FRENTE E VERSO (Propriedades compartilhadas) */
        .cartao-frente, .cartao-verso {
            position: absolute;
            width: 100%;
            height: 100%;
            -webkit-backface-visibility: hidden; /* Esconde a parte de trás enquanto vira */
            backface-visibility: hidden;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            padding: 20px;
        }

        /* Estilo da Frente */
        .cartao-frente {
            background-color: #ffffff;
            color: #333;
        }

        .foto-produto {
            background-color: #ffe8d6;
            height: 180px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
        }

        .info-frente h3 {
            margin-top: 15px;
            font-size: 1.4rem;
        }

        .dica-interacao {
            font-size: 0.85rem;
            color: #888;
            font-style: italic;
        }

        /* Estilo do Verso */
        .cartao-verso {
            background-color: #2b2d42;
            color: #edf2f4;
            transform: rotateY(180deg); /* Já começa invertido */
        }

        .descricao {
            margin-top: 20px;
            font-size: 1rem;
            line-height: 1.5;
        }

        /* O BOTÃO (Onde testamos focus e active) */
        .botao-comprar {
            background-color: #ef233c;
            color: white;
            border: none;
            padding: 12px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.2s ease;
            outline: none; /* Remove o contorno padrão para fazermos o nosso */
        }

        /* 2. :focus - Farol de acessibilidade (quando navega com a tecla TAB) */
        .botao-comprar:focus {
            box-shadow: 0 0 0 4px #ffffff, 0 0 0 7px #ef233c;
        }

        /* 3. :active - Feedback instantâneo do clique */
        .botao-comprar:active {
            transform: scale(0.95);
            background-color: #d90429;
        }
    </style>
</head>
<body>

    <header>
        <p>Visite nossa <a href="#politicas" class="cabecalho-link">Página de Políticas</a> (Teste de :visited)</p>
    </header>

    <div class="cartao">
        <div class="cartao-interno">
            
            <div class="cartao-frente">
                <div class="foto-produto">🎧</div>
                <div class="info-frente">
                    <h3>Headphone Premium</h3>
                    <p>R$ 299,00</p>
                </div>
                <p class="dica-interacao">Passe o mouse ou use TAB</p>
            </div>
            
            <div class="cartao-verso">
                <h3>Detalhes do Produto</h3>
                <p class="descricao">Cancelamento de ruído ativo, bateria de 40 horas e som de alta fidelidade para seus estudos e músicas.</p>
                <button class="botao-comprar">Garantir o meu</button>
            </div>

        </div>
    </div>

</body>
</html>
