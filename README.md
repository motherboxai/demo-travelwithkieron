<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Travel With Kieron — The Travel King Society</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Jost:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
/* ── KIERON BRAND COLORS (from his site: deep navy, teal, white, gold) ── */
:root {
  --navy:   #0d1b2a;
  --navy2:  #112236;
  --teal:   #1a6b72;
  --teal2:  #22858e;
  --gold:   #c9a84c;
  --gold2:  #e0c070;
  --white:  #f5f5f5;
  --cream:  #ede8df;
  --muted:  rgba(245,245,245,0.5);
  --card:   #0f2235;
}

*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
html{scroll-behavior:smooth;}
body{
  background:var(--navy);
  color:var(--white);
  font-family:'Jost',sans-serif;
  font-weight:300;
  overflow-x:hidden;
}

/* ── NAV ── */
nav{
  position:fixed;top:0;left:0;right:0;z-index:500;
  display:flex;justify-content:space-between;align-items:center;
  padding:22px 60px;
  background:rgba(13,27,42,0.92);
  backdrop-filter:blur(12px);
  -webkit-backdrop-filter:blur(12px);
  border-bottom:1px solid rgba(201,168,76,0.15);
  transition:padding 0.3s;
}
nav.scrolled{padding:14px 60px;}
.nav-logo img{height:52px;width:auto;display:block;}
.nav-links{display:flex;gap:32px;list-style:none;align-items:center;}
.nav-links a{
  color:var(--white);text-decoration:none;
  font-size:11px;letter-spacing:0.18em;text-transform:uppercase;
  opacity:0.65;transition:opacity 0.3s;white-space:nowrap;
}
.nav-links a:hover{opacity:1;}
.nav-cta{
  background:var(--gold)!important;
  color:var(--navy)!important;
  padding:9px 20px;opacity:1!important;
  font-weight:500;white-space:nowrap;
  transition:background 0.3s!important;
}
.nav-cta:hover{background:var(--gold2)!important;}

/* hamburger — hidden on desktop */
.hamburger{
  display:none;
  flex-direction:column;gap:5px;
  background:none;border:none;cursor:pointer;
  padding:6px;z-index:501;position:relative;
}
.hamburger span{
  display:block;width:24px;height:2px;
  background:var(--white);border-radius:2px;
  transition:transform 0.3s,opacity 0.3s;
}
.hamburger.open span:nth-child(1){transform:translateY(7px) rotate(45deg);}
.hamburger.open span:nth-child(2){opacity:0;}
.hamburger.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg);}

/* ── MOBILE MENU — full screen overlay ── */
.mobile-menu{
  display:none;
  position:fixed;inset:0;z-index:499;
  background:rgba(13,27,42,0.99);
  flex-direction:column;align-items:center;justify-content:center;
  gap:32px;
  opacity:0;transition:opacity 0.3s;
}
.mobile-menu.open{opacity:1;}
/* each link — large, readable, no overflow */
.mobile-menu a{
  font-family:'Cormorant Garamond',serif;
  font-size:34px;font-weight:400;font-style:italic;
  color:var(--white);text-decoration:none;
  opacity:0.75;transition:color 0.3s,opacity 0.3s;
  text-align:center;width:100%;padding:0 40px;
}
.mobile-menu a:hover{color:var(--gold);opacity:1;}
.mob-cta{
  font-family:'Jost',sans-serif!important;
  font-size:13px!important;font-style:normal!important;
  letter-spacing:0.18em;text-transform:uppercase;
  background:var(--gold)!important;color:var(--navy)!important;
  padding:16px 48px!important;
  opacity:1!important;margin-top:8px;
  display:inline-block;
}
/* social icons inside mobile menu */
.mob-socials{
  display:flex;gap:28px;align-items:center;
  margin-top:16px;padding-top:24px;
  border-top:1px solid rgba(201,168,76,0.2);
  width:80%;justify-content:center;
}
.mob-socials a{
  font-family:'Jost',sans-serif!important;
  font-size:12px!important;font-style:normal!important;
  letter-spacing:0.15em;text-transform:uppercase;
  color:rgba(245,245,245,0.4)!important;
  opacity:1!important;
  padding:0!important;width:auto!important;
}

