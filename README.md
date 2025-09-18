<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cutie😻</title>
    <link rel="shortcut icon" href="./icon.png" type="image/x-icon">
    <link rel="stylesheet" href="main.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap" rel="stylesheet">
</head>
<body>
    <div id="drag-container">
        <div id="spin-container">
            <img src="./images/1.jpg" alt="">
            <img src="./images/2.jpg" alt="">
            <img src="./images/3.jpg" alt="">
            <img src="./images/4.jpg" alt="">
            <img src="./images/5.jpg" alt="">
            <img src="./images/6.jpg" alt="">
            <img src="./images/7.jpg" alt="">
            <img src="./images/8.jpg" alt="">
            <img src="./images/9.jpg" alt="">
            <p>Happy Birthday Dear</p>
        </div>
        <div id="ground"></div>
    </div>
    
    <div id="music-container"></div>
    <!-- <div id="canva">
        <canvas id="canvas"></canvas>
    </div> -->

    <!-- Audio tự động phát -->
    <audio id="myAudio" autoplay playsinline>
        <source src="music/setlove.mp3" type="audio/mpeg">
        <source src="music/setlove.ogg" type="audio/ogg">
    </audio>

    <script src="main.js"></script>

    <script>
        window.onload = function() {
            var audio = document.getElementById("myAudio");
            audio.muted = false;
            audio.play().catch(function(e) {
                console.log('Audio playback failed:', e);
            });

            // Hiệu ứng pháo hoa và trái tim
            const canvas = document.getElementById("canvas");
            const ctx = canvas.getContext("2d");
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;

            function random(min, max) {
                return Math.random() * (max - min) + min;
            }

            function Firework(x, y) {
                this.x = x;
                this.y = y;
                this.radius = random(2, 4);
                this.color = `hsl(${random(0, 360)}, 100%, 50%)`;
                this.vx = random(-3, 3);
                this.vy = random(-3, 3);
                this.life = 100;
            }

            Firework.prototype.draw = function () {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            };

            Firework.prototype.update = function () {
                this.x += this.vx;
                this.y += this.vy;
                this.life--;
            };

            function Heart(x, y) {
                this.x = x;
                this.y = y;
                this.size = random(20, 40);
                this.color = 'red';
                this.vy = random(-2, -1);
                this.opacity = 1;
            }

            Heart.prototype.draw = function () {
                ctx.beginPath();
                ctx.moveTo(this.x, this.y);
                ctx.bezierCurveTo(this.x - this.size / 2, this.y - this.size / 2, this.x - this.size, this.y + this.size / 3, this.x, this.y + this.size);
                ctx.bezierCurveTo(this.x + this.size, this.y + this.size / 3, this.x + this.size / 2, this.y - this.size / 2, this.x, this.y);
                ctx.fillStyle = this.color;
                ctx.globalAlpha = this.opacity;
                ctx.fill();
                ctx.globalAlpha = 1;
            };

            Heart.prototype.update = function () {
                this.y += this.vy;
                this.opacity -= 0.01;
            };

            let fireworks = [];
            let hearts = [];

            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                if (Math.random() < 0.1) {
                    fireworks.push(new Firework(random(0, canvas.width), random(0, canvas.height)));
                }
                if (Math.random() < 0.05) {
                    hearts.push(new Heart(random(0, canvas.width), canvas.height));
                }

                fireworks.forEach((firework, index) => {
                    firework.draw();
                    firework.update();
                    if (firework.life <= 0) {
                        fireworks.splice(index, 1);
                    }
                });

                hearts.forEach((heart, index) => {
                    heart.draw();
                    heart.update();
                    if (heart.opacity <= 0) {
                        hearts.splice(index, 1);
                    }
                });

                requestAnimationFrame(animate);
            }
            animate();
        };
    </script>
</body>
</html>

@import url('https://fonts.googleapis.com/css2?family=Amita:wght@400;700&family=Archivo:ital,wght@0,100..900;1,100..900&family=Bilbo+Swash+Caps&family=Inter:opsz,wght@14..32,500&family=Noto+Serif:ital,wght@0,100..900;1,100..900&family=Pacifico&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Tiro+Devanagari+Marathi:ital@0;1&display=swap');

