<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Studio Nexo — Site moderno</title>
  <meta name="description" content="Modelo de site moderno, responsivo e elegante em HTML, CSS e JavaScript." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&family=Cormorant+Garamond:wght@500;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #f6f1e8;
      --surface: rgba(255,255,255,0.56);
      --surface-strong: rgba(255,255,255,0.82);
      --text: #1c1a18;
      --muted: #645d56;
      --line: rgba(28,26,24,0.12);
      --accent: #a44a2f;
      --accent-2: #2f5d50;
      --shadow: 0 20px 60px rgba(41, 29, 20, 0.10);
      --radius: 24px;
      --max: 1200px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family:"Space Grotesk", sans-serif;
      color:var(--text);
      background:
        radial-gradient(circle at 15% 20%, rgba(164,74,47,0.12), transparent 35%),
        radial-gradient(circle at 85% 15%, rgba(47,93,80,0.10), transparent 32%),
        linear-gradient(180deg, #f9f5ed 0%, #f1eadf 100%);
      overflow-x:hidden;
    }

    body::before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.08;
      background-image:
        linear-gradient(rgba(28,26,24,.08) 1px, transparent 1px),
        linear-gradient(90deg, rgba(28,26,24,.08) 1px, transparent 1px);
      background-size: 36px 36px;
      mask-image: radial-gradient(circle at center, black 35%, transparent 90%);
    }

    h1,h2,h3{
      font-family:"Cormorant Garamond", serif;
      line-height:.95;
      margin:0;
      font-weight:700;
      letter-spacing:-0.03em;
    }

    p{
      margin:0;
      color:var(--muted);
      line-height:1.7;
      font-size:1rem;
    }

    a{text-decoration:none;color:inherit}
    img{max-width:100%}
    .container{
      width:min(calc(100% - 2rem), var(--max));
      margin-inline:auto;
    }

    .site-header{
      position:sticky;
      top:0;
      z-index:50;
      backdrop-filter: blur(18px);
      background:rgba(246,241,232,0.66);
      border-bottom:1px solid rgba(28,26,24,0.08);
    }

    .nav{
      display:flex;
      align-items:center;
      justify-content:space-between;
      min-height:78px;
      gap:1rem;
    }

    .brand{
      display:flex;
      align-items:center;
      gap:.9rem;
      font-weight:700;
      letter-spacing:.04em;
      text-transform:uppercase;
      font-size:.85rem;
    }

    .brand-mark{
      width:42px;height:42px;border-radius:50%;
      display:grid;place-items:center;
      background:
        radial-gradient(circle at 30% 30%, #d79b82, transparent 35%),
        linear-gradient(135deg, var(--accent), var(--accent-2));
      color:#fff;
      box-shadow: var(--shadow);
      font-family:"Cormorant Garamond", serif;
      font-size:1.2rem;
    }

    .nav-links{
      display:flex;
      align-items:center;
      gap:1.2rem;
      color:var(--muted);
      font-size:.95rem;
    }

    .nav-links a{
      position:relative;
      padding:.35rem 0;
    }

    .nav-links a::after{
      content:"";
      position:absolute;
      left:0; bottom:0;
      width:0; height:1px;
      background:var(--text);
      transition:width .3s ease;
    }

    .nav-links a:hover::after{width:100%}

    .nav-toggle{
      display:none;
      background:none;
      border:none;
      width:44px;height:44px;
      border-radius:50%;
      cursor:pointer;
    }

    .nav-toggle span,
    .nav-toggle::before,
    .nav-toggle::after{
      content:"";
      display:block;
      width:22px;height:2px;
      background:var(--text);
      margin:5px auto;
      transition:.3s ease;
    }

    .hero{
      padding: clamp(3rem, 7vw, 7rem) 0 3rem;
    }

    .hero-grid{
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:2rem;
      align-items:end;
    }

    .eyebrow{
      display:inline-flex;
      align-items:center;
      gap:.65rem;
      border:1px solid var(--line);
      border-radius:999px;
      padding:.55rem .9rem;
      background:var(--surface);
      backdrop-filter: blur(14px);
      color:var(--muted);
      font-size:.85rem;
      margin-bottom:1.2rem;
    }

    .dot{
      width:9px;height:9px;border-radius:50%;
      background:linear-gradient(135deg, var(--accent), var(--accent-2));
      box-shadow:0 0 0 6px rgba(164,74,47,.08);
    }

    .hero h1{
      font-size: clamp(3.6rem, 10vw, 8.5rem);
      max-width: 10ch;
    }

    .hero-copy{
      display:grid;
      gap:1.25rem;
      align-content:end;
      padding-bottom:.6rem;
    }

    .hero-copy p{
      font-size:1.05rem;
      max-width:52ch;
    }

    .actions{
      display:flex;
      flex-wrap:wrap;
      gap:.9rem;
      margin-top:.5rem;
    }

    .btn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      gap:.65rem;
      min-height:52px;
      padding:0 1.15rem;
      border-radius:999px;
      border:1px solid transparent;
      font-weight:600;
      transition: transform .25s ease, box-shadow .25s ease, background .25s ease, color .25s ease;
      cursor:pointer;
    }

    .btn-primary{
      background:var(--text);
      color:#f7f1e9;
      box-shadow: 0 14px 35px rgba(28,26,24,.18);
    }

    .btn-primary:hover{
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 18px 40px rgba(28,26,24,.24);
    }

    .btn-secondary{
      background:var(--surface);
      color:var(--text);
      border-color:var(--line);
      backdrop-filter: blur(12px);
    }

    .btn-secondary:hover{
      transform: translateY(-2px);
      background:var(--surface-strong);
    }

    .hero-panel{
      margin-top:2.5rem;
      border:1px solid var(--line);
      background:var(--surface);
      backdrop-filter: blur(18px);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      overflow:hidden;
      display:grid;
      grid-template-columns: 1.2fr .8fr;
      min-height:420px;
    }

    .panel-art{
      position:relative;
      background:
        radial-gradient(circle at 20% 20%, rgba(255,255,255,.6), transparent 30%),
        radial-gradient(circle at 70% 35%, rgba(164,74,47,.22), transparent 28%),
        radial-gradient(circle at 35% 78%, rgba(47,93,80,.18), transparent 24%),
        linear-gradient(135deg, #e9ddcf 0%, #f8f3ec 100%);
      isolation:isolate;
      overflow:hidden;
    }

    .panel-art::before,
    .panel-art::after{
      content:"";
      position:absolute;
      border-radius:48% 52% 61% 39% / 39% 42% 58% 61%;
      filter: blur(0.2px);
    }

    .panel-art::before{
      width:280px;height:280px;
      background:linear-gradient(135deg, var(--accent), #d3a188);
      left:8%;
      bottom:10%;
      opacity:.92;
      transform:rotate(-12deg);
    }

    .panel-art::after{
      width:220px;height:220px;
      background:linear-gradient(135deg, var(--accent-2), #95b3a9);
      right:10%;
      top:14%;
      opacity:.86;
      transform:rotate(10deg);
    }

    .art-lines{
      position:absolute;
      inset:0;
      background:
        repeating-linear-gradient(90deg, transparent 0 34px, rgba(28,26,24,.05) 34px 35px),
        repeating-linear-gradient(transparent 0 34px, rgba(28,26,24,.05) 34px 35px);
      mask-image: linear-gradient(180deg, black, transparent 92%);
    }

    .panel-info{
      display:grid;
      align-content:space-between;
      padding:1.5rem;
      border-left:1px solid var(--line);
      background:linear-gradient(180deg, rgba(255,255,255,.46), rgba(255,255,255,.22));
    }

    .stat{
      display:grid;
      gap:.4rem;
      padding-bottom:1.1rem;
      border-bottom:1px solid var(--line);
    }

    .stat strong{
      font-family:"Cormorant Garamond", serif;
      font-size: clamp(2rem, 4vw, 3.1rem);
      line-height:1;
    }

    .mini-list{
      display:grid;
      gap:.9rem;
      padding-top:1rem;
    }

    .mini-list div{
      display:flex;
      justify-content:space-between;
      gap:1rem;
      font-size:.95rem;
      color:var(--muted);
    }

    section{
      padding: clamp(4rem, 8vw, 7rem) 0;
    }

    .section-head{
      display:grid;
      grid-template-columns: .9fr 1.1fr;
      gap:2rem;
      align-items:end;
      margin-bottom:2.2rem;
    }

    .section-head h2{
      font-size: clamp(2.4rem, 5vw, 5rem);
      max-width:8ch;
    }

    .split-layout{
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:1.2rem;
    }

    .feature-block{
      border-top:1px solid var(--line);
      padding-top:1.15rem;
      display:grid;
      gap:.7rem;
    }

    .feature-block h3{
      font-size: clamp(1.6rem, 3vw, 2.4rem);
    }

    .showcase{
      display:grid;
      grid-template-columns: 1.05fr .95fr;
      gap:1.2rem;
      align-items:stretch;
    }

    .showcase-main, .showcase-side{
      border:1px solid var(--line);
      border-radius: var(--radius);
      overflow:hidden;
      background:var(--surface);
      box-shadow: var(--shadow);
      backdrop-filter: blur(16px);
    }

    .showcase-main{
      min-height:460px;
      position:relative;
      padding:1.5rem;
      display:grid;
      align-content:space-between;
      background:
        radial-gradient(circle at 80% 15%, rgba(47,93,80,.16), transparent 26%),
        radial-gradient(circle at 15% 80%, rgba(164,74,47,.16), transparent 28%),
        linear-gradient(180deg, rgba(255,255,255,.55), rgba(255,255,255,.28));
    }

    .showcase-shape{
      position:absolute;
      inset:auto 6% 8% auto;
      width:min(42vw, 360px);
      aspect-ratio:1;
      border-radius:32px;
      background:
        linear-gradient(135deg, rgba(164,74,47,.9), rgba(47,93,80,.78)),
        linear-gradient(180deg, #fff, #ddd);
      transform:rotate(12deg);
      opacity:.92;
      box-shadow: 0 24px 60px rgba(41,29,20,.18);
    }

    .showcase-main .tag{
      width:max-content;
      border:1px solid var(--line);
      border-radius:999px;
      padding:.45rem .8rem;
      background:rgba(255,255,255,.5);
      color:var(--muted);
      font-size:.85rem;
    }

    .showcase-main h3{
      font-size: clamp(2rem, 4.5vw, 4rem);
      max-width:8ch;
      z-index:1;
    }

    .showcase-side{
      display:grid;
      grid-template-rows: 1fr 1fr;
    }

    .side-panel{
      padding:1.5rem;
      display:grid;
      gap:.8rem;
      align-content:start;
    }

    .side-panel + .side-panel{
      border-top:1px solid var(--line);
    }

    .side-panel h3{
      font-size: clamp(1.5rem, 3vw, 2.2rem);
    }

    .process{
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:1.2rem;
    }

    .step{
      padding:1rem 0 0;
      border-top:1px solid var(--line);
    }

    .step .num{
      font-size:.85rem;
      color:var(--accent);
      letter-spacing:.14em;
      text-transform:uppercase;
      margin-bottom:.6rem;
    }

    .step h3{
      font-size: clamp(1.55rem, 3vw, 2.4rem);
      margin-bottom:.5rem;
    }

    .cta{
      padding-bottom:5.5rem;
    }

    .cta-shell{
      border:1px solid var(--line);
      border-radius: calc(var(--radius) + 8px);
      background:
        radial-gradient(circle at 10% 20%, rgba(164,74,47,.14), transparent 26%),
        radial-gradient(circle at 85% 75%, rgba(47,93,80,.14), transparent 22%),
        linear-gradient(180deg, rgba(255,255,255,.6), rgba(255,255,255,.35));
      backdrop-filter: blur(16px);
      box-shadow: var(--shadow);
      padding: clamp(1.4rem, 3vw, 2.4rem);
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:1.2rem;
      align-items:end;
    }

    .cta-shell h2{
      font-size: clamp(2.2rem, 5vw, 4.6rem);
      max-width:9ch;
    }

    .site-footer{
      padding:1.5rem 0 2.2rem;
      border-top:1px solid rgba(28,26,24,0.08);
      color:var(--muted);
      font-size:.92rem;
    }

    .footer-row{
      display:flex;
      justify-content:space-between;
      gap:1rem;
      flex-wrap:wrap;
    }

    .reveal{
      opacity:0;
      transform:translateY(26px);
      transition:opacity .8s ease, transform .8s ease;
    }

    .reveal.visible{
      opacity:1;
      transform:none;
    }

    .stagger > *{
      opacity:0;
      transform:translateY(22px);
      animation: rise .8s ease forwards;
    }

    .stagger > *:nth-child(1){animation-delay:.08s}
    .stagger > *:nth-child(2){animation-delay:.18s}
    .stagger > *:nth-child(3){animation-delay:.28s}
    .stagger > *:nth-child(4){animation-delay:.38s}
    .stagger > *:nth-child(5){animation-delay:.48s}

    @keyframes rise{
      to{opacity:1;transform:none}
    }

    @media (max-width: 920px){
      .hero-grid,
      .section-head,
      .split-layout,
      .showcase,
      .cta-shell,
      .hero-panel,
      .process{
        grid-template-columns:1fr;
      }

      .hero-panel{
        min-height:auto;
      }

      .panel-info{
        border-left:none;
        border-top:1px solid var(--line);
      }

      .showcase-side{
        grid-template-rows:auto;
      }

      .nav-links{
        position:absolute;
        top:78px;
        left:1rem;
        right:1rem;
        display:grid;
        gap:.4rem;
        padding:1rem;
        border:1px solid var(--line);
        border-radius:20px;
        background:rgba(248,243,236,.96);
        backdrop-filter: blur(16px);
        box-shadow: var(--shadow);
        opacity:0;
        pointer-events:none;
        transform:translateY(-8px);
        transition:.25s ease;
      }

      .nav-links.open{
        opacity:1;
        pointer-events:auto;
        transform:translateY(0);
      }

      .nav-toggle{display:block}
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="container nav">
      <a href="#inicio" class="brand" aria-label="Studio Nexo">
        <span class="brand-mark">N</span>
        <span>Studio Nexo</span>
      </a>

      <nav class="nav-links" id="navLinks" aria-label="Navegação principal">
        <a href="#sobre">Sobre</a>
        <a href="#servicos">Serviços</a>
        <a href="#processo">Processo</a>
        <a href="#contato">Contato</a>
      </nav>

      <button class="nav-toggle" id="navToggle" aria-label="Abrir menu" aria-expanded="false" aria-controls="navLinks">
        <span></span>
      </button>
    </div>
  </header>

  <main id="inicio">
    <section class="hero">
      <div class="container">
        <div class="hero-grid">
          <div class="stagger">
            <div class="eyebrow">
              <span class="dot"></span>
              Design, presença e identidade digital
            </div>
            <h1>Um site com cara de marca de verdade.</h1>
          </div>

          <div class="hero-copy stagger">
            <p>
              Se você quer criar um site bonito, moderno e profissional, este modelo é um ponto de partida forte:
              visual refinado, estrutura responsiva e interações suaves para impressionar no primeiro clique.
            </p>
            <div class="actions">
              <a class="btn btn-primary" href="#contato">Começar agora</a>
              <a class="btn btn-secondary" href="#servicos">Ver estrutura</a>
            </div>
          </div>
        </div>

        <div class="hero-panel reveal" aria-label="Painel visual do projeto">
          <div class="panel-art">
            <div class="art-lines"></div>
          </div>
          <div class="panel-info">
            <div class="stat">
              <span>Presença digital com impacto</span>
              <strong>HTML + CSS + JS</strong>
              <p>Estrutura única, elegante e pronta para você editar com seu conteúdo.</p>
            </div>
            <div class="mini-list">
              <div><span>Responsivo</span><strong>100%</strong></div>
              <div><span>Estética</span><strong>Premium</strong></div>
              <div><span>Customização</span><strong>Fácil</strong></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="sobre">
      <div class="container">
        <div class="section-head reveal">
          <h2>Feito para destacar.</h2>
          <p>
            Em vez de um layout genérico, este site usa tipografia forte, blocos amplos, profundidade com vidro fosco
            e uma composição mais editorial. O resultado é mais sofisticado e menos “template comum”.
          </p>
        </div>

        <div class="split-layout">
          <article class="feature-block reveal">
            <h3>Visual memorável</h3>
            <p>
              Hierarquia tipográfica marcante, cores quentes e composição com personalidade para gerar percepção de valor.
            </p>
          </article>
          <article class="feature-block reveal">
            <h3>Estrutura flexível</h3>
            <p>
              Você pode adaptar este modelo para portfólio, loja, agência, negócio local ou página de apresentação.
            </p>
          </article>
        </div>
      </div>
    </section>

    <section id="servicos">
      <div class="container">
        <div class="showcase">
          <article class="showcase-main reveal">
            <span class="tag">Base ideal para seu projeto</span>
            <h3>Seções grandes, claras e com impacto visual.</h3>
            <div class="showcase-shape" aria-hidden="true"></div>
          </article>

          <div class="showcase-side">
            <article class="side-panel reveal">
              <h3>Landing page</h3>
              <p>
                Hero forte, proposta de valor, chamadas para ação e seções objetivas para converter visitantes.
              </p>
            </article>
            <article class="side-panel reveal">
              <h3>Site institucional</h3>
              <p>
                Perfeito para apresentar serviços, diferenciais, processo de trabalho e formas de contato.
              </p>
            </article>
          </div>
        </div>
      </div>
    </section>

    <section id="processo">
      <div class="container">
        <div class="section-head reveal">
          <h2>Como usar este código.</h2>
          <p>
            Você pode copiar este arquivo inteiro, salvar como <strong>index.html</strong> e abrir no navegador.
            Depois, edite textos, cores, nome da marca e botões do jeito que quiser.
          </p>
        </div>

        <div class="process">
          <article class="step reveal">
            <div class="num">Passo 01</div>
            <h3>Salve o arquivo</h3>
            <p>Crie uma pasta do projeto e cole este código em um arquivo chamado <strong>index.html</strong>.</p>
          </article>

          <article class="step reveal">
            <div class="num">Passo 02</div>
            <h3>Edite o conteúdo</h3>
            <p>Troque textos, títulos, links e nome da marca para combinar com seu objetivo.</p>
          </article>

          <article class="step reveal">
            <div class="num">Passo 03</div>
            <h3>Publique online</h3>
            <p>Hospede em GitHub Pages, Netlify, Vercel ou no seu servidor preferido.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="cta" id="contato">
      <div class="container">
        <div class="cta-shell reveal">
          <div>
            <h2>Quer mais códigos para criar seu site?</h2>
          </div>
          <div class="stagger">
            <p>
              Posso te mandar também versões para <strong>loja</strong>, <strong>portfólio</strong>,
              <strong>barbearia</strong>, <strong>restaurante</strong>, <strong>advogado</strong> ou
              <strong>landing page de produto</strong>.
            </p>
            <div class="actions">
              <a href="mailto:contato@seudominio.com" class="btn btn-primary">Usar este modelo</a>
              <a href="#inicio" class="btn btn-secondary">Voltar ao topo</a>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="container footer-row">
      <span>© 2026 Studio Nexo</span>
      <span>Modelo em HTML, CSS e JavaScript</span>
    </div>
  </footer>

  <script>
    const navToggle = document.getElementById('navToggle');
    const navLinks = document.getElementById('navLinks');

    navToggle.addEventListener('click', () => {
      const isOpen = navLinks.classList.toggle('open');
      navToggle.setAttribute('aria-expanded', isOpen);
    });

    document.querySelectorAll('.nav-links a').forEach(link => {
      link.addEventListener('click', () => {
        navLinks.classList.remove('open');
        navToggle.setAttribute('aria-expanded', 'false');
      });
    });

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if(entry.isIntersecting){
          entry.target.classList.add('visible');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.16 });

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  </script>
</body>
</html>
