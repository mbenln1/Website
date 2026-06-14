<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SwaraJuang — Ebook & Blog</title>
<style>
  /* ===== TOKENS ===== */
  :root {
    --navy: #0D1117;
    --navy2: #161B22;
    --navy3: #21262D;
    --cyan: #00D4FF;
    --cyan-dim: rgba(0,212,255,0.12);
    --gold: #FFB800;
    --white: #F8F9FA;
    --muted: #8B949E;
    --border: rgba(255,255,255,0.08);
    --radius: 12px;
    --font-display: 'Segoe UI', system-ui, sans-serif;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--navy);
    color: var(--white);
    font-family: var(--font-display);
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ===== SCROLLBAR ===== */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--navy); }
  ::-webkit-scrollbar-thumb { background: var(--cyan); border-radius: 3px; }

  /* ===== NAV ===== */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 1rem 2rem;
    background: rgba(13,17,23,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }
  .logo {
    font-size: 1.4rem; font-weight: 800;
    background: linear-gradient(135deg, var(--cyan), var(--gold));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--muted); text-decoration: none; font-size: 0.9rem;
    font-weight: 500; transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--cyan); }
  .nav-cta {
    background: var(--cyan); color: var(--navy);
    padding: 0.5rem 1.2rem; border-radius: 8px;
    font-weight: 700; font-size: 0.85rem; cursor: pointer;
    border: none; transition: opacity 0.2s;
  }
  .nav-cta:hover { opacity: 0.85; }
  .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
  .hamburger span { width: 24px; height: 2px; background: var(--white); border-radius: 2px; transition: 0.3s; }

  /* ===== HERO ===== */
  .hero {
    min-height: 100vh;
    display: flex; align-items: center;
    padding: 8rem 2rem 4rem;
    position: relative; overflow: hidden;
  }
  .hero-bg {
    position: absolute; inset: 0; z-index: 0;
    background:
      radial-gradient(ellipse 80% 60% at 70% 40%, rgba(0,212,255,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 20% 80%, rgba(255,184,0,0.06) 0%, transparent 60%);
  }
  /* Floating particles */
  .particles { position: absolute; inset: 0; z-index: 0; pointer-events: none; }
  .particle {
    position: absolute; border-radius: 50%;
    background: var(--cyan); opacity: 0.15;
    animation: float linear infinite;
  }
  @keyframes float {
    0% { transform: translateY(100vh) scale(0); opacity: 0; }
    10% { opacity: 0.15; }
    90% { opacity: 0.15; }
    100% { transform: translateY(-10vh) scale(1); opacity: 0; }
  }
  .hero-content { position: relative; z-index: 1; max-width: 650px; }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 0.5rem;
    background: var(--cyan-dim); border: 1px solid rgba(0,212,255,0.3);
    padding: 0.4rem 1rem; border-radius: 999px;
    font-size: 0.8rem; color: var(--cyan); font-weight: 600;
    margin-bottom: 1.5rem; letter-spacing: 0.05em;
  }
  .hero-badge::before { content: '●'; font-size: 0.5rem; animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.3; } }
  h1 {
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 900; line-height: 1.1;
    margin-bottom: 1.2rem; letter-spacing: -0.02em;
  }
  h1 .accent { color: var(--cyan); }
  h1 .accent-gold { color: var(--gold); }
  .hero-desc {
    font-size: 1.1rem; color: var(--muted); margin-bottom: 2.5rem;
    max-width: 500px; line-height: 1.7;
  }
  .hero-actions { display: flex; gap: 1rem; flex-wrap: wrap; }
  .btn-primary {
    background: linear-gradient(135deg, var(--cyan), #0099CC);
    color: var(--navy); padding: 0.85rem 2rem;
    border-radius: var(--radius); font-weight: 800;
    font-size: 1rem; border: none; cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 4px 24px rgba(0,212,255,0.3);
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 32px rgba(0,212,255,0.45); }
  .btn-secondary {
    background: transparent; color: var(--white);
    padding: 0.85rem 2rem; border-radius: var(--radius);
    font-weight: 700; font-size: 1rem;
    border: 1px solid var(--border); cursor: pointer;
    transition: border-color 0.2s, color 0.2s;
  }
  .btn-secondary:hover { border-color: var(--cyan); color: var(--cyan); }
  .hero-stats {
    display: flex; gap: 2.5rem; margin-top: 3rem;
    padding-top: 2rem; border-top: 1px solid var(--border);
  }
  .stat-val { font-size: 1.8rem; font-weight: 900; color: var(--white); }
  .stat-label { font-size: 0.78rem; color: var(--muted); margin-top: 0.1rem; }
  .hero-visual {
    position: absolute; right: 5%; top: 50%; transform: translateY(-50%);
    z-index: 1;
  }
  .floating-cards { position: relative; width: 340px; height: 420px; }
  .ebook-card {
    position: absolute;
    background: var(--navy2);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 1.5rem;
    width: 200px;
    transition: transform 0.3s;
  }
  .ebook-card:hover { transform: scale(1.04) !important; }
  .ebook-card:nth-child(1) {
    top: 0; left: 0;
    animation: card-float1 4s ease-in-out infinite;
  }
  .ebook-card:nth-child(2) {
    top: 60px; right: 0;
    animation: card-float2 5s ease-in-out infinite;
    border-color: rgba(0,212,255,0.3);
  }
  .ebook-card:nth-child(3) {
    bottom: 0; left: 30px;
    animation: card-float3 4.5s ease-in-out infinite;
    border-color: rgba(255,184,0,0.3);
  }
  @keyframes card-float1 { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-12px)} }
  @keyframes card-float2 { 0%,100%{transform:translateY(0)} 50%{transform:translateY(10px)} }
  @keyframes card-float3 { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-8px)} }
  .card-cover {
    width: 100%; aspect-ratio: 3/4;
    border-radius: 8px; margin-bottom: 0.8rem;
    display: flex; align-items: center; justify-content: center;
    font-size: 2rem;
  }
  .c1 { background: linear-gradient(135deg, #1a3a5c, #0d5c8a); }
  .c2 { background: linear-gradient(135deg, #1a2a1a, #0d5c2a); }
  .c3 { background: linear-gradient(135deg, #3a2a10, #7a5000); }
  .card-title { font-size: 0.8rem; font-weight: 700; margin-bottom: 0.3rem; }
  .card-price { font-size: 0.85rem; color: var(--cyan); font-weight: 800; }

  /* ===== SECTION BASE ===== */
  section { padding: 5rem 2rem; }
  .section-header { text-align: center; margin-bottom: 3.5rem; }
  .section-eyebrow {
    display: inline-block;
    color: var(--cyan); font-size: 0.75rem;
    font-weight: 700; letter-spacing: 0.12em;
    text-transform: uppercase; margin-bottom: 0.8rem;
  }
  h2 { font-size: clamp(1.8rem, 4vw, 2.8rem); font-weight: 900; line-height: 1.15; }
  .section-sub { color: var(--muted); margin-top: 0.75rem; font-size: 1rem; max-width: 500px; margin-left: auto; margin-right: auto; }
  .container { max-width: 1100px; margin: 0 auto; }

  /* ===== EBOOKS ===== */
  #ebooks { background: var(--navy); }
  .ebooks-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 1.5rem;
  }
  .product-card {
    background: var(--navy2);
    border: 1px solid var(--border);
    border-radius: 16px; overflow: hidden;
    transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
    cursor: pointer;
  }
  .product-card:hover {
    transform: translateY(-6px);
    border-color: rgba(0,212,255,0.4);
    box-shadow: 0 16px 48px rgba(0,212,255,0.1);
  }
  .product-cover {
    aspect-ratio: 16/9;
    display: flex; align-items: center; justify-content: center;
    font-size: 3rem; position: relative;
  }
  .p1 { background: linear-gradient(135deg, #0f2447, #1a4a8a); }
  .p2 { background: linear-gradient(135deg, #1a0f33, #4a1a8a); }
  .p3 { background: linear-gradient(135deg, #0f2f1a, #1a5a2a); }
  .p4 { background: linear-gradient(135deg, #331a0f, #8a3a1a); }
  .badge-new {
    position: absolute; top: 0.75rem; right: 0.75rem;
    background: var(--gold); color: var(--navy);
    font-size: 0.65rem; font-weight: 800;
    padding: 0.2rem 0.6rem; border-radius: 999px;
    letter-spacing: 0.05em;
  }
  .badge-best {
    position: absolute; top: 0.75rem; right: 0.75rem;
    background: var(--cyan); color: var(--navy);
    font-size: 0.65rem; font-weight: 800;
    padding: 0.2rem 0.6rem; border-radius: 999px;
    letter-spacing: 0.05em;
  }
  .product-info { padding: 1.25rem; }
  .product-tag {
    font-size: 0.7rem; color: var(--cyan); font-weight: 700;
    letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 0.4rem;
  }
  .product-title { font-size: 1rem; font-weight: 700; margin-bottom: 0.5rem; line-height: 1.3; }
  .product-desc { font-size: 0.82rem; color: var(--muted); margin-bottom: 1rem; line-height: 1.5; }
  .product-footer { display: flex; align-items: center; justify-content: space-between; }
  .product-price { font-size: 1.15rem; font-weight: 900; color: var(--white); }
  .product-price .orig { font-size: 0.78rem; color: var(--muted); text-decoration: line-through; font-weight: 400; margin-right: 0.3rem; }
  .btn-buy {
    background: var(--cyan); color: var(--navy);
    border: none; border-radius: 8px;
    padding: 0.5rem 1rem; font-weight: 800;
    font-size: 0.82rem; cursor: pointer;
    transition: opacity 0.2s;
  }
  .btn-buy:hover { opacity: 0.85; }
  .rating { display: flex; align-items: center; gap: 0.3rem; font-size: 0.78rem; color: var(--gold); margin-bottom: 0.6rem; }
  .rating span { color: var(--muted); }

  /* ===== PAYMENT MODAL ===== */
  .modal-overlay {
    display: none; position: fixed; inset: 0; z-index: 1000;
    background: rgba(0,0,0,0.75); backdrop-filter: blur(6px);
    align-items: center; justify-content: center; padding: 1rem;
  }
  .modal-overlay.active { display: flex; }
  .modal {
    background: var(--navy2); border: 1px solid var(--border);
    border-radius: 20px; padding: 2rem; max-width: 480px; width: 100%;
    animation: modal-in 0.25s ease;
  }
  @keyframes modal-in { from { opacity:0; transform:scale(0.95); } to { opacity:1; transform:scale(1); } }
  .modal-header { display: flex; justify-content: space-between; align-items: start; margin-bottom: 1.5rem; }
  .modal-title { font-size: 1.1rem; font-weight: 800; }
  .modal-close { background: none; border: none; color: var(--muted); font-size: 1.4rem; cursor: pointer; line-height: 1; }
  .modal-close:hover { color: var(--white); }
  .modal-product { display: flex; gap: 1rem; align-items: center; padding: 1rem; background: var(--navy3); border-radius: 10px; margin-bottom: 1.5rem; }
  .modal-cover { width: 60px; height: 75px; border-radius: 6px; display:flex; align-items:center; justify-content:center; font-size:1.5rem; flex-shrink:0; }
  .modal-product-info h4 { font-size: 0.95rem; font-weight: 700; margin-bottom: 0.3rem; }
  .modal-product-info .price { font-size: 1.2rem; color: var(--cyan); font-weight: 900; }

  .pay-methods { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.75rem; margin-bottom: 1.5rem; }
  .pay-method {
    border: 2px solid var(--border); border-radius: 10px;
    padding: 0.8rem 0.5rem; text-align: center; cursor: pointer;
    transition: border-color 0.2s, background 0.2s;
  }
  .pay-method:hover { border-color: var(--cyan); background: var(--cyan-dim); }
  .pay-method.active { border-color: var(--cyan); background: var(--cyan-dim); }
  .pay-method .pm-icon { font-size: 1.5rem; margin-bottom: 0.3rem; }
  .pay-method .pm-label { font-size: 0.7rem; font-weight: 700; color: var(--muted); }
  .pay-method.active .pm-label { color: var(--cyan); }

  .pay-detail { background: var(--navy3); border-radius: 10px; padding: 1.2rem; margin-bottom: 1.5rem; font-size: 0.88rem; }
  .pay-detail h4 { font-weight: 700; margin-bottom: 0.75rem; font-size: 0.9rem; }
  .pay-detail .acc-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.5rem; }
  .pay-detail .acc-val { font-weight: 800; color: var(--cyan); font-size: 1rem; letter-spacing: 0.08em; }
  .pay-detail .copy-btn {
    background: var(--cyan-dim); color: var(--cyan);
    border: 1px solid rgba(0,212,255,0.3);
    border-radius: 6px; padding: 0.25rem 0.7rem;
    font-size: 0.72rem; font-weight: 700; cursor: pointer;
  }
  .pay-detail .note { color: var(--muted); font-size: 0.78rem; margin-top: 0.5rem; line-height: 1.5; }
  .qris-box { text-align: center; padding: 1rem; }
  .qris-mock {
    width: 160px; height: 160px; margin: 0 auto 0.75rem;
    background: white; border-radius: 8px; display: flex; align-items: center; justify-content: center;
    font-size: 3rem; position: relative;
  }
  .qris-mock::after {
    content: 'QRIS';
    position: absolute; bottom: -1.5rem;
    font-size: 0.75rem; color: var(--muted); font-weight: 700;
  }

  .form-group { margin-bottom: 1rem; }
  .form-group label { display: block; font-size: 0.8rem; font-weight: 600; color: var(--muted); margin-bottom: 0.4rem; }
  .form-group input {
    width: 100%; background: var(--navy3);
    border: 1px solid var(--border); border-radius: 8px;
    color: var(--white); padding: 0.7rem 1rem;
    font-size: 0.9rem; outline: none;
    transition: border-color 0.2s;
  }
  .form-group input:focus { border-color: var(--cyan); }
  .btn-confirm {
    width: 100%; background: linear-gradient(135deg, var(--cyan), #0099CC);
    color: var(--navy); border: none; border-radius: 10px;
    padding: 0.9rem; font-weight: 800; font-size: 1rem; cursor: pointer;
    transition: opacity 0.2s;
  }
  .btn-confirm:hover { opacity: 0.9; }
  .total-row { display: flex; justify-content: space-between; align-items: center; padding: 0.75rem 0; border-top: 1px solid var(--border); margin-bottom: 1rem; }
  .total-label { font-size: 0.85rem; color: var(--muted); }
  .total-val { font-size: 1.2rem; font-weight: 900; color: var(--white); }

  /* ===== BLOG ===== */
  #blog { background: linear-gradient(180deg, var(--navy) 0%, var(--navy2) 100%); }
  .blog-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 1.5rem; }
  .blog-card {
    background: var(--navy);
    border: 1px solid var(--border);
    border-radius: 16px; overflow: hidden;
    transition: transform 0.25s, border-color 0.25s;
    cursor: pointer;
  }
  .blog-card:hover { transform: translateY(-5px); border-color: rgba(0,212,255,0.3); }
  .blog-img {
    aspect-ratio: 16/9; display: flex; align-items: center; justify-content: center;
    font-size: 2.5rem;
  }
  .b1 { background: linear-gradient(135deg, #0f1a2a, #1a3a5c); }
  .b2 { background: linear-gradient(135deg, #1a0a0a, #5c1a1a); }
  .b3 { background: linear-gradient(135deg, #0a1a0a, #1a5c1a); }
  .blog-content { padding: 1.25rem; }
  .blog-tag { font-size: 0.7rem; color: var(--cyan); font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 0.5rem; }
  .blog-title { font-size: 1.05rem; font-weight: 700; line-height: 1.35; margin-bottom: 0.5rem; }
  .blog-excerpt { font-size: 0.82rem; color: var(--muted); margin-bottom: 1rem; line-height: 1.55; }
  .blog-meta { display: flex; align-items: center; justify-content: space-between; font-size: 0.75rem; color: var(--muted); }
  .blog-author { display: flex; align-items: center; gap: 0.5rem; }
  .avatar { width: 28px; height: 28px; border-radius: 50%; background: linear-gradient(135deg, var(--cyan), var(--gold)); display: flex; align-items: center; justify-content: center; font-size: 0.7rem; font-weight: 800; color: var(--navy); }

  /* ===== ABOUT ===== */
  #about { background: var(--navy2); }
  .about-inner { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; }
  .about-img-wrap { position: relative; }
  .about-img {
    width: 100%; aspect-ratio: 1;
    border-radius: 20px; overflow: hidden;
    background: linear-gradient(135deg, var(--navy3), #0a1a2a);
    display: flex; align-items: center; justify-content: center;
    font-size: 6rem;
    border: 2px solid var(--border);
    position: relative;
  }
  .about-img::after {
    content: ''; position: absolute; inset: 0;
    background: linear-gradient(135deg, rgba(0,212,255,0.1), transparent);
    border-radius: 20px;
  }
  .about-badge-float {
    position: absolute; bottom: -1rem; right: -1rem;
    background: var(--gold); color: var(--navy);
    padding: 0.8rem 1.2rem; border-radius: 12px;
    font-size: 0.8rem; font-weight: 800; text-align: center;
    box-shadow: 0 8px 24px rgba(255,184,0,0.3);
  }
  .about-text h2 { margin-bottom: 1rem; }
  .about-text p { color: var(--muted); margin-bottom: 1rem; line-height: 1.7; }
  .skills-list { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-top: 1.5rem; }
  .skill-tag {
    background: var(--cyan-dim); border: 1px solid rgba(0,212,255,0.3);
    color: var(--cyan); padding: 0.3rem 0.8rem;
    border-radius: 999px; font-size: 0.78rem; font-weight: 600;
  }
  .social-links { display: flex; gap: 1rem; margin-top: 2rem; }
  .social-btn {
    background: var(--navy3); border: 1px solid var(--border);
    color: var(--white); padding: 0.6rem 1.2rem;
    border-radius: 8px; font-size: 0.82rem; font-weight: 600;
    cursor: pointer; transition: border-color 0.2s, color 0.2s;
    text-decoration: none; display: inline-flex; align-items: center; gap: 0.4rem;
  }
  .social-btn:hover { border-color: var(--cyan); color: var(--cyan); }

  /* ===== TESTIMONIALS ===== */
  #testimonials { background: var(--navy); }
  .testi-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.2rem; }
  .testi-card {
    background: var(--navy2); border: 1px solid var(--border);
    border-radius: 14px; padding: 1.5rem;
  }
  .testi-stars { color: var(--gold); font-size: 0.85rem; margin-bottom: 0.75rem; letter-spacing: 0.1em; }
  .testi-text { font-size: 0.88rem; color: var(--muted); line-height: 1.6; margin-bottom: 1rem; font-style: italic; }
  .testi-author { display: flex; align-items: center; gap: 0.75rem; }
  .testi-avatar { width: 36px; height: 36px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 0.8rem; font-weight: 800; }
  .a1 { background: linear-gradient(135deg, #0066cc, #00aaff); color: white; }
  .a2 { background: linear-gradient(135deg, #cc6600, #ffaa00); color: white; }
  .a3 { background: linear-gradient(135deg, #006600, #00aa00); color: white; }
  .a4 { background: linear-gradient(135deg, #660066, #aa00cc); color: white; }
  .a5 { background: linear-gradient(135deg, #660000, #cc0000); color: white; }
  .a6 { background: linear-gradient(135deg, #006666, #00aaaa); color: white; }
  .testi-name { font-size: 0.85rem; font-weight: 700; }
  .testi-role { font-size: 0.72rem; color: var(--muted); }

  /* ===== NEWSLETTER ===== */
  .newsletter {
    background: linear-gradient(135deg, rgba(0,212,255,0.05), rgba(255,184,0,0.05));
    border: 1px solid var(--border); border-radius: 20px;
    padding: 3rem 2rem; text-align: center; margin: 0 auto;
    max-width: 600px;
  }
  .newsletter h2 { font-size: 1.8rem; margin-bottom: 0.75rem; }
  .newsletter p { color: var(--muted); margin-bottom: 2rem; }
  .newsletter-form { display: flex; gap: 0.75rem; max-width: 400px; margin: 0 auto; }
  .newsletter-form input {
    flex: 1; background: var(--navy3); border: 1px solid var(--border);
    border-radius: 10px; color: var(--white); padding: 0.75rem 1rem;
    font-size: 0.9rem; outline: none;
  }
  .newsletter-form input:focus { border-color: var(--cyan); }
  .newsletter-form button {
    background: var(--cyan); color: var(--navy);
    border: none; border-radius: 10px; padding: 0.75rem 1.25rem;
    font-weight: 800; font-size: 0.85rem; cursor: pointer;
    white-space: nowrap;
  }

  /* ===== FOOTER ===== */
  footer {
    background: var(--navy2); border-top: 1px solid var(--border);
    padding: 3rem 2rem 2rem;
  }
  .footer-inner { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 2rem; margin-bottom: 2.5rem; }
  .footer-brand .logo { font-size: 1.6rem; display: block; margin-bottom: 0.75rem; }
  .footer-brand p { color: var(--muted); font-size: 0.85rem; line-height: 1.6; }
  .footer-col h4 { font-size: 0.82rem; font-weight: 700; text-transform: uppercase; letter-spacing: 0.1em; color: var(--muted); margin-bottom: 1rem; }
  .footer-col ul { list-style: none; }
  .footer-col li { margin-bottom: 0.6rem; }
  .footer-col a { color: var(--muted); text-decoration: none; font-size: 0.85rem; transition: color 0.2s; }
  .footer-col a:hover { color: var(--cyan); }
  .footer-bottom { max-width: 1100px; margin: 0 auto; display: flex; justify-content: space-between; align-items: center; padding-top: 2rem; border-top: 1px solid var(--border); font-size: 0.78rem; color: var(--muted); }
  .payment-icons { display: flex; gap: 0.75rem; }
  .pay-icon { background: var(--navy3); border: 1px solid var(--border); padding: 0.3rem 0.7rem; border-radius: 6px; font-size: 0.72rem; font-weight: 700; }

  /* ===== TOAST ===== */
  .toast {
    position: fixed; bottom: 2rem; right: 2rem; z-index: 9999;
    background: var(--navy2); border: 1px solid var(--cyan);
    border-radius: 12px; padding: 1rem 1.5rem;
    display: flex; align-items: center; gap: 0.75rem;
    font-size: 0.88rem; font-weight: 600;
    transform: translateY(100px); opacity: 0;
    transition: transform 0.3s, opacity 0.3s;
    max-width: 320px;
  }
  .toast.show { transform: translateY(0); opacity: 1; }
  .toast-icon { font-size: 1.2rem; }

  /* ===== MOBILE ===== */
  @media (max-width: 768px) {
    .nav-links { display: none; }
    .hamburger { display: flex; }
    .hero-visual { display: none; }
    .about-inner { grid-template-columns: 1fr; gap: 2rem; }
    .footer-inner { grid-template-columns: 1fr 1fr; }
    .newsletter-form { flex-direction: column; }
    .hero-stats { gap: 1.5rem; }
  }
  @media (max-width: 480px) {
    .footer-inner { grid-template-columns: 1fr; }
    .pay-methods { grid-template-columns: 1fr 1fr 1fr; }
  }

  /* ===== MOBILE NAV ===== */
  .mobile-nav {
    display: none; position: fixed; top: 64px; left: 0; right: 0; z-index: 99;
    background: var(--navy2); border-bottom: 1px solid var(--border);
    padding: 1.5rem 2rem; flex-direction: column; gap: 1rem;
  }
  .mobile-nav.open { display: flex; }
  .mobile-nav a { color: var(--muted); text-decoration: none; font-weight: 500; padding: 0.4rem 0; }

  /* ===== SUCCESS SCREEN ===== */
  .success-screen { text-align: center; padding: 1rem; }
  .success-icon { font-size: 4rem; margin-bottom: 1rem; }
  .success-screen h3 { font-size: 1.3rem; font-weight: 800; margin-bottom: 0.5rem; }
  .success-screen p { color: var(--muted); font-size: 0.88rem; margin-bottom: 1.5rem; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">RizkyDev</div>
  <ul class="nav-links">
    <li><a href="#ebooks">Ebook</a></li>
    <li><a href="#blog">Blog</a></li>
    <li><a href="#about">Tentang</a></li>
    <li><a href="#testimonials">Testimoni</a></li>
  </ul>
  <button class="nav-cta" onclick="scrollTo({top:document.getElementById('ebooks').offsetTop-80,behavior:'smooth'})">Beli Ebook</button>
  <div class="hamburger" onclick="toggleMobileNav()" id="hamburger">
    <span></span><span></span><span></span>
  </div>
</nav>

<div class="mobile-nav" id="mobileNav">
  <a href="#ebooks" onclick="toggleMobileNav()">📚 Ebook</a>
  <a href="#blog" onclick="toggleMobileNav()">✍️ Blog</a>
  <a href="#about" onclick="toggleMobileNav()">👋 Tentang</a>
  <a href="#testimonials" onclick="toggleMobileNav()">⭐ Testimoni</a>
</div>

<!-- PARTICLES -->
<div class="particles" id="particles"></div>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-bg"></div>
  <div class="hero-content">
    <div class="hero-badge">Baru Rilis — Ebook Python Masterclass 2025</div>
    <h1>Belajar Coding,<br><span class="accent">Scale Up</span> Skill<br><span class="accent-gold">Lo.</span></h1>
    <p class="hero-desc">Dari nol sampai bisa freelance. Gw share ilmu yang gw dapet dari 7 tahun di industri tech — dalam format ebook yang langsung to the point.</p>
    <div class="hero-actions">
      <button class="btn-primary" onclick="scrollTo({top:document.getElementById('ebooks').offsetTop-80,behavior:'smooth'})">🚀 Lihat Semua Ebook</button>
      <button class="btn-secondary" onclick="scrollTo({top:document.getElementById('blog').offsetTop-80,behavior:'smooth'})">✍️ Baca Blog</button>
    </div>
    <div class="hero-stats">
      <div>
        <div class="stat-val">2.4K+</div>
        <div class="stat-label">Pembeli Happy</div>
      </div>
      <div>
        <div class="stat-val">12</div>
        <div class="stat-label">Ebook Tersedia</div>
      </div>
      <div>
        <div class="stat-val">4.9★</div>
        <div class="stat-label">Rating Rata-rata</div>
      </div>
    </div>
  </div>
  <div class="hero-visual">
    <div class="floating-cards">
      <div class="ebook-card">
        <div class="card-cover c1">🐍</div>
        <div class="card-title">Python Masterclass</div>
        <div class="card-price">Rp 149K</div>
      </div>
      <div class="ebook-card">
        <div class="card-cover c2">⚛️</div>
        <div class="card-title">React Fundamentals</div>
        <div class="card-price">Rp 99K</div>
      </div>
      <div class="ebook-card">
        <div class="card-cover c3">💰</div>
        <div class="card-title">Freelance Guide</div>
        <div class="card-price">Rp 79K</div>
      </div>
    </div>
  </div>
</section>

<!-- EBOOKS -->
<section id="ebooks">
  <div class="container">
    <div class="section-header">
      <div class="section-eyebrow">📚 Digital Products</div>
      <h2>Koleksi Ebook Premium</h2>
      <p class="section-sub">Semua ebook langsung bisa didownload setelah pembayaran dikonfirmasi</p>
    </div>
    <div class="ebooks-grid" id="ebooksGrid"></div>
  </div>
</section>

<!-- BLOG -->
<section id="blog">
  <div class="container">
    <div class="section-header">
      <div class="section-eyebrow">✍️ Blog & Insight</div>
      <h2>Pengalaman & Tips</h2>
      <p class="section-sub">Cerita real dari dunia tech, freelance, dan mindset yang gw pelajari</p>
    </div>
    <div class="blog-grid" id="blogGrid"></div>
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="container">
    <div class="about-inner">
      <div class="about-img-wrap">
        <div class="about-img">👨‍💻
          <div class="about-badge-float">7 Tahun<br>Pengalaman</div>
        </div>
      </div>
      <div class="about-text">
        <div class="section-eyebrow">👋 About Me</div>
        <h2>Halo, gw <span style="color:var(--cyan)">Rizky</span></h2>
        <p>Software engineer yang udah ngulik dunia coding dari 2017. Pernah kerja di startup, agency, sampe freelance internasional.</p>
        <p>Sekarang gw fokus sharing knowledge lewat ebook dan blog ini — biar lo bisa shortcut learning curve yang dulu gw laluin dengan cara susah.</p>
        <p>Target gw simpel: bikin lo bisa masuk industri tech atau scale up income lo lewat skill coding yang solid.</p>
        <div class="skills-list">
          <span class="skill-tag">Python</span>
          <span class="skill-tag">JavaScript</span>
          <span class="skill-tag">React</span>
          <span class="skill-tag">Node.js</span>
          <span class="skill-tag">UI/UX</span>
          <span class="skill-tag">Freelancing</span>
          <span class="skill-tag">System Design</span>
        </div>
        <div class="social-links">
          <a href="#" class="social-btn">𝕏 Twitter</a>
          <a href="#" class="social-btn">in LinkedIn</a>
          <a href="#" class="social-btn">📸 Instagram</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials">
  <div class="container">
    <div class="section-header">
      <div class="section-eyebrow">⭐ Testimoni</div>
      <h2>Kata Mereka</h2>
      <p class="section-sub">2.400+ orang udah beli ebook gw. Ini yang mereka bilang.</p>
    </div>
    <div class="testi-grid" id="testiGrid"></div>
  </div>
</section>

<!-- NEWSLETTER -->
<section style="padding:4rem 2rem;">
  <div class="container">
    <div class="newsletter">
      <div style="font-size:2.5rem;margin-bottom:1rem">📬</div>
      <h2>Dapet Tips Gratis</h2>
      <p>Subscribe newsletter gw, tiap minggu ada tips tech & freelance langsung ke inbox lo. Gratis selamanya.</p>
      <div class="newsletter-form">
        <input type="email" placeholder="email@kamu.com" id="newsletterEmail">
        <button onclick="subscribeNewsletter()">Subscribe</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-brand">
      <span class="logo">RizkyDev</span>
      <p>Platform ebook dan blog untuk developer Indonesia yang mau level up karir dan income mereka.</p>
    </div>
    <div class="footer-col">
      <h4>Produk</h4>
      <ul>
        <li><a href="#ebooks">Semua Ebook</a></li>
        <li><a href="#">Bundle Deal</a></li>
        <li><a href="#">Affiliate</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Konten</h4>
      <ul>
        <li><a href="#blog">Blog</a></li>
        <li><a href="#">Newsletter</a></li>
        <li><a href="#">YouTube</a></li>
      </ul>
    </div>
    <div class="footer-col">
      <h4>Info</h4>
      <ul>
        <li><a href="#about">Tentang</a></li>
        <li><a href="#">Kebijakan Privasi</a></li>
        <li><a href="#">Syarat & Ketentuan</a></li>
        <li><a href="#">FAQ</a></li>
      </ul>
    </div>
  </div>
  <div class="footer-bottom">
    <div>© 2025 RizkyDev. All rights reserved.</div>
    <div class="payment-icons">
      <div class="pay-icon">BCA</div>
      <div class="pay-icon">BRI</div>
      <div class="pay-icon">GoPay</div>
      <div class="pay-icon">OVO</div>
      <div class="pay-icon">QRIS</div>
    </div>
  </div>
</footer>

<!-- PAYMENT MODAL -->
<div class="modal-overlay" id="payModal">
  <div class="modal">
    <div id="modalContent"></div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast">
  <span class="toast-icon" id="toastIcon">✅</span>
  <span id="toastMsg">Berhasil!</span>
</div>

<script>
// ===== DATA =====
const ebooks = [
  { id:1, emoji:'🐍', bg:'p1', tag:'Python', title:'Python Masterclass 2025', desc:'Dari dasar sampai advanced. Cocok buat pemula yang mau serius belajar Python.', price:'149.000', orig:'299.000', badge:'BEST', rating:4.9, reviews:312 },
  { id:2, emoji:'⚛️', bg:'p2', tag:'Frontend', title:'React & Next.js Modern', desc:'Build full-stack web app modern dengan React 18 dan Next.js 14. Deploy ke Vercel.', price:'129.000', orig:'249.000', badge:'NEW', rating:4.8, reviews:187 },
  { id:3, emoji:'💼', bg:'p3', tag:'Freelance', title:'Freelance Tech Guide', desc:'Panduan lengkap cari klien, nego harga, dan build portofolio yang menarik.', price:'79.000', orig:'149.000', badge:null, rating:4.9, reviews:428 },
  { id:4, emoji:'🗄️', bg:'p4', tag:'Backend', title:'Node.js & MongoDB API', desc:'Build REST API solid dengan authentication, file upload, dan deployment.', price:'99.000', orig:'199.000', badge:'NEW', rating:4.7, reviews:156 },
];

const blogPosts = [
  { emoji:'💡', bg:'b1', tag:'Career', title:'Dari Gaji 3 Juta ke Freelance 30 Juta — Cerita Gw', excerpt:'Gw mau jujur soal perjalanan ini. Bukan karena gw jenius, tapi karena gw nemu formula yang bisa diulang...', date:'12 Des 2024', read:'8 min' },
  { emoji:'🔥', bg:'b2', tag:'Tech', title:'5 Library Python yang Wajib Lo Tau di 2025', excerpt:'Ecosystem Python berkembang cepet banget. Ini yang menurut gw paling worth buat dipelajarin tahun ini...', date:'5 Des 2024', read:'5 min' },
  { emoji:'🧠', bg:'b3', tag:'Mindset', title:'Kenapa 90% Self-Taught Dev Nyerah di Bulan ke-3', excerpt:'Setelah ngobrol sama ratusan developer pemula, gw nemu pola yang sama terus. Dan solusinya simpel...', date:'28 Nov 2024', read:'6 min' },
];

const testimonials = [
  { avatar:'AS', ac:'a1', name:'Andi Saputra', role:'Junior Dev, Jakarta', stars:'★★★★★', text:'Ebook Python-nya beda banget dari tutorial gratis. Langsung practice-oriented dan ada case study nyata. Worth every penny!' },
  { avatar:'DN', ac:'a2', name:'Dewi Nurhaliza', role:'Freelancer, Bandung', stars:'★★★★★', text:'Gw udah invest ke banyak kursus tapi Freelance Guide ini yang paling actionable. Dalam 2 bulan gw dapet klien pertama dari luar negeri.' },
  { avatar:'RP', ac:'a3', name:'Reza Pratama', role:'Student, Surabaya', stars:'★★★★★', text:'Awalnya ragu beli karena budget mepet. Tapi ROI-nya gila — dalam sebulan gw dapet project freelance yang balik modal 10x.' },
  { avatar:'FK', ac:'a4', name:'Fiki Kurniawan', role:'Backend Dev, Yogyakarta', stars:'★★★★★', text:'React ebook-nya sangat well-structured. Dari yang tadinya bingung sama hooks, sekarang udah confident build full-stack app.' },
  { avatar:'SL', ac:'a5', name:'Sari Lestari', role:'UI Designer → Dev', stars:'★★★★★', text:'Transisi dari designer ke developer terbantu banget sama ebook ini. Penjelasannya relate dan mudah dicerna.' },
  { avatar:'MH', ac:'a6', name:'Miko Hartono', role:'CTO, Startup Fintech', stars:'★★★★★', text:'Gw rekomendasiin ke seluruh tim junior gw. Kualitasnya setara dengan kursus berbayar yang harganya 10x lipat.' },
];

// ===== RENDER =====
function renderEbooks() {
  document.getElementById('ebooksGrid').innerHTML = ebooks.map(e => `
    <div class="product-card">
      <div class="product-cover ${e.bg}">
        <span>${e.emoji}</span>
        ${e.badge ? `<span class="${e.badge==='NEW'?'badge-new':'badge-best'}">${e.badge}</span>` : ''}
      </div>
      <div class="product-info">
        <div class="product-tag">${e.tag}</div>
        <div class="product-title">${e.title}</div>
        <div class="rating">★★★★★ <span>${e.rating} (${e.reviews} ulasan)</span></div>
        <div class="product-desc">${e.desc}</div>
        <div class="product-footer">
          <div class="product-price">
            <span class="orig">Rp ${e.orig}</span>Rp ${e.price}
          </div>
          <button class="btn-buy" onclick="openPayModal(${e.id})">Beli</button>
        </div>
      </div>
    </div>
  `).join('');
}

function renderBlog() {
  document.getElementById('blogGrid').innerHTML = blogPosts.map(p => `
    <div class="blog-card">
      <div class="blog-img ${p.bg}">${p.emoji}</div>
      <div class="blog-content">
        <div class="blog-tag">${p.tag}</div>
        <div class="blog-title">${p.title}</div>
        <div class="blog-excerpt">${p.excerpt}</div>
        <div class="blog-meta">
          <div class="blog-author">
            <div class="avatar">R</div>
            <span>Rizky</span>
          </div>
          <span>${p.date} · ${p.read} read</span>
        </div>
      </div>
    </div>
  `).join('');
}

function renderTestimonials() {
  document.getElementById('testiGrid').innerHTML = testimonials.map(t => `
    <div class="testi-card">
      <div class="testi-stars">${t.stars}</div>
      <div class="testi-text">"${t.text}"</div>
      <div class="testi-author">
        <div class="testi-avatar ${t.ac}">${t.avatar}</div>
        <div>
          <div class="testi-name">${t.name}</div>
          <div class="testi-role">${t.role}</div>
        </div>
      </div>
    </div>
  `).join('');
}

// ===== PARTICLES =====
function createParticles() {
  const container = document.getElementById('particles');
  for(let i = 0; i < 20; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    const size = Math.random() * 4 + 2;
    p.style.cssText = `
      width:${size}px; height:${size}px;
      left:${Math.random()*100}%;
      animation-duration:${Math.random()*15+10}s;
      animation-delay:-${Math.random()*15}s;
    `;
    container.appendChild(p);
  }
}

// ===== PAYMENT MODAL =====
let currentProduct = null;
let currentMethod = 'bca';

function openPayModal(id) {
  currentProduct = ebooks.find(e => e.id === id);
  currentMethod = 'bca';
  renderModalContent();
  document.getElementById('payModal').classList.add('active');
}

function closePayModal() {
  document.getElementById('payModal').classList.remove('active');
}

function renderModalContent() {
  const e = currentProduct;
  document.getElementById('modalContent').innerHTML = `
    <div class="modal-header">
      <div class="modal-title">Pilih Metode Pembayaran</div>
      <button class="modal-close" onclick="closePayModal()">✕</button>
    </div>
    <div class="modal-product">
      <div class="modal-cover ${e.bg}" style="border-radius:8px">${e.emoji}</div>
      <div class="modal-product-info">
        <h4>${e.title}</h4>
        <div class="price">Rp ${e.price}</div>
      </div>
    </div>
    <div class="pay-methods">
      <div class="pay-method ${currentMethod==='bca'?'active':''}" onclick="selectMethod('bca')">
        <div class="pm-icon">🏦</div>
        <div class="pm-label">Transfer Bank</div>
      </div>
      <div class="pay-method ${currentMethod==='ewallet'?'active':''}" onclick="selectMethod('ewallet')">
        <div class="pm-icon">💚</div>
        <div class="pm-label">E-Wallet</div>
      </div>
      <div class="pay-method ${currentMethod==='qris'?'active':''}" onclick="selectMethod('qris')">
        <div class="pm-icon">▦</div>
        <div class="pm-label">QRIS</div>
      </div>
    </div>
    ${getPayDetail()}
    <div class="total-row">
      <div class="total-label">Total yang dibayar</div>
      <div class="total-val">Rp ${e.price}</div>
    </div>
    <div class="form-group">
      <label>Email (untuk kirim ebook)</label>
      <input type="email" id="buyerEmail" placeholder="email@kamu.com">
    </div>
    <div class="form-group">
      <label>Nama Lengkap</label>
      <input type="text" id="buyerName" placeholder="Nama untuk konfirmasi">
    </div>
    <button class="btn-confirm" onclick="confirmOrder()">✅ Konfirmasi Pesanan</button>
  `;
}

function getPayDetail() {
  if(currentMethod === 'bca') return `
    <div class="pay-detail">
      <h4>🏦 Transfer Bank — BCA / BRI / Mandiri</h4>
      <div class="acc-row">
        <span style="color:var(--muted);font-size:0.82rem">BCA</span>
        <div style="display:flex;align-items:center;gap:0.5rem">
          <span class="acc-val">1234567890</span>
          <button class="copy-btn" onclick="copyText('1234567890')">Salin</button>
        </div>
      </div>
      <div class="acc-row">
        <span style="color:var(--muted);font-size:0.82rem">BRI</span>
        <div style="display:flex;align-items:center;gap:0.5rem">
          <span class="acc-val">0987654321</span>
          <button class="copy-btn" onclick="copyText('0987654321')">Salin</button>
        </div>
      </div>
      <div class="acc-row">
        <span style="color:var(--muted);font-size:0.82rem">Mandiri</span>
        <div style="display:flex;align-items:center;gap:0.5rem">
          <span class="acc-val">1122334455</span>
          <button class="copy-btn" onclick="copyText('1122334455')">Salin</button>
        </div>
      </div>
      <div class="note">a.n. <strong>Rizky Pratama</strong>. Konfirmasi via WhatsApp setelah transfer, ebook dikirim ke email dalam 1x24 jam.</div>
    </div>
  `;
  if(currentMethod === 'ewallet') return `
    <div class="pay-detail">
      <h4>💚 E-Wallet — GoPay / OVO / Dana</h4>
      <div class="acc-row">
        <span style="color:var(--muted);font-size:0.82rem">GoPay / OVO / Dana</span>
        <div style="display:flex;align-items:center;gap:0.5rem">
          <span class="acc-val">0812-3456-7890</span>
          <button class="copy-btn" onclick="copyText('081234567890')">Salin</button>
        </div>
      </div>
      <div class="note">Kirim ke nomor di atas via GoPay, OVO, atau Dana. Screenshot bukti bayar dan kirim ke WA <strong>0812-3456-7890</strong>. Ebook langsung dikirim!</div>
    </div>
  `;
  if(currentMethod === 'qris') return `
    <div class="pay-detail">
      <h4>▦ Bayar via QRIS</h4>
      <div class="qris-box">
        <div class="qris-mock">▦</div>
        <p style="color:var(--muted);font-size:0.78rem;margin-top:2rem;line-height:1.5">Scan QR ini pakai GoPay, OVO, Dana, ShopeePay, atau mobile banking apapun yang support QRIS.</p>
      </div>
    </div>
  `;
}

function selectMethod(m) {
  currentMethod = m;
  renderModalContent();
}

function copyText(text) {
  navigator.clipboard.writeText(text).then(() => showToast('✅', 'Nomor rekening disalin!'));
}

function confirmOrder() {
  const email = document.getElementById('buyerEmail').value;
  const name = document.getElementById('buyerName').value;
  if(!email || !name) { showToast('⚠️', 'Isi email dan nama dulu ya!'); return; }
  document.getElementById('modalContent').innerHTML = `
    <div class="success-screen">
      <div class="success-icon">🎉</div>
      <h3>Pesanan Diterima!</h3>
      <p>Makasih, <strong>${name}</strong>! Ebook akan dikirim ke <strong>${email}</strong> setelah pembayaran dikonfirmasi.<br><br>
      Estimasi 1-3 jam kerja. Kalau ada masalah, DM di Instagram atau WA ya.</p>
      <button class="btn-confirm" onclick="closePayModal()">Tutup</button>
    </div>
  `;
  showToast('🎉', 'Pesanan berhasil dibuat!');
}

// ===== TOAST =====
function showToast(icon, msg) {
  const t = document.getElementById('toast');
  document.getElementById('toastIcon').textContent = icon;
  document.getElementById('toastMsg').textContent = msg;
  t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3000);
}

// ===== NEWSLETTER =====
function subscribeNewsletter() {
  const email = document.getElementById('newsletterEmail').value;
  if(!email) { showToast('⚠️', 'Masukkin email lo dulu!'); return; }
  document.getElementById('newsletterEmail').value = '';
  showToast('📬', 'Sukses subscribe! Cek inbox lo ya.');
}

// ===== MOBILE NAV =====
function toggleMobileNav() {
  document.getElementById('mobileNav').classList.toggle('open');
}

// ===== CLOSE MODAL ON OVERLAY CLICK =====
document.getElementById('payModal').addEventListener('click', function(e) {
  if(e.target === this) closePayModal();
});

// ===== INIT =====
createParticles();
renderEbooks();
renderBlog();
renderTestimonials();
</script>
</body>
</html>