* {
    margin: 0;
    padding: 0;
  }
  
  html,
  body {
    height: 100%;
    /* for touch screen */
    touch-action: none; 
  }
  
  body {
    overflow: hidden;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    font-family: "Pacifico", sans-serif;
    background: #ffffff;
    -webkit-perspective: 1000px;
            perspective: 1000px;
    -webkit-transform-style: preserve-3d;
            transform-style: preserve-3d;
  }
  
  #drag-container, #spin-container {
    position: relative;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    margin: auto;
    -webkit-transform-style: preserve-3d;
            transform-style: preserve-3d;
    -webkit-transform: rotateX(-10deg);
            transform: rotateX(-10deg);
            z-index: 100;
  }
  
  #drag-container img, #drag-container video {
    -webkit-transform-style: preserve-3d;
            transform-style: preserve-3d;
    position: absolute;
    left: 0;
    top: 0;
    max-width: 120%;
    max-height: 120%; 
    line-height: 200px;
    font-size: 50px;
    text-align: center;
    -webkit-box-shadow: 0 0 8px #fff;
            box-shadow: 0 0 8px #fff;
    -webkit-box-reflect: below 10px linear-gradient(transparent, transparent, #0005);
  }
  
  #drag-container img:hover, #drag-container video:hover {
    -webkit-box-shadow: 0 0 15px #fffd;
            box-shadow: 0 0 15px #fffd;
    -webkit-box-reflect: below 10px linear-gradient(transparent, transparent, #0007);
  }
  
  #drag-container p {
    
    position: absolute;
    top: 100%;
    left: 50%;
    -webkit-transform: translate(-50%,-50%) rotateX(90deg);
            transform: translate(-50%,-50%) rotateX(90deg);
    color: rgb(0, 195, 255);
    animation: fadein ease 15s;
  }

  @keyframes fadein {
      from {
          opacity:0;
          
      }
      to {
          opacity: 1;
          
      }
  }
  
  #ground {
    width: 900px;
    height: 900px;
    position: absolute;
    top: 100%;
    left: 50%;
    -webkit-transform: translate(-50%,-50%) rotateX(90deg);
            transform: translate(-50%,-50%) rotateX(90deg);
    background: -webkit-radial-gradient(center center, farthest-side , #9993, transparent);
  }
  
  #music-container {
    position: absolute;
    top: 0;
    left: 0;
    display: none;
  }
  
  @-webkit-keyframes spin {
    from{
      -webkit-transform: rotateY(0deg);
              transform: rotateY(0deg);
    } to{
      -webkit-transform: rotateY(360deg);
              transform: rotateY(360deg);
    }
  }
  
  @keyframes spin {
    from{
      -webkit-transform: rotateY(0deg);
              transform: rotateY(0deg);
    } to{
      -webkit-transform: rotateY(360deg);
              transform: rotateY(360deg);
    }
  }
  @-webkit-keyframes spinRevert {
    from{
      -webkit-transform: rotateY(360deg);
              transform: rotateY(360deg);
    } to{
      -webkit-transform: rotateY(0deg);
              transform: rotateY(0deg);
    }
  }
  @keyframes spinRevert {
    from{
      -webkit-transform: rotateY(360deg);
              transform: rotateY(360deg);
    } to{
      -webkit-transform: rotateY(0deg);
              transform: rotateY(0deg);
    }
  }

  #canvas {
    background-color:transparent;   
    color: transparent; 
    margin: 0;
    overflow: hidden;
    background-repeat: no-repeat;
    width: 100vw;
  }


#canva {
    position: absolute;
    top: 0px;
    right: 0px;
    overflow: hidden;
}

p {
    font-weight: 600;
    font-size: 4vw;
    text-align: center;
    
}

@media screen and (max-width: 658px)    {
  p {
    font-weight: 600;
    font-size: 12vw;
    text-align: center;
}
}

// You can change global variables here:
var radius = 240; // how big of the radius
var autoRotate = true; // auto rotate or not
var rotateSpeed = -60; // unit: seconds/360 degrees
var imgWidth = 120; // width of images (unit: px)
var imgHeight = 170; // height of images (unit: px)

// Link of background music - set 'null' if you dont want to play background music
var bgMusicURL = 'https://api.soundcloud.com/tracks/143041228/stream?client_id=587aa2d384f7333a886010d5f52f302a';
var bgMusicControls = true; // Show UI music control



// ===================== start =======================
// animation start after 1000 miliseconds
setTimeout(init, 1000);

var odrag = document.getElementById('drag-container');
var ospin = document.getElementById('spin-container');
var aImg = ospin.getElementsByTagName('img');
var aVid = ospin.getElementsByTagName('video');
var aEle = [...aImg, ...aVid]; // combine 2 arrays

// Size of images
ospin.style.width = imgWidth + "px";
ospin.style.height = imgHeight + "px";

// Size of ground - depend on radius
var ground = document.getElementById('ground');
ground.style.width = radius * 3 + "px";
ground.style.height = radius * 3 + "px";

function init(delayTime) {
  for (var i = 0; i < aEle.length; i++) {
    aEle[i].style.transform = "rotateY(" + (i * (360 / aEle.length)) + "deg) translateZ(" + radius + "px)";
    aEle[i].style.transition = "transform 1s";
    aEle[i].style.transitionDelay = delayTime || (aEle.length - i) / 4 + "s";
  }
}

function applyTranform(obj) {
  // Constrain the angle of camera (between 0 and 180)
  if(tY > 180) tY = 180;
  if(tY < 0) tY = 0;

  // Apply the angle
  obj.style.transform = "rotateX(" + (-tY) + "deg) rotateY(" + (tX) + "deg)";
}

function playSpin(yes) {
  ospin.style.animationPlayState = (yes?'running':'paused');
}

var sX, sY, nX, nY, desX = 0,
    desY = 0,
    tX = 0,
    tY = 10;

// auto spin
if (autoRotate) {
  var animationName = (rotateSpeed > 0 ? 'spin' : 'spinRevert');
  ospin.style.animation = `${animationName} ${Math.abs(rotateSpeed)}s infinite linear`;
}

// add background music
if (bgMusicURL) {
  document.getElementById('music-container').innerHTML += `
<audio src="${bgMusicURL}" ${bgMusicControls? 'controls': ''} autoplay loop>    
<p>If you are reading this, it is because your browser does not support the audio element.</p>
</audio>
`;
}

// setup events
document.onpointerdown = function (e) {
  clearInterval(odrag.timer);
  e = e || window.event;
  var sX = e.clientX,
      sY = e.clientY;

  this.onpointermove = function (e) {
    e = e || window.event;
    var nX = e.clientX,
        nY = e.clientY;
    desX = nX - sX;
    desY = nY - sY;
    tX += desX * 0.1;
    tY += desY * 0.1;
    applyTranform(odrag);
    sX = nX;
    sY = nY;
  };

  this.onpointerup = function (e) {
    odrag.timer = setInterval(function () {
      desX *= 0.95;
      desY *= 0.95;
      tX += desX * 0.1;
      tY += desY * 0.1;
      applyTranform(odrag);
      playSpin(false);
      if (Math.abs(desX) < 0.5 && Math.abs(desY) < 0.5) {
        clearInterval(odrag.timer);
        playSpin(true);
      }
    }, 17);
    this.onpointermove = this.onpointerup = null;
  };

  return false;
};