/* ── HERO ── */
.hero{
  min-height:100vh;
  display:grid;
  grid-template-columns:1fr 1fr;
  align-items:center;
  gap:0;
  padding-top:88px;
  position:relative;
  overflow:hidden;
}
.hero-bg{
  position:absolute;inset:0;
  background:
    radial-gradient(ellipse 60% 80% at 80% 30%,rgba(26,107,114,0.25) 0%,transparent 65%),
    radial-gradient(ellipse 50% 60% at 10% 80%,rgba(201,168,76,0.08) 0%,transparent 60%),
    var(--navy);
}
.hero-left{
  position:relative;z-index:2;
  padding:80px 60px 80px 60px;
  display:flex;flex-direction:column;justify-content:center;
}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:12px;
  font-size:10px;letter-spacing:0.28em;text-transform:uppercase;
  color:var(--gold);margin-bottom:28px;
  opacity:0;animation:fadeUp 0.9s 0.2s forwards;
}
.hero-eyebrow::before{content:'';width:36px;height:1px;background:var(--gold);flex-shrink:0;}
.hero h1{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(46px,5.5vw,80px);
  font-weight:300;line-height:1.0;
  margin-bottom:24px;
  opacity:0;animation:fadeUp 0.9s 0.4s forwards;
}
.hero h1 em{font-style:italic;color:var(--gold2);display:block;}
.hero-sub{
  font-size:15px;line-height:1.85;
  color:var(--muted);max-width:420px;
  margin-bottom:40px;letter-spacing:0.03em;
  opacity:0;animation:fadeUp 0.9s 0.6s forwards;
}
.hero-actions{
  display:flex;gap:18px;align-items:center;flex-wrap:wrap;
  opacity:0;animation:fadeUp 0.9s 0.8s forwards;
}
.btn-gold{
  background:var(--gold);color:var(--navy);
  padding:15px 36px;
  font-family:'Jost',sans-serif;font-size:11px;font-weight:500;
  letter-spacing:0.18em;text-transform:uppercase;
  text-decoration:none;display:inline-block;
  transition:background 0.3s,transform 0.2s;white-space:nowrap;
}
.btn-gold:hover{background:var(--gold2);transform:translateY(-2px);}
.btn-outline{
  color:var(--white);text-decoration:none;
  font-size:11px;letter-spacing:0.18em;text-transform:uppercase;
  display:flex;align-items:center;gap:8px;
  opacity:0.55;transition:opacity 0.3s;white-space:nowrap;
}
.btn-outline:hover{opacity:1;}
.btn-outline::after{content:'→';transition:transform 0.3s;}
.btn-outline:hover::after{transform:translateX(5px);}

/* hero right — real photo grid */
.hero-right{
  position:relative;z-index:2;
  height:100vh;min-height:600px;
  overflow:hidden;
}
.hero-photo-main{
  width:100%;height:100%;
  object-fit:cover;object-position:center top;
  display:block;
}
.hero-photo-overlay{
  position:absolute;inset:0;
  background:linear-gradient(to right,var(--navy) 0%,transparent 30%),
             linear-gradient(to top,var(--navy) 0%,transparent 25%);
}
.hero-badge{
  position:absolute;bottom:40px;left:40px;
  background:var(--gold);color:var(--navy);
  padding:14px 20px;
  font-size:10px;letter-spacing:0.15em;text-transform:uppercase;
  font-weight:500;
}
.hero-badge strong{
  display:block;
  font-family:'Cormorant Garamond',serif;
  font-size:28px;font-weight:600;letter-spacing:0;
  line-height:1;margin-bottom:2px;
}

/* ── MARQUEE ── */
.marquee{
  padding:16px 0;
  border-top:1px solid rgba(201,168,76,0.15);
  border-bottom:1px solid rgba(201,168,76,0.15);
  overflow:hidden;background:rgba(26,107,114,0.08);
}
.marquee-track{
  display:flex;gap:60px;
  animation:marquee 20s linear infinite;white-space:nowrap;
}
.marquee-item{
  font-size:10px;letter-spacing:0.28em;text-transform:uppercase;
  color:rgba(245,245,245,0.3);flex-shrink:0;
  display:flex;align-items:center;gap:60px;
}
.marquee-item::after{content:'✦';color:var(--gold);opacity:0.5;}
@keyframes marquee{from{transform:translateX(0);}to{transform:translateX(-50%);}}

