# New-repository
lotto-generator
<!DOCTYPE html>
<html lang="sv">

<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>🚂 Tåg-Generatorn V7 Svensk Edition</title>

<style>

body{
    font-family:Arial,sans-serif;
    background:#0b0c10;
    color:white;
    padding:15px;
    text-align:center;
}

.container{
    max-width:700px;
    margin:auto;
    background:#1f2833;
    padding:20px;
    border-radius:15px;
    box-shadow:0 0 25px rgba(102,252,241,.3);
}

h1{
    color:#66fcf1;
}

.version{
    color:#45a29e;
    margin-bottom:20px;
}

label{
    display:block;
    text-align:left;
    margin-top:12px;
    color:#66fcf1;
    font-weight:bold;
}

input,select{
    width:100%;
    padding:12px;
    border-radius:8px;
    border:1px solid #45a29e;
    background:#0b0c10;
    color:white;
    box-sizing:border-box;
    margin-top:5px;
}

button{
    width:100%;
    margin-top:15px;
    padding:15px;
    border:none;
    border-radius:8px;
    font-size:18px;
    font-weight:bold;
    cursor:pointer;
}

.mainBtn{
    background:#66fcf1;
    color:#000;
}

.voiceBtn{
    background:#ffcc00;
    color:#000;
}

.result{
    display:none;
    margin-top:20px;
    background:#0b0c10;
    border-left:5px solid #66fcf1;
    border-radius:10px;
    padding:15px;
    text-align:left;
}

.numbers{
    background:#1f2833;
    color:#ffcc00;
    padding:12px;
    border-radius:8px;
    font-size:24px;
    font-weight:bold;
    margin-top:10px;
}

.stars{
    color:#ff007f;
}

.small{
    font-size:13px;
    color:#aaa;
}

.historyItem{
    background:#1f2833;
    padding:10px;
    border-radius:8px;
    margin-top:10px;
}

.theme-dark{
    background:#0b0c10;
}

.theme-galaxy{
    background:#140021;
}

.theme-retro{
    background:#1b1b00;
}

</style>
</head>

<body class="theme-dark">

<div class="container">

<h1>🚂 Tåg-Generatorn V7</h1>

<div class="version">
Svensk Edition • Offline • Historik • Röster
</div>

<label>👤 Profilnamn</label>
<input type="text"
       id="profileName"
       placeholder="Ex: Martin">

<label>⭐ Favoritspel</label>
<select id="favoriteGame">

<option>Lotto</option>
<option>Eurojackpot</option>
<option>Vikinglotto</option>

</select>

<label>🎨 Tema</label>
<select id="themeSelect">

<option value="theme-dark">
Mörkt Tågtema
</option>

<option value="theme-galaxy">
Galaxläge
</option>

<option value="theme-retro">
Retroterminal
</option>

</select>

<label>🎂 Födelsedatum</label>
<input type="date"
       id="birthdate">

<label>♏ Stjärntecken</label>

<select id="zodiac">

<option value="1">Väduren</option>
<option value="2">Oxen</option>
<option value="3">Tvillingarna</option>
<option value="4">Kräftan</option>
<option value="5">Lejonet</option>
<option value="6">Jungfrun</option>
<option value="7">Vågen</option>
<option value="8">Skorpionen</option>
<option value="9">Skytten</option>
<option value="10">Stenbocken</option>
<option value="11">Vattumannen</option>
<option value="12">Fiskarna</option>

</select>

<label>🎯 Favoritnummer LOTTO</label>
<input type="text"
       id="lottoFavorites"
       placeholder="Ex: 4, 18, 22">

<label>🌟 Favoritnummer EUROJACKPOT</label>
<input type="text"
       id="euroFavorites"
       placeholder="Ex: 11, 25, 44">

<label>🧠 Turmotor</label>

<select id="luckMode">

<option value="balans">
Balanserad Tur
</option>

<option value="turbo">
Turbo-Tur
</option>

<option value="kosmisk">
Kosmiskt Läge
</option>

</select>

<label>🇸🇪 Lotto-system</label>

<select id="lottoSystem">

<option value="8">
M8 • 32 kr
</option>

<option value="9">
M9 • 144 kr
</option>

<option value="10" selected>
M10 • 480 kr
</option>

<option value="11">
M11 • 1 320 kr
</option>

<option value="12">
M12 • 3 168 kr
</option>

</select>

<label>🇪🇺 Eurojackpot-system</label>