document.onmousewheel = function(e) {
  e = e || window.event;
  var d = e.wheelDelta / 20 || -e.detail;
  radius += d;
  init(1);
};



















var canvas = document.getElementById("canvas");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

// Initialize the GL context
var gl = canvas.getContext('webgl');
if(!gl){
  console.error("Unable to initialize WebGL.");
}

//Time
var time = 0.0;

//************** Shader sources **************

var vertexSource = `
attribute vec2 position;
void main() {
	gl_Position = vec4(position, 0.0, 1.0);
}
`;

var fragmentSource = `
precision highp float;

uniform float width;
uniform float height;
vec2 resolution = vec2(width, height);

uniform float time;

#define POINT_COUNT 8

vec2 points[POINT_COUNT];
const float speed = -0.5;
const float len = 0.25;
float intensity = 1.3;
float radius = 0.008;

//https://www.shadertoy.com/view/MlKcDD
//Signed distance to a quadratic bezier
float sdBezier(vec2 pos, vec2 A, vec2 B, vec2 C){    
	vec2 a = B - A;
	vec2 b = A - 2.0*B + C;
	vec2 c = a * 2.0;
	vec2 d = A - pos;

	float kk = 1.0 / dot(b,b);
	float kx = kk * dot(a,b);
	float ky = kk * (2.0*dot(a,a)+dot(d,b)) / 3.0;
	float kz = kk * dot(d,a);      

	float res = 0.0;

	float p = ky - kx*kx;
	float p3 = p*p*p;
	float q = kx*(2.0*kx*kx - 3.0*ky) + kz;
	float h = q*q + 4.0*p3;

	if(h >= 0.0){ 
		h = sqrt(h);
		vec2 x = (vec2(h, -h) - q) / 2.0;
		vec2 uv = sign(x)*pow(abs(x), vec2(1.0/3.0));
		float t = uv.x + uv.y - kx;
		t = clamp( t, 0.0, 1.0 );

		// 1 root
		vec2 qos = d + (c + b*t)*t;
		res = length(qos);
	}else{
		float z = sqrt(-p);
		float v = acos( q/(p*z*2.0) ) / 3.0;
		float m = cos(v);
		float n = sin(v)*1.732050808;
		vec3 t = vec3(m + m, -n - m, n - m) * z - kx;
		t = clamp( t, 0.0, 1.0 );

		// 3 roots
		vec2 qos = d + (c + b*t.x)*t.x;
		float dis = dot(qos,qos);
        
		res = dis;

		qos = d + (c + b*t.y)*t.y;
		dis = dot(qos,qos);
		res = min(res,dis);
		
		qos = d + (c + b*t.z)*t.z;
		dis = dot(qos,qos);
		res = min(res,dis);

		res = sqrt( res );
	}
    
	return res;
}


//http://mathworld.wolfram.com/HeartCurve.html
vec2 getHeartPosition(float t){
	return vec2(16.0 * sin(t) * sin(t) * sin(t),
							-(13.0 * cos(t) - 5.0 * cos(2.0*t)
							- 2.0 * cos(3.0*t) - cos(4.0*t)));
}

//https://www.shadertoy.com/view/3s3GDn
float getGlow(float dist, float radius, float intensity){
	return pow(radius/dist, intensity);
}

float getSegment(float t, vec2 pos, float offset, float scale){
	for(int i = 0; i < POINT_COUNT; i++){
		points[i] = getHeartPosition(offset + float(i)*len + fract(speed * t) * 6.28);
	}
    
	vec2 c = (points[0] + points[1]) / 2.0;
	vec2 c_prev;
	float dist = 10000.0;
    
	for(int i = 0; i < POINT_COUNT-1; i++){
		//https://tinyurl.com/y2htbwkm
		c_prev = c;
		c = (points[i] + points[i+1]) / 2.0;
		dist = min(dist, sdBezier(pos, scale * c_prev, scale * points[i], scale * c));
	}
	return max(0.0, dist);
}

void main(){
	vec2 uv = gl_FragCoord.xy/resolution.xy;
	float widthHeightRatio = resolution.x/resolution.y;
	vec2 centre = vec2(0.5, 0.5);
	vec2 pos = centre - uv;
	pos.y /= widthHeightRatio;
	//Shift upwards to centre heart
	pos.y += 0.02;
	float scale = 0.000015 * height;
	
	float t = time;
    
	//Get first segment
  float dist = getSegment(t, pos, 0.0, scale);
  float glow = getGlow(dist, radius, intensity);
  
  vec3 col = vec3(0.0);

	//White core
  col += 10.0*vec3(smoothstep(0.003, 0.001, dist));
  //Pink glow
  col += glow * vec3(1.0,0.05,0.3);
  
  //Get second segment
  dist = getSegment(t, pos, 3.4, scale);
  glow = getGlow(dist, radius, intensity);
  
  //White core
  col += 10.0*vec3(smoothstep(0.003, 0.001, dist));
  //Blue glow
  col += glow * vec3(0.1,0.4,1.0);
        
	//Tone mapping
	col = 1.0 - exp(-col);

	//Gamma
	col = pow(col, vec3(0.4545));

	//Output to screen
 	gl_FragColor = vec4(col,1.0);
}
`;

//************** Utility functions **************

window.addEventListener('resize', onWindowResize, false);

function onWindowResize(){
  canvas.width  = window.innerWidth;
  canvas.height = window.innerHeight;
	gl.viewport(0, 0, canvas.width, canvas.height);
  gl.uniform1f(widthHandle, window.innerWidth);
  gl.uniform1f(heightHandle, window.innerHeight);
}


//Compile shader and combine with source
function compileShader(shaderSource, shaderType){
  var shader = gl.createShader(shaderType);
  gl.shaderSource(shader, shaderSource);
  gl.compileShader(shader);
  if(!gl.getShaderParameter(shader, gl.COMPILE_STATUS)){
  	throw "Shader compile failed with: " + gl.getShaderInfoLog(shader);
  }
  return shader;
}