/* ── ABOUT ── */
.about{
  padding:120px 60px;
  display:grid;grid-template-columns:1fr 1fr;
  gap:80px;align-items:center;
  background:var(--navy2);
}
.about-label{
  font-size:10px;letter-spacing:0.28em;text-transform:uppercase;
  color:var(--gold);margin-bottom:18px;
  display:flex;align-items:center;gap:12px;
}
.about-label::before{content:'';width:28px;height:1px;background:var(--gold);}
.about h2{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(34px,3.5vw,52px);font-weight:300;
  line-height:1.1;margin-bottom:24px;
}
.about h2 em{font-style:italic;color:var(--gold2);}
.about p{
  font-size:14px;line-height:1.9;color:var(--muted);
  margin-bottom:14px;letter-spacing:0.02em;
}
.about-quote{
  font-family:'Cormorant Garamond',serif;
  font-size:19px;font-style:italic;font-weight:300;
  color:var(--cream);line-height:1.6;
  margin:24px 0 36px;
  padding-left:20px;
  border-left:2px solid var(--gold);
}

/* real photo grid */
.photo-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  grid-template-rows:auto auto;
  gap:10px;
}
.pgrid-img{
  width:100%;display:block;
  object-fit:cover;
}
.pgrid-img.tall{
  grid-row:span 2;
  height:100%;
  object-position:center top;
  aspect-ratio:2/3;
}
.pgrid-img.sq{aspect-ratio:3/4;object-position:center top;}

/* ── GALLERY STRIP ── */
.gallery{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:4px;
  overflow:hidden;
}
.gallery-img{
  width:100%;aspect-ratio:3/4;
  object-fit:cover;object-position:center top;
  display:block;
  filter:brightness(0.85);
  transition:filter 0.4s,transform 0.5s;
}
.gallery-img:hover{filter:brightness(1.05);transform:scale(1.02);}

/* ── BENEFITS ── */
.benefits{
  padding:120px 60px;
  background:var(--navy);
  border-top:1px solid rgba(201,168,76,0.1);
}
.section-header{text-align:center;margin-bottom:72px;}
.section-label{
  font-size:10px;letter-spacing:0.28em;text-transform:uppercase;
  color:var(--gold);margin-bottom:18px;
  display:flex;align-items:center;justify-content:center;gap:12px;
}
.section-label::before,.section-label::after{
  content:'';width:28px;height:1px;background:var(--gold);
}
.section-header h2{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(34px,4vw,54px);font-weight:300;line-height:1.1;
}
.section-header h2 em{font-style:italic;color:var(--gold2);}

.benefits-grid{
  display:grid;grid-template-columns:repeat(3,1fr);
  gap:2px;
}
.benefit-card{
  background:var(--card);
  padding:48px 36px;position:relative;overflow:hidden;
  transition:background 0.4s;
}
.benefit-card::after{
  content:'';position:absolute;
  bottom:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,transparent,var(--teal2),transparent);
  transform:scaleX(0);transform-origin:left;transition:transform 0.5s;
}
.benefit-card:hover{background:#142840;}
.benefit-card:hover::after{transform:scaleX(1);}
.benefit-num{
  font-family:'Cormorant Garamond',serif;
  font-size:64px;font-weight:300;
  color:rgba(201,168,76,0.08);line-height:1;
  margin-bottom:16px;transition:color 0.4s;
}
.benefit-card:hover .benefit-num{color:rgba(201,168,76,0.16);}
.benefit-icon{font-size:26px;margin-bottom:16px;}
.benefit-title{
  font-family:'Cormorant Garamond',serif;
  font-size:22px;font-weight:400;margin-bottom:12px;
}
.benefit-desc{font-size:13px;line-height:1.85;color:var(--muted);letter-spacing:0.02em;}

/* ── HOW IT WORKS ── */
.how{
  padding:120px 60px;
  background:var(--navy2);
  border-top:1px solid rgba(201,168,76,0.1);
}
.how-inner{
  display:grid;grid-template-columns:1fr 1.3fr;
  gap:100px;align-items:start;
}
.how-left{position:sticky;top:110px;}
.how-left p{font-size:14px;line-height:1.9;color:var(--muted);margin-bottom:36px;letter-spacing:0.02em;}
.steps{display:flex;flex-direction:column;}
.step{
  display:flex;gap:24px;
  padding:30px 0;
  border-bottom:1px solid rgba(201,168,76,0.08);
}
.step:last-child{border-bottom:none;}
.step-dot-wrap{display:flex;flex-direction:column;align-items:center;flex-shrink:0;}
.dot{
  width:10px;height:10px;border-radius:50%;
  border:1px solid var(--gold);margin-top:5px;
  transition:background 0.3s;
}
.step:hover .dot{background:var(--gold);}
.dotline{width:1px;flex:1;background:rgba(201,168,76,0.15);margin-top:8px;}
.step:last-child .dotline{display:none;}
.step-label{font-size:10px;color:var(--gold);letter-spacing:0.15em;margin-bottom:6px;opacity:0.7;}
.step-body h3{
  font-family:'Cormorant Garamond',serif;
  font-size:22px;font-weight:400;margin-bottom:8px;
}
.step-body p{font-size:13px;line-height:1.8;color:var(--muted);letter-spacing:0.02em;}

/* ── PROOF ── */
.proof{
  padding:100px 60px;text-align:center;
  background:var(--navy);
  border-top:1px solid rgba(201,168,76,0.1);
  position:relative;overflow:hidden;
}
.proof::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(ellipse 70% 60% at center,rgba(26,107,114,0.12) 0%,transparent 70%);
}
.proof-quote{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(24px,3.5vw,46px);font-style:italic;font-weight:300;
  line-height:1.3;max-width:760px;margin:0 auto 36px;position:relative;
}
.proof-quote::before{
  content:'"';font-size:140px;color:rgba(201,168,76,0.1);
  line-height:0;position:absolute;top:48px;left:-24px;
}
.proof-attr{
  font-size:11px;letter-spacing:0.2em;text-transform:uppercase;
  color:var(--gold);margin-bottom:64px;
}
.proof-stats{display:flex;justify-content:center;gap:72px;flex-wrap:wrap;}
.stat-num{
  font-family:'Cormorant Garamond',serif;
  font-size:52px;font-weight:300;color:var(--gold2);line-height:1;
}
.stat-lbl{
  font-size:10px;letter-spacing:0.18em;text-transform:uppercase;
  color:var(--muted);margin-top:6px;
}

