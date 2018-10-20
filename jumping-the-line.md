# Jumping the line

## The code

```javascript
var canvasWidth = 680;
var canvasHeight = 580;

var cw = canvasWidth;
var ch = canvasHeight;

function setup() {
  createCanvas(canvasWidth, canvasHeight);
  strokeWeight(5);
}

function draw() {
  background(85, 128, 198);
  drawTriangle();
  drawHexagon();
  fill(85, 128, 198);
  stroke(85, 128, 198);
  rect(
    0.25 * canvasWidth,
    0.75 * canvasHeight,
    0.5 * canvasWidth,
    0.25 * canvasHeight
  );
  stroke(255, 255, 255);
  line(
    0.25 * canvasWidth,
    0.75 * canvasHeight,
    0.75 * canvasWidth,
    0.75 * canvasHeight
  );
  updateTrianglePosition();
  updateHexagonPosition();
}

var speed = 0;
var position = ch;
var hexagonSpeed = 0;
var hexagonPosition = ch / 2;

function updateTrianglePosition() {
  if (position >= ch) {
    speed = -14;
  }

  speed += 0.2;
  position += speed;
}

function updateHexagonPosition() {
  if (hexagonPosition >= ch) {
    hexagonSpeed = -11;
  }

  hexagonSpeed += 0.2;
  hexagonPosition += hexagonSpeed;
}

function drawTriangle() {
  var size = 0.125 * cw;
  var triangleHeight = canvasHeight / 2;
  push();
  fill(0, 0, 0);
  noFill();
  stroke(0, 0, 0);
  translate(canvasWidth / 2, position);
  rotate(frameCount / 50);
  angle0 = 0;
  x0 = size * cos(angle0);
  y0 = size * sin(angle0);
  angle1 = TWO_PI / 3;
  x1 = size * cos(angle1);
  y1 = size * sin(angle1);
  angle2 = (2 * TWO_PI) / 3;
  x2 = size * cos(angle2);
  y2 = size * sin(angle2);
  triangle(x0, y0, x1, y1, x2, y2);
  pop();
}

function drawHexagon() {
  push();
  translate(cw / 2, hexagonPosition);
  fill(255, 255, 255);
  noFill();
  rotate(frameCount / 50);
  beginShape();
  const size = 0.125 * cw;
  for (var i = 0; i <= 6; i++) {
    var angle = (i * 2 * Math.PI) / 6;
    var x = size * cos(angle);
    var y = size * sin(angle);
    vertex(x, y);
  }
  endShape();
  pop();
}
```

## My attempt

![My attempt](/images/jumping-the-line.gif)
