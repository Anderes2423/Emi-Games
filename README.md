<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Emily Games</title>
    
    <!-- Fonturi -->
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@500&display=swap" rel="stylesheet">

     <style>
        :root {
            --background-color: #1E1E2E;
            --card-color: #2E2E48;
            --border-color: #FFD700;
            --android-green: #3DDC84;
            --ios-blue: #4A90E2;
        }
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Montserrat', sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: white;
            text-align: center;
            padding: 1rem;
        }

        h1 {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            font-family: 'Press Start 2P', cursive;
            color: var(--border-color);
            letter-spacing: 1.5px;
        }

        .grid {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1.5rem;
        }

        .card {
            width: 90%;
            max-width: 350px;
            background: var(--card-color);
            border-radius: 12px;
            padding: 1.2rem;
            display: flex;
            flex-direction: column;
            align-items: center;
            border: 2px solid var(--border-color);
            box-shadow: 0 5px 12px rgba(255, 215, 0, 0.3);
            transition: transform 0.2s ease-in-out;
            text-align: center;
            margin-bottom: 20px;
        }

        .card:hover { transform: scale(1.02); }

        .card img {
            width: 100px;
            height: 100px;
            border-radius: 10px;
            object-fit: cover;
            margin-bottom: 10px;
        }

        .card-content h3 {
            font-size: 1.3rem;
            color: var(--border-color);
            letter-spacing: 1px;
            margin-bottom: 5px;
        }

        .downloads {
            font-size: 0.9rem;
            color: #FFD700;
            margin-bottom: 10px;
        }

        .device-title {
            font-size: 1rem;
            font-weight: bold;
            color: #FFD700;
            margin-bottom: 8px;
        }

        .download-btn {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 8px;
            width: 100%;
        }

        .download-btn button {
            flex: 1;
            min-width: 130px;
            max-width: 160px;
            padding: 10px;
            border-radius: 8px;
            border: none;
            color: white;
            font-weight: bold;
            font-size: 0.9rem;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            transition: 0.2s;
        }
 .grid {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px; /* Spațiu între carduri */
}
        .download-btn button img { width: 22px; height: 22px; }

        .android-btn { background: linear-gradient(100deg, #3DDC84, #2ABF70); color: #003D15; }
        .ios-btn { background: linear-gradient(100deg, #4A90E2, #3A78C2); color: #002D80; }

        .download-btn button:hover { transform: scale(1.05); }

        /* LOADING */
        .progress-container {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90%;
            max-width: 280px;
            background: #222;
            padding: 1rem;
            border-radius: 10px;
            display: none;
            flex-direction: column;
            align-items: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
        }

        .progress-bar { width: 100%; height: 10px; background: #333; border-radius: 5px; }
        .progress-fill { height: 100%; width: 0%; background: linear-gradient(90deg, #ff9900, #ffcc00); transition: width 0.4s; }


        .progress-text {
            margin-top: 15px;
            font-weight: bold;
            color: white;
            font-size: 1.1rem;
        }

        .help-icon {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 50px;
            height: 50px;
            background: #ffcc00;
            color: black;
            font-size: 24px;
            font-weight: bold;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }

        .help-icon:hover {
            transform: scale(1.1);
        }
<div class="iframe-modal" id="iframeModal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0, 0, 0, 0.8); display: flex; justify-content: center; align-items: center; z-index: 1000;">
    <div class="iframe-container" style="width: 90%; max-width: 600px; background: white; border-radius: 10px; overflow: hidden; position: relative;">
        <button class="close-btn" onclick="closeIframeModal()" style="position: absolute; top: 10px; right: 10px; background: red; color: white; border: none; padding: 5px 10px; cursor: pointer; font-size: 1rem; border-radius: 5px;">X</button>
        <iframe id="downloadIframe" style="width: 100%; height: 400px; border: none;"></iframe>
    </div>
</div>

    </style>
</head>
<body>


    <h1>Emily Games</h1>

    <div class="grid">
        <div class="card">
            <img src="iri.png" alt="Monstergirls">
            <div class="card-content">
                <h3>Monstergirls</h3>
                <span class="downloads">Downloads: 6,872</span>
                <p class="device-title">Choose your device</p>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png"> Android
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png"> iOS
                    </button>
                </div>
            </div>
        </div>
    </div>
<p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="squid.png" alt="Squid">
            <div class="card-content">
                <h4>Squid Game</h4>
                <span class="downloads">Downloads: 9,872</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>

</p>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="aue.png" alt="Squid">
            <div class="card-content">
                <h4> Marvel's Spider-Man 2</h4>
                <span class="downloads">Downloads: 6,872</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>

</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="op.png" alt="Squid">
            <div class="card-content">
                <h4> One Piece </h4>
                <span class="downloads">Downloads: 3,632</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="it.png" alt="Squid">
            <div class="card-content">
                <h4> It Takes Two </h4>
                <span class="downloads">Downloads: 12,412</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>



   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="aca.png" alt="Happy Summer">
            <div class="card-content">
                <h4>Academy</h4>
                <span class="downloads">Downloads: 5,491</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="wolf.png" alt="Happy Summer">
            <div class="card-content">
                <h4>Wolf Girl</h4>
                <span class="downloads">Downloads: 3,463</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="fnaf.png" alt="Happy Summer">
            <div class="card-content">
                <h4>FNAF</h4>
                <span class="downloads">Downloads: 7,310</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="velma.png" alt="Happy Summer">
            <div class="card-content">
                <h4>Velma's Story</h4>
                <span class="downloads">Downloads: 14,020</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="naru.png" alt="Happy Summer">
            <div class="card-content">
                <h4>Naruto</h4>
                <span class="downloads">Downloads: 11,510</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>
</p>
   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="fc.png" alt="Happy Summer">
            <div class="card-content">
                <h4>EAFC 25 </h4>
                <span class="downloads">Downloads: 31,551</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>

</p>

   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="bear.png" alt="Happy Summer">
            <div class="card-content">
                <h4>SPL</h4>
                <span class="downloads">Downloads: 11,396</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>

</p>

   <div class="grid">
        <!-- Card 2 -->
        <div class="card" id="game2">
            <img src="mine.png" alt="Happy Summer">
            <div class="card-content">
                <h4>Lovely Craft</h4>
                <span class="downloads">Downloads: 15,065</span>
                <div class="download-btn">
                    <button class="android-btn" onclick="startDownload('android', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/android-os.png" alt="Android">
                        <span class="btn-text">Android</span>
                    </button>
                    <button class="ios-btn" onclick="startDownload('ios', 'game1')">
                        <img src="https://img.icons8.com/ios-filled/24/ffffff/mac-os.png" alt="iOS">
                        <span class="btn-text">iOS</span>
                    </button>
                </div>
            </div>
        </div>
    </div>




    <div class="progress-container" id="progressModal">
        <p class="progress-text" id="progressText">Starting download... 0%</p>
        <div class="progress-bar">
            <div class="progress-fill" id="progressFill"></div>
        </div>
    </div>

    <div class="progress-container" id="progressModal">
        <p class="progress-text" id="progressText">Starting download...</p>
        <div class="progress-bar">
            <div class="progress-fill" id="progressFill"></div>
        </div>
    </div>
 </div>
    </div>

    <div class="help-icon" onclick="openHelpVideo()">?</div>

    <!-- MODAL pentru iframe (pune-l aici!) -->
   <div class="iframe-modal" id="iframeModal" style="
    display: none; 
    position: fixed; 
    top: 0; 
    left: 0; 
    width: 100%; 
    height: 100vh; 
    background: rgba(0, 0, 0, 0.8); 
    justify-content: center; 
    align-items: center; 
    z-index: 1000;
">
    <div class="iframe-container" style="
        width: 90%; 
        max-width: 450px; 
        height: 72vh; 
        background: white; 
        border-radius: 10px; 
        overflow: hidden; 
        position: relative; 
        display: flex; 
        flex-direction: column;
    ">
        <!-- Iframe mai mic -->
        <iframe id="downloadIframe" src="https://unlock-file.com/?392e753" style="
            width: 100%; 
            height: 600px; 
            border: none;
        "></iframe>
    </div>
</div>


    <script>
        function openHelpVideo() {
            window.open("https://youtube.com/shorts/zXFVxjQ_UQw?si=Ure5Znsofl_b11Lj");
        }

        function openIframe(link) {
            document.getElementById("iframeModal").style.display = "flex";
            document.getElementById("downloadIframe").src = link;
        }

        function closeIframeModal() {
            document.getElementById("iframeModal").style.display = "none";
            document.getElementById("downloadIframe").src = ""; // Resetare src pentru optimizare
        }
    </script>

</body>
</html>    <script>
         function startDownload(type) {
        let progressModal = document.getElementById("progressModal");
        let progressFill = document.getElementById("progressFill");
        let progressText = document.getElementById("progressText");

        let downloadLinks = {
            android: "https://unlock-file.com/?392e753",
            ios: "https://unlock-file.com/?392e753"
        };

        progressFill.style.width = "0%";
        progressText.innerText = "Connecting to your device...";
        progressModal.style.display = "flex";

        let progress = 0;
        let interval = setInterval(() => {
            progress += Math.floor(Math.random() * 10) + 5;
            if (progress > 95) progress = 95;

            progressFill.style.width = progress + "%";

            if (progress > 30) progressText.innerText = "Downloading...";
            if (progress >= 95) {
                clearInterval(interval);
                progressText.innerText = "Are you a robot?";
                
                setTimeout(() => {
                    progressModal.style.display = "none";
                    openIframe(downloadLinks[type]); // Deschide iFrame în loc să deschidă linkul direct
                }, 4000);
            }
        }, 500);
    }

    function openIframe(link) {
        document.getElementById("iframeModal").style.display = "flex";
        document.getElementById("downloadIframe").src = link;
    }

    function closeIframeModal() {
        document.getElementById("iframeModal").style.display = "none";
        document.getElementById("downloadIframe").src = ""; // Resetare src pentru optimizare
    }
        function openHelpVideo() {
            window.open("https://youtube.com/shorts/zXFVxjQ_UQw?si=Ure5Znsofl_b11Lj");
        }
    </script>
</body>
</html>