<select id="euroSystem">

<option value="5-3">
5+3 • 75 kr
</option>

<option value="6-2" selected>
6+2 • 150 kr
</option>

<option value="6-3">
6+3 • 450 kr
</option>

<option value="7-2">
7+2 • 525 kr
</option>

<option value="8-2">
8+2 • 1 400 kr
</option>

</select>

<button class="mainBtn"
        onclick="generateSystems()">

🚀 GENERERA KOSMISKA SYSTEM

</button>

<button class="voiceBtn"
        onclick="speakResults()">

🔊 Läs upp nummer

</button>

<div id="lottoBox"
     class="result">

<h2>🇸🇪 LOTTO</h2>

<div class="small"
     id="lottoInfo"></div>

<div class="numbers"
     id="lottoNumbers"></div>

</div>

<div id="euroBox"
     class="result">

<h2>🇪🇺 EUROJACKPOT</h2>

<div class="small"
     id="euroInfo"></div>

<div class="numbers"
     id="euroNumbers"></div>

<div class="small">
Stjärnnummer
</div>

<div class="numbers stars"
     id="starNumbers"></div>

</div>

<div id="vikingBox"
     class="result">

<h2>⚔️ VIKINGLOTTO</h2>

<div class="numbers"
     id="vikingNumbers"></div>

</div>

<div id="historyBox"
     class="result">

<h2>📜 Senaste Generering</h2>

<div id="history"></div>

</div>

</div>

<script>

let latestSpeech = "";

//
// KOSMISK RANDOM
//

function cosmicRandom(max,count,seed){

    let set = new Set();

    let counter = seed;

    while(set.size < count){

        counter =
            (counter * 9301 + 49297) % 233280;

        set.add((counter % max) + 1);
    }

    return Array.from(set)
        .sort((a,b)=>a-b);
}

//
// FAVORITER
//

function parseFavorites(text){

    return text
        .split(',')
        .map(n =>
            parseInt(n.trim())
        )
        .filter(n =>
            !isNaN(n)
        );
}

function injectFavorites(array,favs,max){

    favs.forEach(n => {

        if(n >=1 && n <= max){

            array[0] = n;
        }
    });

    return array.sort((a,b)=>a-b);
}

//
// GENERERA SYSTEM
//

