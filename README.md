
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<meta name="theme-color" content="#050918">
<title>COSMOS 7 | Space Explorer</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#050918;color:#f3f7ff;font-family:Tahoma,Arial,sans-serif}
header{padding:45px 15px;text-align:center;background:radial-gradient(ellipse at top,#183b70,#080e20 65%,#050918)}
header h1{font-size:42px;color:#80d7ff;margin:8px}
header p{color:#c4d8ed}
nav{position:sticky;top:0;z-index:5;background:#091328ed;backdrop-filter:blur(12px);display:flex;justify-content:center;gap:8px;flex-wrap:wrap;padding:12px}
button,input,select{font:inherit;border:1px solid #29476e;background:#11213b;color:white;padding:12px;border-radius:10px}
button{cursor:pointer}
button:hover{background:#24548b}
input{width:min(100%,440px)}
section{padding:25px 15px;max-width:1150px;margin:auto}
h2{text-align:center;color:#82d4ff}
.intro{text-align:center;color:#bdcde2;line-height:2}
.search{text-align:center;margin:20px auto;display:flex;gap:8px;justify-content:center;flex-wrap:wrap}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:16px}
.card{background:#101d33;border:1px solid #263e60;border-radius:16px;padding:14px;overflow:hidden}
.card img{width:100%;height:175px;object-fit:cover;border-radius:11px;background:#080e1b}
.card h3{color:#8bd5ff}
.card p{font-size:14px;color:#c4d1e2;line-height:1.9}
.small{font-size:12px;color:#9eb2cc}
.actions{display:flex;gap:8px;flex-wrap:wrap;margin-top:12px}
.actions button{flex:1}
.panel{background:#101d33;border:1px solid #263e60;border-radius:16px;padding:18px;margin-top:16px}
#detail img{max-width:100%;max-height:430px;object-fit:contain;border-radius:12px}
#detail{text-align:center;line-height:2}
#detail p{text-align:right}
#results img{height:190px}
.diagram{width:100%;max-width:480px;display:block;margin:15px auto;background:#0a1427;border-radius:15px}
footer{text-align:center;color:#8ca5c5;padding:30px}
a{color:#8bd5ff}
.loading{color:#8bd5ff;text-align:center;padding:20px}
</style>
</head>
<body>

<header>
<h1>🌌 COSMOS 7</h1>
<p>کاوشگر جهان هستی | Explore the Universe</p>
<p>از منظومه شمسی تا دورترین کهکشان‌ها</p>
</header>

<nav>
<button onclick="go('solar')">🪐 منظومه شمسی</button>
<button onclick="go('detail')">🔬 ساختار داخلی</button>
<button onclick="go('space')">🌠 آرشیو ناسا</button>
<button onclick="go('scientists')">👨‍🚀 دانشمندان</button>
<button onclick="go('wonders')">✨ شگفتی‌ها</button>
<select id="language" onchange="translatePage()">
<option value="fa">فارسی</option>
<option value="en">English</option>
<option value="ar">العربية</option>
<option value="fr">Français</option>
<option value="zh-CN">中文</option>
<option value="de">Deutsch</option>
<option value="ru">Русский</option>
<option value="tr">Türkçe</option>
<option value="es">Español</option>
<option value="ja">日本語</option>
<option value="it">Italiano</option>
<option value="pt">Português</option>
<option value="hi">हिन्दी</option>
</select>
</nav>

<section id="solar">
<h2>🪐 منظومه شمسی</h2>
<p class="intro">سیارات، سیاره‌های کوتوله، خورشید و ماه را جست‌وجو کن و اطلاعات علمی آن‌ها را ببین.</p>
<div class="search">
<input id="planetSearch" placeholder="نام سیاره را جست‌وجو کن..." oninput="renderPlanets()">
</div>
<div class="grid" id="planetGrid"></div>
</section>

<section id="detail">
<h2>🔬 آزمایشگاه ساختار داخلی سیارات</h2>
<p class="intro">ساختار درونی اجرام آسمانی را با نمودارهای علمی آموزشی بررسی کن.</p>
<div class="search">
<select id="bodySelect" onchange="showStructure()">
<option value="Earth">زمین</option>
<option value="Mars">مریخ</option>
<option value="Mercury">عطارد</option>
<option value="Venus">زهره</option>
<option value="Jupiter">مشتری</option>
<option value="Saturn">زحل</option>
<option value="Uranus">اورانوس</option>
<option value="Neptune">نپتون</option>
<option value="Moon">ماه</option>
<option value="Sun">خورشید</option>
</select>
<button onclick="showStructure()">نمایش ساختار</button>
</div>
<div class="panel" id="structure"></div>
</section>

<section id="space">
<h2>📡 آرشیو تصاویر ناسا</h2>
<p class="intro">در مجموعه تصاویر و ویدئوهای فضایی ناسا جست‌وجو کن.</p>
<div class="search">
<input id="nasaQuery" placeholder="مثلاً Saturn, Mars, Black Hole">
<button onclick="searchNASA()">جست‌وجو</button>
</div>
<div class="grid" id="results"></div>
</section>

<section id="scientists">
<h2>👨‍🚀 دانشنامه دانشمندان</h2>
<p class="intro">زندگی و دستاوردهای دانشمندان نجوم و علوم فضایی را پیدا کن.</p>
<div class="search">
<input id="scientistQuery" placeholder="نام دانشمند را وارد کن">
<button onclick="searchScientist()">جست‌وجو</button>
</div>
<div class="grid" id="scientistResults"></div>
</section>

<section id="wonders">
<h2>✨ شگفتی‌ها و رازهای کیهان</h2>
<div class="grid">
<div class="card"><h3>🕳️ سیاه‌چاله‌ها</h3><p>ناحیه‌هایی از فضا با گرانش بسیار قوی؛ حتی نور هم نمی‌تواند از افق رویداد آن‌ها فرار کند.</p></div>
<div class="card"><h3>🌌 کهکشان راه شیری</h3><p>کهکشانی مارپیچی که منظومه شمسی ما در یکی از بازوهای آن قرار دارد.</p></div>
<div class="card"><h3>💥 ابرنواختر</h3><p>انفجار عظیم برخی ستارگان در پایان مراحل زندگی آن‌ها.</p></div>
<div class="card"><h3>🌫️ سحابی‌ها</h3><p>ابرهای عظیم گاز و غبار میان‌ستاره‌ای؛ برخی محل تولد ستارگان هستند.</p></div>
<div class="card"><h3>⭐ ستاره نوترونی</h3><p>بقایای بسیار چگال برخی ستارگان پس از انفجار ابرنواختری.</p></div>
<div class="card"><h3>🪐 سیارات فراخورشیدی</h3><p>جهان‌هایی که به دور ستاره‌هایی غیر از خورشید می‌چرخند.</p></div>
<div class="card"><h3>🌑 ماده تاریک</h3><p>ماده‌ای که نور منتشر یا جذب نمی‌کند و وجود آن از اثر گرانشی‌اش بررسی می‌شود.</p></div>
<div class="card"><h3>⚡ انرژی تاریک</h3><p>نامی برای پدیده ناشناخته‌ای که با شتاب‌گرفتن انبساط کیهان مرتبط است.</p></div>
</div>
</section>

<footer>
COSMOS 7<br>
Explore • Discover • Understand<br>
© 2026 COSMOS 7
</footer>

<script>
const planets=[
{name:"عطارد",en:"Mercury",type:"سیاره سنگی",desc:"نزدیک‌ترین سیاره به خورشید و کوچک‌ترین سیاره منظومه شمسی.",query:"Mercury planet NASA"},
{name:"زهره",en:"Venus",type:"سیاره سنگی",desc:"زهره جوی بسیار چگال و سطحی بسیار داغ دارد.",query:"Venus planet NASA"},
{name:"زمین",en:"Earth",type:"سیاره سنگی",desc:"خانه ما؛ دارای آب مایع پایدار در سطح و حیات شناخته‌شده.",query:"Earth planet NASA"},
{name:"مریخ",en:"Mars",type:"سیاره سنگی",desc:"سیاره سرخ با آتشفشان‌های عظیم و شواهدی از آب گذشته.",query:"Mars planet NASA"},
{name:"مشتری",en:"Jupiter",type:"غول گازی",desc:"بزرگ‌ترین سیاره منظومه شمسی با طوفان بزرگ سرخ.",query:"Jupiter NASA"},
{name:"زحل",en:"Saturn",type:"غول گازی",desc:"جهانی زیبا با حلقه‌هایی از یخ و سنگ.",query:"Saturn NASA"},
{name:"اورانوس",en:"Uranus",type:"غول یخی",desc:"سیاره‌ای با محور چرخش بسیار مایل و جو سرد.",query:"Uranus NASA"},
{name:"نپتون",en:"Neptune",type:"غول یخی",desc:"دورترین سیاره اصلی منظومه شمسی با بادهای سریع.",query:"Neptune NASA"},
{name:"پلوتو",en:"Pluto",type:"سیاره کوتوله",desc:"جهانی یخی در کمربند کویپر.",query:"Pluto New Horizons NASA"},
{name:"سرس",en:"Ceres",type:"سیاره کوتوله",desc:"بزرگ‌ترین جرم کمربند سیارکی میان مریخ و مشتری.",query:"Ceres Dawn NASA"},
{name:"اریس",en:"Eris",type:"سیاره کوتوله",desc:"جرمی دوردست در منظومه شمسی بیرونی.",query:"Eris dwarf planet"},
{name:"ماه",en:"Moon",type:"قمر طبیعی",desc:"تنها قمر طبیعی زمین و مقصد مأموریت‌های فضایی.",query:"Earth Moon NASA"},
{name:"خورشید",en:"Sun",type:"ستاره",desc:"ستاره مرکز منظومه شمسی و منبع اصلی انرژی زمین.",query:"Sun NASA"}
];

const fallback="https://images.unsplash.com/photo-1462331940025-496dfbfc7564?w=800";

function go(id){document.getElementById(id).scrollIntoView({behavior:"smooth"});}

function renderPlanets(){
const q=document.getElementById("planetSearch").value.toLowerCase();
const grid=document.getElementById("planetGrid");
grid.innerHTML="";
planets.filter(p=>(p.name+" "+p.en+" "+p.type).toLowerCase().includes(q)).forEach(p=>{
const card=document.createElement("div");
card.className="card";
card.innerHTML=`
<img src="${fallback}" alt="${p.en}" loading="lazy">
<h3>${p.name} | ${p.en}</h3>
<p>${p.type}</p>
<p>${p.desc}</p>
<div class="actions">
<button>اطلاعات و تصاویر</button>
<button>ساختار داخلی</button>
</div>`;
card.querySelectorAll("button")[0].onclick=()=>{document.getElementById("nasaQuery").value=p.query;go("space");searchNASA();};
card.querySelectorAll("button")[1].onclick=()=>{document.getElementById("bodySelect").value=p.en==="Moon"?"Moon":p.en==="Sun"?"Sun":p.en;showStructure();go("detail");};
grid.appendChild(card);
});
}

async function searchNASA(){
const q=document.getElementById("nasaQuery").value.trim();
if(!q)return;
const box=document.getElementById("results");
box.innerHTML='<p class="loading">در حال دریافت تصاویر از آرشیو ناسا...</p>';
try{
const r=await fetch("https://images-api.nasa.gov/search?q="+encodeURIComponent(q)+"&media_type=image&page_size=30");
if(!r.ok)throw Error("NASA API");
const data=await r.json();
box.innerHTML="";
data.collection.items.slice(0,24).forEach(item=>{
const info=item.data?.[0];
const image=item.links?.find(x=>x.render==="image")?.href;
if(!info||!image)return;
const card=document.createElement("div");
card.className="card";
const img=document.createElement("img");
img.src=image;img.loading="lazy";img.alt=info.title||"NASA image";
const title=document.createElement("h3");title.textContent=info.title||"NASA Image";
const desc=document.createElement("p");desc.textContent=(info.description||"تصویر از آرشیو ناسا").slice(0,220);
const link=document.createElement("a");link.href=image;link.target="_blank";link.rel="noopener";link.textContent="نمایش تصویر اصلی";
card.append(img,title,desc,link);box.appendChild(card);
});
if(!box.children.length)box.textContent="تصویری پیدا نشد.";
}catch(e){box.textContent="دریافت تصاویر ناموفق بود. اتصال اینترنت را بررسی کن.";}
}

const structures={
Earth:["پوسته","گوشته","هسته خارجی مایع","هسته داخلی جامد"],
Mars:["پوسته","گوشته","هسته فلزی"],
Mercury:["پوسته","گوشته سیلیکاتی","هسته فلزی بزرگ"],
Venus:["پوسته","گوشته","هسته فلزی"],
Jupiter:["جو","هیدروژن فلزی","هسته مرکزی احتمالی"],
Saturn:["جو","هیدروژن فلزی","هسته مرکزی"],
Uranus:["جو","لایه سیالات داغ و متراکم","هسته سنگی احتمالی"],
Neptune:["جو","لایه آب و مواد فرّار","هسته سنگی احتمالی"],
Moon:["پوسته","گوشته","هسته کوچک"],
Sun:["هسته","ناحیه تابشی","ناحیه همرفتی","فوتوسفر","کروموسفر","تاج خورشیدی"]
};

function showStructure(){
const name=document.getElementById("bodySelect").value;
const labels=structures[name]||["ساختار دقیق هنوز به‌طور کامل شناخته نشده است"];
const box=document.getElementById("structure");
let colors=["#80cfff","#e3a15d","#d45c48","#f4d36c","#aa82ff","#64d7b1"];
let circles=labels.map((x,i)=>`<circle cx="180" cy="180" r="${135-i*19}" fill="${colors[i%colors.length]}" stroke="#fff" stroke-width="1"/>`).join("");
let legend=labels.map((x,i)=>`<p>🔹 ${x}</p>`).join("");
box.innerHTML=`
<h3>${name} | نمودار آموزشی ساختار داخلی</h3>
<svg class="diagram" viewBox="0 0 360 360" role="img" aria-label="نمودار لایه‌های داخلی">
${circles}
<circle cx="180" cy="180" r="17" fill="#fff"/>
</svg>
<p>این تصویر یک نمودار شماتیک آموزشی از لایه‌هاست و عکس واقعی داخل سیاره نیست.</p>
${legend}
<p class="small">ساختار دقیق بعضی اجرام هنوز موضوع پژوهش علمی است.</p>`;
}

async function searchScientist(){
const q=document.getElementById("scientistQuery").value.trim();
if(!q)return;
const box=document.getElementById("scientistResults");
box.innerHTML='<p class="loading">در حال جست‌وجو...</p>';
try{
const lang=document.documentElement.lang==="fa"?"fa":"en";
const url="https://"+lang+".wikipedia.org/w/api.php?action=query&generator=search&gsrsearch="+encodeURIComponent(q+" astronomer space scientist")+"&gsrlimit=12&prop=pageimages|extracts&exintro=1&explaintext=1&piprop=thumbnail&pithumbsize=500&format=json&origin=*";
const r=await fetch(url);
const data=await r.json();
box.innerHTML="";
Object.values(data.query?.pages||{}).forEach(p=>{
const card=document.createElement("div");card.className="card";
const img=document.createElement("img");img.src=p.thumbnail?.source||fallback;img.alt=p.title;
const title=document.createElement("h3");title.textContent=p.title;
const desc=document.createElement("p");desc.textContent=(p.extract||"اطلاعات بیشتری در صفحه دانشنامه موجود است.").slice(0,350);
const link=document.createElement("a");link.href="https://"+lang+".wikipedia.org/wiki/"+encodeURIComponent(p.title.replaceAll(" ","_"));link.target="_blank";link.rel="noopener";link.textContent="مطالعه بیشتر";
card.append(img,title,desc,link);box.appendChild(card);
});
if(!box.children.length)box.textContent="نتیجه‌ای پیدا نشد.";
}catch(e){box.textContent="جست‌وجو ناموفق بود. اینترنت را بررسی کن.";}
}

function translatePage(){
const lang=document.getElementById("language").value;
if(lang==="fa"){
location.reload();
return;
}
let old=document.getElementById("google_translate_script");
if(!old){
const script=document.createElement("script");
script.id="google_translate_script";
script.src="//translate.google.com/translate_a/element.js?cb=googleTranslateInit";
document.body.appendChild(script);
}
window.googleTranslateTarget=lang;
if(window.google&&google.translate){
const select=document.querySelector(".goog-te-combo");
if(select){select.value=lang;select.dispatchEvent(new Event("change"));}
}
}
window.googleTranslateInit=function(){
new google.translate.TranslateElement({
pageLanguage:"fa",
includedLanguages:"en,ar,fr,zh-CN,de,ru,tr,es,ja,it,pt,hi",
autoDisplay:false
},"google_translate_element");
const select=document.querySelector(".goog-te-combo");
if(select&&window.googleTranslateTarget){
select.value=window.googleTranslateTarget;
select.dispatchEvent(new Event("change"));
}
};

renderPlanets();
showStructure();
</script>
<div id="google_translate_element"></div>
</body>
</html>

