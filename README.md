
[a.js](https://github.com/user-attachments/files/22318112/a.js)![4a0a9d924fd271737c0813852160ae89 jpg](https://github.com/user-attachments/assets/8cc6b9bb-f1ee-4f75-a3b4-9c237865f0f3)

[Uploafunction initengahan(){
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
}ding a.js…]()

https://github.com/user-attachments/assets/5f9ee181-00ae-41c9-ab40-e4bfddf8094f
<img width="2149" height="2431" alt="GiftBox" src="https://github.com/user-attachments/assets/62c3cec3-8b5e-4483-9343-55337da61a28" />
<img width="500" height="489" alt="helo" src="https://github.com/user-attachments/assets/022b5f5f-fcd8-4462-991c-fea9cbdf8212" />
[index.html](https://github.com/user-attachments/files/22318116/index.html)
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
![r](https://github.com/user-attachments/assets/f9521fc3-d045-432c-b5b0-f15673c181e0)
<img width="555" height="543" alt="Screenshot 2025-03-01 162514" src="https://github.com/user-attachments/assets/f2c0be36-da86-4bd6-8ee6-5815504f0d22" />
[style.css](https://github.com/user-attachments/files/22318119/style.css)
<img width="2528" height="2203" alt="v" src="https://github.com/user-attachments/assets/db1b02d5-aff8-407a-bb9f-8e9889c2e9ec" />
<img width="2532" height="2356" alt="Valentine-Surprise" src="https://github.com/user-attachments/assets/b0fd4c8c-c333-4f83-a859-e52651a62c55" />
[y2mate (mp3cut.net).mp3](https://github.com/user-attachments/files/22318120/y2mate.mp3cut.net.mp3)
[index.html](https://github.com/user-attachments/files/22318121/index.html)
