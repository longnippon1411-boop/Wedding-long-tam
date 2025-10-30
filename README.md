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
.container{margin-left:200px;padding:20px;transition:0.3s;}
.side-menu{position:fixed;top:0;left:0;width:180px;height:100%;background:rgba(255,255,255,0.95);padding:20px;box-shadow:2px 2px 12px rgba(0,0,0,0.1);}
.side-menu ul{list-style:none;padding:0;}
.side-menu li{margin-bottom:16px;font-weight:600;}
.side-menu a:hover{color:var(--accent-dark);}
section{padding:30px 0;border-bottom:1px solid #f2e5f0;}
h1,h2,h3{margin:6px 0;}
button{padding:10px 16px;background:linear-gradient(90deg,var(--accent),var(--accent-dark));border:none;color:#fff;border-radius:8px;cursor:pointer;}
.countdown{display:flex;gap:12px;margin-top:12px;}
.countdown .col{background:rgba(255,255,255,0.9);padding:12px;border-radius:8px;text-align:center;min-width:70px;}
.gallery{display:flex;flex-wrap:wrap;gap:8px;}
.gallery img{width:calc(33.33% - 6px);height:120px;object-fit:cover;border-radius:8px;cursor:pointer;}
.modal{display:none;position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.6);justify-content:center;align-items:center;}
.modal-content{background:#fff;padding:20px;border-radius:12px;max-width:90%;max-height:90%;overflow:auto;}
.close-btn{position:absolute;top:10px;right:10px;cursor:pointer;font-weight:bold;}
@media(max-width:900px){.container{margin-left:0}.gallery img{width:calc(50% - 6px)}}
</style>
</head>
<body>

<nav class="side-menu">
  <ul>
    <li><a href="#home">Trang chủ</a></li>
    <li><a href="#story">Câu chuyện</a></li>
    <li><a href="#schedule">Chương trình</a></li>
    <li><a href="#gallery">Gallery</a></li>
    <li><a href="#rsvp">RSVP</a></li>
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

<section id="story">
  <h2>Câu chuyện tình yêu</h2>
  <p>Minh Tâm và Trường Long gặp nhau từ... [bạn điền chi tiết]</p>
</section>

<section id="schedule">
  <h2>Chương trình</h2>
  <ul>
    <li>10:30 — Khách đến ổn định</li>
    <li>11:00 — Lễ gia tiên</li>
    <li>12:00 — Tiệc chính</li>
    <li>14:30 — Kết thúc</li>
  </ul>
</section>

<section id="gallery">
  <h2>Gallery</h2>
  <div class="gallery">
    <img src="cover.jpg" alt="Ảnh 1">
    <img src="a1.jpg" alt="Ảnh 2">
    <img src="a2.jpg" alt="Ảnh 3">
  </div>
</section>

<section id="rsvp">
  <h2>RSVP</h2>
  <iframe src="https://docs.google.com/forms/d/e/YOUR_FORM_ID/viewform?embedded=true" width="100%" height="800" frameborder="0" marginheight="0" marginwidth="0">Đang tải…</iframe>
</section>

</div>

<audio id="bgmusic" loop src="music.mp3"></audio>

<div class="modal" id="modal">
  <div class="modal-content">
    <span class="close-btn" id="closeModal">&times;</span>
    <div id="modal-body"></div>
  </div>
</div>

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

// Smooth scroll menu
document.querySelectorAll('.side-menu a').forEach(link=>{
  link.addEventListener('click', e=>{
    e.preventDefault();
    const target=document.querySelector(link.getAttribute('href'));
    target.scrollIntoView({behavior:'smooth'});
  });
});

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
