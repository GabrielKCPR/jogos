const sprites = new Image();
sprites.src = 'E:/VSCodes/Site_Games/imagens/sprites3.png';

let frames = 0;
const somHit = new Audio();
somHit.src = 'E:/VSCodes/Site_Games/efeitos/hit.wav';
const somPulo = new Audio();
somPulo.src = 'E:/VSCodes/Site_Games/efeitos/pulo.wav';


const canvas = document.querySelector('canvas');
const contexto = canvas.getContext('2d');

const planoDeFundo = {
    spriteX: 212,
    spriteY: 272,
    largura: 1473,
    altura: 681,
    x: 0,
    y: canvas.height - 681,
    desenha() {

        contexto.fillStyle = '#70c5ce';
        contexto.fillRect(0,0, canvas.width, canvas.height);
  
        contexto.drawImage(
            sprites,
            planoDeFundo.spriteX, planoDeFundo.spriteY,
            planoDeFundo.largura, planoDeFundo.altura,
            planoDeFundo.x, planoDeFundo.y,
            planoDeFundo.largura, planoDeFundo.altura,
        );

        contexto.drawImage(

            sprites,
            planoDeFundo.spriteX, planoDeFundo.spriteY,
            planoDeFundo.largura, planoDeFundo.altura,
            (planoDeFundo.x + planoDeFundo.largura), planoDeFundo.y,
            planoDeFundo.largura, planoDeFundo.altura,
        );
    },
};
  
function criarChao(){
    const chao = {
        spriteX: 460,
        spriteY: 71,
        largura: 477,
        altura: 87,
        x: 0,
        y: canvas.height - 50,
        atualiza() {
            const movimentoChao = 1;
            const repeteEm = chao.largura / 1.5;
            const movimentacao = chao.x - movimentoChao;

            chao.x = movimentacao % repeteEm;
        },
        desenha() {
            contexto.drawImage(
                sprites,
                chao.spriteX, chao.spriteY,
                chao.largura, chao.altura,
                chao.x, chao.y,
                chao.largura, chao.altura,
            );
    
            contexto.drawImage(
                sprites,
                chao.spriteX, chao.spriteY,
                chao.largura, chao.altura,
                (chao.x + chao.largura), chao.y,
                chao.largura, chao.altura,
            );

            contexto.drawImage(
                sprites,
                chao.spriteX, chao.spriteY,
                chao.largura, chao.altura,
                (chao.x + chao.largura + chao.largura), chao.y,
                chao.largura, chao.altura,
            );

            contexto.drawImage(
                sprites,
                chao.spriteX, chao.spriteY,
                chao.largura, chao.altura,
                (chao.x + chao.largura + chao.largura + chao.largura), chao.y,
                chao.largura, chao.altura,
            );
        },
    };
    return chao;
};

function fazColisao(flappyBird, chao){
    const flappyBirdY = flappyBird.y + flappyBird.altura;
    const chaoY = chao.y;

    if(flappyBirdY >= chaoY){
        somHit.play();

        setTimeout(() => {
            
        }, 600);
        
        return true;
    };
    
    return false;

};

function criarFlappyBird(){
    const flappyBird = {
        spriteX: 12,
        spriteY: 12,
        largura: 33,
        altura: 24,
        x: 10,
        y: 50,
        pulo: 4.6,
        
        pula(){
            flappyBird.velocidade = - flappyBird.pulo;  
            somPulo.play()
        },
        
        gravidade : 0.25,
        velocidade : 0,
        
        atualiza() {
            if(fazColisao(flappyBird, globais.chao)){
                mudaParaTela(Telas.GAMEOVER);
                return;
            }
        
            flappyBird.velocidade = flappyBird.velocidade + flappyBird.gravidade;
            flappyBird.y = flappyBird.y + flappyBird.velocidade;
        },

        movimentos: [
            {spriteX: 12, spriteY: 12},
            {spriteX: 12, spriteY: 38},
            {spriteX: 12, spriteY: 64},
            {spriteX: 12, spriteY: 38}
        ],
        frameAtual: 0,

        atualizaOFrameAtual() {
            const intervaloDeFrames = 10;
            const passouOIntervalo = frames % intervaloDeFrames === 0;
        
            if(passouOIntervalo) {
                const baseDeIncremento = 1;
                const incremento = baseDeIncremento + flappyBird.frameAtual;
                const baseRepeticao = flappyBird.movimentos.length;

                flappyBird.frameAtual = incremento % baseRepeticao
            }
        },

        desenha() {
            flappyBird.atualizaOFrameAtual();
            const { spriteX, spriteY } = flappyBird.movimentos[flappyBird.frameAtual];

            contexto.drawImage(
                sprites,
                spriteX, spriteY, // Sprite X, Sprite Y
                flappyBird.largura, flappyBird.altura, // Tamanho do recorte na sprite
                flappyBird.x, flappyBird.y,
                flappyBird.largura, flappyBird.altura,
            );
        }
    }
    return flappyBird;
};


const MensagemGetReady = {
    sX: 165,
    sY: 37,
    largura: 176,
    altura: 156,
    x: (canvas.width / 2) - 176 / 2,
    y: 150,
    desenha() {
        contexto.drawImage(
            sprites,
            MensagemGetReady.sX, MensagemGetReady.sY,
            MensagemGetReady.largura, MensagemGetReady.altura,
            MensagemGetReady.x, MensagemGetReady.y,
            MensagemGetReady.largura, MensagemGetReady.altura
        );
    },
};

