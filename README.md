<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>منصة القراءة</title>

  <!-- خطوط -->
  <link href="https://fonts.googleapis.com/css2?family=Merriweather&family=Montserrat:wght@600&family=Roboto&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg: #f9f9f9;
      --card-bg: #ffffff;
      --text: #222;
      --muted: #6b6b6b;
      --accent: #2b7cff;
      --reader-font-size: 18px;
      --radius: 10px;
      --shadow: 0 6px 18px rgba(0,0,0,0.06);
    }

    /* ثيم داكن */
    [data-theme="dark"]{
      --bg: #0f1113;
      --card-bg: #161718;
      --text: #eaeaea;
      --muted: #bdbdbd;
      --accent: #4da3ff;
      --shadow: 0 6px 18px rgba(0,0,0,0.45);
    }

    /* عام */
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: 'Roboto', sans-serif;
      background:var(--bg);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      transition: background-color .25s ease, color .25s ease;
      line-height:1.5;
    }

    header{
      background:var(--card-bg);
      padding:14px 20px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:12px;
      border-bottom:1px solid rgba(0,0,0,0.04);
      position:sticky;
      top:0;
      z-index:10;
    }

    header h1{
      margin:0;
      font-family:'Montserrat', sans-serif;
      color:var(--accent);
      font-size:20px;
      display:flex;
      align-items:center;
      gap:8px;
    }

    nav{
      display:flex;
      align-items:center;
      gap:10px;
    }

    nav a{
      text-decoration:none;
      color:var(--text);
      font-weight:600;
      padding:6px 8px;
      border-radius:6px;
    }
    nav a:hover{background:rgba(0,0,0,0.03)}

    /* أزرار عامة */
    .btn{
      display:inline-flex;
      align-items:center;
      gap:8px;
      border:0;
      cursor:pointer;
      padding:8px 12px;
      border-radius:8px;
      background:var(--accent);
      color:#fff;
      font-weight:600;
      transition: transform .12s ease, opacity .12s;
    }
    .btn:active{transform:translateY(1px)}
    .btn.ghost{
      background:transparent;
      color:var(--text);
      border:1px solid rgba(0,0,0,0.06);
    }

    /* بطل البداية */
    .hero{
      text-align:center;
      padding:48px 20px;
    }
    .hero h2{
      margin:0 0 18px 0;
      font-family:'Merriweather', serif;
      font-size:28px;
      color:var(--text);
    }
    .hero .cta{font-size:16px}

    /* شبكة البطاقات */
    .cards{
      padding:20px;
      display:grid;
      gap:18px;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      max-width:1200px;
      margin:0 auto;
    }
    .card{
      background:var(--card-bg);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
      overflow:hidden;
      transition: transform .18s ease, box-shadow .18s ease;
      cursor:pointer;
    }
    .card:hover{ transform:translateY(-6px) }
    .card img{ width:100%; height:150px; object-fit:cover; display:block }
    .card h3{ margin:12px; font-family:'Merriweather', serif; font-size:16px }

    /* صفحة القارئ */
    .reader{
      max-width:900px;
      margin:28px auto;
      background:var(--card-bg);
      padding:22px;
      border-radius:12px;
      box-shadow:var(--shadow);
      font-family:'Merriweather', serif;
      font-size:var(--reader-font-size);
      line-height:1.85;
      transition: background .2s, color .2s;
    }

    .reader .reader-controls{
      display:flex;
      gap:8px;
      justify-content:flex-end;
      margin-bottom:12px;
      flex-wrap:wrap;
    }

    .reader .reader-controls button{
      padding:8px 10px;
      border-radius:8px;
      border:1px solid rgba(0,0,0,0.06);
      background:transparent;
      color:var(--text);
      cursor:pointer;
      font-weight:600;
    }

    .reader .meta{ color:var(--muted); font-size:14px; margin-bottom:10px }

    footer{
      text-align:center;
      padding:18px 12px;
      color:var(--muted);
      margin-top:30px;
    }

    /* استجابة */
    @media (max-width:700px){
      header{ padding:10px 12px }
      .hero h2{ font-size:22px }
      .card img{ height:140px }
      .reader{ padding:16px }
    }
  </style>
