# Newyear2026
<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy New Year 2026</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <div class="wish-box">
            <h2 id="display-name">Aapko</h2>
            <h1 class="main-wish">Happy New Year <br><span>2026</span></h1>
            <p>Naya Saal aapke liye dher saari khushiyan lekar aaye!</p>
        </div>

        <div class="input-section">
            <input type="text" id="nameInput" placeholder="Apna Naam Likhein...">
            <button onclick="generateWish()">Apne Naam se Banayein</button>
        </div>

        <div id="share-section" style="display:none;">
            <button class="whatsapp-btn" onclick="shareWhatsApp()">WhatsApp par Bhejein</button>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>

body {
    background: linear-gradient(to bottom, #0f0c29, #302b63, #24243e);
    color: white;
    font-family: 'Arial', sans-serif;
    text-align: center;
    margin: 0;
    padding: 20px;
}

.container {
    margin-top: 50px;
}

.main-wish {
    font-size: 3rem;
    text-shadow: 0 0 10px #ffcc00, 0 0 20px #ffcc00;
}

.main-wish span {
    color: #ffcc00;
    font-size: 4rem;
}

input {
    padding: 10px;
    border-radius: 5px;
    border: none;
    width: 200px;
}

button {
    padding: 10px 20px;
    background-color: #25d366;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    margin-top: 10px;
}

.whatsapp-btn {
    background-color: #128C7E;
    margin-top: 20px;
}

// URL se naam check karne ke liye
const urlParams = new URLSearchParams(window.location.search);
const senderName = urlParams.get('name');

if (senderName) {
    document.getElementById('display-name').innerText = senderName + " ki taraf se";
}

function generateWish() {
    const name = document.getElementById('nameInput').value;
    if (name) {
        const newUrl = window.location.origin + window.location.pathname + "?name=" + encodeURIComponent(name);
        window.location.href = newUrl;
    } else {
        alert("Kripya apna naam likhein!");
    }
}

function shareWhatsApp() {
    const name = senderName || "Main";
    const currentUrl = window.location.href;
    const text = `🎉 *${name}* ne aapko Naye Saal ki badhai bheji hai! %0A Dekhne ke liye niche link par click karein: %0A ${currentUrl}`;
    window.open(`https://api.whatsapp.com/send?text=${text}`, '_blank');
}

// Agar naam URL mein hai to share button dikhao
if (senderName) {
    document.getElementById('share-section').style.display = 'block';
}