//From https://codepen.io/jlfwong/pen/GqmroZ
//Utility to complain loudly if we fail to find the attribute/uniform
function getAttribLocation(program, name) {
  var attributeLocation = gl.getAttribLocation(program, name);
  if (attributeLocation === -1) {
  	throw 'Cannot find attribute ' + name + '.';
  }
  return attributeLocation;
}

function getUniformLocation(program, name) {
  var attributeLocation = gl.getUniformLocation(program, name);
  if (attributeLocation === -1) {
  	throw 'Cannot find uniform ' + name + '.';
  }
  return attributeLocation;
}

//************** Create shaders **************

//Create vertex and fragment shaders
var vertexShader = compileShader(vertexSource, gl.VERTEX_SHADER);
var fragmentShader = compileShader(fragmentSource, gl.FRAGMENT_SHADER);

//Create shader programs
var program = gl.createProgram();
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);
gl.linkProgram(program);

gl.useProgram(program);

//Set up rectangle covering entire canvas 
var vertexData = new Float32Array([
  -1.0,  1.0, 	// top left
  -1.0, -1.0, 	// bottom left
   1.0,  1.0, 	// top right
   1.0, -1.0, 	// bottom right
]);

//Create vertex buffer
var vertexDataBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, vertexDataBuffer);
gl.bufferData(gl.ARRAY_BUFFER, vertexData, gl.STATIC_DRAW);

// Layout of our data in the vertex buffer
var positionHandle = getAttribLocation(program, 'position');

gl.enableVertexAttribArray(positionHandle);
gl.vertexAttribPointer(positionHandle,
  2, 				// position is a vec2 (2 values per component)
  gl.FLOAT, // each component is a float
  false, 		// don't normalize values
  2 * 4, 		// two 4 byte float components per vertex (32 bit float is 4 bytes)
  0 				// how many bytes inside the buffer to start from
  );

//Set uniform handle
var timeHandle = getUniformLocation(program, 'time');
var widthHandle = getUniformLocation(program, 'width');
var heightHandle = getUniformLocation(program, 'height');

gl.uniform1f(widthHandle, window.innerWidth);
gl.uniform1f(heightHandle, window.innerHeight);

var lastFrame = Date.now();
var thisFrame;

function draw(){
	
  //Update time
	thisFrame = Date.now();
  time += (thisFrame - lastFrame)/1000;	
	lastFrame = thisFrame;

	//Send uniforms to program
  gl.uniform1f(timeHandle, time);
  //Draw a triangle strip connecting vertices 0-4
  gl.drawArrays(gl.TRIANGLE_STRIP, 0, 4);

  requestAnimationFrame(draw);
}

draw();



<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <meta content="width=device-width, initial-scale=1, user-scalable=1, minimum-scale=1, maximum-scale=5" name="viewport" />
  <meta content="IE=edge" http-equiv="X-UA-Compatible" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Shippori+Antique:wght@400;700&display=swap" rel="stylesheet" />
  <link href="https://fonts.googleapis.com/css2?family=Dancing+Script&display=swap" rel="stylesheet" />
  <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11.0.19/dist/sweetalert2.all.min.js"></script>
  <link rel="stylesheet" href="./style.css">
  <script src="https://unpkg.com/typeit@8.7.0/dist/index.umd.js"></script>

  <!-- Update title and description for a birthday theme -->
  <title>BIRTHDAY.</title>
  <link rel="icon" type="image/x-icon" href="https://www.palingit.com/favicon.ico" />
  <meta name="description" content="A special birthday greeting" />
</head>

