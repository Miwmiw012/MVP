# MVP
Game

<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#10172a">
<title>Pixel Esports Manager</title>
<style>
:root {
  --bg:#0b1020;
  --panel:#16223b;
  --line:#344969;
  --blue:#58a6ff;
  --gold:#ffd166;
  --text:#edf4ff;
  --muted:#9aaccb;
}
* { box-sizing:border-box; }
body {
  margin:0;
  background:var(--bg);
  color:var(--text);
  font-family:system-ui,sans-serif;
}
header {
  padding:18px 14px;
  background:#101a30;
  border-bottom:2px solid var(--line);
}
.logo {
  font-size:27px;
}
h1 {
  font-size:19px;
  margin:4px 0;
}
.subtitle {
  font-size:10px;
  color:var(--blue);
  letter-spacing:2px;
  font-weight:bold;
}
.stats {
  display:flex;
  gap:8px;
  overflow:auto;
  margin-top:14px;
}
.stat {
  white-space:nowrap;
  background:var(--bg);
  border:1px solid var(--line);
  border-radius:7px;
  padding:7px 10px;
  font-size:12px;
}
.stat b { color:var(--gold); }
main {
  max-width:760px;
  margin:auto;
  padding:14px 12px 100px;
}
.hero {
  background:linear-gradient(135deg,#203c67,#142038);
  border:2px solid #456797;
  border-radius:12px;
  padding:18px;
}
.label {
  color:#67e8f9;
  font-size:10px;
  font-weight:bold;
  letter-spacing:2px;
}
h2 { font-size:21px; margin:8px 0; }
p { color:var(--muted); font-size:13px; }
button {
  border:1px solid #5489c6;
  background:#244b80;
  color:white;
  padding:11px 13px;
  border-radius:8px;
  font-weight:bold;
  cursor:pointer;
}
button:active { transform:translateY(2px); }
button.secondary {
  background:#202e49;
  border-color:var(--line);
}
.section-title {
  margin:22px 2px 10px;
  font-size:16px;
}
.grid {
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:10px;
}
.card {
  padding:13px;
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:10px;
}
.card h3 { margin:0 0 8px; font-size:14px; }
.big { font-size:23px; font-weight:900; }
.muted { color:var(--muted); font-size:12px; }
.menu {
  position:fixed;
  bottom:0;
  left:0;
  right:0;
  display:grid;
  grid-template-columns:repeat(5,1fr);
  gap:3px;
  padding:8px 4px;
  padding-bottom:calc(8px + env(safe-area-inset-bottom));
  background:#101a30;
  border-top:2px solid var(--line);
}
.menu button {
  background:transparent;
  border:0;
  padding:6px 1px;
  font-size:10px;
  color:var(--muted);
}
.menu button span {
  display:block;
  font-size:21px;
}
.menu button.active {
  color:white;
  background:#244064;
  border-radius:8px;
}
.notice {
  margin-top:12px;
  padding:12px;
  border:1px solid var(--line);
  border-radius:9px;
  background:#111b30;
  font-size:12px;
  color:var(--muted);
}
.footer {
  text-align:center;
  padding:25px 0;
  color:#687c9d;
  font-size:10px;
}
@media(min-width:600px) {
  main { padding-top:22px; }
  .grid { grid-template-columns:repeat(3,minmax(0,1fr)); }
  .menu {
    position:static;
    max-width:760px;
    margin:0 auto 10px;
    border:1px solid var(--line);
    border-radius:10px;
  }
}
</style>
</head>
<body>

<header>
  <div class="logo">⚔️ 🏆</div>
  <div class="subtitle">16-BIT MANAGEMENT SIMULATOR</div>
  <h1>PIXEL ESPORTS MANAGER</h1>
  <div class="stats">
    <div class="stat">💰 <b id="money">$120,000</b></div>
    <div class="stat">📅 <b>Season 1</b></div>
    <div class="stat">⭐ ชื่อเสียง <b>15</b></div>
  </div>
</header>

<main id="app"></main>

<nav class="menu" id="menu">
  <button class="active" data-page="home">
    <span>🏠</span>สโมสร
  </button>
  <button data-page="roster">
    <span>👥</span>นักแข่ง
  </button>
  <button data-page="market">
    <span>💱</span>ตลาด
  </button>
  <button data-page="training">
    <span>🎯</span>ฝึกซ้อม
  </button>
  <button data-page="league">
    <span>🏆</span>ลีก/แข่ง
  </button>
</nav>

<script>
const pages = {
  home: `
    <section class="hero">
      <div class="label">WELCOME, MANAGER</div>
      <h2>YOUR TEAM 🦊</h2>
      <p>ทุกตำนานเริ่มต้นจากทีมเล็ก ๆ
      สร้างทีมของคุณ ปั้นนักแข่ง และมุ่งสู่แชมป์โลก</p>
      <button onclick="showPage('roster')">
        👥 จัดการนักแข่ง
      </button>
      <button class="secondary"
        onclick="showPage('league')">
        🏆 ดูการแข่งขัน
      </button>
    </section>

    <h2 class="section-title">📊 ภาพรวมสโมสร</h2>
    <div class="grid">
      <div class="card">
        <h3>⚔️ พลังทีม</h3>
        <div class="big">52</div>
        <div class="muted">จาก 100 คะแนน</div>
      </div>
      <div class="card">
        <h3>🏆 ผลงาน</h3>
        <div class="big">0W - 0L</div>
        <div class="muted">ยังไม่มีการแข่งขัน</div>
      </div>
      <div class="card">
        <h3>💸 ค่าเหนื่อย</h3>
        <div class="big">$8,500</div>
        <div class="muted">ต่อเดือน</div>
      </div>
    </div>

    <h2 class="section-title">🗓️ ตารางสัปดาห์นี้</h2>
    <div class="card">
      <h3>เตรียมทีมสำหรับฤดูกาลแรก</h3>
      <p>ตรวจสอบรายชื่อนักแข่ง
      ฝึกซ้อม และวางแผนก่อนลงสนาม</p>
      <button onclick="showPage('training')">
        เริ่มเตรียมทีม
      </button>
    </div>

    <div class="notice">
      💡 เป้าหมายแรก: สร้างทีมที่แข็งแกร่ง
      ก่อนเริ่มไล่ล่าแชมป์ลีก
    </div>
  `,

  roster: `
    <h2>👥 รายชื่อนักแข่ง</h2>
    <p>ผู้เล่นตัวจริง 5 ตำแหน่งของสโมสร</p>
    <div class="card">
      <h3>🛡️ TOP — ผู้เล่นเลนบน</h3>
      <p>ยังไม่ได้สร้างฐานข้อมูลนักแข่ง</p>
    </div>
    <div class="card" style="margin-top:8px">
      <h3>🌲 JUNGLE — ป่า</h3>
      <p>ระบบนักแข่งจะถูกเพิ่มในขั้นที่ 2</p>
    </div>
    <div class="card" style="margin-top:8px">
      <h3>🔮 MID — เลนกลาง</h3>
      <p>ระบบนักแข่งจะถูกเพิ่มในขั้นที่ 2</p>
    </div>
    <div class="card" style="margin-top:8px">
      <h3>🏹 ADC — แครี่</h3>
      <p>ระบบนักแข่งจะถูกเพิ่มในขั้นที่ 2</p>
    </div>
    <div class="card" style="margin-top:8px">
      <h3>💚 SUPPORT — ซัพพอร์ต</h3>
      <p>ระบบนักแข่งจะถูกเพิ่มในขั้นที่ 2</p>
    </div>
  `,

  market: `
    <h2>💱 ตลาดนักแข่ง</h2>
    <div class="card">
      <h3>ตลาดซื้อขายยังไม่เปิด</h3>
      <p>ในขั้นถัดไป คุณจะสามารถค้นหา
      ซื้อ และเจรจาสัญญากับนักแข่งได้</p>
    </div>
  `,

  training: `
    <h2>🎯 ศูนย์ฝึกซ้อม</h2>
    <div class="card">
      <h3>โปรแกรมฝึกซ้อม</h3>
      <p>การฝึกกลไกการเล่น ทีมเวิร์ก และแท็กติก
      จะเปิดใช้งานหลังสร้างระบบนักแข่ง</p>
    </div>
  `,

  league: `
    <h2>🏆 ลีกการแข่งขัน</h2>
    <div class="card">
      <h3>PIXEL PRO LEAGUE</h3>
      <p>12 ทีมกำลังเตรียมตัวสำหรับฤดูกาลใหม่</p>
      <div class="notice">
        🥇 รอบลีก<br>
        🥈 รอบเพลย์ออฟ<br>
        🏆 รอบชิงแชมป์
      </div>
    </div>
  `
};

function showPage(name) {
  document.getElementById("app").innerHTML =
    pages[name] + '<div class="footer">PIXEL ESPORTS MANAGER · BUILD 0.1</div>';

  document.querySelectorAll("#menu button").forEach(button => {
    button.classList.toggle("active", button.dataset.page === name);
  });

  window.scrollTo({ top: 0, behavior: "smooth" });
}

document.getElementById("menu").addEventListener("click", event => {
  const button = event.target.closest("button[data-page]");
  if (button) showPage(button.dataset.page);
});

showPage("home");
</script>

</body>
</html>
