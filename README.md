# Wedding-long-tam
<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Minh Tâm & Trường Long — Thiệp Cưới</title>
  <style>
    /* --- Reset & fonts --- */
    :root{
      --bg:#fff6fb;
      --accent:#f8c2d9;
      --text:#2b2b2b;
      --muted:#7a7a7a;
      --card-bg: rgba(255,255,255,0.9);
      --accent-dark:#eaa7c6;
    }
    html,body{height:100%;margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;}
    body{
      background: linear-gradient(180deg, #fff6fb 0%, #fff0f6 100%);
      color:var(--text); -webkit-font-smoothing:antialiased;
    }
    .container{max-width:980px;margin:20px auto;padding:18px;}
    header{display:flex;gap:16px;align-items:center;}
    .logo{width:84px;height:84px;border-radius:12px;background:linear-gradient(135deg,var(--accent),var(--accent-dark));display:flex;align-items:center;justify-content:center;font-weight:700;color:#fff;font-size:20px;box-shadow:0 6px 18px rgba(234,167,198,0.18);}
    h1{margin:0;font-size:28px;}
    .sub{color:var(--muted);}
    .hero{display:grid;grid-template-columns:1fr 340px;gap:20px;margin-top:18px;align-items:start;}
    .card{background:var(--card-bg);padding:18px;border-radius:12px;box-shadow:0 6px 20px rgba(0,0,0,0.06);}
    .hero-left{padding:8px;}
    .cover{height:320px;border-radius:10px;background-image:url('cover.jpg');background-size:cover;background-position:center;display:flex;align-items:flex-end;padding:18px;color:#fff;text-shadow:0 4px 14px rgba(0,0,0,0.35);}
    .date{background:rgba(0,0,0,0.32);padding:10px;border-radius:8px;}
    .countdown{display:flex;gap:10px;margin-top:12px;}
    .countdown .col{background:rgba(255,255,255,0.9);padding:10px;border-radius:8px;min-width:70px;text-align:center;}
    .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;margin-top:12px;}
    .btn{display:inline-block;padding:10px 14px;border-radius:8px;background:linear-gradient(90deg,var(--accent),var(--accent-dark));color:#fff;text-decoration:none;font-weight:600;border:none;cursor:pointer;}
    .muted{color:var(--muted);font-size:14px;}
    .map iframe{width:100%;height:220px;border:0;border-radius:8px;}
    /* gallery */
    .gallery{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;}
    .gallery img{width:calc(33.333% - 5px);height:120px;object-fit:cover;border-radius:8px;}
    /* RSVP */
    form input, form textarea, form select {width:100%;padding:10px;border-radius:8px;border:1px solid #eee;margin-top:8px}
    form label{font-weight:600;font-size:14px}
    .guestbook-list{max-height:220px;overflow:auto;margin-top:10px;}
    .guest-item{padding:8px;border-radius:8px;background:#fff;margin-bottom:8px;border:1px solid #f1e5ec}
    footer{margin-top:18px;text-align:center;color:var(--muted);font-size:13px}
    /* responsive */
    @media (max-width:900px){
      .hero{grid-template-columns:1fr;}
      .gallery img{width:calc(50% - 6px)}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="logo">MT ♥ TL</div>
      <div>
        <h1>Minh Tâm & Trường Long</h1>
        <div class="sub">Hân hoan chào đón — Lãng mạn, hồng nhẹ & sang</div>
      </div>
      <div style="margin-left:auto;text-align:right;">
        <button id="music-toggle" class="btn">Bật nhạc</button>
        <div style="font-size:12px;color:var(--muted);margin-top:6px">Lễ: 30/04/2026 • 11:00</div>
      </div>
    </header>

    <section class="hero">
      <div class="hero-left card">
        <div class="cover" id="cover">
          <div>
            <div style="font-size:18px;font-weight:700">Minh Tâm & Trường Long</div>
            <div class="date">30 April 2026 — 11:00</div>
          </div>
        </div>

        <div class="countdown" style="margin-top:16px;">
          <div class="col"><div style="font-size:20px" id="days">0</div><div class="muted">Ngày</div></div>
          <div class="col"><div style="font-size:20px" id="hours">0</div><div class="muted">Giờ</div></div>
          <div class="col"><div style="font-size:20px" id="mins">0</div><div class="muted">Phút</div></div>
          <div class="col"><div style="font-size:20px" id="secs">0</div><div class="muted">Giây</div></div>
        </div>

        <div class="card" style="margin-top:14px;">
          <h3>Chương trình (dự kiến)</h3>
          <ul class="muted">
            <li>10:30 — Khách đến, ổn định</li>
            <li>11:00 — Lễ gia tiên</li>
            <li>12:00 — Tiệc chính</li>
            <li>14:30 — Kết thúc</li>
          </ul>
        </div>

        <div class="card" style="margin-top:14px;">
          <h3>Thư mời</h3>
          <p>Hân hạnh mời bạn đến chung vui cùng chúng tôi trong ngày trọng đại.</p>
        </div>

        <div class="card" style="margin-top:14px;">
          <h3>Gallery</h3>
          <div class="gallery" id="gallery">
            <!-- Thay cover.jpg, a1.jpg... bằng ảnh của bạn -->
            <img src="cover.jpg" alt="ảnh 1">
            <img src="a1.jpg" alt="ảnh 2">
            <img src="a2.jpg" alt="ảnh 3">
          </div>
        </div>

        <div class="card" style="margin-top:14px;">
          <h3>Lời chúc & Sổ ký tên</h3>
          <form id="guestForm">
            <label for="name">Tên</label>
            <input id="gname" placeholder="Tên của bạn" required>
            <label for="message">Lời chúc</label>
            <textarea id="gmsg" rows="3" placeholder="Chúc mừng..."></textarea>
            <button type="submit" class="btn" style="margin-top:8px">Gửi lời chúc</button>
          </form>
          <div class="guestbook-list" id="guestList"></div>
        </div>

      </div>

      <aside class="card">
        <h3>Thông tin sự kiện</h3>
        <p><strong>Thời gian:</strong> 30/04/2026 — 11:00</p>
        <p><strong>Địa điểm:</strong> Nhà hàng Bù Đốp</p>

        <div class="map card" style="margin-top:10px;">
          <!-- iframe tìm "Nhà hàng Bù Đốp" trên Google Maps -->
          <iframe id="gmap" src="https://www.google.com/maps?q=Nh%C3%A0+h%C3%A0ng+B%C3%B9+%C4%90%E1%BB%9Fp&output=embed"></iframe>
        </div>

        <div style="margin-top:12px;">
          <h4>RSVP</h4>
          <!-- Option 1: Google Forms embed (nếu bạn có link thay src) -->
          <!-- Option 2: Form tạm dùng localStorage (thích hợp thử nghiệm) -->
          <form id="rsvpForm">
            <label>Tên khách</label>
            <input id="r_name" placeholder="Tên khách" required>
            <label>Số lượng</label>
            <select id="r_qty"><option>1</option><option>2</option><option>3</option><option>4</option></select>
            <label>Ghi chú (ví dụ: món chay)</label>
            <input id="r_note" placeholder="Ghi chú">
            <button type="submit" class="btn" style="margin-top:8px">Xác nhận tham dự</button>
          </form>
          <div id="rsvpList" class="muted" style="margin-top:10px"></div>
        </div>

        <div style="margin-top:12px;">
          <h4>Chia sẻ</h4>
          <a class="btn" id="shareFB" style="display:inline-block;margin-right:8px">Chia sẻ FB</a>
          <a class="btn" id="shareZalo" style="display:inline-block;background:#ff6b6b">Chia sẻ Zalo</a>
          <div style="margin-top:10px">
            <img id="qrcode" src="" alt="QR" style="width:120px;border-radius:8px"/>
            <div class="muted">Quét để mở thiệp</div>
          </div>
        </div>

      </aside>
    </section>

    <footer>
      <div>© Minh Tâm & Trường Long — 30/04/2026</div>
    </footer>
  </div>

  <!-- Audio (bật/tắt bằng nút) -->
  <audio id="bgmusic" loop src="music.mp3"></audio>

  <script>
    /* === CONFIG - chỉnh ở đây nếu cần === */
    const weddingDate = new Date('2026-04-30T11:00:00'); // chỉnh năm, giờ nếu cần
    const inviteUrl = location.href; // dùng url hiện tại
    const couple = { bride: "Minh Tâm", groom: "Trường Long" };

    /* === Countdown chạy liên tục === */
    function updateCountdown(){
      const now = new Date();
      let diff = weddingDate - now;
      if(diff < 0) diff = 0;
      const days = Math.floor(diff / (1000*60*60*24));
      const hours = Math.floor((diff / (1000*60*60)) % 24);
      const mins = Math.floor((diff / (1000*60)) % 60);
      const secs = Math.floor((diff / 1000) % 60);
      document.getElementById('days').textContent = days;
      document.getElementById('hours').textContent = String(hours).padStart(2,'0');
      document.getElementById('mins').textContent = String(mins).padStart(2,'0');
      document.getElementById('secs').textContent = String(secs).padStart(2,'0');
    }
    setInterval(updateCountdown, 1000);
    updateCountdown();

    /* === Music toggle === */
    const bg = document.getElementById('bgmusic');
    const btn = document.getElementById('music-toggle');
    let musicOn = false;
    btn.addEventListener('click', ()=>{
      if(!musicOn){ bg.play().catch(()=>{}); btn.textContent='Tắt nhạc'; musicOn=true; }
      else { bg.pause(); btn.textContent='Bật nhạc'; musicOn=false; }
    });

    /* === Guestbook (lưu localStorage) === */
    const guestForm = document.getElementById('guestForm');
    const guestListEl = document.getElementById('guestList');
    function loadGuests(){
      const arr = JSON.parse(localStorage.getItem('wedding_guestbook')||'[]');
      guestListEl.innerHTML = arr.map(g => `<div class="guest-item"><strong>${escapeHtml(g.name)}</strong><div class="muted">${escapeHtml(g.time)}</div><div>${escapeHtml(g.msg)}</div></div>`).join('');
    }
    guestForm.addEventListener('submit', e=>{
      e.preventDefault();
      const name = document.getElementById('gname').value.trim() || 'Vô danh';
      const msg = document.getElementById('gmsg').value.trim() || 'Chúc mừng!';
      const arr = JSON.parse(localStorage.getItem('wedding_guestbook')||'[]');
      arr.unshift({name, msg, time: (new Date()).toLocaleString()});
      localStorage.setItem('wedding_guestbook', JSON.stringify(arr));
      guestForm.reset();
      loadGuests();
    });
    loadGuests();

    /* === RSVP form (lưu localStorage, hoặc bạn có thể embed Google Forms) === */
    const rsvpForm = document.getElementById('rsvpForm');
    const rsvpList = document.getElementById('rsvpList');
    function loadRSVP(){
      const arr = JSON.parse(localStorage.getItem('wedding_rsvp')||'[]');
      if(!arr.length) rsvpList.innerHTML = '<div class="muted">Chưa có xác nhận nào.</div>';
      else rsvpList.innerHTML = arr.map(r=>`<div style="padding:6px;border-radius:8px;background:#fff;margin-bottom:8px;border:1px solid #f8eaf0"><strong>${escapeHtml(r.name)}</strong> — ${r.qty} khách<br><small class="muted">${escapeHtml(r.note)}</small></div>`).join('');
    }
    rsvpForm.addEventListener('submit', e=>{
      e.preventDefault();
      const name = document.getElementById('r_name').value.trim() || 'Vô danh';
      const qty = document.getElementById('r_qty').value;
      const note = document.getElementById('r_note').value.trim();
      const arr = JSON.parse(localStorage.getItem('wedding_rsvp')||'[]');
      arr.unshift({name, qty, note, time: (new Date()).toLocaleString()});
      localStorage.setItem('wedding_rsvp', JSON.stringify(arr));
      rsvpForm.reset();
      loadRSVP();
      alert('Cảm ơn! Đã ghi nhận xác nhận tham dự.');
    });
    loadRSVP();

    /* === Share buttons === */
    document.getElementById('shareFB').addEventListener('click', ()=>{
      const url = encodeURIComponent(inviteUrl);
      const fb = `https://www.facebook.com/sharer/sharer.php?u=${url}`;
      window.open(fb,'_blank');
    });
    document.getElementById('shareZalo').addEventListener('click', ()=>{
      const url = encodeURIComponent(inviteUrl);
      // Zalo share fallback: open web zalo share (may work on mobile)
      const zalo = `https://zalo.me/share?url=${url}`;
      window.open(zalo,'_blank');
    });

    /* === QR code === */
    const qr = document.getElementById('qrcode');
    qr.src = `https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=${encodeURIComponent(inviteUrl)}`;

    /* === Utility === */
    function escapeHtml(s){ return String(s).replace(/[&<>"']/g, c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c])); }

    /* === Notes for images/music ===
       - Thay cover.jpg, a1.jpg, a2.jpg, music.mp3 bằng file thực tế trong cùng thư mục.
       - Nếu bạn muốn lưu RSVP/guestbook ra server: embed Google Forms hoặc dùng Formspree/Getform.
    */

  </script>
</body>
</html>