<body style="background: linear-gradient(to bottom, #ffe1e1, #ff217de0), url(./r.jpg);
    height: 100vh;">
  <audio src="./y2mate (mp3cut.net).mp3" id="linkmp3" class="sembunyi"></audio>

  <div id="bodyblur">
    <!-- Wallpaper -->
    <img src="love/wall.jpg" id="wallpaper" />
  </div>

  <div id="Content">
    <div id="kadoIn">
      <!-- Gift Button -->
      <img src="./Valentine-Surprise.png" alt="Open Gift Button" />
    </div>
    <p id="ket">
      <span style="font-style: italic; color: rgb(0,0,0); margin-top: 3px !important; ">Open the gift, cutie:3</span>
    </p>

    <div class="kumpulanstiker" style="margin-top: 95px;">
      <!-- Stickers for Content -->
      <img src="https://media.tenor.com/4Ijycn6xFzUAAAAj/mochi-blue-roses.gif" id="fotostiker" />
      <img src="https://feeldreams.github.io/bunga.gif" id="fotostiker1" />
      <img src="https://feeldreams.github.io/pandacoklat.gif" id="fotostiker2" />
      <img src="https://media.tenor.com/snFoLI-S9CQAAAAj/milk-and-mocha.gif" id="fotostiker3" />
      <img src="https://feeldreams.github.io/emawh.gif" id="fotostiker4" />
      <img src="https://feeldreams.github.io/pandacoklat.gif" id="fotostiker5" />
    </div>

    <p id="halo" class="halo"></p>

    <div>
      <blockquote id="bq" data-text="💞">
        <!-- Update the messages for a birthday greeting -->
        <p id="kalimat">
          Happy Birthday, gorgeous! Today is all about celebrating you.
        </p>

        <!-- Message -->
        <p id="pesan1">Tap here for your birthday surprise! 🎉</p>
        <div id="kolombaru">
          <li id="lv1">🎂</li>
          <li id="lv2">🎁</li>
          <li id="lv3">🥳</li>
          <li id="lv4">💖</li>
        </div>

        <p id="pesan2">You shine brighter every year! ✨</p>
        <p id="pesan3">Do you know what makes today extra special?</p>
        <p id="pesan4" class="sty2">It’s your birthday!</p>
        <p id="pesan5" class="sty2">
          Today, I wish you a year filled with laughter, love, and unforgettable moments.
        </p>
        <p id="pesan6" class="sty2">
          Remember, you deserve every happiness in the world. Celebrate big and enjoy every moment!
        </p>

        <!-- Next Button -->
        <p id="opsL">Tap to continue the celebration!</p>
      </blockquote>
    </div>

    <!-- Send Message Button -->
    <div id="Tombol"><a id="By">&#128140; Next</a></div>

    <!-- Rejected Message (if needed) -->
    <div id="pesanditolak">
      <img id="stikerditolak" src="https://feeldreams.github.io/weee.gif" />
      <p id="kataditolak">
        Oops! You can’t skip this birthday magic.
      </p>
    </div>
  </div>

  <script>
    // Main script remains similar; further changes are made in a.js if needed.
    const body = document.querySelector("body");
    const swalst = Swal.mixin({
      timer: 2300,
      allowOutsideClick: false,
      showConfirmButton: false,
      timerProgressBar: true,
      imageHeight: 90,
    });
    audio = new Audio("" + linkmp3.src);
    ftganti = 0;
    fungsi = 0;
    fungsiAwal = 0;
    deffotostiker = fotostiker.src;
    Content.style = "opacity:1;margin-top:16vh";
    const swals = Swal.mixin({
      allowOutsideClick: false,
      cancelButtonColor: "#FF0040",
      imageHeight: 80,
    });

    document.getElementById("kadoIn").onclick = function () {
      if (fungsiAwal == 0) {
        audio.play();
        fungsiAwal = 1;
        kadoIn.style =
          "transition:all .8s ease;transform:scale(10);opacity:0";
        wallpaper.style = "transform: scale(1.5);";
        ket.style = "display:none";
        setTimeout(initengahan, 300);
        setTimeout(inipesan, 500);
      }
    };

    async function inipesan() {
      var { value: nama } = await swals.fire({
        title: "What's your beautiful name?",
        input: "text",
      });
      if (nama && nama.length < 11) {
        window.nama = nama;
        vketikhalo = "Happy Birthday, " + nama + "!";
        mulainama();
      } else {
        await Swal.fire({
          title: "Your name is lovely, but it seems a bit long.",
          text: "Please enter a shorter name.",
          icon: "warning",
        });
        inipesan();
      }
    }

    var tanya = "How about we celebrate your birthday in style?";
    var opstanya = "Your choice is:";
    var tompositif = "Absolutely, let’s celebrate! 🎉";
    var tomnegatif = "Maybe another time";

    async function pertanyaan() {
      var { isConfirmed: prtanya } = await swals.fire({
        title: nama + ", " + tanya,
        text: "" + opstanya,
        imageUrl: "" + fotostiker5.src,
        showCancelButton: true,
        confirmButtonText: "" + tompositif,
        cancelButtonText: "" + tomnegatif,
      });
      if (prtanya) {
        pesanwhatsapp = "Yes " + nama + ", let the birthday magic begin!";
        menuju();
      } else {
        pesanwhatsapp = nama + ", don't miss out on the birthday fun!";
        await swalst.fire({
          title: "" + kataditolak.innerHTML,
          timer: 2000,
          imageUrl: "" + stikerditolak.src,
        });
        menuju();
      }
    }
  </script>
  <script src="a.js"></script>
</body>

</html>


[style.css](https://github.com/user-attachments/files/22318291/style.css)
@import url('https://fonts.googleapis.com/css2?family=Amita:wght@400;700&family=Archivo:ital,wght@0,100..900;1,100..900&family=Bilbo+Swash+Caps&family=Inter:opsz,wght@14..32,500&family=Noto+Serif:ital,wght@0,100..900;1,100..900&family=Pacifico&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Tiro+Devanagari+Marathi:ital@0;1&family=Dancing+Script:wght@400;700&display=swap');

:root {
    --tombol-bg: rgb(20 4 4 / 59%);
    --tombol-teks: #fff;
    --tombol-bingkai: #fff;
    --bingkai: 8px;
    --bingkai-kiri: 1.3px solid var(--tombol-bingkai);
    --bingkai-kanan: 1.3px solid var(--tombol-bingkai);
    --gaya-font: 'Archivo', sans-serif;
    --gaya-font2: 'Dancing Script', cursive;
}

body {
    font-family: "Archivo", sans-serif;
    height: 100vh;
}

@keyframes fanim {
    0% {background-position: 0% 0%;}
    25% {background-position: 100% 100%;}
    50% {background-position: 0% 100%;}
    75% {background-position: 50% 50%;}
    100% {background-position: 0% 0%;}
}

#bodyblur {
    opacity: 0;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(to bottom, #ffe1e1, #ff217de0), url(./r.jpg);
    transition: all 1s ease;
}

#wallpaper {
    width: 100%;
    height: 100%;
    transform: scale(2);
    transition: all 1.3s ease;
}

#beneranblur {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    -webkit-backdrop-filter: blur(0px);
    backdrop-filter: blur(0px);
    transition: all 3s ease;
}

@keyframes jj {0% {transform: scale(1.1);} 50% {transform: scale(1.2);} 100% {transform: scale(1.1);}}
@keyframes rts {from {transform: scale(0.1);} to {transform: scale(1);}}
@keyframes rto {from {transform: scale(1);} to {transform: scale(1.1);}}
@keyframes aniopa {0% {transform: scale(1);} 50% {transform: scale(0.75);} 100% {transform: scale(1);}}
@keyframes rtf {from {transform: rotate(0deg);} to {transform: rotate(360deg);}}
@keyframes rt {from {transform: scale(0.9);} to {transform: scale(1);}}
@keyframes kont {0% {left: -1px; top: -3px;} 50% {left: 1px; top: 3px;} 100% {left: -1px; top: -3px;}}

