[equip_system_business_v14_login_fixed.html](https://github.com/user-attachments/files/26414672/equip_system_business_v14_login_fixed.html)
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>裝備平台｜商業最終整合版 v14</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<style>
:root{
  --blue:#0b3d91; --blue2:#144fb8; --line:#dbe7f3; --text:#101828; --muted:#667085;
  --danger:#b91c1c; --ok:#15803d; --shadow:0 14px 30px rgba(11,61,145,.08)
}
*{box-sizing:border-box}
html,body{margin:0;padding:0;font-family:Arial,sans-serif;color:var(--text);background:linear-gradient(180deg,#e8f4ff 0%,#f8fbff 100%)}
.topbar{background:linear-gradient(90deg,var(--blue),var(--blue2));color:#fff;text-align:center;padding:18px 14px;font-size:clamp(24px,4vw,32px);font-weight:900}
.wrap{max-width:1380px;margin:18px auto;padding:0 14px 30px}
.panel{background:#fff;border-radius:24px;padding:26px;border:1px solid rgba(11,61,145,.08);box-shadow:var(--shadow)}
.center{text-align:center}.hidden{display:none!important}
.row{display:flex;flex-wrap:wrap;gap:22px;justify-content:center;align-items:center}
.main-buttons{display:flex;flex-wrap:wrap;gap:18px;justify-content:center;margin-bottom:24px}
button{border:none;border-radius:14px;padding:13px 22px;font-size:16px;font-weight:700;cursor:pointer;min-height:50px}
.primary{background:linear-gradient(180deg,var(--blue2),var(--blue));color:#fff}
.secondary{background:#fff;color:var(--blue);border:2px solid var(--blue)}
.active-btn,.login-active,.pick-active{background:linear-gradient(180deg,var(--blue2),var(--blue))!important;color:#fff!important;border-color:var(--blue)!important}
.mode-card{background:linear-gradient(180deg,#fff,#fbfdff);border:1px solid var(--line);border-radius:20px;padding:32px 28px;margin:0 auto 32px auto}
.mode-title{font-size:clamp(22px,3.4vw,30px);font-weight:900;margin-bottom:18px;text-align:center}
.section{display:none}
input,textarea,select{border:1px solid #c8d6e5;border-radius:12px;padding:12px 14px;font-size:16px;background:#fff;max-width:100%}
textarea{width:min(96vw,420px);height:92px;resize:vertical}
.notice{font-size:14px;color:var(--muted);line-height:1.5}
.summary-box{max-width:1100px;margin:22px auto;background:#fff;border:1px solid var(--line);border-radius:18px;padding:20px;line-height:2}
.toast{position:fixed;top:16px;left:50%;transform:translateX(-50%);background:var(--blue);color:#fff;padding:12px 16px;border-radius:12px;opacity:0;pointer-events:none;transition:.2s;z-index:9999}.toast.show{opacity:1}
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:22px}
.stock-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:18px;align-items:start}
.stock-3>div{min-width:0}
.login-grid{display:grid;grid-template-columns:repeat(3,minmax(120px,1fr));gap:14px;max-width:760px;margin:0 auto 8px}
.login-grid button{width:100%}
.login-box{max-width:460px;margin:18px auto 0}
.kpis{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-top:16px}
.kpi{background:#fff;border:1px solid var(--line);border-radius:16px;padding:16px}
.kpi .l{font-size:13px;color:var(--muted);font-weight:800}.kpi .v{font-size:32px;font-weight:900;margin-top:8px}
.rank-box{max-width:1100px;margin:14px auto 0 auto;background:#fff;border:1px solid var(--line);border-radius:16px;padding:14px}
.rank-item{display:flex;justify-content:space-between;align-items:center;padding:9px 0;border-bottom:1px dashed #e7eef7}.rank-item:last-child{border-bottom:none}
table{width:100%;border-collapse:collapse;margin-top:10px;background:#fff}
th,td{border:1px solid #e6eaf0;padding:10px;text-align:center;vertical-align:middle}
th{background:#f8fafc}.table-wrap{overflow:auto}
.low-stock-row td{background:#fff5f5}.danger{color:var(--danger);font-weight:800}.ok{color:var(--ok);font-weight:800}
#productButtons,#sizeButtons{gap:20px 28px;margin-bottom:18px}
#qtyRow{margin-top:18px;gap:18px}
#labelsBox{display:grid;grid-template-columns:repeat(auto-fill,minmax(250px,1fr));gap:28px;max-width:1180px;margin:24px auto 0}
.label{position:relative;border:1px solid #222;border-radius:16px;padding:18px;min-height:260px;background:#fff;overflow:hidden;display:flex;flex-direction:column;align-items:center;justify-content:flex-start}
.wm{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-size:30px;font-weight:900;opacity:.08;transform:rotate(-18deg);pointer-events:none}
.label-top,.label-size,.label-code{position:relative;z-index:2;text-align:center}
.label-top{font-size:20px;font-weight:900;margin-top:2px}
.label-size{font-size:16px;margin:8px 0 12px}
.label-code{font-size:14px;line-height:1.25;word-break:break-all;margin-top:12px}
.code-row{position:relative;z-index:2;display:flex;justify-content:center;align-items:center;gap:18px;width:100%;margin-top:10px}
.qr-box,.barcode-box{display:flex;justify-content:center;align-items:center}
.barcode-box svg{width:138px;height:52px}
.reader{width:min(96vw,460px);margin:12px auto;min-height:40px}
.reader video{width:100%;display:block;border-radius:14px;border:1px solid var(--line);background:#000}
.scan-status{font-size:13px;color:var(--muted);text-align:center;margin-top:10px}
.chart-wrap{max-width:1100px;margin:0 auto;background:#fff;border:1px solid var(--line);border-radius:18px;padding:14px}
#reportSvg{width:100%;height:auto;display:block}
.small-btn{padding:7px 10px;font-size:14px;border-radius:999px}
.history-box{max-width:1100px;margin:22px auto 0;background:#fff;border:1px solid var(--line);border-radius:16px;padding:14px}
.print-hint{font-size:13px;color:#667085;text-align:center;margin-top:8px}
@media (max-width:1024px){.kpis{grid-template-columns:repeat(2,1fr)}}
@media (max-width:900px){
  .grid-2{grid-template-columns:1fr}
  .main-buttons button{flex:1 1 42%}
  #labelsBox{grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:20px}
}
@media (max-width:560px){
  .kpis{grid-template-columns:1fr}
  button{width:100%}
  #labelsBox{grid-template-columns:1fr}
  .code-row{flex-direction:column}
  #productButtons,#sizeButtons{gap:16px}
  #qtyRow{flex-direction:column;gap:14px}
}
</style>
</head>
<body>
<div class="topbar">裝備平台｜商業最終整合版 v14</div>
<div id="toast" class="toast"></div>

<div class="wrap">
  <div id="loginView" class="panel center">
    <h2>登入</h2>
    <div id="loginRow" class="login-grid">
      <button id="login-jerry" class="secondary" onclick="selectCoach('jerry')">佳祐</button>
      <button id="login-msmdick" class="secondary" onclick="selectCoach('msmdick')">土豆</button>
      <button id="login-h072012" class="secondary" onclick="selectCoach('h072012')">小宇</button>
      <button id="login-zemo" class="secondary" onclick="selectCoach('zemo')">阿澤</button>
      <button id="login-ma" class="secondary" onclick="selectCoach('ma')">小馬</button>
      <button id="login-chuu" class="secondary" onclick="selectCoach('chuu')">莉筑</button>
    </div>
    <div class="mode-card login-box">
      <div class="mode-title">輸入密碼</div>
      <div id="selectedUserText" class="notice">請先選擇人員</div>
      <div class="row"><input id="pwInput" type="password" placeholder="密碼" onkeydown="if(event.key==='Enter') login()"></div>
      <div class="row"><button class="primary" onclick="login()">登入</button></div>
    </div>
  </div>

  <div id="appView" class="panel hidden">
    <h2 class="center" id="welcomeText"></h2>

    <div class="main-buttons">
      <button id="navIn" class="secondary" onclick="showView('in')">📦進貨</button>
      <button id="navOut" class="secondary" onclick="showView('out')">📤出貨</button>
      <button id="navStock" class="secondary" onclick="showView('stock')">📋庫存</button>
      <button id="navReport" class="secondary" onclick="showView('report')">📊報表</button>
      <button class="primary" onclick="toggleBigMode()">🔍大字模式</button>
      <button class="primary" onclick="logout()">🚪登出</button>
    </div>

    <section id="viewIn" class="section">
      <div class="mode-card">
        <div class="mode-title">步驟1：印貼紙</div>
        <div class="row" id="productButtons"></div>
        <div class="row" id="sizeButtons" style="display:none"></div>
        <div class="row" id="qtyRow" style="display:none">
          <input id="qtyInput" type="number" min="1" value="1" style="max-width:180px">
          <button class="primary" onclick="createPrintedLabels()">產生貼紙</button>
        </div>
      </div>

      <div class="mode-card">
        <div class="mode-title">步驟2：掃描或輸入後入庫</div>
        <div class="row">
          <input id="inCodeInput" placeholder="輸入條碼">
          <button class="primary" onclick="addToStock(document.getElementById('inCodeInput').value)">手動回庫</button>
        </div>
        <div id="readerIn" class="reader"></div>
        <div id="scanStatusIn" class="scan-status">電腦不支援鏡頭掃描時，可直接用掃描槍或手動輸入條碼後按 Enter。</div>
        <div class="row">
          <button class="primary" onclick="startScan('in')">開始掃描進貨</button>
          <button class="secondary" onclick="stopScan('in')">停止掃描進貨</button>
        </div>
      </div>

      <div id="printSummary" class="summary-box center"></div>
      <div class="row"><button class="primary" onclick="printLabels()">🖨️列印貼紙</button></div>
      <div class="print-hint">列印版面已調整成置中、放大、間距拉開。</div>
      <div id="labelsBox"></div>
    </section>

    <section id="viewOut" class="section">
      <div class="mode-card">
        <div class="mode-title">出貨</div>
        <div class="row">
          <input id="outCodeInput" placeholder="輸入條碼">
          <button class="primary" onclick="stockOut(document.getElementById('outCodeInput').value)">確認出貨</button>
        </div>
        <div id="readerOut" class="reader"></div>
        <div id="scanStatusOut" class="scan-status">電腦不支援鏡頭掃描時，可直接用掃描槍或手動輸入條碼後按 Enter。</div>
        <div class="row">
          <button class="primary" onclick="startScan('out')">開始掃描出貨</button>
          <button class="secondary" onclick="stopScan('out')">停止掃描出貨</button>
        </div>
      </div>

      <div class="history-box">
        <div class="mode-title" style="font-size:24px;margin-bottom:6px">最近出貨紀錄</div>
        <div class="table-wrap">
          <table id="shipLogTable">
            <tr><th>出貨人</th><th>品項</th><th>尺寸</th><th>條碼</th><th>時間</th></tr>
          </table>
        </div>
      </div>
    </section>

    <section id="viewStock" class="section">
      <div id="stockDashboard"></div>
      <div id="stockAddBox" class="mode-card hidden">
        <div class="mode-title">➕新增商品</div>
        <div class="row"><input id="newNameInput" placeholder="商品名稱，例如 手套"></div>
        <div class="row"><textarea id="newSizesInput" placeholder="尺寸，用逗號分隔，例如 XS,S,M,L 或 13J,10J,2,4"></textarea></div>
        <div class="row"><button class="primary" onclick="addProduct()">新增</button></div>
      </div>
    </section>

    <section id="viewReport" class="section">
      <div class="mode-card">
        <div class="mode-title">報表</div>
        <div class="row center">
          <label>年份：</label>
          <select id="reportYearSelect" onchange="renderReport()"></select>
          <label>模式：</label>
          <select id="reportModeSelect" onchange="renderReport()">
            <option value="month">月報</option>
            <option value="year">年報</option>
          </select>
          <button class="primary" onclick="exportDetailedReportExcel()">匯出Excel</button>
        </div>
        <div id="kpis" class="kpis"></div>
        <div class="chart-wrap center"><svg id="reportSvg" viewBox="0 0 980 360" preserveAspectRatio="none"></svg></div>
        <div id="ranking" class="rank-box"></div>
        <div id="reportSummary" class="summary-box"></div>
      </div>
    </section>
  </div>
</div>

<script>
const USERS={jerry:{password:"0606",name:"佳祐"},msmdick:{password:"1111",name:"土豆"},h072012:{password:"2222",name:"小宇"},zemo:{password:"3333",name:"阿澤"},ma:{password:"5555",name:"小馬"},chuu:{password:"6666",name:"莉筑"}};
const DEFAULT_PRODUCTS={MH:{name:"梅花帽",sizes:["XS","S","M","L","XL"]},GL:{name:"護具",sizes:["XS","S","M","L","XL"]},SK:{name:"鞋子",sizes:["13J","10J","2","4","6","8","10","12"]},CL:{name:"衣服",sizes:["8","12","14","XS","S","M","L","XL"]}};
let state={currentUserKey:"",currentUserName:"",isAdmin:false,products:{},stock:{},logs:[],counter:{},printedRegistry:{},selectedProductCode:"",selectedSize:"",scanIn:null,scanOut:null};

function toast(msg){const el=document.getElementById("toast");el.textContent=msg;el.classList.add("show");clearTimeout(window.__toastTimer);window.__toastTimer=setTimeout(()=>el.classList.remove("show"),1600);}
function saveState(){localStorage.setItem("equip_products_v8",JSON.stringify(state.products));localStorage.setItem("equip_stock_v8",JSON.stringify(state.stock));localStorage.setItem("equip_logs_v8",JSON.stringify(state.logs));localStorage.setItem("equip_counter_v8",JSON.stringify(state.counter));localStorage.setItem("equip_printed_v8",JSON.stringify(state.printedRegistry));}
function loadState(){try{state.products=JSON.parse(localStorage.getItem("equip_products_v8")||"null")||JSON.parse(JSON.stringify(DEFAULT_PRODUCTS));state.stock=JSON.parse(localStorage.getItem("equip_stock_v8")||"{}");state.logs=JSON.parse(localStorage.getItem("equip_logs_v8")||"[]");state.counter=JSON.parse(localStorage.getItem("equip_counter_v8")||"{}");state.printedRegistry=JSON.parse(localStorage.getItem("equip_printed_v8")||"{}");}catch(e){state.products=JSON.parse(JSON.stringify(DEFAULT_PRODUCTS));state.stock={};state.logs=[];state.counter={};state.printedRegistry={};}}
function getCurrentYear(){return new Date().getFullYear();}
function getCurrentMonth(){return new Date().getMonth()+1;}
function parseDateSafe(value){const d=new Date(value||"");return Number.isNaN(d.getTime())?null:d;}
function getYearFromTimeString(value){const d=parseDateSafe(value);if(d) return d.getFullYear();const m=String(value||"").match(/(20\d{2})/);return m?parseInt(m[1],10):getCurrentYear();}
function getMonthFromTimeString(value){const d=parseDateSafe(value);if(d) return d.getMonth()+1;return 1;}

function selectCoach(key){
  state.currentUserKey=key;
  document.getElementById("selectedUserText").textContent="已選擇："+USERS[key].name;
  document.querySelectorAll("#loginRow button").forEach(btn=>btn.classList.remove("login-active"));
  const picked=document.getElementById("login-"+key);
  if(picked)picked.classList.add("login-active");
  const pw=document.getElementById("pwInput");
  if(pw) pw.focus();
}
function login(){
  const key=state.currentUserKey;
  const pw=document.getElementById("pwInput").value.trim();
  if(!key){alert("請先選擇人員");return;}
  if(String(USERS[key].password)!==String(pw)){alert("密碼錯誤");document.getElementById("pwInput").focus();return;}
  state.currentUserName=USERS[key].name;
  state.isAdmin=(key==="jerry");
  document.getElementById("loginView").classList.add("hidden");
  document.getElementById("appView").classList.remove("hidden");
  document.getElementById("welcomeText").textContent="歡迎 "+state.currentUserName;
  document.getElementById("pwInput").value="";
  renderProductButtons();
  populateReportYears();
  showView("stock");
}
function logout(){stopScan('in');stopScan('out');state.currentUserKey="";state.currentUserName="";state.isAdmin=false;state.selectedProductCode="";state.selectedSize="";document.getElementById("appView").classList.add("hidden");document.getElementById("loginView").classList.remove("hidden");document.querySelectorAll("#loginRow button").forEach(btn=>btn.classList.remove("login-active"));document.getElementById("selectedUserText").textContent="請先選擇人員";toast("已登出");}
function showView(view){
  document.querySelectorAll(".section").forEach(el=>el.style.display="none");
  ["navIn","navOut","navStock","navReport"].forEach(id=>document.getElementById(id).classList.remove("active-btn"));
  if(view==="in"){
    if(!state.isAdmin){alert("只有佳祐可以進貨");return;}
    document.getElementById("viewIn").style.display="block";
    document.getElementById("navIn").classList.add("active-btn");
  }else if(view==="out"){
    document.getElementById("viewOut").style.display="block";
    document.getElementById("navOut").classList.add("active-btn");
    renderShipLogs();
  }else if(view==="stock"){
    document.getElementById("viewStock").style.display="block";
    document.getElementById("navStock").classList.add("active-btn");
    document.getElementById("stockAddBox").classList.toggle("hidden",!state.isAdmin);
    renderDashboard();
  }else if(view==="report"){
    document.getElementById("viewReport").style.display="block";
    document.getElementById("navReport").classList.add("active-btn");
    populateReportYears();
    renderReport();
  }
}
function toggleBigMode(){document.body.classList.toggle("big-mode");toast(document.body.classList.contains("big-mode")?"大字模式開啟":"大字模式關閉");}

function renderProductButtons(){const box=document.getElementById("productButtons");box.innerHTML="";Object.keys(state.products).forEach(code=>{const p=state.products[code];const btn=document.createElement("button");btn.className="secondary";btn.textContent=p.name;btn.onclick=()=>{state.selectedProductCode=code;state.selectedSize="";[...box.children].forEach(b=>b.classList.remove("pick-active"));btn.classList.add("pick-active");renderSizeButtons(p.sizes||[]);document.getElementById("qtyRow").style.display="flex";};box.appendChild(btn);});}
function renderSizeButtons(sizes){const box=document.getElementById("sizeButtons");box.innerHTML="";sizes.forEach(size=>{const btn=document.createElement("button");btn.className="secondary";btn.textContent=size;btn.onclick=()=>{state.selectedSize=size;[...box.children].forEach(b=>b.classList.remove("pick-active"));btn.classList.add("pick-active");};box.appendChild(btn);});box.style.display="flex";}
function generateProductCode(){let i=1,code="";do{code="PR"+String(i).padStart(3,"0");i++;}while(state.products[code]);return code;}
function addProduct(){if(!state.isAdmin){alert("只有佳祐可以新增商品");return;}const name=document.getElementById("newNameInput").value.trim();const sizes=document.getElementById("newSizesInput").value.split(",").map(s=>s.trim().toUpperCase()).filter(Boolean);if(!name||!sizes.length){alert("請輸入商品名稱與尺寸");return;}const code=generateProductCode();state.products[code]={name,sizes};saveState();document.getElementById("newNameInput").value="";document.getElementById("newSizesInput").value="";renderProductButtons();toast("新增商品："+name);}

const CODE39={'0':'nnnwwnwnn','1':'wnnwnnnnw','2':'nnwwnnnnw','3':'wnwwnnnnn','4':'nnnwwnnnw','5':'wnnwwnnnn','6':'nnwwwnnnn','7':'nnnwnnwnw','8':'wnnwnnwnn','9':'nnwwnnwnn','A':'wnnnnwnnw','B':'nnwnnwnnw','C':'wnwnnwnnn','D':'nnnnwwnnw','E':'wnnnwwnnn','F':'nnwnwwnnn','G':'nnnnnwwnw','H':'wnnnnwwnn','I':'nnwnnwwnn','J':'nnnnwwwnn','K':'wnnnnnnww','L':'nnwnnnnww','M':'wnwnnnnwn','N':'nnnnwnnww','O':'wnnnwnnwn','P':'nnwnwnnwn','Q':'nnnnnnwww','R':'wnnnnnwwn','S':'nnwnnnwwn','T':'nnnnwnwwn','U':'wwnnnnnnw','V':'nwwnnnnnw','W':'wwwnnnnnn','X':'nwnnwnnnw','Y':'wwnnwnnnn','Z':'nwwnwnnnn','-':'nwnnnnwnw','.':'wwnnnnwnn',' ':'nwwnnnwnn','$':'nwnwnwnnn','/':'nwnwnnnwn','+':'nwnnnwnwn','%':'nnnwnwnwn','*':'nwnnwnwnn'};
function createCode39Svg(text){
  text='*'+String(text).toUpperCase()+'*';
  const narrow=2, wide=5, gap=2, h=42;
  let x=8, svg=['<svg xmlns="http://www.w3.org/2000/svg" width="138" height="52" viewBox="0 0 138 52">'];
  for(let c=0;c<text.length;c++){
    const patt=CODE39[text[c]] || CODE39['-'];
    for(let i=0;i<patt.length;i++){
      const w=(patt[i]==='w'?wide:narrow), isBar=i%2===0;
      if(isBar) svg.push('<rect x="'+x+'" y="4" width="'+w+'" height="'+h+'" fill="#000"/>');
      x+=w;
    }
    x+=gap;
  }
  svg.push('</svg>');
  return svg.join('');
}
function renderQrInto(el,text){
  if(window.QRCode){
    el.innerHTML='';
    new QRCode(el,{text:text,width:84,height:84});
  }else{
    el.innerHTML='<div style="width:84px;height:84px;border:1px solid #999;display:flex;align-items:center;justify-content:center;font-size:10px">QR</div>';
  }
}
function createPrintedLabels(){
  const code=state.selectedProductCode, size=state.selectedSize, qty=parseInt(document.getElementById("qtyInput").value||"0",10);
  if(!code||!size||!qty||qty<1){alert("請先選商品、尺寸、數量");return;}
  const key=code+"-"+size;
  if(!state.counter[key]) state.counter[key]=1;
  const name=state.products[code].name;
  const labelsBox=document.getElementById("labelsBox");
  labelsBox.innerHTML="";
  let first="",last="",qrJobs=[];
  for(let i=0;i<qty;i++){
    const num=String(state.counter[key]).padStart(4,"0");
    const fullCode=code+"-"+size+num;
    if(i===0) first=fullCode;
    last=fullCode;
    state.printedRegistry[fullCode]={name,size,productCode:code,code:fullCode,printedTime:new Date().toLocaleString(),scannedIn:false};
    const qrId='qr_'+fullCode.replace(/[^A-Za-z0-9]/g,'');
    const div=document.createElement("div");
    div.className="label";
    div.innerHTML='<div class="wm">BETTA</div><div class="label-top">'+name+'</div><div class="label-size">尺寸：'+size+'</div><div class="code-row"><div class="qr-box" id="'+qrId+'"></div><div class="barcode-box">'+createCode39Svg(fullCode)+'</div></div><div class="label-code">'+fullCode+'</div>';
    labelsBox.appendChild(div);
    qrJobs.push({id:qrId,text:fullCode});
    state.counter[key]++;
  }
  saveState();
  document.getElementById("printSummary").innerHTML='✅ 貼紙已建立<br>物品：'+name+'<br>尺寸：'+size+'<br>數量：'+qty+'<br>條碼範圍：'+first+' ～ '+last;
  qrJobs.forEach(job=>{const el=document.getElementById(job.id); if(el) renderQrInto(el,job.text);});
  renderDashboard();
  toast("貼紙已建立");
}
function printLabels(){
  const content=document.getElementById("labelsBox").innerHTML;
  if(!content.trim()){alert("沒有可列印的貼紙");return;}
  const w=window.open("","_blank","width=1080,height=900");
  w.document.write('<html><head><meta charset="UTF-8"><title>列印貼紙</title><style>@page{margin:4mm}body{font-family:Arial;padding:0}.grid{display:grid;grid-template-columns:repeat(2,90mm);justify-content:center;gap:8mm}.label{position:relative;border:1px solid #222;border-radius:12px;padding:10px;min-height:70mm;background:#fff;overflow:hidden;display:flex;flex-direction:column;align-items:center}.wm{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;font-size:30px;font-weight:900;opacity:.08;transform:rotate(-18deg)}.label-top{text-align:center;font-weight:900;font-size:18px}.label-size{text-align:center;font-size:16px;margin:6px 0 10px}.label-code{text-align:center;font-size:14px;line-height:1.2;word-break:break-all;margin-top:10px}.code-row{display:flex;justify-content:center;align-items:center;gap:14px;width:100%;margin-top:8px}.barcode-box svg{width:138px;height:52px}.qr-box{min-width:84px;min-height:84px;display:flex;align-items:center;justify-content:center}</style></head><body><div class="grid">'+content+'</div></body></html>');
  w.document.close();
  setTimeout(()=>w.print(),700);
}

function addToStock(code){
  code=String(code||"").trim().toUpperCase();
  if(!state.isAdmin){alert("只有佳祐可以進貨");return;}
  if(!state.printedRegistry[code]){alert("此條碼尚未印製");return;}
  if(state.printedRegistry[code].scannedIn){alert("此條碼已入庫");return;}
  const item=state.printedRegistry[code];
  state.stock[code]={name:item.name,size:item.size,productCode:item.productCode,code:item.code,status:"in",inTime:new Date().toLocaleString(),outTime:""};
  state.printedRegistry[code].scannedIn=true;
  saveState();
  document.getElementById("inCodeInput").value="";
  renderDashboard();
  toast("已加入庫存");
}
function stockOut(code){
  code=String(code||"").trim().toUpperCase();
  if(!state.stock[code]){alert("查無此條碼");return;}
  if(state.stock[code].status==="out"){alert("這件已出貨");return;}
  const item=state.stock[code];
  item.status="out";
  item.outTime=new Date().toLocaleString();
  state.logs.push({user:state.currentUserName,name:item.name,size:item.size,code:item.code,time:item.outTime});
  saveState();
  document.getElementById("outCodeInput").value="";
  renderDashboard();
  renderShipLogs();
  toast("已出貨");
}
document.addEventListener('DOMContentLoaded',()=>{
  const inInput=document.getElementById('inCodeInput');
  const outInput=document.getElementById('outCodeInput');
  inInput.addEventListener('keydown',e=>{if(e.key==='Enter'){addToStock(inInput.value);}});
  outInput.addEventListener('keydown',e=>{if(e.key==='Enter'){stockOut(outInput.value);}});
});

function renderShipLogs(){
  const tbody=document.getElementById('shipLogTable');
  if(!tbody) return;
  const logs=[...state.logs].reverse().slice(0,50);
  tbody.innerHTML='<tr><th>出貨人</th><th>品項</th><th>尺寸</th><th>條碼</th><th>時間</th></tr>' + (logs.length ? logs.map(l=>'<tr><td>'+l.user+'</td><td>'+l.name+'</td><td>'+l.size+'</td><td>'+l.code+'</td><td>'+l.time+'</td></tr>').join('') : '<tr><td colspan="5">目前沒有出貨紀錄</td></tr>');
}

function setScanStatus(target,msg){document.getElementById(target==='in'?'scanStatusIn':'scanStatusOut').textContent=msg;}
async function startScan(target){
  const holder=document.getElementById(target==='in'?'readerIn':'readerOut');
  const stateKey=target==='in'?'scanIn':'scanOut';
  const handler=target==='in'?addToStock:stockOut;
  stopScan(target);
  if(!('BarcodeDetector' in window)){
    setScanStatus(target,'這台裝置的瀏覽器不支援原生掃描，請直接輸入條碼或用掃描槍。');
    return;
  }
  try{
    const formats=await BarcodeDetector.getSupportedFormats();
    const want=['code_39','code_128','qr_code'].filter(f=>formats.includes(f));
    if(!want.length){setScanStatus(target,'這台裝置沒有可用的掃描格式，請直接輸入條碼或用掃描槍。');return;}
    const stream=await navigator.mediaDevices.getUserMedia({video:{facingMode:'environment'}});
    const video=document.createElement('video');
    video.setAttribute('playsinline','true');
    video.autoplay=true; video.muted=true; video.srcObject=stream;
    holder.innerHTML=''; holder.appendChild(video);
    const detector=new BarcodeDetector({formats:want});
    const loop=async()=>{
      if(!state[stateKey]) return;
      try{
        const barcodes=await detector.detect(video);
        if(barcodes && barcodes.length){
          const val=String(barcodes[0].rawValue||'').trim().toUpperCase();
          if(val){ handler(val); stopScan(target); return; }
        }
      }catch(e){}
      state[stateKey].raf=requestAnimationFrame(loop);
    };
    state[stateKey]={stream,video,detector,raf:0};
    setScanStatus(target,'掃描中...');
    video.onloadedmetadata=()=>{video.play(); state[stateKey].raf=requestAnimationFrame(loop);};
  }catch(e){
    setScanStatus(target,'相機打不開，請直接輸入條碼或用掃描槍。');
  }
}
function stopScan(target){
  const stateKey=target==='in'?'scanIn':'scanOut';
  const holder=document.getElementById(target==='in'?'readerIn':'readerOut');
  if(state[stateKey]){
    try{cancelAnimationFrame(state[stateKey].raf);}catch(e){}
    try{state[stateKey].stream.getTracks().forEach(t=>t.stop());}catch(e){}
    state[stateKey]=null;
  }
  holder.innerHTML='';
  setScanStatus(target,'掃描已停止。');
}

function summaryData(){
  const summary={};
  Object.keys(state.stock).forEach(code=>{
    const item=state.stock[code],k=item.name+"__"+item.size;
    if(!summary[k]) summary[k]={name:item.name,size:item.size,in:0,out:0};
    if(item.status==="in") summary[k].in++;
    else summary[k].out++;
  });
  return summary;
}
function findPendingPrinted(){
  return Object.keys(state.printedRegistry)
    .filter(code=>!state.printedRegistry[code].scannedIn)
    .sort()
    .map(code=>({code,name:state.printedRegistry[code].name,size:state.printedRegistry[code].size}));
}
function extractCodeParts(code){
  const text=String(code||'').trim().toUpperCase();
  const match=text.match(/^([A-Z0-9]+)-(.+?)(\d{4})$/);
  if(!match) return null;
  return {productCode:match[1],size:match[2],num:parseInt(match[3],10),numText:match[3],prefix:match[1]+'-'+match[2]};
}
function buildSeries(sourceCodes){
  const groups={};
  sourceCodes.forEach(code=>{
    const p=extractCodeParts(code);
    if(!p) return;
    if(!groups[p.prefix]) groups[p.prefix]={productCode:p.productCode,size:p.size,nums:[]};
    groups[p.prefix].nums.push(p.num);
  });
  Object.keys(groups).forEach(k=>groups[k].nums=[...new Set(groups[k].nums)].sort((a,b)=>a-b));
  return groups;
}
function detectInboundMissing(){
  const printedSeries=buildSeries(Object.keys(state.printedRegistry));
  const inboundSet=new Set(Object.keys(state.stock));
  const rows=[];
  Object.keys(printedSeries).forEach(prefix=>{
    const nums=printedSeries[prefix].nums;
    nums.forEach(num=>{
      const code=prefix+String(num).padStart(4,'0');
      if(!inboundSet.has(code)){
        const productName=(state.products[printedSeries[prefix].productCode]||{}).name||printedSeries[prefix].productCode;
        rows.push({item:productName,size:printedSeries[prefix].size,code,status:'進貨漏掃'});
      }
    });
  });
  return rows;
}
function detectOutboundMissing(){
  const inSeries=buildSeries(Object.keys(state.stock));
  const rows=[];
  Object.keys(inSeries).forEach(prefix=>{
    const info=inSeries[prefix];
    const productName=(state.products[info.productCode]||{}).name||info.productCode;
    const nums=info.nums;
    if(nums.length<2) return;
    const outNums=nums.filter(num=>{
      const code=prefix+String(num).padStart(4,'0');
      return state.stock[code] && state.stock[code].status==='out';
    }).sort((a,b)=>a-b);
    if(outNums.length<2) return;
    const min=outNums[0], max=outNums[outNums.length-1];
    for(let n=min;n<=max;n++){
      const code=prefix+String(n).padStart(4,'0');
      if(state.stock[code] && state.stock[code].status!=='out'){
        rows.push({item:productName,size:info.size,code,status:'出貨跳號 / 可能漏掃'});
      }
    }
  });
  return rows;
}

function renderDashboard(){
  const sum=summaryData(), keys=Object.keys(sum).sort();
  const pending=findPendingPrinted();
  const inboundMissing=detectInboundMissing();
  const outboundMissing=detectOutboundMissing();

  const stockRows=keys.length?keys.map(k=>{
    const low=Number(sum[k].in)<=3;
    return '<tr class="'+(low?'low-stock-row':'')+'"><td>'+sum[k].name+'</td><td>'+sum[k].size+'</td><td>'+sum[k].in+'</td><td>'+(low?'<span class="danger">⚠️低庫存</span>':'')+'</td></tr>';
  }).join(''):'<tr><td colspan="4">目前沒有庫存</td></tr>';

  const outRows=keys.length?keys.map(k=>'<tr><td>'+sum[k].name+'</td><td>'+sum[k].size+'</td><td>'+sum[k].out+'</td></tr>').join(''):'<tr><td colspan="3">目前沒有資料</td></tr>';

  const inboundRows=inboundMissing.length?inboundMissing.map(r=>'<tr><td>'+r.item+'</td><td>'+r.size+'</td><td>'+r.code+'</td><td><span class="danger">'+r.status+'</span></td></tr>').join(''):'<tr><td colspan="4">目前正常</td></tr>';

  const outboundRows=outboundMissing.length?outboundMissing.map(r=>'<tr><td>'+r.item+'</td><td>'+r.size+'</td><td>'+r.code+'</td><td><span class="danger">'+r.status+'</span></td></tr>').join(''):'<tr><td colspan="4">目前正常</td></tr>';

  const pendingRows=pending.length?pending.map(item=>'<tr><td>'+item.name+'</td><td>'+item.size+'</td><td>'+item.code+'</td></tr>').join(''):'<tr><td colspan="3">無</td></tr>';

  document.getElementById('stockDashboard').innerHTML=
    '<div class="mode-card">'+
      '<div class="grid-2">'+
        '<div class="table-wrap"><h3 class="center">📤 出貨數量</h3><table><tr><th>物品</th><th>尺寸</th><th>出貨數量</th></tr>'+outRows+'</table></div>'+
        '<div class="table-wrap"><h3 class="center">📦 目前庫存（已掃描入庫）</h3><table><tr><th>物品</th><th>尺寸</th><th>庫存</th><th>警告</th></tr>'+stockRows+'</table></div>'+
      '</div>'+
      '<div class="stock-3" style="margin-top:24px">'+
        '<div class="table-wrap"><h3 class="center">🔎 進貨漏掃檢查</h3><table><tr><th>物品</th><th>尺寸</th><th>缺少條碼</th><th>狀態</th></tr>'+inboundRows+'</table></div>'+
        '<div class="table-wrap"><h3 class="center">🕒 未掃描入庫清單</h3><table><tr><th>物品</th><th>尺寸</th><th>條碼</th></tr>'+pendingRows+'</table></div>'+
        '<div class="table-wrap"><h3 class="center">🔎 出貨跳號檢查</h3><table><tr><th>物品</th><th>尺寸</th><th>缺少條碼</th><th>狀態</th></tr>'+outboundRows+'</table></div>'+
      '</div>'+
    '</div>';
}


function populateReportYears(){
  const years=new Set([getCurrentYear()]);
  Object.values(state.stock).forEach(item=>years.add(getYearFromTimeString(item.inTime)));
  state.logs.forEach(log=>years.add(getYearFromTimeString(log.time)));
  const arr=[...years].sort((a,b)=>b-a);
  document.getElementById('reportYearSelect').innerHTML=arr.map(y=>'<option value="'+y+'">'+y+'</option>').join('');
}
function renderKpis(mode,totalIn,totalOut,itemCount,lowCount,currentMonth){
  document.getElementById('kpis').innerHTML=
    '<div class="kpi"><div class="l">'+(mode==='month'?'本年總出貨':'本年進貨')+'</div><div class="v">'+(mode==='month'?totalOut:totalIn)+'</div></div>'+
    '<div class="kpi"><div class="l">'+(mode==='month'?'有出貨商品':'本年出貨')+'</div><div class="v">'+(mode==='month'?itemCount:totalOut)+'</div></div>'+
    '<div class="kpi"><div class="l">低庫存品項</div><div class="v">'+lowCount+'</div></div>'+
    '<div class="kpi"><div class="l">'+(mode==='month'?'目前月份':'出貨率')+'</div><div class="v">'+(mode==='month'?currentMonth+'月':(totalIn>0?Math.round(totalOut/totalIn*100):0)+'%')+'</div></div>';
}
function renderRanking(rank){
  document.getElementById('ranking').innerHTML=rank.length?rank.map((r,i)=>'<div class="rank-item"><span>'+(['🥇','🥈','🥉','4.','5.'][i]||((i+1)+'.'))+' '+r[0]+'</span><span>'+r[1]+'</span></div>').join(''):'沒有資料';
}
function renderSvgLineChart(labels,datasets){
  const svg=document.getElementById('reportSvg');
  const W=980,H=360,pL=60,pR=40,pT=34,pB=42,innerW=W-pL-pR,innerH=H-pT-pB;
  let vals=[]; datasets.forEach(ds=>ds.data.forEach(v=>{if(v!==null&&v!==undefined) vals.push(Number(v)||0);}));
  const max=Math.max(1,...vals);
  let out=['<rect x="0" y="0" width="'+W+'" height="'+H+'" fill="#fff"/>'];
  for(let i=0;i<5;i++){
    const y=pT+innerH*(i/4), val=Math.round(max*(1-i/4));
    out.push('<line x1="'+pL+'" y1="'+y+'" x2="'+(W-pR)+'" y2="'+y+'" stroke="#e5edf7" stroke-width="1"/>');
    out.push('<text x="'+(pL-12)+'" y="'+(y+4)+'" font-size="12" text-anchor="end" fill="#667085">'+val+'</text>');
  }
  labels.forEach((lab,i)=>{
    const x=(labels.length===1)?(pL+innerW/2):(pL+innerW*i/(labels.length-1));
    out.push('<text x="'+x+'" y="'+(H-12)+'" font-size="12" text-anchor="middle" fill="#667085">'+lab+'</text>');
  });
  datasets.forEach(ds=>{
    let pts=[];
    ds.data.forEach((v,i)=>{
      if(v===null||v===undefined) return;
      const x=(labels.length===1)?(pL+innerW/2):(pL+innerW*i/(labels.length-1));
      const y=pT+innerH-(Number(v)||0)/max*innerH;
      pts.push({x,y,v});
    });
    if(pts.length===1){
      out.push('<line x1="'+pL+'" y1="'+pts[0].y+'" x2="'+(W-pR)+'" y2="'+pts[0].y+'" stroke="'+ds.color+'" stroke-width="3" stroke-dasharray="6 4"/>');
    }else if(pts.length>1){
      out.push('<polyline fill="none" stroke="'+ds.color+'" stroke-width="3" points="'+pts.map(p=>p.x+','+p.y).join(' ')+'"/>');
    }
    pts.forEach(p=>out.push('<circle cx="'+p.x+'" cy="'+p.y+'" r="5" fill="'+ds.color+'"><title>'+ds.label+'：'+p.v+' 件</title></circle>'));
  });
  const legendY=18;
  datasets.forEach((ds,i)=>{
    const x=pL+i*130;
    out.push('<line x1="'+x+'" y1="'+legendY+'" x2="'+(x+26)+'" y2="'+legendY+'" stroke="'+ds.color+'" stroke-width="3"/>');
    out.push('<text x="'+(x+32)+'" y="'+(legendY+4)+'" font-size="12" fill="#344054">'+ds.label+'</text>');
  });
  svg.innerHTML=out.join('');
}
function renderReport(){
  const year=parseInt(document.getElementById('reportYearSelect').value||getCurrentYear(),10);
  const mode=document.getElementById('reportModeSelect').value;
  const lowCount=Object.values(summaryData()).filter(v=>Number(v.in)<=3).length;
  const currentMonth=(year===getCurrentYear()?getCurrentMonth():12);
  let labels=[],datasets=[],summary='',ranking=[],totalIn=0,totalOut=0,itemCount=0;

  if(mode==='month'){
    const itemMap={};
    state.logs.forEach(log=>{
      const y=getYearFromTimeString(log.time);
      if(y!==year) return;
      const m=getMonthFromTimeString(log.time);
      if(m>currentMonth) return;
      const name=log.name||'未命名';
      if(!itemMap[name]) itemMap[name]=new Array(currentMonth).fill(0);
      itemMap[name][m-1]+=1;
    });
    labels=Array.from({length:currentMonth},(_,i)=>(i+1)+'月');
    const colors=['#2563eb','#22c55e','#ef4444','#f59e0b','#7c3aed','#14b8a6','#e11d48','#0ea5e9'];
    datasets=Object.keys(itemMap).map((name,i)=>({label:name,data:itemMap[name],color:colors[i%colors.length]}));
    if(!datasets.length) datasets=[{label:'沒有出貨資料',data:new Array(currentMonth).fill(0),color:'#94a3b8'}];
    ranking=Object.entries(itemMap).map(([k,v])=>[k,v.reduce((a,b)=>a+(b||0),0)]).sort((a,b)=>b[1]-a[1]).slice(0,5);
    totalOut=state.logs.filter(log=>getYearFromTimeString(log.time)===year && getMonthFromTimeString(log.time)<=currentMonth).length;
    itemCount=Object.keys(itemMap).length;
    summary='📊 年份：'+year+'<br>月報（依目前時間自動顯示到 '+currentMonth+' 月）<br><br>🔥 總出貨：'+totalOut+'<br>📦 商品數：'+itemCount+'<br><br>🏆 熱銷排行<br>'+(ranking.length?ranking.map(r=>r[0]+'：'+r[1]).join('<br>'):'沒有資料')+'<br><br>X軸＝1-'+currentMonth+'月｜線＝物品';
  } else {
    const inMap={}, outMap={};
    Object.values(state.stock).forEach(item=>{if(getYearFromTimeString(item.inTime)!==year) return; inMap[item.name]=(inMap[item.name]||0)+1; totalIn++;});
    state.logs.forEach(log=>{if(getYearFromTimeString(log.time)!==year) return; outMap[log.name]=(outMap[log.name]||0)+1; totalOut++;});
    labels=[...new Set([...Object.keys(inMap),...Object.keys(outMap)])];
    if(!labels.length) labels=['沒有資料'];
    datasets=[
      {label:'進貨',data:labels[0]==='沒有資料'?[0]:labels.map(l=>inMap[l]||0),color:'#2563eb'},
      {label:'出貨',data:labels[0]==='沒有資料'?[0]:labels.map(l=>outMap[l]||0),color:'#22c55e'}
    ];
    ranking=labels[0]==='沒有資料'?[]:labels.map(l=>[l,outMap[l]||0]).sort((a,b)=>b[1]-a[1]).slice(0,5);
    itemCount=labels[0]==='沒有資料'?0:labels.length;
    summary='📊 年份：'+year+'<br><br>📥 進貨：'+totalIn+'<br>📤 出貨：'+totalOut+'<br>📦 商品數：'+itemCount+'<br>📈 出貨率：'+(totalIn>0?Math.round(totalOut/totalIn*100):0)+'%<br><br>X軸＝物品｜線＝進貨 / 出貨';
  }
  renderKpis(mode,totalIn,totalOut,itemCount,lowCount,currentMonth);
  renderRanking(ranking);
  renderSvgLineChart(labels,datasets);
  document.getElementById('reportSummary').innerHTML=summary;
}

function xmlEscape(v){return String(v??'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}
function sheetXml(name,rows){
  let xml='<Worksheet ss:Name="'+xmlEscape(name)+'"><Table>';
  rows.forEach(r=>{xml+='<Row>'; r.forEach(c=>{xml+='<Cell><Data ss:Type="String">'+xmlEscape(c)+'</Data></Cell>';}); xml+='</Row>';});
  xml+='</Table></Worksheet>';
  return xml;
}
function exportDetailedReportExcel(){
  const year=parseInt(document.getElementById('reportYearSelect').value||getCurrentYear(),10);
  const mode=document.getElementById('reportModeSelect').value;
  const currentMonth=(year===getCurrentYear()?getCurrentMonth():12);
  const overview=[['年份','模式','進貨總數','出貨總數']];
  const inRows=[['類型','年份','月份','物品','尺寸','條碼','時間']];
  const outRows=[['類型','年份','月份','物品','尺寸','條碼','時間','教練']];
  const monthRows=[['月份','物品','出貨數量']];
  let totalIn=0,totalOut=0;
  Object.values(state.stock).forEach(item=>{
    const y=getYearFromTimeString(item.inTime);
    if(y!==year) return;
    const m=getMonthFromTimeString(item.inTime);
    inRows.push(['進貨',y,m,item.name||'',item.size||'',item.code||'',item.inTime||'']);
    totalIn++;
  });
  state.logs.forEach(log=>{
    const y=getYearFromTimeString(log.time);
    if(y!==year) return;
    const m=getMonthFromTimeString(log.time);
    if(m>currentMonth) return;
    outRows.push(['出貨',y,m,log.name||'',log.size||'',log.code||'',log.time||'',log.user||'']);
    totalOut++;
  });
  const monthMap={};
  state.logs.forEach(log=>{
    const y=getYearFromTimeString(log.time);
    if(y!==year) return;
    const m=getMonthFromTimeString(log.time);
    if(m>currentMonth) return;
    const key=m+'__'+(log.name||'未命名');
    monthMap[key]=(monthMap[key]||0)+1;
  });
  Object.keys(monthMap).sort((a,b)=>{const aa=a.split('__'), bb=b.split('__'); return Number(aa[0])-Number(bb[0]) || aa[1].localeCompare(bb[1]);}).forEach(k=>{const p=k.split('__'); monthRows.push([p[0]+'月',p[1],monthMap[k]]);});
  overview.push([year,mode==='month'?'月報':'年報',totalIn,totalOut]);
  let workbook='<?xml version="1.0"?><?mso-application progid="Excel.Sheet"?><Workbook xmlns="urn:schemas-microsoft-com:office:spreadsheet" xmlns:ss="urn:schemas-microsoft-com:office:spreadsheet">';
  workbook+=sheetXml('總覽',overview);
  workbook+=sheetXml('月報明細',monthRows);
  workbook+=sheetXml('進貨詳細',inRows);
  workbook+=sheetXml('出貨詳細',outRows);
  workbook+='</Workbook>';
  const blob=new Blob([workbook],{type:'application/vnd.ms-excel'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='商業報表_'+year+'_'+mode+'.xls';
  a.click();
  setTimeout(()=>URL.revokeObjectURL(a.href),1000);
}

loadState();
</script>
</body>
</html>