</head>
<body>

  <header>
    <h1>📚 منصتي للقراءة</h1>

    <nav>
      <a href="#">الرئيسية</a>
      <a href="#">التصنيفات</a>
      <a href="#">حسابي</a>

      <div style="width:8px"></div>

      <button id="themeToggle" class="btn ghost" aria-label="تبديل الوضع">🌙</button>
    </nav>
  </header>

  <main>
    <section class="hero">
      <h2>اكتشف عالم الكتب والمقالات</h2>
      <button id="startReading" class="btn cta">ابدأ القراءة</button>
    </section>

    <section class="cards" aria-label="قائمة الكتب">
      <article class="card" tabindex="0">
        <img src="https://via.placeholder.com/400x250?text=Cover+1" alt="غلاف كتاب 1">
        <h3>عنوان الكتاب الأول</h3>
      </article>

      <article class="card" tabindex="0">
        <img src="https://via.placeholder.com/400x250?text=Cover+2" alt="غلاف كتاب 2">
        <h3>عنوان الكتاب الثاني</h3>
      </article>

      <article class="card" tabindex="0">
        <img src="https://via.placeholder.com/400x250?text=Cover+3" alt="غلاف كتاب 3">
        <h3>عنوان الكتاب الثالث</h3>
      </article>
    </section>

    <section class="reader" id="reader" aria-label="صفحة القراءة">
      <div class="reader-controls" role="toolbar" aria-label="أدوات القارئ">
        <button id="fontDecrease" title="تصغير الخط" aria-label="تصغير الخط">-</button>
        <button id="fontReset" title="إعادة الحجم الافتراضي" aria-label="إعادة حجم الخط">حجم افتراضي</button>
        <button id="fontIncrease" title="تكبير الخط" aria-label="تكبير الخط">+</button>
      </div>

      <div class="meta">المؤلف • تصنيف • 2025</div>

      <h2 style="margin-top:0">صفحة القراءة</h2>

      <p>
        هذا مثال لنص داخل صفحة القراءة. تم تصميم المسافات والخط لتكون مريحة للعين، مع إمكانية تغيير حجم الخط من الأزرار أعلاه.
      </p>

      <p>
        يمكنك إضافة ميزات إضافية لاحقاً مثل حفظ الملاحظات، تمييز النص، أو الانتقال بين الفصول. الكود هنا يركّز على تجربة قراءة نظيفة وسهلة التخصيص.
      </p>
    </section>
  </main>

  <footer>
    © 2025 منصتي للقراءة - جميع الحقوق محفوظة
  </footer>

  <script>
    // عناصر
    const body = document.body;
    const themeToggle = document.getElementById('themeToggle');
    const startReading = document.getElementById('startReading');
    const reader = document.getElementById('reader');
    const root = document.documentElement;

    const btnInc = document.getElementById('fontIncrease');
    const btnDec = document.getElementById('fontDecrease');
    const btnReset = document.getElementById('fontReset');

    // إعدادات افتراضية
    const DEFAULT_FONT = 18;
    const MIN_FONT = 12;
    const MAX_FONT = 28;
    const STEP = 2;

    // تحميل الإعدادات من localStorage
    function loadSettings(){
      const savedTheme = localStorage.getItem('theme');
      if(savedTheme === 'dark') body.setAttribute('data-theme','dark');
      else body.removeAttribute('data-theme');

      const savedSize = parseInt(localStorage.getItem('readerFontSize'), 10);
      if(savedSize && !isNaN(savedSize)){
        root.style.setProperty('--reader-font-size', savedSize + 'px');
      } else {
        root.style.setProperty('--reader-font-size', DEFAULT_FONT + 'px');
      }

      // زر الوضع
      updateThemeButton();
    }

    // تبديل الوضع الليلي
    function toggleTheme(){
      const isDark = body.getAttribute('data-theme') === 'dark';
      if(isDark){
        body.removeAttribute('data-theme');
        localStorage.setItem('theme','light');
      } else {
        body.setAttribute('data-theme','dark');
        localStorage.setItem('theme','dark');
      }
      updateThemeButton();
    }

    function updateThemeButton(){
      const isDark = body.getAttribute('data-theme') === 'dark';
      themeToggle.textContent = isDark ? '☀️' : '🌙';
      themeToggle.setAttribute('aria-pressed', isDark ? 'true' : 'false');
    }

    // التحكم في حجم الخط
    function getCurrentFontSize(){
      const val = getComputedStyle(root).getPropertyValue('--reader-font-size').trim();
      return parseInt(val.replace('px',''), 10) || DEFAULT_FONT;
    }

    function setFontSize(size){
      const clamped = Math.min(MAX_FONT, Math.max(MIN_FONT, size));
      root.style.setProperty('--reader-font-size', clamped + 'px');
      localStorage.setItem('readerFontSize', clamped);
    }

    btnInc.addEventListener('click', () => {
      setFontSize(getCurrentFontSize() + STEP);
    });

    btnDec.addEventListener('click', () => {
      setFontSize(getCurrentFontSize() - STEP);
    });

    btnReset.addEventListener('click', () => {
      setFontSize(DEFAULT_FONT);
    });

    // زر تبديل الثيم
    themeToggle.addEventListener('click', toggleTheme);

    // زر ابدأ القراءة
    startReading.addEventListener('click', () => {
      reader.scrollIntoView({behavior:'smooth', block:'start'});
      // تركيز على العنصر لتحسين الوصول
      setTimeout(()=> reader.focus({preventScroll:true}), 400);
    });

    // تحميل الإعدادات عند بدء الصفحة
    loadSettings();

    // اختصارات لوحة مفاتيح مفيدة
    document.addEventListener('keydown', (e) => {
      if(e.key === '+' || (e.key === '=' && (e.ctrlKey || e.metaKey))) {
        e.preventDefault();
        setFontSize(getCurrentFontSize() + STEP);
      } else if(e.key === '-' ) {
        e.preventDefault();
        setFontSize(getCurrentFontSize() - STEP);
      } else if(e.key.toLowerCase() === 'd' && (e.ctrlKey || e.metaKey)) {
        e.preventDefault();
        toggleTheme();
      }
    });
  </script>
</body>
</html>