blockquote {
    position: absolute;
    opacity: 0;
    visibility: hidden;
    margin-top: 120px;
    background: rgb(0 0 0 / 73%);
    border-radius: 18px 0 18px 0;
    box-shadow: rgba(255,255,255, 0.3) 0px 7px 29px 0px;
    transform: scale(0.1);
    transition: all 1s ease;
    margin-left: 0;
    margin-right: 0;
    color: var(--tombol-teks);
    text-shadow: 0px 2px 2px rgba(0, 0, 0, .8);
}

blockquote {
    width: 400px;
    text-align: center;
    line-height: 1.3em;
    padding: 20px 25px;
}

blockquote::before {
    content: attr(data-text);
    opacity: .7;
    font-family: sans-serif;
    position: absolute;
    left: 8px;
    top: 8px;
    min-width: 15px;
    font-size: 16px;
    text-align: center;
}

blockquote::after {
    content: "";
    position: absolute;
    border: 1px solid #fff;
    border-radius: 18px 0 18px 0;
    top: -8px;
    bottom: -8px;
    left: -8px;
    right: -8px;
}

blockquote p {
    font-size: 16px;
    font-weight: 700;
    line-height: 1.4em;
    transition: all .5s ease;
}

blockquote > #kalimatb,
blockquote > .sty2 {
    font-size: 15px;
    font-weight: 400;
}

blockquote > #pesan4 {margin-top: 25px;}
blockquote > .sty2 {line-height: 1em;}

blockquote p:not(#opsL, #kalimat, #kalimatb, .sty2) {display: none;}

blockquote > #opsL {
    text-align: right;
    font-size: 11px;
    font-weight: 400;
    line-height: 0;
    margin-top: 24px;
    color: white;
    opacity: 0;
    transition: all .2s ease;
}

#waktu {display: none;}
#kado1, #kado2, #kado3 {font-size: 16px; font-weight: 400;}
#kalimatAkhir {transform: scale(0.1);}
#kado1 {position: absolute; opacity: 0;}
#kalove {font-size: 25px; line-height: 0;}
.kolombar .inibar {position: absolute; opacity: 0; visibility: hidden; background-color: #fff; height: 5px; width: 100%;}

#Tombol {
    position: relative;
    opacity: 0;
    margin: 0;
    display: flex;
    align-items: flex-start;
    list-style: none;
    transform: scale(0.1);
    transition: all 1s ease;
}

#Tombol a {
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    margin: 12px 0;
    transition: all .2s ease;
    padding: 10px;
    outline: 0;
    border: 1px solid #fff;
    border-radius: 18px;
    line-height: 15px;
    background: rgba(0,0,0,.5);
    color: var(--tombol-teks);
    font-size: 12px;
    font-weight: 700;
    white-space: nowrap;
    overflow: hidden;
    box-shadow: rgba(255,255,255, 0.3) 0px 7px 29px 0px;
    z-index: 1;
}

#Bn {margin: 12px 0 12px 12px !important;}
#Bn2 {position: absolute; opacity: 0; width: 0;}

#Content {
    animation-name: none;
    animation-duration: 3s;
    animation-iteration-count: infinite;
    position: relative;
    opacity: 0;
    margin-top: 50px;
    width: 100%;
    height: 100vh;
    transition: all .7s ease;
}

#Content > * {
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
    margin-top: 19px;
}

.kumpulanstiker > img {
    display: none;
    background: rgba(255, 255, 255, 0.2);
    box-shadow: 0 4px 30px rgba(255,255,255, 0.3);
    backdrop-filter: blur(5px);
    -webkit-backdrop-filter: blur(5px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    padding: 10px;
    width: 100px;
    height: 100px;
    margin: 20px 0;
}

#fotostiker {
    opacity: .1;
    transition: all 1.2s ease;
    transform: scale(0.1);
}

.halo {
    font-size: 18px !important;
    position: relative;
    margin: 15px 0 20px 0;
}

.halo.sty2 {
    font-family: var(--gaya-font2);
    font-size: 24px !important;
    margin-top: 20px !important;
}

.halo.sty3 {
    position: absolute !important;
    font-size: 14px !important;
    font-weight: 400 !important;
    margin: 30px 20px !important;
}

#kalimatbawah {
    position: absolute;
    opacity: 0;
    transform: scale(0.3);
    margin: 50px 0;
    font-family: var(--gaya-font2);
    font-size: 20px;
    font-weight: 700;
    color: white;
    text-shadow: 0px 2px 2px rgba(0, 0, 0, .8);
    transition: all .5s ease;
}

#tanggal {
    position: absolute;
    opacity: 0;
    transform: scale(0.3);
    transition: all .5s ease;
}

#fotolove img {
    transition: all .5s ease;
    width: 75px;
    height: 75px;
    padding: 0;
    background: none;
}

#kadoIn img {
    display: inline-flex;
    background: none;
    width: 317px;
    height: 280px;
    margin-bottom: 26px;
    transition: all .3s ease;
}

#ket, .halo {
    text-shadow: 1px 1px 2px rgb(10 3 3 / 67%);
    font-size: 1.3rem;
    letter-spacing: 2px;
    font-weight: 700;
    margin-left: 36px;
    color: #240606;
}

#kadoIn img:hover {transform: scale(0.9);}

#kolombaru {
    position: absolute;
    opacity: 0;
    display: flex;
    transform: scale(0.1);
    transition: all 1s ease;
    align-items: center;
    text-align: center;
    justify-content: center;
    z-index: 1;
}

#kolombaru > li {
    margin: 8px;
    padding: 0;
    list-style-type: none;
}

#kolombaru li {
    opacity: .8;
    display: flex;
    font-size: 30px;
}