function generateSystems(){

    let birth =
        document.getElementById(
            'birthdate'
        ).value.replace(/-/g,'');

    if(!birth){

        alert("Välj födelsedatum");

        return;
    }

    let zodiac =
        parseInt(
            document.getElementById(
                'zodiac'
            ).value
        );

    let mode =
        document.getElementById(
            'luckMode'
        ).value;

    let modifier = 0;

    if(mode === 'turbo')
        modifier = 7777;

    if(mode === 'kosmisk')
        modifier = 9999;

    let seed =
        parseInt(birth) +
        zodiac +
        modifier +
        Date.now();

    //
    // LOTTO
    //

    let lottoSize =
        parseInt(
            document.getElementById(
                'lottoSystem'
            ).value
        );

    let lotto =
        cosmicRandom(
            35,
            lottoSize,
            seed
        );

    lotto =
        injectFavorites(

            lotto,

            parseFavorites(

                document.getElementById(
                    'lottoFavorites'
                ).value

            ),

            35
        );

    //
    // EUROJACKPOT
    //

    let euroSystem =
        document.getElementById(
            'euroSystem'
        ).value;

    let euroMain =
        parseInt(
            euroSystem.split('-')[0]
        );

    let euroStars =
        parseInt(
            euroSystem.split('-')[1]
        );

    let euro =
        cosmicRandom(
            50,
            euroMain,
            seed + 500
        );

    euro =
        injectFavorites(

            euro,

            parseFavorites(

                document.getElementById(
                    'euroFavorites'
                ).value

            ),

            50
        );

    let stars =
        cosmicRandom(
            12,
            euroStars,
            seed + 900
        );

    //
    // VIKINGLOTTO
    //

    let viking =
        cosmicRandom(
            48,
            6,
            seed + 1500
        );

    //
    // PRISER
    //

    let lottoPrices = {

        8:"32 kr",
        9:"144 kr",
        10:"480 kr",
        11:"1 320 kr",
        12:"3 168 kr"
    };

    let euroPrices = {

        "5-3":"75 kr",
        "6-2":"150 kr",
        "6-3":"450 kr",
        "7-2":"525 kr",
        "8-2":"1 400 kr"
    };

    //
    // VISA RESULTAT
    //

    document.getElementById(
        'lottoInfo'
    ).innerText =

        "System M" +
        lottoSize +
        " • Pris: " +
        lottoPrices[lottoSize];

    document.getElementById(
        'lottoNumbers'
    ).innerText =
        lotto.join(', ');

    document.getElementById(
        'euroInfo'
    ).innerText =

        "System " +
        euroSystem.replace('-', '+') +
        " • Pris: " +
        euroPrices[euroSystem];

    document.getElementById(
        'euroNumbers'
    ).innerText =
        euro.join(', ');

    document.getElementById(
        'starNumbers'
    ).innerText =
        '★ ' + stars.join(' ★ ');

    document.getElementById(
        'vikingNumbers'
    ).innerText =
        viking.join(', ');

    //
    // VISA BOXAR
    //

    document.getElementById(
        'lottoBox'
    ).style.display='block';

    document.getElementById(
        'euroBox'
    ).style.display='block';

    document.getElementById(
        'vikingBox'
    ).style.display='block';

    document.getElementById(
        'historyBox'
    ).style.display='block';

    //
    // HISTORIK
    //

    let profile =
        document.getElementById(
            'profileName'
        ).value || 'Spelare';

    let favoriteGame =
        document.getElementById(
            'favoriteGame'
        ).value;

    document.getElementById(
        'history'
    ).innerHTML =

        "<div class='historyItem'>" +

        "<b>" + profile + "</b><br><br>" +

        "Favoritspel: " +
        favoriteGame + "<br>" +

        "Turmotor: " +
        document.getElementById(
            'luckMode'
        ).selectedOptions[0].text +
        "<br><br>" +

        "🇸🇪 Lotto:<br>" +
        lotto.join(', ') +
        "<br><br>" +

        "🇪🇺 Eurojackpot:<br>" +
        euro.join(', ') +
        "<br><br>" +

        "⚔️ Vikinglotto:<br>" +
        viking.join(', ') +

        "</div>";

    //
    // TAL
    //

    latestSpeech =

        profile +

        ". Dina Lotto nummer är " +

        lotto.join(', ') +

        ". Dina Eurojackpot nummer är " +

        euro.join(', ') +

        ". Dina Vikinglotto nummer är " +

        viking.join(', ');

    //
    // SPARA
    //

    saveData();

    //
    // VIBRATION
    //

    if(navigator.vibrate){

        navigator.vibrate([150,100,150]);
    }
}

//
// TALSYNTES
//

function speakResults(){

    if(!latestSpeech){

        alert("Generera nummer först");

        return;
    }

    let speech =
        new SpeechSynthesisUtterance(
            latestSpeech
        );

    speech.lang = 'sv-SE';

    speech.rate = 0.9;

    speechSynthesis.speak(speech);
}

//
// SPARA
//

function saveData(){

    const data = {

        profileName:
            document.getElementById(
                'profileName'
            ).value,

        favoriteGame:
            document.getElementById(
                'favoriteGame'
            ).value,

        birthdate:
            document.getElementById(
                'birthdate'
            ).value,

        zodiac:
            document.getElementById(
                'zodiac'
            ).value,

        lottoFavorites:
            document.getElementById(
                'lottoFavorites'
            ).value,

        euroFavorites:
            document.getElementById(
                'euroFavorites'
            ).value,

        luckMode:
            document.getElementById(
                'luckMode'
            ).value,

        lottoSystem:
            document.getElementById(
                'lottoSystem'
            ).value,

        euroSystem:
            document.getElementById(
                'euroSystem'
            ).value,

        theme:
            document.getElementById(
                'themeSelect'
            ).value
    };

    localStorage.setItem(
        'tagGeneratorV7',
        JSON.stringify(data)
    );
}

//
// LADDA
//

function loadData(){

    let saved =
        localStorage.getItem(
            'tagGeneratorV7'
        );

    if(!saved) return;

    let data =
        JSON.parse(saved);

    Object.keys(data)
    .forEach(key => {

        let el =
            document.getElementById(
                key
            );

        if(el){

            el.value = data[key];
        }
    });

    applyTheme();
}

//
// TEMA
//

function applyTheme(){

    document.body.className =
        document.getElementById(
            'themeSelect'
        ).value;

    saveData();
}

document.getElementById(
    'themeSelect'
).addEventListener(
    'change',
    applyTheme
);

window.onload = loadData;

</script>

</body>
</html>