/* ── SOCIAL / CONNECT ── */
.social-section{
  padding:80px 60px;
  background:var(--teal);
  text-align:center;
}
.social-section h2{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(32px,4vw,52px);font-weight:300;
  margin-bottom:12px;color:var(--white);
}
.social-section h2 em{font-style:italic;color:var(--gold2);}
.social-section p{font-size:14px;color:rgba(245,245,245,0.7);margin-bottom:40px;letter-spacing:0.03em;}
/* social buttons — side by side, NO overlap */
.social-btns{
  display:flex;
  gap:16px;
  justify-content:center;
  align-items:center;
  flex-wrap:wrap;
}
.social-btn{
  display:inline-flex;align-items:center;gap:10px;
  padding:14px 32px;
  text-decoration:none;
  font-size:11px;letter-spacing:0.18em;text-transform:uppercase;
  font-weight:500;white-space:nowrap;
  transition:transform 0.2s,opacity 0.3s;
}
.social-btn:hover{transform:translateY(-2px);opacity:0.9;}
.social-btn-ig{background:#fff;color:var(--navy);}
.social-btn-tt{background:var(--navy);color:#fff;border:1px solid rgba(255,255,255,0.2);}
.social-btn img{width:18px;height:18px;object-fit:contain;flex-shrink:0;}

/* ── CTA ── */
.cta{
  padding:120px 60px;text-align:center;
  position:relative;overflow:hidden;
  background:var(--navy);
}
.cta::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(ellipse 80% 70% at center,rgba(26,107,114,0.15) 0%,transparent 70%);
}
.cta h2{
  font-family:'Cormorant Garamond',serif;
  font-size:clamp(40px,6vw,76px);font-weight:300;
  line-height:1.05;margin-bottom:20px;position:relative;
}
.cta h2 em{font-style:italic;color:var(--gold2);}
.cta p{
  font-size:15px;line-height:1.8;color:var(--muted);
  margin-bottom:48px;position:relative;letter-spacing:0.03em;
}
.cta-btns{
  display:flex;gap:18px;justify-content:center;
  align-items:center;flex-wrap:wrap;position:relative;
}

/* ── FOOTER ── */
footer{
  padding:36px 60px;
  border-top:1px solid rgba(201,168,76,0.12);
  display:flex;justify-content:space-between;align-items:center;
  flex-wrap:wrap;gap:14px;
  background:var(--navy2);
}
.footer-logo img{height:44px;width:auto;display:block;}
.footer-copy{font-size:11px;color:rgba(245,245,245,0.25);letter-spacing:0.06em;}
.footer-credit{
  font-size:10px;color:rgba(201,168,76,0.45);
  letter-spacing:0.06em;text-align:center;width:100%;
  padding-top:14px;border-top:1px solid rgba(201,168,76,0.08);
}

/* ── ANIMATIONS ── */
@keyframes fadeUp{from{opacity:0;transform:translateY(26px);}to{opacity:1;transform:translateY(0);}}
.reveal{opacity:0;transform:translateY(32px);transition:opacity 0.85s,transform 0.85s;}
.reveal.visible{opacity:1;transform:translateY(0);}

/* ── MOBILE ── */
@media(max-width:900px){

  /* nav */
  nav{padding:16px 20px;}
  nav.scrolled{padding:12px 20px;}
  .nav-logo img{height:40px;}
  .nav-links{display:none;}
  .hamburger{display:flex;}

  /* mobile menu link sizing — fits any screen */
  .mobile-menu a{font-size:28px;padding:0 32px;}
  .mob-cta{font-size:12px!important;padding:14px 36px!important;}

  /* hero — stack vertically */
  .hero{
    grid-template-columns:1fr;
    padding-top:72px;min-height:auto;
  }
  .hero-left{padding:56px 24px 40px;}
  .hero h1{font-size:clamp(40px,10vw,64px);}
  .hero-sub{font-size:15px;max-width:100%;}
  .hero-actions{flex-direction:column;align-items:stretch;gap:14px;}
  .btn-gold{text-align:center;padding:18px 24px;}
  .btn-outline{justify-content:center;}
  .hero-right{height:300px;min-height:0;}
  .hero-badge{bottom:20px;left:20px;}

  /* about */
  .about{padding:80px 24px;grid-template-columns:1fr;gap:40px;}
  .photo-grid{display:none;}

  /* gallery — 2 col on mobile */
  .gallery{grid-template-columns:1fr 1fr;}
  .gallery-img{aspect-ratio:1;}

  /* benefits */
  .benefits{padding:80px 24px;}
  .benefits-grid{grid-template-columns:1fr;}
  .benefit-card{padding:36px 24px;}

  /* how */
  .how{padding:80px 24px;}
  .how-inner{grid-template-columns:1fr;gap:40px;}
  .how-left{position:static;}

  /* proof */
  .proof{padding:80px 24px;}
  .proof-stats{gap:36px;}

  /* social section — buttons stack properly */
  .social-section{padding:64px 24px;}
  .social-btns{flex-direction:column;align-items:center;gap:12px;width:100%;}
  .social-btn{width:100%;max-width:280px;justify-content:center;}

  /* cta */
  .cta{padding:80px 24px;}
  .cta-btns{flex-direction:column;align-items:stretch;}
  .cta-btns .btn-gold{text-align:center;}

  /* footer */
  footer{padding:24px 20px;flex-direction:column;text-align:center;gap:10px;}
}

@media(max-width:480px){
  .hero h1{font-size:38px;}
  .proof-stats{flex-direction:column;gap:24px;}
  .mobile-menu a{font-size:24px;}
}
</style>
</head>
<body>

<!-- NAV -->
<nav id="nav">
  <a href="#">
    <img class="nav-logo" src="https://static.wixstatic.com/media/637089_2620c72feced452a94baf9eb9802aece~mv2.png/v1/fill/w_181,h_145,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/Add%20a%20heading.png" alt="Travel With Kieron">
  </a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#how">How It Works</a></li>
    <li><a href="https://www.travelwithkieron.com/faqs" target="_blank">FAQs</a></li>
    <li><a href="https://www.travelwithkieron.com/meet-the-team" target="_blank">Meet the Team</a></li>
    <li><a href="https://www.travelwithkieron.com/i-m-ready-to-join-the-king" class="nav-cta" target="_blank">Join the Society</a></li>
  </ul>
  <button class="hamburger" id="hamburger" aria-label="Open menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- MOBILE MENU -->
<div class="mobile-menu" id="mobileMenu">
  <a href="#about" class="mlink">About</a>
  <a href="#how" class="mlink">How It Works</a>
  <a href="https://www.travelwithkieron.com/faqs" class="mlink" target="_blank">FAQs</a>
  <a href="https://www.travelwithkieron.com/meet-the-team" class="mlink" target="_blank">Meet the Team</a>
  <a href="https://www.travelwithkieron.com/i-m-ready-to-join-the-king" class="mlink mob-cta" target="_blank">Join the Society</a>
  <div class="mob-socials">
    <a href="https://www.instagram.com/itskieron.ellis" class="mlink" target="_blank">Instagram</a>
    <a href="https://www.tiktok.com/@itskieron.ellis" class="mlink" target="_blank">TikTok</a>
  </div>
</div>

<!-- HERO -->
<section class="hero">
  <div class="hero-bg"></div>
  <div class="hero-left">
    <div class="hero-eyebrow">The Travel King Society</div>
    <h1>Elevate Your<br>Lifestyle &amp;<br><em>Bank Account.</em></h1>
    <p class="hero-sub">Since 2020, Kieron has been building a thriving luxury travel business that gives total freedom, 5-star experiences, and an income that grows while you explore the world.</p>
    <div class="hero-actions">
      <a href="https://www.travelwithkieron.com/i-m-ready-to-join-the-king" class="btn-gold" target="_blank">I'm Ready to Join</a>
      <a href="#about" class="btn-outline">See how it works</a>
    </div>
  </div>
  <div class="hero-right">
    <img class="hero-photo-main"
      src="https://static.wixstatic.com/media/637089_390b1b170dce42948909b7de3e216d10~mv2.jpg/v1/fill/w_450,h_600,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_6300_JPG.jpg"
      alt="Kieron Ellis — The Travel King">
    <div class="hero-photo-overlay"></div>
    <div class="hero-badge">
      <strong>Since</strong>Jan 2020
    </div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee">
  <div class="marquee-track">
    <div class="marquee-item">Luxury Travel</div>
    <div class="marquee-item">Financial Freedom</div>
    <div class="marquee-item">Work Anywhere</div>
    <div class="marquee-item">The Travel King Society</div>
    <div class="marquee-item">Earn &amp; Explore</div>
    <div class="marquee-item">5-Star Experiences</div>
    <div class="marquee-item">Luxury Travel</div>
    <div class="marquee-item">Financial Freedom</div>
    <div class="marquee-item">Work Anywhere</div>
    <div class="marquee-item">The Travel King Society</div>
    <div class="marquee-item">Earn &amp; Explore</div>
    <div class="marquee-item">5-Star Experiences</div>
  </div>
</div>

<!-- ABOUT -->
<section class="about" id="about">
  <div>
    <div class="about-label reveal">Meet Kieron</div>
    <h2 class="reveal">The Travel King<br>Who <em>Cracked the Code.</em></h2>
    <p class="reveal">I'm Kieron, aka THE TRAVEL KING — and since January 2020 I've been running a thriving network marketing business in the luxury travel space. It's given me freedom, unforgettable experiences and a community of like-minded go-getters who love to live life to the fullest.</p>
    <p class="reveal">I created The Travel King Society to share everything you need to know to start your own journey in the most lucrative, exciting and fun industry in the world — TRAVEL!</p>
    <p class="reveal">Whether you're dreaming of earning more income flexibly, saying goodbye to the 9-5, or simply living life on your own terms — I'm here to help you make it happen.</p>
    <div class="about-quote reveal">"Earn more. Travel more. Experience more. That's how we do it around here."</div>
    <a href="https://www.travelwithkieron.com/about" class="btn-gold reveal" target="_blank">Learn More About Kieron</a>
  </div>
  <div class="photo-grid reveal">
    <img class="pgrid-img tall"
      src="https://static.wixstatic.com/media/637089_390b1b170dce42948909b7de3e216d10~mv2.jpg/v1/fill/w_450,h_600,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_6300_JPG.jpg"
      alt="Kieron Ellis">
    <img class="pgrid-img sq"
      src="https://static.wixstatic.com/media/637089_240e1ee6db294b6caf8137f34096f1bc~mv2.jpg/v1/fill/w_282,h_376,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_6345_JPG.jpg"
      alt="Travel Life">
    <img class="pgrid-img sq"
      src="https://static.wixstatic.com/media/637089_33be5305dccc497ba566d7f8cdff5d68~mv2.png/v1/fill/w_282,h_376,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_4281_HEIC.png"
      alt="Luxury Travel">
  </div>
</section>

<!-- GALLERY STRIP — all 4 real photos -->
<div class="gallery">
  <img class="gallery-img" src="https://static.wixstatic.com/media/637089_390b1b170dce42948909b7de3e216d10~mv2.jpg/v1/fill/w_450,h_600,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_6300_JPG.jpg" alt="Kieron">
  <img class="gallery-img" src="https://static.wixstatic.com/media/637089_240e1ee6db294b6caf8137f34096f1bc~mv2.jpg/v1/fill/w_282,h_376,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_6345_JPG.jpg" alt="Travel">
  <img class="gallery-img" src="https://static.wixstatic.com/media/637089_33be5305dccc497ba566d7f8cdff5d68~mv2.png/v1/fill/w_282,h_376,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_4281_HEIC.png" alt="Lifestyle">
  <img class="gallery-img" src="https://static.wixstatic.com/media/637089_7663f495583343c28f2455b9040f9fc8~mv2.jpg/v1/fill/w_282,h_376,al_c,q_80,usm_0.66_1.00_0.01,enc_avif,quality_auto/IMG_2485_JPG.jpg" alt="Experience">
</div>

<!-- BENEFITS -->
<section class="benefits">
  <div class="section-header reveal">
    <div class="section-label">Why join</div>
    <h2>Everything You <em>Gain</em></h2>
  </div>
  <div class="benefits-grid">
    <div class="benefit-card reveal">
      <div class="benefit-num">01</div>
      <div class="benefit-icon">✈️</div>
      <div class="benefit-title">Luxury Travel Discounts</div>
      <p class="benefit-desc">Access exclusive rates on 5-star hotels, first-class flights and once-in-a-lifetime experiences that most people only dream about.</p>
    </div>
    <div class="benefit-card reveal">
      <div class="benefit-num">02</div>
      <div class="benefit-icon">💰</div>
      <div class="benefit-title">Flexible Income Stream</div>
      <p class="benefit-desc">Build a business that earns for you — whether you're poolside in Bali or skiing in the Alps. Your income doesn't stop when you do.</p>
    </div>
    <div class="benefit-card reveal">
      <div class="benefit-num">03</div>
      <div class="benefit-icon">👑</div>
      <div class="benefit-title">The King's Community</div>
      <p class="benefit-desc">Surround yourself with driven, like-minded go-getters who are living proof that a different kind of life is not only possible — it's happening.</p>
    </div>
    <div class="benefit-card reveal">
      <div class="benefit-num">04</div>
      <div class="benefit-icon">🎓</div>
      <div class="benefit-title">Full Training &amp; Support</div>
      <p class="benefit-desc">Kieron personally guides you through everything. No guesswork, no going it alone — just a clear, proven path to your freedom.</p>
    </div>
    <div class="benefit-card reveal">
      <div class="benefit-num">05</div>
      <div class="benefit-icon">🌍</div>
      <div class="benefit-title">Work From Anywhere</div>
      <p class="benefit-desc">Your phone is your office. Work from a beach, a café, a mountain top — the world becomes your workplace.</p>
    </div>
    <div class="benefit-card reveal">
      <div class="benefit-num">06</div>
      <div class="benefit-icon">🚀</div>
      <div class="benefit-title">Fast Start System</div>
      <p class="benefit-desc">Hit the ground running with a step-by-step system designed to get results quickly. No experience needed — just ambition.</p>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="how" id="how">
  <div class="how-inner">
    <div class="how-left reveal">
      <div class="section-label" style="justify-content:flex-start;">
        <span style="width:28px;height:1px;background:var(--gold);display:block;"></span>
        The roadmap
      </div>
      <h2 style="font-family:'Cormorant Garamond',serif;font-size:clamp(34px,3.5vw,52px);font-weight:300;line-height:1.1;margin-bottom:20px;">Your Path to <em style="font-style:italic;color:var(--gold2);">Total Freedom</em></h2>
      <p>Four simple steps. Real results. A life you actually want to live — not just scroll past on Instagram.</p>
      <a href="https://www.travelwithkieron.com/i-m-ready-to-join-the-king" class="btn-gold" target="_blank">I'm Ready to Join</a>
    </div>
    <div class="steps">
      <div class="step reveal">
        <div class="step-dot-wrap"><div class="dot"></div><div class="dotline"></div></div>
        <div class="step-body">
          <div class="step-label">Step 01</div>
          <h3>Join the Society</h3>
          <p>Apply for your spot in The Travel King Society. Kieron personally welcomes you and gets you set up from day one.</p>
        </div>
      </div>
      <div class="step reveal">
        <div class="step-dot-wrap"><div class="dot"></div><div class="dotline"></div></div>
        <div class="step-body">
          <div class="step-label">Step 02</div>
          <h3>Get the Blueprint</h3>
          <p>Access Kieron's complete, proven system for building your travel business, attracting customers and growing fast.</p>
        </div>
      </div>
      <div class="step reveal">
        <div class="step-dot-wrap"><div class="dot"></div><div class="dotline"></div></div>
        <div class="step-body">
          <div class="step-label">Step 03</div>
          <h3>Start Earning</h3>
          <p>Launch your business, make your first commissions and watch an income stream you control grow month after month.</p>
        </div>
      </div>
      <div class="step reveal">
        <div class="step-dot-wrap"><div class="dot"></div></div>
        <div class="step-body">
          <div class="step-label">Step 04</div>
          <h3>Travel Like Royalty</h3>
          <p>Book the trips. Live the experiences. Build the life. The only question is — where do you want to go first?</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROOF -->
<section class="proof reveal">
  <p class="proof-quote">I never thought I could earn money while lying on a beach in Thailand. Kieron's system changed everything for me.</p>
  <p class="proof-attr">— Society Member, 2024</p>
  <div class="proof-stats">
    <div class="reveal">
      <div class="stat-num">5+</div>
      <div class="stat-lbl">Years in luxury travel</div>
    </div>
    <div class="reveal">
      <div class="stat-num">30+</div>
      <div class="stat-lbl">Countries explored</div>
    </div>
    <div class="reveal">
      <div class="stat-num">100%</div>
      <div class="stat-lbl">Location freedom</div>
    </div>
  </div>
</section>

<!-- SOCIAL / CONNECT -->
<section class="social-section">
  <h2 class="reveal">Follow the <em>Journey</em></h2>
  <p class="reveal">See the life in real-time — the travels, the wins, the community.</p>
  <div class="social-btns reveal">
    <a href="https://www.instagram.com/itskieron.ellis" class="social-btn social-btn-ig" target="_blank">
      <img src="https://static.wixstatic.com/media/40898a93cfff4578b1779073137eb1b4.png/v1/fill/w_60,h_60,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/40898a93cfff4578b1779073137eb1b4.png" alt="Instagram">
      Follow on Instagram
    </a>
    <a href="https://www.tiktok.com/@itskieron.ellis" class="social-btn social-btn-tt" target="_blank">
      <img src="https://static.wixstatic.com/media/11062b_c7468ec61d494ead83af6058b76cadc0~mv2.png/v1/fill/w_60,h_60,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/11062b_c7468ec61d494ead83af6058b76cadc0~mv2.png" alt="TikTok">
      Follow on TikTok
    </a>
  </div>
</section>

<!-- CTA -->
<section class="cta">
  <h2 class="reveal">Your Royal Life<br><em>Starts Right Here.</em></h2>
  <p class="reveal">No more watching others live the life you want. Join The Travel King Society and start your journey to total freedom today.</p>
  <div class="cta-btns reveal">
    <a href="https://www.travelwithkieron.com/i-m-ready-to-join-the-king" class="btn-gold" target="_blank">I'm Ready to Join the Society</a>
    <a href="https://www.travelwithkieron.com/faqs" class="btn-outline" target="_blank">Read the FAQs first</a>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <a href="#">
    <img class="footer-logo" src="https://static.wixstatic.com/media/637089_2620c72feced452a94baf9eb9802aece~mv2.png/v1/fill/w_181,h_145,al_c,q_85,usm_0.66_1.00_0.01,enc_avif,quality_auto/Add%20a%20heading.png" alt="Travel With Kieron">
  </a>
  <p class="footer-copy">© 2025 Travel With Kieron. All rights reserved.</p>
  <p class="footer-credit">✦ Demo website created by Abman Media — dropafy@gmail.com · +94 77 213 6757</p>
</footer>

<script>
  /* nav scroll effect */
  const nav = document.getElementById('nav');
  window.addEventListener('scroll', () => nav.classList.toggle('scrolled', scrollY > 50));

  /* hamburger */
  const btn = document.getElementById('hamburger');
  const menu = document.getElementById('mobileMenu');
  btn.addEventListener('click', () => {
    const open = menu.classList.contains('open');
    if (open) {
      menu.classList.remove('open'); btn.classList.remove('open');
      document.body.style.overflow = '';
      setTimeout(() => menu.style.display = 'none', 320);
    } else {
      menu.style.display = 'flex';
      requestAnimationFrame(() => requestAnimationFrame(() => {
        menu.classList.add('open'); btn.classList.add('open');
      }));
      document.body.style.overflow = 'hidden';
    }
  });
  document.querySelectorAll('.mlink').forEach(l => l.addEventListener('click', () => {
    menu.classList.remove('open'); btn.classList.remove('open');
    document.body.style.overflow = '';
    setTimeout(() => menu.style.display = 'none', 320);
  }));

  /* scroll reveal */
  const obs = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) setTimeout(() => e.target.classList.add('visible'), i * 80);
    });
  }, { threshold: 0.07 });
  document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
</script>
</body>
</html>
