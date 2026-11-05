# HIERONDER MIJN CODE

let flower1;
let flower2;
let flower3;
let water;

let garden;

let flowerY = 200;

async function setup() {
  // Load the image files.
  flower1 = await loadImage("flower-1.png");
  flower2 = await loadImage("flower-2.png");
  flower3 = await loadImage("flower-3.png");
  water = await loadImage("Water.gif");

  createCanvas(400,400);

  garden = createGraphics(400, 400);

  imageMode(CENTER);

  flower1.resize(100, 100);
  flower2.resize(100, 100);
  flower3.resize(100, 100);

  water.resize(50, 50);

  water.pause();
}

function draw() {
  background(255);
  drawStems();

  image(garden, width / 2, height / 2);

  image(water, mouseX, mouseY);

if (mouseIsPressed) {
  paintFlower(flower1, 50, 100);
  paintFlower(flower2, 150, 100);
  paintFlower(flower3, 250, 100);
}
}

function paintFlower(img, x, y) {
  let sourceX = random(0, img.width)
  let sourceY = random(0, img.height);
  let c = img.get(sourceX, sourceY);
 
  garden.stroke(c);
  garden.strokeWeight(random(5, 10));
  garden.point(sourceX + x, sourceY + y);
}

function mousePressed() {
  water.play();
}
function mouseReleased() {
  water.reset();
  water.pause();
}

function drawStems() {
  stroke("brown");
  strokeWeight(3);
  line(100, 400, 100, flowerY);
  line(200, 400, 200, flowerY);
  line(300, 400, 300, flowerY);
}

function keyPressed() {

  if (key === "s") {
    saveGif('garden', 5);
  }

  garden.clear();
}