const MensagemGameOver = {
    sX: 1017,
    sY: 7,
    largura: 226,
    altura: 200,
    x: (canvas.width / 2) - 226 / 2,
    y: 150,
    desenha() {
        contexto.drawImage(
            sprites,
            MensagemGameOver.sX, MensagemGameOver.sY,
            MensagemGameOver.largura, MensagemGameOver.altura,
            MensagemGameOver.x, MensagemGameOver.y,
            MensagemGameOver.largura, MensagemGameOver.altura
        );
    },
    
};

function criaCanos(){
    const canos = {
        largura: 52,
        altura: 400,
        chao: {
            spriteX: 8,
            spriteY: 192,
        },
        ceu: {
            spriteX: 61, 
            spriteY: 192,
        },
        espaco: 80,
        
        desenha(){
            canos.pares.forEach(function(par){
                const yRandom = par.y;
                const espacamentoEntreCanos = 90;

                const canoCeuX = par.x;
                const canoCeuY = yRandom;

                // cano céu
                contexto.drawImage(
                    sprites,
                    canos.ceu.spriteX, canos.ceu.spriteY,
                    canos.largura, canos.altura,
                    canoCeuX, canoCeuY,
                    canos.largura, canos.altura,
                )
                
                // cano chão
                const canoChaoX = par.x;
                const canoChaoY = canos.altura + espacamentoEntreCanos + yRandom;
                contexto.drawImage(
                    sprites,
                    canos.chao.spriteX, canos.chao.spriteY,
                    canos.largura, canos.altura,
                    canoChaoX, canoChaoY,
                    canos.largura, canos.altura,
                )

                par.canoCeu = {
                    x: canoCeuX,
                    y: canos.altura + canoCeuY
                }

                par.canoChao = {
                    x: canoChaoX,
                    y: canoChaoY
                }
            })
        },
        temColisasaoComOFlappyBird(par){
            const cabecaDoFlappy = globais.flappyBird.y;
            const peDoFlappy = globais.flappyBird.y + globais.flappyBird.altura;

            if((globais.flappyBird.x + globais.flappyBird.largura) >= par.x) {
                if(cabecaDoFlappy <= par.canoCeu.y){
                    return true;
                }

                if(peDoFlappy >= par.canoChao.y){
                    return true;
                }
            }
            return false;
        },
        pares: [],

        atualiza(){
            const passou100Frames = frames % 100 === 0;
            if (passou100Frames){
                canos.pares.push({
                    x: canvas.width,
                    y: -150 * (Math.random() + 1),
                });
            }

            canos.pares.forEach(function(par){
                par.x = par.x - 2;

                if(canos.temColisasaoComOFlappyBird(par)){
                    somHit.play();
                    mudaParaTela(Telas.GAMEOVER);
                }

                if(par.x + canos.largura <= 0){
                    canos.pares.shift();
                }
            });
        }
    }
    return canos;
};

function criarPlacar(){
    const placar = {
        pontuacao: 0,
        desenha(){
            contexto.font = '35px "VT323"';
            contexto.textAlign = 'right';
            contexto.fillStyle = 'white';
            contexto.fillText(`${placar.pontuacao}`, canvas.width - 10, 35)
        },
        atualiza(){
            const intervaloDeFrames = 20;
            const passou100Frames = frames % intervaloDeFrames === 0;

            if(passou100Frames){
                placar.pontuacao = placar.pontuacao + 1;
            }
        }
    }
    return placar;
};

const globais = {};
let TelaAtiva = {};

function mudaParaTela(novaTela){
    TelaAtiva = novaTela;
    if(TelaAtiva.inicializa){
        TelaAtiva.inicializa();
    }
};

const Telas = {
    INICIO: {
        inicializa(){
            globais.flappyBird = criarFlappyBird();
            globais.chao = criarChao();
            globais.canos = criaCanos();
        },
        desenha() {
            planoDeFundo.desenha();
            globais.flappyBird.desenha();
            globais.chao.desenha();
            MensagemGetReady.desenha();
        },
        space(){
            mudaParaTela(Telas.JOGO)
        },
        atualiza(){
            globais.chao.atualiza();
        }
    }
};

Telas.JOGO = {
    inicializa(){
        globais.criarPlacar = criarPlacar()
    },
    desenha(){
        planoDeFundo.desenha();
        globais.canos.desenha();
        globais.chao.desenha();
        globais.flappyBird.desenha();
        globais.criarPlacar.desenha();
    },
    space(){
        globais.flappyBird.pula();
    },
    atualiza(){
        globais.canos.atualiza();
        globais.chao.atualiza();
        globais.flappyBird.atualiza();
        globais.criarPlacar.atualiza();
    }
};

Telas.GAMEOVER = {
    desenha(){
        MensagemGameOver.desenha();
    },
    atualiza(){
        
    },
    click(){
        mudaParaTela(Telas.INICIO);
    }
}

function loop() {
    TelaAtiva.desenha()
    TelaAtiva.atualiza()

    frames = frames + 1;
    requestAnimationFrame(loop);
};

window.addEventListener('keydown', function(e) {
    if(e.keyCode == '32' && TelaAtiva.space){
        TelaAtiva.space();
    };
});

window.addEventListener('click', function(){
    if(TelaAtiva.click){
        TelaAtiva.click();
    }
});

mudaParaTela(Telas.INICIO);
loop();
