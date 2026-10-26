
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Color Palette Generator</title>
<style>
body{margin:0;padding:25px;background:#111827;color:white;font-family:Arial;text-align:center}
h1{margin-top:25px}
.palette{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:12px;margin:35px auto;max-width:800px}
.color{height:180px;border-radius:14px;display:flex;align-items:end;justify-content:center;padding:12px;box-sizing:border-box;font-weight:bold;cursor:pointer;box-shadow:0 5px 20px #0003}
button{padding:13px 20px;background:#a78bfa;color:#160d2d;border:0;border-radius:9px;font-weight:bold;cursor:pointer}
p{color:#cbd5e1}
</style>
</head>
<body>
<h1>🎨 Color Palette Generator</h1>
<p>Generate colors for your next website design.</p>
<button onclick="generate()">Generate New Palette</button>
<div class="palette" id="palette"></div>
<p id="message">Tap a color to copy its HEX code.</p>
<script>
function generate(){
const palette=document.getElementById("palette");
palette.innerHTML="";
for(let i=0;i<5;i++){
const hex="#"+Math.floor(Math.random()*16777216).toString(16).padStart(6,"0");
const card=document.createElement("div");
card.className="color";
card.style.background=hex;
card.style.color="white";
card.style.textShadow="0 1px 4px #000";
card.textContent=hex.toUpperCase();
card.onclick=async()=>{
try{
await navigator.clipboard.writeText(hex);
document.getElementById("message").textContent="Copied "+hex.toUpperCase();
}catch(e){
document.getElementById("message").textContent="HEX code: "+hex.toUpperCase();
}
};
palette.appendChild(card);
}
}
generate();
</script>
</body>
</html>
# color-palette-generator