#kolombaru li:hover {
    opacity: .5;
    transform: scale(1.15);
    transition: all .3s ease;
}

.kolomrange {
    padding: 0;
    background: none;
    position: relative;
    z-index: 1;
    display: none;
    transition: all 1s ease;
    align-items: center;
}

.kolomrange .inirange {
    width: 100%;
    height: 40px;
    margin-right: 15px;
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
}

.kolomrange .inirange input {
    height: 10px;
    width: 100%;
    -webkit-appearance: none;
    outline: none;
    background: #f2f2f2;
    border-radius: 25px;
    box-shadow: inset 0px 0px 4px rgba(0,0,0,0.2);
}

.kolomrange .inirange input::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 3px solid #006FFF;
    background: white;
    transition: all .2s ease;
}

.kolomrange .inirange input::-webkit-slider-thumb:hover {
    border: 5px solid #006FFF;
}

.kolomrange .inivalue {
    color: white;
    font-size: 20px;
}

.swal2-modal > * {font-size: 16px;}
.swal2-title {line-height: 1.3em; font-size: 17px; text-align: center; padding: 15px 30px 0 30px;}
.swal2-timer-progress-bar-container > * {opacity: .7; background: #00B6FF; margin: 0 2px;}
.swal2-modal {
    background: #ffffff;
    box-shadow: 0 4px 30px rgb(74 74 74 / 57%);
    backdrop-filter: blur(2px);
    -webkit-backdrop-filter: blur(2px);
    border: 1px solid rgba(255, 255, 255, 0.3);
    border-radius: 8px;
    max-width: 330px;
    top: -60px;
}

.swal2-styled.swal2-confirm,
.swal2-styled.swal2-cancel {
    position: relative;
    background-color: #4839eb;
    color: #fff;
    border-radius: 18px;
    z-index: 1;
    transition: all 0.2s;
}

.fa-snowflake {
    opacity: .3;
    color: white;
    font-size: 20px;
    position: absolute;
    animation: heartMove linear 1;
    top: -10vh;
    z-index: 0;
}

@keyframes heartMove {
    0% {transform: translateY(-10vh);}
    100% {transform: translateY(100vh);}
}

.sembunyi,
#pesanditolak > *,
#kado2,
#kado3 {
    display: none !important;
}

