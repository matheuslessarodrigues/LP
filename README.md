# lessa.codes/LP
Scripts feitos em LP 1003

## Avaliações
- B3
  - ~~[AV2](b3-av2.md)~~
  - ~~[AV3](b3-av3.md)~~
- B4
  - ~~[AV1](b4-av1.md)~~
  - [AV2](b4-av2.md)

## Conceitos Bacanas

### html
Conteúdo do site. Desde textos e imagens até códigos

### javascript
Linguagem de programação que a gente usa.

Com ela é possível executar códigos pelo navegador.

### canvas
Onde a gente desenha. A tela do pintor.

Exemplo:
```html
<canvas id="meuCanvas" width="800" height="600"></canvas>
<script>
var canvas = document.getElementById("meuCanvas");
// outros códigos vão aqui
</script>
```

### context
O carinha que desenha!

Exemplo:
```javascript
var context = canvas.getContext("2d");
```

### fillRect
O DESENHO!

Exemplo:
```javascript
context.fillRect(posicaoX, posicaoY, largura, altura);
// Lembrando que a posição (0,0) começa no canto *superior esquerdo* da tela.
```
Exemplo completo com outras formas básicas [aqui](https://github.com/matheuslessarodrigues/LP/blob/master/desenhos-base.html)

### fillStyle
A cor do desenho

Exemplo:
```javascript
context.fillStyle = "red"; // a partir dessa linha, todos os desenhos são vermelhos
// Lembrando que o fillStyle apenas surte efeitos nos comandos de desenho que vêm *depois* dele.
```

### variável
Uma _caixa_ onde você pode guardar _valores_

Exemplo:
```javascript
var nomeDaVariavel = "texto"; // o "var" indica que estamos criando a variável
var outraVariavel = 42;
context.fillRect( outraVariavel, 0, 50, 50 ); // apenas escrever o nome da variável faz a gente usar seu valor
```

### prompt
Pegar valores do usuário

Exemplo:
```javascript
var minhaVariavel = parseInt( prompt( "texto que mostra pro usuario" ) ); // aparecerá uma caixa pro usuário escrever um valor
// minhaVariavel agora tem o valor que o usuário escreveu
```

### animação
Estrutura base para fazer desenhos animados com javascript
```html
<canvas id="meuCanvas" width="800" height="600"></canvas>
<script>
var canvas = document.getElementById("meuCanvas");
var context = canvas.getContext("2d");

// declaração de variáveis ficam aqui
var x = 0;

function draw() {
  // limpa o canvas  
  context.clearRect(0,0,800,600);

  // desenha um quadrado na posição determinada pela variável x
  context.fillRect(x, 50, 100,100);
  
  // "move o quadrado para a direita"
  x = x + 1;

  // prepara pra desenhar novamente
  requestAnimationFrame(draw);
}
draw();
</script>
```
Exemplo completo [aqui](https://github.com/matheuslessarodrigues/LP/blob/master/animation.html).

### condições `if`
Controla o fluxo do programa. O código dentro das chaves `{}` apenas é executado caso a condição dentro do `if` ser verdadeira.

Exemplo:
```javascript
var num = parseInt(prompt("Escreve um número aí")); // pega um número do usuário
if( num < 100 )
{
  // apenas desenha o retângulo se o número
  // que o usuário escrever for menor que 100
  context.fillRect(50, 50, 100,100);
}
else
{
  // esse trecho de código executa apenas
  // quando a condição for falsa
}
```

#### tipos de condição

- Igual a `==`
```javascript
if( x == 3 )
{
  // executa aqui quando x é igual 3
}
```

- Maior que `>`
```javascript
if( x > 3 )
{
  // executa aqui quando x é maior que 3
}
```

- Maior ou igual a `>=`
```javascript
if( x >= 3 )
{
  // executa aqui quando x é maior ou igual a 3
}
```

- Menor que `<=`
```javascript
if( x <= 3 )
{
  // executa aqui quando x é menor ou igual a 3
}
```

### input de teclado

Código pra pegar eventos do teclado. Sobre os parâmetros de `addEventListener`: `"keydown"` significa executar código quando uma tecla é pressionada (também pode usar `"keyup"` pra saber quando soltam uma tecla); `onKeyDown` é o bloco de código definido por você que é executado quando o evento acontece (uma tecla é pressionada).

**IMPORTANTE**

Esses códigos ficam *antes* do `function draw()`.

```javascript
window.addEventListener( "keydown", onKeyDown, true );

function onKeyDown( e )
{
  // Todo esse código entre chaves executa quando apertam uma tecla
  
  if( e.keyCode == 65 ) // Testa se o cara especificamente apertou a tecla 'A'
  {
    alert( "apertou a tecla 'A'" );
  }
  else if( e.keyCode == 66 ) // Testa se outra tecla foi pressionada
  {
    alert( "apertou outra tecla 'B'" );
  }
}
```

Exemplo completo [aqui](https://github.com/matheuslessarodrigues/LP/blob/master/input.html).

Alguns códigos de input:
- `setinha pra esquerda`: `event.keyCode == 37`
- `setinha pra cima`: `event.keyCode == 38`
- `setinha pra direita`: `event.keyCode == 39`
- `setinha pra baixo`: `event.keyCode == 40`
- `A`: `65`
- `B`: `66`
- `C`: `67`
- etc

Site pra descobrir qualquer _keycode_: [keycode.info](http://keycode.info/)

### imagens

Para desenhar imagens, chamamos a função `context.drawImage(imagem, posicaoX, posicaoY)`:
```javascript
context.drawImage(minhaImagem, 30, 50);
```

Nesse caso, `minhaImagem` é uma veriável que representa a imagem que estamos desenhando.
Para o programa saber qual imagem desenhar, nós a carregamos uma vez no código, assim:
```javascript
var minhaImagem = new Image();
minhaImagem.src = "imagens/uma_imagem_qualquer.png";
```

Repare que ali estamos carregando uma imagem chamada `uma_imagem_qualquer.png` que se encontra dentro da pasta `imagens`. Importante
reparar que essa pasta `imagens` é relativa a onde está seu arquivo html. Ou seja, a pasta deve estar ao lado de seu arquivo html.
Então, se você mover essa imagem para outro lugar, lembre-s de atualizar o código para o programa continuar sabendo onde ela está.

Exemplo completo [aqui](https://github.com/matheuslessarodrigues/LP/blob/master/imagem.html).

### funções

Uma função é um código que pode ser repetido quando quisermos. É comparável a um vídeo onde gravamos algo que aconteceu uma vez e,
depois, podemos dar play quantas vezes quisermos.

Exemplo:
```javascript
// Declaração da função (assim como variável, funções precisam ser declaradas)
// Isso aqui é equivalente ao "gravar um vídeo"
function desenhaRetangulo()
{
  context.fillRect( 10, 10, 80, 80 );
  // podem ter mais códigos aqui também
}

// Aqui é onde a gente chama a função e todo o código que estava dentro dela
// é executado como se fosse copiar e colar
// Isso aqui é equivalente ao "dar play em um vídeo"
desenhaRetangulo();
```

Funções podem também receber valores para que, cada vez que for chamada, fazer algo um pouquinho diferente.

Exemplo:
```javascript
// Agora, onde o retângulo aparece depende do valor que passamos pra nossa função
function desenhaRetangulo( posicaoX, posicaoY )
{
  context.fillRect( posicaoX, posicaoY, 80, 80 );
}

// Aqui são duas chamadas à mesma função. Porém, cada chamada irá desenhar o
// retângulo em posições diferentes porque estamos passando valores diferentes!
desenhaRetangulo( 0, 0 );
desenhaRetangulo( 100, 75 );
```

Se você reparar bem, poderá ver que já vimos funções anteriormente. Afinal, nosso código de desenhar _coisas_
no canvas **é uma função**!

### se organizando pra fazer um jogo (SHAZAM!)

Até agora vimos códigos simples de javascript. Aí, quando partirmos para fazer um jogo, a coisa pode sair de
controle se a gente não tomar cuidado. Um código mal organizado pode dificultar (muito) achar bug ou fazer
alterações.

Por isso, aqui vai uma sugestão de como organizar tudinho e não se perder quando estiver fazendo seu jogo em
javascript: [CÓDIGO BASE PRA FAZER UM JOGO](https://github.com/matheuslessarodrigues/LP/blob/master/game.html).

**IMPORTANTE**

Não se esqueça que um jogo envolve imagens (pra ficar bonito né). Então esteja certo de que está baixando também
a pasta com as imagens do jogo!

### random!

Quando queremos coisas aleatórias em nosso programa, usamos a função `Math.random()`. Ela dá pra gente um valor entre
`0.0` e `1.0`. Se chamarmos essa função várias vezes seguidas, ela sempre terá um valor diferente (entre `0.0` e `1.0`).

Exemplo:
```javascript
var posicaoX = Mathf.random(); // posicaoX varia entre 0.0 e 1.0
context.fillRect( posicaoX, 100, 80, 80 );
```

Nesse exemplo, cada vez que abrirmos nosso html, o retângulo estará em um lugar diferente, **porém a diferença entre
posições será tão pequena que é imperceptível**. Por causa disso, geralmente multiplicamos o resultado de `Math.random()`
pelo intervalo desejado.

Exemplo:
```javascript
var posicaoX = 100 * Mathf.random(); // posicaoX varia entre 0.0 e 100.0!!
context.fillRect( posicaoX, 100, 80, 80 );
```

Agora a posição de nosso retângulo fica entre `0.0` e `100.0`. Por fim, se quisermos que o valor aleatório comece em um valor
maior que zero, fazemos uma adição.

Exemplo:
```javascript
var posicaoX = 100 * Mathf.random() + 50; // posicaoX varia entre 50.0 e 150.0!!
context.fillRect( posicaoX, 100, 80, 80 );
```

Podemos inclusive fazer uma função pra facilitar nossa vida:
```javascript
function rand(min, max)
{
  return Math.random() * (max - min) + min;
}
```

E então podemos utilizá-la dessa forma:
```javascript
var posicaoX = rand(50, 100); // posicaoX varia entre 50.0 e 100.0!!
context.fillRect( posicaoX, 100, 80, 80 );
```
