<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Minh Tâm & Trường Long — Thiệp Cưới</title>
<style>
:root{
  --bg:#fff6fb;
  --accent:#f8c2d9;
  --accent-dark:#eaa7c6;
  --text:#2b2b2b;
  --muted:#7a7a7a;
}
body{margin:0;font-family:system-ui;background:var(--bg);color:var(--text);}
a{text-decoration:none;color:var(--accent);}
.side-menu{
  position:fixed;top:0;left:0;width:180px;height:100%;
  background:rgba(255,255,255,0.95);padding:20px;
  box-shadow:2px 2px 12px rgba(0,0,0,0.1);
}
.side-menu ul{list-style:none;padding:0;}
.side-menu li{margin-bottom:16px;font-weight:600;}
.side-menu button{
  width:100%;padding:10px;background:linear-gradient(90deg,var(--accent),var(--accent-dark));
  border:none;color:#fff;border-radius:8px;cursor:pointer;font-size:14px;text-align:left;
}
.side-menu button:hover{background:linear-gradient(90deg,var(--accent-dark),var(--accent));}

.container{margin-left:200px;padding:20px;transition:0.3s;}
h1,h2,h3{margin:6px 0;}
.countdown{display:flex;gap:12px;margin-top:12px;}
.countdown .col{background:rgba(255,255,255,0.9);padding:12px;border-radius:8px;text-align:center;min-width:70px;}
.window{
  display:none;
  position:fixed;top:50%;left:50%;
  transform:translate(-50%,-50%);
  background:#fff;padding:20px;
  border-radius:12px;
  box-shadow:0 4px 20px rgba(0,0,0,0.3);
  width:80%;max-width:500px;
  max-height:80%;
  overflow:auto;
  z-index:1000;
}
.window h2{margin-top:0;}
.close{position:absolute;top:10px;right:15px;cursor:pointer;font-size:20px;font-weight:bold;}
.gallery{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;}
.gallery img{width:calc(33.33% - 6px);height:120px;object-fit:cover;border-radius:8px;cursor:pointer;}
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.6);justify-content:center;align-items:center;z-index:2000;}
.modal-content{background:#fff;padding:20px;border-radius:12px;max-width:90%;max-height:90%;overflow:auto;position:relative;}
.close-btn{position:absolute;top:10px;right:10px;cursor:pointer;font-weight:bold;font-size:20px;}
@media(max-width:900px){.container{margin-left:0}.gallery img{width:calc(50% - 6px)}}
</style>
</head>
<body>

<nav class="side-menu">
  <ul>
    <li><button onclick="openWindow('story')">Câu chuyện</button></li>
    <li><button onclick="openWindow('schedule')">Chương trình</button></li>
    <li><button onclick="openWindow('galleryWindow')">Gallery</button></li>
    <li><button onclick="openWindow('rsvpWindow')">RSVP</button></li>
  </ul>
</nav>

<div class="container">
  <section id="home">
    <h1>Minh Tâm & Trường Long</h1>
    <p>Hân hoan chào đón — Lãng mạn, hồng nhẹ & sang</p>
    <div class="countdown">
      <div class="col"><div id="days">0</div>Ngày</div>
      <div class="col"><div id="hours">0</div>Giờ</div>
      <div class="col"><div id="mins">0</div>Phút</div>
      <div class="col"><div id="secs">0</div>Giây</div>
    </div>
    <button id="music-toggle">Bật nhạc</button>
  </section>
</div>

<!-- Các cửa sổ -->
<div class="window" id="story">
  <span class="close" onclick="closeWindow('story')">&times;</span>
  <h2>Câu chuyện tình yêu</h2>
  <p>Minh Tâm & Trường Long gặp nhau từ... [Điền chi tiết]</p>
</div>

<div class="window" id="schedule">
  <span class="close" onclick="closeWindow('schedule')">&times;</span>
  <h2>Chương trình</h2>
  <ul>
    <li>10:30 — Khách đến ổn định</li>
    <li>11:00 — Lễ gia tiên</li>
    <li>12:00 — Tiệc chính</li>
    <li>14:30 — Kết thúc</li>
  </ul>
</div>

<div class="window" id="galleryWindow">
  <span class="close" onclick="closeWindow('galleryWindow')">&times;</span>
  <h2>Gallery</h2>
  <div class="gallery">
    <img src="cover.jpg" alt="Ảnh 1">
    <img src="a1.jpg" alt="Ảnh 2">
    <img src="a2.jpg" alt="Ảnh 3">
  </div>
</div>

<div class="window" id="rsvpWindow">
  <span class="close" onclick="closeWindow('rsvpWindow')">&times;</span>
  <h2>RSVP</h2>
  <iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true" width="100%" height="500" frameborder="0" marginheight="0" marginwidth="0">Đang tải…</iframe>
</div>

<!-- Modal gallery popup -->
<div class="modal" id="modal">
  <div class="modal-content">
    <span class="close-btn" id="closeModal">&times;</span>
    <div id="modal-body"></div>
  </div>
</div>

<audio id="bgmusic" loop src="music.mp3"></audio>

<script>
// Countdown
const weddingDate = new Date('2026-04-30T11:00:00');
function updateCountdown(){
  const now = new Date();
  let diff = weddingDate-now;
  if(diff<0) diff=0;
  const days=Math.floor(diff/(1000*60*60*24));
  const hours=Math.floor((diff/(1000*60*60))%24);
  const mins=Math.floor((diff/(1000*60))%60);
  const secs=Math.floor((diff/1000)%60);
  document.getElementById('days').textContent=days;
  document.getElementById('hours').textContent=String(hours).padStart(2,'0');
  document.getElementById('mins').textContent=String(mins).padStart(2,'0');
  document.getElementById('secs').textContent=String(secs).padStart(2,'0');
}
setInterval(updateCountdown,1000);
updateCountdown();

// Music toggle
const bg=document.getElementById('bgmusic');
const btn=document.getElementById('music-toggle');
let musicOn=false;
btn.addEventListener('click',()=>{
  if(!musicOn){bg.play().catch(()=>{});btn.textContent='Tắt nhạc';musicOn=true;}
  else{bg.pause();btn.textContent='Bật nhạc';musicOn=false;}
});

// Open/Close windows
function openWindow(id){document.getElementById(id).style.display='block';}
function closeWindow(id){document.getElementById(id).style.display='none';}

// Gallery modal
const modal=document.getElementById('modal');
const modalBody=document.getElementById('modal-body');
const closeModal=document.getElementById('closeModal');
document.querySelectorAll('.gallery img').forEach(img=>{
  img.addEventListener('click', ()=>{
    modal.style.display='flex';
    modalBody.innerHTML=`<img src="${img.src}" style="max-width:100%; max-height:80vh; border-radius:8px;">`;
  });
});
closeModal.addEventListener('click',()=>{modal.style.display='none';});
modal.addEventListener('click', e=>{if(e.target==modal) modal.style.display='none';});

</script>

</body>
</html>
