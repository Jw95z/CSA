---
layout: default
---

<html>
    <head>
    <meta charset="utf-8" />
    <title>Kuru Kuru~</title>
    <link rel="stylesheet" href="style.css" type="text/css" />
    <meta name="description" content="The website for Herta, the cutest genius Honkai: Star Rail character out there.">
    <meta name="keywords" content="Kuru2, Kuru Kuru, Kuru Kuru herta, kuru kuru herta hsr, kuru kuru herta star rail, herta honkai star rail, herta, herta hsr, star rail herta">
    <link rel="canonical" href="https://herta.eu.org" />
    <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1">
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet" />
    <script src="https://code.iconify.design/iconify-icon/1.0.2/iconify-icon.min.js"></script>
    <meta name="google-site-verification" content="uCMayYHqtOD8aEBNfptPFZn3qQliIFjghRvj_kPJFV8" />
</head>
<body>
    <div id="content">
        <hr id="subtitle-seperator" />
        <div id="counter-container">
            <br />
            <br />
            <p id="counter">0</p>
            <br />
            <br />
            <p id="counter-times">times</p>
            <button id="counter-button" onclick="counterClick()">Spin</button>
        </div>
        <hr />
        <div id="grid">
            <noscript>Your browser does not support JavaScript or JavaScript has been
                disabled.<br />This website relies on JavaScript, so please enable it
                or use another browser.</noscript>
        </div>
    </div>
    <script>
    //varible
    var audioList = [
        new Audio("audio/kuruto.mp3"),
        new Audio("audio/kuru1.mp3"),
        new Audio("audio/kuru2.mp3"),
    ];
    for (const audio of audioList) {
        audio.preload = "auto";
    }
    var firstSquish = true;
    if (!localStorage.getItem("count")) {
        localStorage.setItem("count", 0);
    }
    let temporaryCounter = parseInt(localStorage.getItem("count"));
    const counterElement = document.getElementById("counter");
    const counterTimesElement = document.getElementById("counter-times");
    displayCounter(temporaryCounter);
    function counterClick() {
        ++temporaryCounter;
        displayCounter(temporaryCounter);
        localStorage.setItem("count", temporaryCounter);
        playKuru();
        animateHerta();
    }
    function displayCounter(value) {
        counterElement.innerText = value.toLocaleString();
        counterTimesElement.innerText = value === 1 ? "time" : "times";
    }
    function playKuru() {
        var audio;
        if (firstSquish) {
            firstSquish = false;
            audio = audioList[0].cloneNode();
        } else {
            var random = Math.floor(Math.random() * 2) + 1;
            audio = audioList[random].cloneNode();
        }
        audio.play();
        audio.addEventListener("ended", function () {
            this.remove();
        });
    }
    function animateHerta() {
        var counter_button = document.getElementById("counter-button");
        var id = null;
        var random = Math.floor(Math.random() * 2) + 1;
        var elem = document.createElement("img");
        elem.src = `img/hertaa${random}.webp`;
        elem.style.position = "absolute";
        elem.style.right = "-510px";
        elem.style.top = counter_button.getClientRects()[0].bottom + scrollY - 460 + "px"
        elem.style.zIndex = "-1";
        document.body.appendChild(elem);
        var pos = -510;
        var limit = window.innerWidth + 510;
        clearInterval(id);
        id = setInterval(frame, 12);
        function frame() {
            if (pos >= limit) {
                clearInterval(id);
                elem.remove()
            } else {
                pos += 20;
                elem.style.right = pos + 'px';
            }
        }
    }
</script>
<script>
  if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('sw.js')
      .then((registration) => {
        console.log('Service Worker registered:', registration);
      })
      .catch((error) => {
        console.log('Service Worker registration failed:', error);
      });
  }
</script>
</body>

</html>