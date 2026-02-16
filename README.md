index.html
<!DOCTYPE html>
<html>
<head>
<title>Happy Birthday 🎂</title>
<style>
body{
    margin:0;
    padding:0;
    font-family: Arial, sans-serif;
    text-align:center;
    background: linear-gradient(135deg,#000000,#0a1f44,#800000);
    color:white;
}

.container{
    margin-top:100px;
}

h1{
    font-size:40px;
    color:#00bfff;
    animation: glow 2s infinite alternate;
}

@keyframes glow{
    from{ text-shadow:0 0 10px #00bfff; }
    to{ text-shadow:0 0 25px #800000; }
}

p{
    font-size:20px;
    margin:20px;
}

button{
    padding:12px 25px;
    font-size:18px;
    border:none;
    border-radius:25px;
    background:#800000;
    color:white;
    cursor:pointer;
    transition:0.3s;
}

button:hover{
    background:#00bfff;
    transform:scale(1.1);
}

.heart{
    font-size:30px;
    animation: float 3s infinite;
}

@keyframes float{
    0%{transform:translateY(0);}
    50%{transform:translateY(-20px);}
    100%{transform:translateY(0);}
}
</style>
</head>

<body>

<div class="container">
    <h1>Happy Birthday Princess 👑</h1>
    <p>May your day be filled with love, smiles and happiness 💙</p>
    <p>You are special, beautiful and amazing ✨</p>
    <div class="heart">💙 💖 💙</div>
    <br><br>
    <button onclick="showMessage()">Click for Surprise 🎁</button>
</div>

<script>
function showMessage(){
    alert("Wishing you endless happiness and sweet memories 💕🎂");
}
</script>

</body>
</html>
