# projeto-java-ana-limao
let objeto;
let padrao;
let fonte;
let pontos;
let pts;
let pbs;
let tempo = 0;
let imagem;

function preload(){
  fonte = loadFont('roch.ttf');
  objeto = loadModel('teste.stl.obj', true);
  padrao = loadImage('Capturar.PNG');
  carn = loadImage('carnaval.jpg');
  curso = loadImage('curso.png');
  ciclismo = loadImage('ciclismo.jpg');
}

function setup() {
  createCanvas(848, 1200, WEBGL);
  image(curso,-450,-600,848,400);
  image(carn,-450,-200,848,400);
  image(ciclismo,-450,200,848,400);
  
  textFont(fonte);
  textSize(100);
  fill('#1B81C4');
  
  text("ESAD.TV", -400, -370);

  pts = fonte.textToPoints(
    "ESAD.TV", -400, -370);
  
  fill('#E61F2A');
  text("carnaval", -25, 10);

  pontos = fonte.textToPoints(
    "carnaval", -25,10);
  
  fill('#D2A835');
  text("ciclismo", -400,450);

  pbs = fonte.textToPoints(
    "ciclismo", -400,450
  );
}

function draw() {
  
  
  
  glitch();
  text("ESAD.TV", -400, -370);
  textESAD();
  text("carnaval", -25, 10);
  textCiclismo();
    text("ciclismo", -400,450);
  textCarnaval();
  
}

function textESAD() {
  push();
  stroke('#1B81C4');
  for (let pt of pts) {
    circle(pt.x, pt.y, 0.3);
    pt.x += random(2, -1);
    pt.y += random(1, -1);
  }
  pop();
}

function textCarnaval() {
  push();
  stroke('red');
  for (let ponto of pontos) {
    circle(ponto.x, ponto.y, 0.3);
    ponto.x += random(-2, 1);
    ponto.y += random(-1,1);
  }
  pop();
}

function textCiclismo() {
  push();
  stroke('yellow');
  for (let pb of pbs) {
    circle(pb.x, pb.y, 0.3);
    pb.x += random(2, -1);
    pb.y += random(1, -1);
  }
  pop();
}

//glitch
function glitch(){
  push();
  const img1 = get(random(600),random(800),80,80);
  image(img1, random(width) -width/2, random(height)-height/2);
  pop();
}

//cubo
function cena1(){
  push();
  background('black');
  
  rotateX(0.01*frameCount);
  rotateY(0.01*frameCount);
  
  fill(255);
  noStroke();
  texture(padrao);
  box(250);
  pop();
}

function cena2(){
  push();
  background('black');
  
  fill('#D2A835');
  text("É neste curso", -400, -370);
  
  fill('white');
  text("Que o teu", -25, 10);
  
  fill('#1B81C4');
  text("Futuro começa!", -400,450);
  pop();
}