.swal2-container.swal2-backdrop-show,
.swal2-container.swal2-noanimation {
    background: linear-gradient(to bottom, #ffe1e1, #ff217de0), url(./r.jpg);
    height: 100vh;
}

.kumpulanstiker img {
    transform: scale(2) !important;
}

#ket {
    margin-top: 3px !important;
    backdrop-filter: blur(8px);
}
![4a0a9d924fd271737c0813852160ae89 jpg](https://github.com/user-attachments/assets/f4cf7aaf-6ac0-4795-8295-adf8daa82835)
https://github.com/user-attachments/assets/dfc9c8ac-13ab-4a47-816c-dcd07e6fc2f8
<img width="2149" height="2431" alt="GiftBox" src="https://github.com/user-attachments/assets/0d41d56d-3179-4ce6-a266-d09afb09afe2" />
<img width="500" height="489" alt="helo" src="https://github.com/user-attachments/assets/d79620be-d6ad-464b-8db9-f56b198be4ba" />
![r](https://github.com/user-attachments/assets/34827ccd-9214-4ce5-9483-f7662bf1e546)
<img width="555" height="543" alt="Screenshot 2025-03-01 162514" src="https://github.com/user-attachments/assets/a1b0f62c-d70c-4163-8fcb-b7a6d1dfdd17" />
<img width="2528" height="2203" alt="v" src="https://github.com/user-attachments/assets/b07e2c69-f377-47ea-950a-ff4c3cb47f1a" />
<img width="2528" height="2203" alt="v" src="https://github.com/user-attachments/assets/90fcdb56-61ea-45ec-8963-85cbd08d756a" />
<img width="2532" height="2356" alt="Valentine-Surprise" src="https://github.com/user-attachments/assets/45b2c7ca-91ca-4916-830b-cd39dfb7ae64" />
[y2mate (mp3cut.net).mp3](https://github.com/user-attachments/files/22318182/y2mate.mp3cut.net.mp3)
<img width="555" height="543" alt="Screenshot 2025-03-01 162514" src="https://github.com/user-attachments/assets/ebaefe34-4d3b-4f22-a2ca-1f08b4d0ab54" />

function initengahan(){
  kadoIn.style = "display:none";
  ket.style = "display:none";
  Content.style = "opacity:1;margin-top:0";
  bodyblur.style = "opacity:.7";
  wallpaper.style = "transform: scale(1.5);";
}

async function mulainama() {
  bodyblur.style = "opacity:0";
  wallpaper.style = "transform: scale(1);";
  fotostiker.style = "display:inline-flex;";
  setTimeout(ftmuncul, 200);
  setTimeout(kethalo, 500);
}

function ftmuncul() {
  if (ftganti == 0) { fotostiker.src = deffotostiker; }
  if (ftganti == 1) { fotostiker.src = fotostiker1.src; }
  if (ftganti == 2) { fotostiker.src = fotostiker2.src; }
  if (ftganti == 3) { fotostiker.src = fotostiker3.src; }
  if (ftganti == 4) { fotostiker.src = fotostiker4.src; }
  fotostiker.style = "display:inline-flex;opacity:1;transform:scale(1)";
}

function fthilang() {
  fotostiker.style = "display:inline-flex;opacity:1;transition:all .7s ease;transform:scale(.1)";
}

function jjfoto() {
  fotostiker.style.animation = "rto .8s infinite alternate";
}

function bqmuncul() {
  bq.style = "position:relative;opacity:1;visibility:visible;transform: scale(1);margin-top:0";
  mulaiketik1();
  fungsi = 1;
}

function bqhilang() {
  wallpaper.style = "transform: scale(2);";
  bodyblur.style = "opacity:.3";
  bq.style = "position:relative;transition:all .7s ease;";
}

function kethalo() {
  new TypeIt("#halo", {
    strings: ["" + vketikhalo],
    startDelay: 50,
    speed: 40,
    waitUntilVisible: true,
    afterComplete: function () {
      halo.innerHTML = vketikhalo;
      setTimeout(bqmuncul, 200);
    },
  }).go();
}

function tombol() {
  wallpaper.style = "transform: scale(1);";
  Tombol.style = "opacity:1;transform: scale(1);";
  fungsi = 1;
}

document.getElementById("By").onclick = function() {
  if (fungsi == 1) { pertanyaan(); }
  if (fungsi == 2) { menuju(); }
}

async function menuju(){
  await swals.fire('Yay!', 'And here comes another birthday surprise for you!', 'success');
  window.location = "./love/index.html";
}

vketik1 = kalimat.innerHTML;
kalimat.innerHTML = "";
function mulaiketik1(){
  new TypeIt("#kalimat", {
    strings: ["" + vketik1],
    startDelay: 400,
    speed: 20,
    cursor: false,
    deleteSpeed: 20,
    breakLines: false,
    waitUntilVisible: true,
    lifelike: true,
    afterComplete: function(){
      aktiopsL();
    },
  }).go();
}

opsLclick = 0;
opsLcheck = 0;
defopsL = opsL.innerHTML;
document.getElementById("bq").onclick = function() {
  if (opsLclick == 1) {
    if (opsLcheck == 1) { setTimeout(aktipesan1, 400); }
    if (opsLcheck == 2) { mulaiketik3(); }
    if (opsLcheck == 3) { mulaiketik4(); }
    if (opsLcheck == 4) { mulaiketik5(); }
    if (opsLcheck == 5) { kethalo2(); }
    otomatis();
    opsL.style.opacity = "0";
    opsLclick = 0;
  }
}

function aktiopsL() {
  opsL.innerHTML = defopsL;
  opsL.style.opacity = ".8";
  opsLclick = 1;
  opsLcheck += 1;
}

function gantiopsL() {
  opsL.innerHTML = "[ Tap one of the birthday icons! ]";
  opsL.style.opacity = ".8";
}

function otomatis() {
  kalimat.style = "opacity:0";
  setTimeout(otolanj, 400);
}

function otolanj() {
  kalimat.style = "opacity:1";
}

function aktipesan1() {
  kalimat.innerHTML = pesan1.innerHTML;
  kolombaru.style = "position:relative;opacity:1;transform:scale(1);";
}

vketik2 = pesan2.innerHTML;
vketik3 = pesan3.innerHTML;
function aktipesan2(){
  wallpaper.style = "transform: scale(1.5);";
  kolombaru.style = "";
  kalimat.innerHTML = "";
  new TypeIt("#kalimat", {
    strings: ["" + vketik2, "" + vketik3],
    startDelay: 20,
    speed: 30,
    cursor: true,
    deleteSpeed: 30,
    breakLines: false,
    waitUntilVisible: true,
    lifelike: true,
    afterComplete: function(){
      kalimat.innerHTML = vketik3;
      setTimeout(aktipesan4, 700);
    },
  }).go();
}

vketik4 = pesan4.innerHTML;
pesan4.innerHTML = "";
function aktipesan4(){
  wallpaper.style = "transform: scale(1);";
  fthilang();
  ftganti = 2;
  setTimeout(ftmuncul, 300);
  new TypeIt("#pesan4", {
    strings: ["" + vketik4],
    startDelay: 1,
    speed: 52,
    cursor: true,
    waitUntilVisible: true,
    lifelike: true,
    afterComplete: function(){
      pesan4.innerHTML = vketik4;
      setTimeout(aktipesan5, 700);
    },
  }).go();
}

vketik5 = pesan5.innerHTML;
pesan5.innerHTML = "";
function aktipesan5(){
  wallpaper.style = "transform: scale(1.5);";
  fthilang();
  ftganti = 3;
  setTimeout(ftmuncul, 300);
  new TypeIt("#pesan5", {
    strings: ["" + vketik5],
    startDelay: 1,
    speed: 52,
    cursor: true,
    waitUntilVisible: true,
    lifelike: true,
    afterComplete: function(){
      pesan5.innerHTML = vketik5 + " 😊";
      setTimeout(aktipesan6, 700);
    },
  }).go();
}

vketik6 = pesan6.innerHTML;
pesan6.innerHTML = "";
function aktipesan6(){
  wallpaper.style = "transform: scale(1);";
  fthilang();
  ftganti = 4;
  setTimeout(ftmuncul, 300);
  new TypeIt("#pesan6", {
    strings: ["" + vketik6],
    startDelay: 1,
    speed: 52,
    cursor: true,
    waitUntilVisible: true,
    lifelike: true,
    afterComplete: function(){
      pesan6.innerHTML = vketik6;
      setTimeout(tombol, 400);
    },
  }).go();
}

var slov = 0;
document.getElementById("lv1").onclick = function() { lv1.style = "opacity:0"; slov += 1; this.onclick = null; checkslov(); }
document.getElementById("lv2").onclick = function() { lv2.style = "opacity:0"; slov += 1; this.onclick = null; checkslov(); }
document.getElementById("lv3").onclick = function() { lv3.style = "opacity:0"; slov += 1; this.onclick = null; checkslov(); }
document.getElementById("lv4").onclick = function() { lv4.style = "opacity:0"; slov += 1; this.onclick = null; checkslov(); }

function checkslov() {
  if (slov == 4) {
    kolombaru.style = "position:relative;transform:scale(1)";
    fthilang();
    ftganti = 1;
    setTimeout(ftmuncul, 300);
    otomatis();
    setTimeout(aktipesan2, 400);
  }
}
