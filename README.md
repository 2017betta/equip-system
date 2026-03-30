[STEP1.html](https://github.com/user-attachments/files/26354880/STEP1.html)
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>裝備平台｜STEP1升級版</title>

<script src="https://cdn.jsdelivr.net/npm/jsbarcode@3.11.6/dist/JsBarcode.all.min.js"></script>
<script src="https://unpkg.com/html5-qrcode"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<style>
body{margin:0;font-family:Arial;background:#d9f1ff;text-align:center}
.topbar{background:#0b3d91;color:white;padding:16px;font-size:28px}
.panel{background:white;width:min(95vw,1200px);margin:20px auto;padding:20px;border-radius:12px}

button{padding:10px 14px;margin:5px;border-radius:8px;border:none;cursor:pointer}
.primary{background:#0b3d91;color:white}
.secondary{background:white;border:2px solid #0b3d91;color:#0b3d91}
.active{background:#2563eb!important;color:white}

.section{display:none;margin-top:20px}

/* 🔥 超小貼紙 */
.label-grid{
display:grid;
grid-template-columns:repeat(4,1fr);
gap:6px;
}
.label{
border:1px solid #000;
padding:5px;
font-size:10px;
position:relative;
height:120px;
}
.watermark{
position:absolute;
opacity:0.07;
font-size:26px;
top:40%;
left:50%;
transform:translate(-50%,-50%) rotate(-20deg);
}

#readerOut{width:300px;margin:auto}
</style>
</head>

<body>

<div class="topbar">裝備平台 STEP1</div>

<div id="loginArea" class="panel">
<button onclick="login('jerry')">佳祐</button>
<button onclick="login('msmdick')">土豆</button>
</div>

<div id="main" class="panel" style="display:none">

<button id="btnIn" class="primary" onclick="show('in')">進貨</button>
<button id="btnOut" class="primary" onclick="show('out')">出貨</button>

<div id="in" class="section">
<h3>進貨</h3>

<button onclick="selectProduct('MH','梅花帽')">梅花帽</button>
<button onclick="selectProduct('GL','護具')">護具</button>

<br>

<button onclick="setSize('S')">S</button>
<button onclick="setSize('M')">M</button>

<br>

<input id="qty" type="number" value="1">

<button onclick="gen()">產生</button>

<div id="labels" class="label-grid"></div>

<button onclick="window.print()">列印</button>

</div>

<div id="out" class="section">
<h3>出貨</h3>

<input id="outCode">
<button onclick="out()">出貨</button>

<h4>掃描</h4>
<div id="readerOut"></div>
<button onclick="scan()">開始掃描</button>

</div>

</div>

<script>

let current="";
let pCode="",pName="",size="";
let counter={};
let stock={};

function login(user){
current=user;
document.getElementById("loginArea").style.display="none";
document.getElementById("main").style.display="block";
}

function show(id){
document.querySelectorAll(".section").forEach(s=>s.style.display="none");
document.getElementById(id).style.display="block";

document.getElementById("btnIn").classList.remove("active");
document.getElementById("btnOut").classList.remove("active");

if(id==="in") document.getElementById("btnIn").classList.add("active");
if(id==="out") document.getElementById("btnOut").classList.add("active");
}

function selectProduct(c,n){pCode=c;pName=n}
function setSize(s){size=s}

function gen(){
let q=document.getElementById("qty").value;
let grid=document.getElementById("labels");
grid.innerHTML="";

for(let i=0;i<q;i++){
let num=String(counter[pCode+size]||1).padStart(4,"0");
let code=pCode+"-"+size+num;

stock[code]={name:pName,size:size};

let div=document.createElement("div");
div.className="label";

let id="b"+code;
let qr="q"+code;

div.innerHTML=`
<div class="watermark">BETTA</div>
${pName}<br>${size}
<div id="${qr}"></div>
<svg id="${id}"></svg>
${code}
`;

grid.appendChild(div);

JsBarcode("#"+id,code,{width:1,height:25,displayValue:false});
new QRCode(document.getElementById(qr),{text:code,width:40,height:40});

counter[pCode+size]=(counter[pCode+size]||1)+1;
}
}

function out(){
let code=document.getElementById("outCode").value;
if(!stock[code]) return alert("錯誤");

delete stock[code];
alert("出貨成功");
}

let scanner;

function scan(){
if(scanner) return;

scanner=new Html5Qrcode("readerOut");

scanner.start(
{ facingMode: "environment" },
{ fps:10, qrbox:200 },
(txt)=>{
document.getElementById("outCode").value=txt;
out();

// 🔥 不停止 = 連續掃描
},
()=>{}
);
}

</script>

</body>
</html>
