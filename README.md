<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WebEnarly — Where Great Websites Begin</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,600;0,700;0,900;1,300;1,700&display=swap" rel="stylesheet">
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{--neon:#d8ff30;--bg:#000f08;--bg2:#08150e;--gd:#214211;}
html{scroll-behavior:smooth}
body{font-family:'Poppins',sans-serif;background:#000;color:#fff;overflow-x:hidden;cursor:none;}

/* ── CURSOR ── */
#cur{position:fixed;width:10px;height:10px;border-radius:50%;background:var(--neon);pointer-events:none;z-index:9999;transform:translate(-50%,-50%);transition:width .25s,height .25s;mix-blend-mode:screen;}
#cur-ring{position:fixed;width:36px;height:36px;border-radius:50%;border:1.5px solid rgba(216,255,48,.55);pointer-events:none;z-index:9998;transform:translate(-50%,-50%);mix-blend-mode:screen;}
a:hover~#cur,button:hover~#cur{width:18px;height:18px;}

/* ── NAV ── */
nav{position:fixed;bottom:18px;left:50%;transform:translateX(-50%);width:min(780px,calc(100vw - 1rem));height:68px;z-index:900;}
.nav-wrap{position:relative;height:100%;background:rgba(0,15,8,.88);border:1px solid rgba(216,255,48,.16);border-radius:29px;backdrop-filter:blur(24px);display:flex;align-items:center;justify-content:space-between;padding:0 18px;box-shadow:0 24px 80px rgba(0,0,0,.7);}
.nav-wrap::before{content:'';position:absolute;inset:-1.5px;border-radius:36px;background:conic-gradient(from 180deg,rgba(0,255,213,.18),rgba(216,255,48,.10),rgba(33,66,17,.22),rgba(0,255,213,.18));filter:blur(12px);opacity:.65;z-index:-1;}
.logo{display:flex;align-items:center;gap:9px;text-decoration:none;background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.08);border-radius:9999px;padding:5px 13px 5px 5px;}
.logo-icon{width:34px;height:34px;border-radius:9px;background:linear-gradient(135deg,#d8ff30,#a7c81f);display:flex;align-items:center;justify-content:center;font-weight:900;font-size:12px;color:#000;}
.logo span{font-size:13px;font-weight:700;color:#fff;}
.logo b{color:#d8ff30;}
.nav-links{display:flex;align-items:center;gap:2px;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:9999px;padding:5px 6px;}
.nl{color:rgba(255,255,255,.68);text-decoration:none;font-size:13px;font-weight:600;padding:7px 14px;border-radius:9999px;border:1px solid transparent;transition:all .25s;cursor:none;}
.nl:hover,.nl.on{border-color:rgba(216,255,48,.25);background:linear-gradient(180deg,rgba(216,255,48,.12),rgba(255,255,255,.05));color:#fff;}
.nav-cta{display:inline-flex;align-items:center;gap:7px;background:linear-gradient(135deg,#d8ff30,#b5df2b 58%,#7d9820);color:#000;font-weight:700;font-size:13px;padding:7px 18px;border-radius:9999px;border:none;text-decoration:none;transition:transform .25s;box-shadow:0 10px 28px rgba(0,255,213,.25);cursor:none;}
.nav-cta:hover{transform:scale(1.05);}

/* ── PAGES ── */
.pg{display:none;}
.pg.on{display:block;}

/* ── GENERIC BUTTONS ── */
.btn-p{background:linear-gradient(135deg,#d8ff30,#b5df2b);color:#000;font-weight:900;font-size:14px;padding:16px 34px;border-radius:13px;text-decoration:none;border:none;cursor:none;transition:transform .25s,box-shadow .25s;box-shadow:0 0 36px rgba(216,255,48,.28);display:inline-block;}
.btn-p:hover{transform:scale(1.05);box-shadow:0 0 56px rgba(216,255,48,.46);}
.btn-s{background:rgba(255,255,255,.05);color:#fff;font-weight:700;font-size:14px;padding:16px 34px;border-radius:13px;text-decoration:none;border:1px solid rgba(255,255,255,.14);transition:all .25s;display:inline-block;cursor:none;}
.btn-s:hover{border-color:rgba(216,255,48,.28);background:rgba(255,255,255,.08);}

/* ── SCROLL REVEAL ── */
.rv{opacity:0;transform:translateY(38px);transition:opacity .65s,transform .65s;}
.rv.in{opacity:1;transform:none;}
.rvl{opacity:0;transform:translateX(-38px);transition:opacity .65s,transform .65s;}
.rvl.in{opacity:1;transform:none;}
.rvr{opacity:0;transform:translateX(38px);transition:opacity .65s,transform .65s;}
.rvr.in{opacity:1;transform:none;}
.rvs{opacity:0;transform:scale(.9);transition:opacity .65s,transform .65s;}
.rvs.in{opacity:1;transform:scale(1);}

/* ── SECTION ATOMS ── */
.tag{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.3em;color:#d8ff30;display:block;margin-bottom:8px;}
.pill{display:inline-flex;border:1px solid rgba(216,255,48,.2);background:rgba(216,255,48,.08);padding:5px 14px;border-radius:9999px;font-size:10px;font-weight:900;letter-spacing:.28em;text-transform:uppercase;color:#d8ff30;}
.sh2{font-size:clamp(30px,4vw,50px);font-weight:900;letter-spacing:-.04em;margin:8px 0 14px;}
.sdesc{font-size:15px;color:rgba(255,255,255,.52);line-height:1.7;}

/* ────────────────────────
   HOME
──────────────────────── */

/* hero */
.hero{min-height:110vh;display:flex;align-items:center;background:var(--bg);position:relative;overflow:hidden;padding:80px 24px 140px;}
.h-g1{position:absolute;top:10%;left:5%;width:320px;height:320px;background:rgba(33,66,17,.28);border-radius:50%;filter:blur(110px);animation:gp 4s ease-in-out infinite;}
.h-g2{position:absolute;bottom:8%;right:5%;width:400px;height:400px;background:rgba(216,255,48,.09);border-radius:50%;filter:blur(130px);}
@keyframes gp{0%,100%{opacity:.5}50%{opacity:1}}
.hero-grid{max-width:1200px;width:100%;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;position:relative;z-index:10;}
.hero-badge{display:flex;align-items:center;gap:12px;margin-bottom:28px;}
.ping{position:relative;width:11px;height:11px;}
.ping::before{content:'';position:absolute;inset:0;border-radius:50%;background:#d8ff30;opacity:.75;animation:pa 1.5s ease-in-out infinite;}
.ping::after{content:'';position:absolute;inset:0;border-radius:50%;background:#b7db20;}
@keyframes pa{0%,100%{transform:scale(1);opacity:.75}50%{transform:scale(2.2);opacity:0}}
h1.h1{font-weight:900;letter-spacing:-.02em;line-height:.94;margin-bottom:28px;}
.l1{display:block;font-size:clamp(48px,7vw,96px);background:linear-gradient(to right,#fff,#fff,#555);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.l2{display:block;font-size:clamp(26px,4vw,52px);color:#d8ff30;font-weight:300;font-style:italic;margin-top:8px;}
.l3{display:block;font-size:clamp(34px,5vw,74px);margin-top:14px;background:linear-gradient(to right,#d8ff30,#f3ffc1,#87a919);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.hero-desc{color:rgba(255,255,255,.4);font-size:17px;line-height:1.72;max-width:440px;margin-bottom:44px;border-left:2px solid rgba(216,255,48,.28);padding-left:22px;font-weight:300;}
.hero-btns{display:flex;gap:18px;flex-wrap:wrap;}
.hero-vis{position:relative;display:flex;justify-content:flex-end;}
.hcard{width:290px;height:410px;border-radius:48px;overflow:hidden;border:1px solid rgba(255,255,255,.09);transform:rotate(2deg);transition:transform .7s;background:var(--bg2);position:relative;}
.hcard:hover{transform:rotate(0);}
.hcard img{width:100%;height:100%;object-fit:cover;filter:grayscale(1);transition:filter 1s;}
.hcard:hover img{filter:grayscale(0);}
.hcard::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.55),transparent);pointer-events:none;}
.sf{position:absolute;background:rgba(255,255,255,.05);backdrop-filter:blur(20px);border:1px solid rgba(216,255,48,.1);border-radius:18px;padding:18px;}
.sf.l{left:-38px;top:66px;}
.sf.r{right:-28px;bottom:66px;}
.sf .n{font-size:30px;font-weight:900;font-style:italic;}
.sf .lb{font-size:9px;text-transform:uppercase;letter-spacing:.28em;color:#d8ff30;font-weight:700;margin-top:3px;}
.badge{position:absolute;bottom:-18px;left:22%;background:linear-gradient(135deg,#d8ff30,#b5df2b);color:#000;font-weight:900;font-size:12px;padding:13px 20px;border-radius:13px;transform:rotate(-5deg);box-shadow:0 20px 50px rgba(0,0,0,.5);}

/* stats bar */
.sbar{background:rgba(255,255,255,.025);border-top:1px solid rgba(255,255,255,.05);border-bottom:1px solid rgba(255,255,255,.05);padding:22px 0;overflow:hidden;}
.sbar-in{display:flex;gap:60px;white-space:nowrap;animation:mq 22s linear infinite;width:max-content;}
.sbar-in:hover{animation-play-state:paused;}
@keyframes mq{to{transform:translateX(-50%)}}
.si{display:flex;align-items:center;gap:10px;flex-shrink:0;}
.si .nv{font-size:26px;font-weight:900;background:linear-gradient(to right,#d8ff30,#f3ffc1);-webkit-background-clip:text;-webkit-text-fill-color:transparent;}
.si .lv{font-size:12px;color:rgba(255,255,255,.45);text-transform:uppercase;letter-spacing:.18em;}
.sdot{color:rgba(216,255,48,.28);font-size:22px;flex-shrink:0;}

/* about */
.about{background:var(--bg);padding:96px 24px;}
.about-grid{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;}
.aim{aspect-ratio:3/4;width:88%;margin-left:auto;border-radius:18px;overflow:hidden;border:1px solid rgba(255,255,255,.07);position:relative;background:var(--bg2);}
.aim img{width:100%;height:100%;object-fit:cover;filter:grayscale(1);transition:all .7s;}
.aim:hover img{filter:grayscale(0);transform:scale(1.04);}
.aim::after{content:'';position:absolute;inset:0;background:rgba(33,66,17,.28);opacity:.45;transition:opacity .5s;}
.aim:hover::after{opacity:0;}
.ais{position:absolute;bottom:-18px;left:0;width:50%;aspect-ratio:1;border-radius:14px;overflow:hidden;border:2px solid #000;box-shadow:0 18px 50px rgba(0,0,0,.45);}
.ais img{width:100%;height:100%;object-fit:cover;}
.a-h2{font-size:clamp(26px,3.4vw,44px);font-weight:700;line-height:1.18;margin-bottom:18px;}
.a-desc{font-size:15px;line-height:1.8;color:rgba(255,255,255,.42);margin-bottom:30px;}
.stats3{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;border-top:1px solid rgba(255,255,255,.08);padding-top:24px;margin-bottom:32px;}
.s3n{font-size:clamp(26px,3vw,38px);font-weight:700;margin-bottom:3px;}
.s3l{font-size:12px;color:rgba(255,255,255,.42);font-weight:500;}
.arr-link{display:inline-flex;align-items:center;gap:7px;color:#fff;text-decoration:none;font-weight:600;font-size:14px;border-bottom:1px solid #d8ff30;padding-bottom:3px;transition:color .25s;cursor:none;}
.arr-link:hover{color:#d8ff30;}

/* services */
.svc-sec{background:var(--bg);padding:96px 0;}
.sec-h{text-align:center;padding:0 24px 64px;max-width:1200px;margin:0 auto;}
.svc-wrap{max-width:1200px;margin:0 auto;padding:0 24px;}
.sg{display:grid;grid-template-columns:repeat(3,1fr);gap:26px;}
.sc{position:relative;border-radius:26px;overflow:hidden;height:390px;background:var(--bg2);border:1px solid rgba(255,255,255,.06);cursor:none;transition:all .45s;}
.sc:hover{border-color:rgba(216,255,48,.28);}
.sc img{width:100%;height:100%;object-fit:cover;transition:transform .7s,filter .7s;filter:grayscale(.38);}
.sc:hover img{transform:scale(1.1);filter:grayscale(0);}
.sc-ov{position:absolute;inset:0;background:linear-gradient(to top,rgba(0,15,8,.94),rgba(0,15,8,.28),transparent);transition:opacity .28s;}
.sc:hover .sc-ov{opacity:.45;}
.sc-hov{position:absolute;inset:0;background:linear-gradient(to top,rgba(216,255,48,.93),transparent);opacity:0;transition:opacity .28s;z-index:2;}
.sc:hover .sc-hov{opacity:.9;}
.sc-body{position:absolute;bottom:0;left:0;width:100%;padding:26px;z-index:3;transition:transform .28s;}
.sc:hover .sc-body{transform:translateY(-7px);}
.sc-num{font-size:30px;font-weight:700;color:rgba(255,255,255,.22);display:block;margin-bottom:5px;transition:color .28s;}
.sc:hover .sc-num{color:rgba(216,255,48,.38);}
.sc-n{font-size:18px;font-weight:700;color:#fff;transition:color .28s;margin-bottom:5px;}
.sc:hover .sc-n{color:#000;}
.sc-d{font-size:12px;font-weight:500;color:rgba(255,255,255,.68);transition:color .28s;display:-webkit-box;-webkit-line-clamp:3;-webkit-box-orient:vertical;overflow:hidden;}
.sc:hover .sc-d{color:rgba(0,0,0,.86);}
.sc-ico{position:absolute;top:-16px;left:-18px;width:56px;height:56px;border-radius:50%;background:linear-gradient(180deg,#d8ff30,#a7c81f);display:flex;align-items:center;justify-content:center;font-size:20px;color:#000;border:4px solid var(--bg);z-index:10;transition:transform .28s;}
.sc:hover .sc-ico{transform:scale(1.1) rotate(12deg);}

/* why */
.why{background:var(--bg);padding:108px 24px;position:relative;overflow:hidden;}
.why::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at top,rgba(216,255,48,.07),transparent 32%),radial-gradient(circle at bottom,rgba(33,66,17,.14),transparent 28%);pointer-events:none;}
.wg{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(4,1fr);gap:14px;position:relative;z-index:1;}
.wc{background:linear-gradient(180deg,rgba(13,13,13,.94),rgba(8,8,8,.96));border:1px solid rgba(255,255,255,.09);border-radius:34px;padding:26px;position:relative;overflow:hidden;cursor:none;transition:all .28s;}
.wc::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(216,255,48,.14),rgba(216,255,48,.05),transparent);opacity:.8;}
.wc::after{content:'';position:absolute;inset-x:26px;top:0;height:1px;background:linear-gradient(to right,transparent,rgba(255,255,255,.28),transparent);}
.wc:hover{transform:translateY(-5px);border-color:rgba(216,255,48,.22);}
.wi{width:56px;height:56px;border-radius:18px;border:1px solid rgba(255,255,255,.09);background:rgba(0,0,0,.18);display:flex;align-items:center;justify-content:center;margin-bottom:18px;position:relative;z-index:1;}
.wi svg{width:20px;height:20px;stroke:#d8ff30;fill:none;stroke-width:1.8;}
.wn{font-size:9px;font-weight:900;letter-spacing:.28em;text-transform:uppercase;color:rgba(255,255,255,.42);margin-bottom:9px;position:relative;z-index:1;}
.wc h3{font-size:18px;font-weight:900;letter-spacing:-.03em;margin-bottom:10px;position:relative;z-index:1;transition:color .28s;}
.wc:hover h3{color:#d8ff30;}
.wc p{font-size:12px;line-height:1.7;color:rgba(255,255,255,.52);position:relative;z-index:1;}

/* portfolio preview */
.pp{background:var(--bg);padding:96px 24px;}
.pg3{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:26px;}
.pi{position:relative;aspect-ratio:4/3;border-radius:14px;overflow:hidden;cursor:none;background:var(--bg2);}
.pi img{width:100%;height:100%;object-fit:cover;transition:transform .7s;}
.pi:hover img{transform:scale(1.09);}
.pi-ov{position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,15,8,.06),rgba(0,15,8,.8));opacity:0;transition:opacity .28s;}
.pi:hover .pi-ov{opacity:1;}
.pi-info{position:absolute;bottom:0;padding:22px;opacity:0;transition:opacity .28s;}
.pi:hover .pi-info{opacity:1;}
.pi-cat{font-size:11px;font-weight:700;text-transform:uppercase;color:#d8ff30;margin-bottom:3px;letter-spacing:.2em;}
.pi-t{font-size:17px;font-weight:700;}

/* testimonials */
.testi{background:var(--bg);padding:92px 0;overflow:hidden;}
.t-track{display:flex;gap:22px;overflow:hidden;padding:14px 0;}
.t-in{display:flex;gap:22px;animation:tmq 32s linear infinite;width:max-content;}
.t-in:hover{animation-play-state:paused;}
@keyframes tmq{to{transform:translateX(-50%)}}
.tc{width:390px;flex-shrink:0;border-radius:14px;border:1px solid rgba(255,255,255,.07);background:linear-gradient(180deg,rgba(33,66,17,.18),rgba(8,15,12,.96));padding:26px;transition:border-color .28s;}
.tc:hover{border-color:rgba(216,255,48,.22);}
.tstars{color:#d8ff30;margin-bottom:12px;font-size:13px;}
.tq{font-size:14px;font-style:italic;line-height:1.7;color:rgba(255,255,255,.68);margin-bottom:18px;}
.ta h4{font-weight:700;font-size:14px;margin-bottom:2px;}
.ta p{font-size:12px;color:rgba(216,255,48,.72);}

/* faq */
.faq{background:var(--bg);padding:92px 24px;}
.faq-g{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 2fr;gap:72px;}
.faq-side h2{font-size:clamp(26px,3.3vw,42px);font-weight:700;margin:8px 0 18px;}
.faq-side p{color:rgba(255,255,255,.5);font-size:15px;margin-bottom:28px;}
.fi{border:1px solid rgba(255,255,255,.07);border-radius:14px;margin-bottom:12px;overflow:hidden;transition:all .28s;cursor:none;background:linear-gradient(180deg,rgba(255,255,255,.025),rgba(255,255,255,.01));}
.fi.op{border-color:rgba(216,255,48,.22);background:linear-gradient(180deg,rgba(33,66,17,.36),rgba(8,15,12,.95));}
.fh{display:flex;justify-content:space-between;align-items:center;padding:18px 22px;gap:14px;}
.fh h3{font-size:15px;font-weight:700;color:rgba(255,255,255,.7);transition:color .28s;}
.fi.op .fh h3{color:#fff;}
.ft{width:28px;height:28px;border-radius:50%;border:1px solid rgba(255,255,255,.16);display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all .28s;font-size:17px;color:rgba(255,255,255,.45);}
.fi.op .ft{background:#d8ff30;border-color:#d8ff30;color:#000;transform:rotate(45deg);}
.fb{max-height:0;overflow:hidden;transition:max-height .38s ease;}
.fi.op .fb{max-height:180px;}
.fb p{padding:0 22px 18px;color:rgba(255,255,255,.52);font-size:13px;line-height:1.7;border-top:1px solid rgba(255,255,255,.04);padding-top:13px;}

/* cta */
.cta-s{background:linear-gradient(135deg,#123b22 0%,#0b170f 50%,#123b22 100%);padding:80px 24px;position:relative;overflow:hidden;}
.cta-s::before{content:'';position:absolute;left:-8%;top:-20%;width:280px;height:280px;border-radius:50%;background:rgba(216,255,48,.07);filter:blur(70px);}
.cta-s::after{content:'';position:absolute;right:-10%;top:-14%;width:280px;height:280px;border-radius:50%;background:rgba(216,255,48,.06);filter:blur(70px);}
.cta-in{max-width:760px;margin:0 auto;text-align:center;position:relative;z-index:1;}
.cta-in h2{font-size:clamp(30px,4.5vw,52px);font-weight:900;letter-spacing:-.04em;margin:14px 0 18px;}
.cta-in p{color:rgba(255,255,255,.58);font-size:16px;margin-bottom:32px;}
.cta-btns{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;}

/* footer */
footer{background:#000;border-top:1px solid rgba(216,255,48,.07);padding:60px 24px 40px;position:relative;overflow:hidden;}
footer::before{content:'WEBENARLY';position:absolute;bottom:-90px;left:50%;transform:translateX(-50%);font-size:clamp(70px,13vw,190px);font-weight:900;color:rgba(255,255,255,.025);white-space:nowrap;pointer-events:none;letter-spacing:.05em;}
.fp-row{border-bottom:1px solid rgba(255,255,255,.07);margin-bottom:36px;padding-bottom:28px;display:grid;grid-template-columns:repeat(6,1fr);gap:12px;max-width:1200px;margin-left:auto;margin-right:auto;}
.fpc{text-align:center;padding:14px;}
.fpc .fn{font-size:18px;font-weight:700;margin-bottom:5px;}
.fpc .fr{font-size:11px;color:rgba(255,255,255,.38);}
.footer-cols{display:grid;grid-template-columns:2fr 1fr 1fr 1.2fr;gap:36px;max-width:1200px;margin:0 auto 36px;position:relative;z-index:1;}
.fc-brand a{font-size:20px;font-weight:700;background:linear-gradient(to right,#fff,#f6ffd0,#d8ff30);-webkit-background-clip:text;-webkit-text-fill-color:transparent;text-decoration:none;display:block;margin-bottom:12px;}
.fc-brand p{font-size:12px;color:rgba(255,255,255,.4);line-height:1.7;margin-bottom:18px;}
.socials{display:flex;gap:10px;}
.sa{width:36px;height:36px;border-radius:50%;border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.04);display:flex;align-items:center;justify-content:center;color:rgba(255,255,255,.6);text-decoration:none;transition:all .25s;cursor:none;}
.sa:hover{background:#d8ff30;color:#000;}
.fc h3{font-size:15px;font-weight:700;margin-bottom:18px;}
.fc ul{list-style:none;}
.fc ul li{margin-bottom:9px;}
.fc ul li a{font-size:12px;color:rgba(255,255,255,.42);text-decoration:none;transition:color .25s;cursor:none;}
.fc ul li a:hover{color:#d8ff30;}
.fc-news p{font-size:12px;color:rgba(255,255,255,.42);margin-bottom:12px;}
.fc-news input{width:100%;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.09);border-radius:7px;padding:10px 12px;color:#fff;font-family:'Poppins',sans-serif;font-size:12px;outline:none;margin-bottom:9px;transition:border-color .25s;}
.fc-news input:focus{border-color:#d8ff30;}
.fc-news button{width:100%;background:#d8ff30;color:#000;font-family:'Poppins',sans-serif;font-weight:600;border:none;border-radius:7px;padding:10px;cursor:none;font-size:12px;transition:all .25s;}
.fc-news button:hover{transform:scale(1.03);}
.f-bot{display:flex;justify-content:space-between;align-items:center;border-top:1px solid rgba(255,255,255,.07);padding-top:24px;max-width:1200px;margin:0 auto;flex-wrap:wrap;gap:14px;position:relative;z-index:1;}
.f-bot p{font-size:12px;color:rgba(255,255,255,.32);}
.f-bot-links{display:flex;gap:18px;}
.f-bot-links a{font-size:12px;color:rgba(255,255,255,.32);text-decoration:none;cursor:none;}
.f-bot-links a:hover{color:#d8ff30;}
.stb{width:36px;height:36px;background:rgba(255,255,255,.09);border-radius:50%;border:none;color:#fff;font-size:15px;cursor:none;transition:all .25s;display:flex;align-items:center;justify-content:center;}
.stb:hover{background:#d8ff30;color:#000;}

/* ────────────────────────
   PORTFOLIO PAGE
──────────────────────── */
.port-page{background:var(--bg);min-height:100vh;padding:96px 24px 80px;}
.port-hdr{max-width:1200px;margin:0 auto 52px;}
.port-filters{display:flex;flex-wrap:wrap;gap:9px;margin-top:28px;}
.fbt{padding:7px 18px;border-radius:9999px;font-size:12px;font-weight:600;border:1px solid rgba(255,255,255,.11);background:rgba(255,255,255,.03);color:rgba(255,255,255,.58);cursor:none;transition:all .25s;}
.fbt.on{border-color:#d8ff30;background:#d8ff30;color:#000;}
.fbt:hover:not(.on){border-color:rgba(216,255,48,.22);color:#fff;}
.port-grid-full{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:26px;}
.pfc{border-radius:22px;overflow:hidden;border:1px solid rgba(255,255,255,.07);background:linear-gradient(180deg,rgba(10,21,16,.96),rgba(33,66,17,.18));}
.pfc-img{position:relative;height:210px;overflow:hidden;}
.pfc-img img{width:100%;height:100%;object-fit:cover;transition:transform .48s;}
.pfc:hover .pfc-img img{transform:scale(1.06);}
.pfc-img::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.78),rgba(0,0,0,.18),transparent);}
.pb{position:absolute;bottom:11px;left:11px;z-index:1;background:rgba(0,0,0,.38);border:1px solid rgba(255,255,255,.22);border-radius:9999px;padding:3px 10px;font-size:9px;text-transform:uppercase;letter-spacing:.18em;color:#f0f0f0;}
.py{position:absolute;bottom:11px;right:11px;z-index:1;font-size:11px;color:rgba(255,255,255,.55);}
.pfc-body{padding:18px;}
.pfc-body h3{font-size:18px;font-weight:800;line-height:1.22;margin-bottom:3px;}
.pcl{font-size:12px;color:#f3ffc2;margin-bottom:10px;}
.pfc-body p{font-size:12px;color:rgba(255,255,255,.58);line-height:1.6;margin-bottom:14px;}
.pmeta{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px;}
.pmi{border:1px solid rgba(255,255,255,.07);background:rgba(255,255,255,.03);border-radius:10px;padding:8px 10px;}
.pmi .k{font-size:9px;color:rgba(255,255,255,.38);text-transform:uppercase;letter-spacing:.15em;margin-bottom:2px;}
.pmi .v{font-size:11px;font-weight:600;}
.pcbtns{display:flex;gap:7px;flex-wrap:wrap;}
.pcb1{padding:7px 14px;background:linear-gradient(135deg,#d8ff30,#b5df2b);color:#000;font-weight:700;font-size:11px;border-radius:9px;border:none;cursor:none;transition:transform .2s;}
.pcb1:hover{transform:scale(1.03);}
.pcb2{padding:7px 14px;background:rgba(255,255,255,.04);color:#fff;font-weight:600;font-size:11px;border-radius:9px;border:1px solid rgba(255,255,255,.11);cursor:none;transition:background .2s;}
.pcb2:hover{background:rgba(255,255,255,.09);}

/* ────────────────────────
   SERVICES PAGE
──────────────────────── */
.svc-page{background:var(--bg);min-height:100vh;padding:96px 24px 80px;}
.svc-p-hero{max-width:1200px;margin:0 auto 56px;text-align:center;}
.svc-tabs{display:flex;gap:9px;flex-wrap:wrap;max-width:1200px;margin:0 auto 44px;}
.stab{padding:11px 18px;border-radius:13px;border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.03);color:rgba(255,255,255,.58);cursor:none;text-align:left;transition:all .25s;}
.stab.on{border-color:rgba(216,255,48,.28);background:rgba(216,255,48,.09);color:#fff;}
.stab .stn{font-size:13px;font-weight:600;}
.stab .stc{font-size:10px;color:rgba(255,255,255,.38);margin-top:2px;}
.stab.on .stc{color:rgba(216,255,48,.65);}
.svc-full-g{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:18px;}
.sfc{border-radius:18px;overflow:hidden;border:1px solid rgba(255,255,255,.09);background:linear-gradient(180deg,rgba(12,24,18,.96),rgba(33,66,17,.18));}
.sfc-img{position:relative;height:170px;overflow:hidden;}
.sfc-img img{width:100%;height:100%;object-fit:cover;}
.sfc-img::after{content:'';position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.72),transparent);}
.stl{position:absolute;top:12px;right:12px;z-index:1;background:rgba(0,15,8,.62);border:1px solid rgba(216,255,48,.18);border-radius:9999px;padding:3px 10px;font-size:9px;text-transform:uppercase;letter-spacing:.18em;color:#f3ffc2;}
.sfc-body{padding:18px;}
.sfc-body h3{font-size:16px;font-weight:700;margin-bottom:8px;}
.sfc-body p{font-size:12px;color:rgba(255,255,255,.58);line-height:1.6;margin-bottom:14px;}
.smg{display:grid;grid-template-columns:1fr 1fr;gap:7px;margin-bottom:14px;}
.smb{border:1px solid rgba(255,255,255,.07);background:rgba(255,255,255,.03);border-radius:9px;padding:9px 10px;}
.smb .k{font-size:8px;text-transform:uppercase;letter-spacing:.15em;color:rgba(255,255,255,.38);margin-bottom:2px;}
.smb .v{font-size:11px;font-weight:600;}
.scbtns{display:flex;gap:7px;flex-wrap:wrap;}
.scb1{padding:6px 13px;background:rgba(216,255,48,.09);color:#f6ffd0;font-weight:600;font-size:10px;border-radius:7px;border:1px solid rgba(216,255,48,.26);cursor:none;transition:background .2s;}
.scb1:hover{background:rgba(216,255,48,.17);}
.scb2{padding:6px 13px;background:rgba(255,255,255,.03);color:#fff;font-weight:600;font-size:10px;border-radius:7px;border:1px solid rgba(255,255,255,.13);cursor:none;transition:background .2s;}
.scb2:hover{background:rgba(255,255,255,.09);}

/* ────────────────────────
   PRICING PAGE
──────────────────────── */
.pricing-pg{background:linear-gradient(180deg,rgba(33,66,17,.16) 0%,rgba(8,18,7,.99) 18%,#000703 55%);min-height:100vh;padding:96px 24px 80px;position:relative;}
.pricing-pg::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at top,rgba(33,66,17,.26) 0%,transparent 33%);}
.price-hero{max-width:880px;margin:0 auto 56px;text-align:center;position:relative;z-index:1;}
.price-hero h1{font-size:clamp(34px,5vw,54px);font-weight:700;line-height:1.15;margin:14px 0 14px;}
.ptabs{display:flex;flex-wrap:wrap;gap:7px;justify-content:center;margin-top:28px;}
.ptb{padding:7px 16px;border-radius:11px;font-size:12px;font-weight:600;transition:all .25s;cursor:none;}
.ptb.on{background:#d8ff30;color:#000;box-shadow:0 0 18px rgba(216,255,48,.28);}
.ptb:not(.on){color:rgba(255,255,255,.62);border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.04);}
.price-cards{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:22px;position:relative;z-index:1;}
.prcc{border-radius:26px;padding:28px;position:relative;overflow:hidden;backdrop-filter:blur(28px);border:1px solid rgba(255,255,255,.07);background:rgba(5,12,5,.9);transition:all .38s;min-height:620px;display:flex;flex-direction:column;}
.prcc:hover{border-color:rgba(216,255,48,.32);transform:translateY(-4px);}
.prcc.feat{background:linear-gradient(180deg,#163014,#081207,#000);border-color:rgba(216,255,48,.48);box-shadow:0 0 56px rgba(216,255,48,.11);}
.prcc-glow{position:absolute;top:-70px;right:-70px;width:220px;height:220px;border-radius:50%;background:rgba(216,255,48,.04);filter:blur(70px);pointer-events:none;}
.pop-badge{position:absolute;top:18px;right:18px;background:#d8ff30;color:#000;font-size:8px;font-weight:900;letter-spacing:.2em;text-transform:uppercase;padding:3px 10px;border-radius:9999px;}
.pplan{font-size:20px;font-weight:700;margin-bottom:10px;}
.pdesc{font-size:12px;color:rgba(255,255,255,.42);min-height:38px;margin-bottom:20px;}
.pbox{background:rgba(255,255,255,.025);border:1px solid rgba(255,255,255,.05);border-radius:14px;padding:18px;margin-bottom:20px;}
.porig{font-size:14px;color:rgba(255,255,255,.26);text-decoration:line-through;margin-bottom:3px;}
.pnrow{display:flex;align-items:center;gap:9px;}
.pnum{font-size:44px;font-weight:900;letter-spacing:-.03em;}
.pbdge{font-size:8px;font-weight:900;color:#d8ff30;background:rgba(216,255,48,.09);border:1px solid rgba(216,255,48,.18);padding:3px 7px;border-radius:5px;}
.pper{font-size:8px;color:rgba(255,255,255,.32);text-transform:uppercase;letter-spacing:.2em;margin-top:3px;}
.pfeats{flex:1;margin-bottom:18px;}
.pfeat{display:flex;align-items:flex-start;gap:9px;font-size:11px;color:rgba(255,255,255,.72);line-height:1.5;margin-bottom:12px;}
.pchk{width:15px;height:15px;border-radius:50%;background:rgba(216,255,48,.09);border:1px solid rgba(216,255,48,.28);display:flex;align-items:center;justify-content:center;color:#d8ff30;font-size:8px;flex-shrink:0;margin-top:1px;}
.pcta{width:100%;padding:13px;border-radius:11px;font-family:'Poppins',sans-serif;font-weight:700;font-size:12px;cursor:none;transition:all .28s;text-align:center;border:none;}
.pcta.main{background:#d8ff30;color:#000;}
.pcta.main:hover{box-shadow:0 0 28px rgba(216,255,48,.38);transform:scale(1.02);}
.pcta.ghost{background:rgba(255,255,255,.04);color:#fff;border:1px solid rgba(255,255,255,.09);}
.pcta.ghost:hover{background:rgba(255,255,255,.08);}
.pnote{text-align:center;font-size:8px;color:rgba(255,255,255,.22);text-transform:uppercase;letter-spacing:.2em;margin-top:10px;}
.ptrust{max-width:1200px;margin:26px auto 0;background:rgba(255,255,255,.025);border:1px solid rgba(216,255,48,.09);border-radius:14px;padding:18px;display:grid;grid-template-columns:repeat(4,1fr);gap:10px;position:relative;z-index:1;}
.trit{display:flex;align-items:center;gap:7px;font-size:12px;color:rgba(255,255,255,.72);}
.trck{color:#d8ff30;font-size:13px;}

/* ────────────────────────
   CONTACT PAGE
──────────────────────── */
.contact-pg{background:var(--bg);min-height:100vh;padding:96px 24px 80px;position:relative;overflow:hidden;}
.contact-pg::before{content:'';position:absolute;inset:0;background:radial-gradient(circle at top,rgba(255,255,255,.035),transparent 28%);}
.ct-hero{max-width:1200px;margin:0 auto 56px;}
.ct-hero-grid{display:grid;grid-template-columns:1fr 1fr;gap:44px;align-items:center;background:linear-gradient(135deg,rgba(255,255,255,.03),rgba(33,66,17,.16));border:1px solid rgba(255,255,255,.07);border-radius:26px;padding:36px;}
.ct-tags{display:flex;flex-wrap:wrap;gap:7px;margin-top:20px;}
.cttag{padding:7px 14px;border-radius:9999px;border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.03);font-size:12px;color:rgba(255,255,255,.62);}
.ct-vis{position:relative;display:flex;align-items:center;justify-content:center;}
.ct-orb{width:240px;height:240px;border-radius:50%;background:radial-gradient(circle at top,rgba(216,255,48,.13),rgba(255,255,255,.02) 45%,rgba(33,66,17,.22) 100%);border:1px solid rgba(255,255,255,.07);display:flex;align-items:center;justify-content:center;position:relative;}
.ct-orb::before{content:'';position:absolute;width:82%;height:82%;border-radius:50%;border:1px dashed rgba(216,255,48,.18);animation:spslow 20s linear infinite;}
@keyframes spslow{to{transform:rotate(360deg)}}
.ct-orb-in{position:relative;z-index:10;text-align:center;width:130px;height:130px;border-radius:18px;background:linear-gradient(180deg,rgba(216,255,48,.15),rgba(33,66,17,.28));border:1px solid rgba(216,255,48,.2);display:flex;align-items:center;justify-content:center;flex-direction:column;}
.ctol{font-size:8px;font-weight:700;letter-spacing:.26em;text-transform:uppercase;color:rgba(255,255,255,.42);}
.ctog{font-size:40px;font-weight:900;color:#f6ffd0;margin-top:6px;}
.ctfl{position:absolute;border-radius:9999px;border:1px solid rgba(255,255,255,.09);background:linear-gradient(180deg,rgba(255,255,255,.04),rgba(33,66,17,.13));padding:7px 14px;font-size:10px;font-weight:600;color:rgba(255,255,255,.62);backdrop-filter:blur(14px);}
.ctfl.f1{top:18%;left:2%;}
.ctfl.f2{top:22%;right:4%;}
.ctfl.f3{bottom:14%;left:12%;}
.ct-body{max-width:1200px;margin:0 auto;display:grid;grid-template-columns:1fr 1.1fr;gap:44px;position:relative;z-index:1;}
.ct-steps{border-radius:18px;border:1px solid rgba(255,255,255,.07);background:linear-gradient(180deg,rgba(255,255,255,.02),rgba(33,66,17,.10));overflow:hidden;}
.ct-step{display:flex;gap:14px;padding:18px 22px;border-bottom:1px solid rgba(255,255,255,.05);}
.ct-step:last-of-type{border-bottom:none;}
.csn{width:42px;height:42px;border-radius:11px;background:rgba(216,255,48,.07);border:1px solid rgba(216,255,48,.13);font-size:12px;font-weight:900;color:#d8ff30;display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.ct-step h3{font-size:15px;font-weight:700;margin-bottom:3px;}
.ct-step p{font-size:12px;color:rgba(255,255,255,.48);line-height:1.6;}
.ci-items{margin-top:20px;}
.cii{display:flex;align-items:flex-start;gap:14px;background:rgba(255,255,255,.02);border:1px solid rgba(255,255,255,.05);border-radius:14px;padding:16px;margin-bottom:16px;transition:border-color .25s;}
.cii:hover{border-color:rgba(216,255,48,.22);}
.cii-ico{width:42px;height:42px;border-radius:50%;background:rgba(216,255,48,.1);display:flex;align-items:center;justify-content:center;flex-shrink:0;}
.cii-ico svg{width:20px;height:20px;stroke:#d8ff30;fill:none;stroke-width:1.5;}
.cii h4{font-weight:700;font-size:14px;margin-bottom:3px;}
.cii p{font-size:12px;color:rgba(255,255,255,.38);}
.ct-form{border-radius:26px;border:1px solid rgba(255,255,255,.07);background:linear-gradient(180deg,rgba(9,18,13,.98),rgba(33,66,17,.16));padding:32px;position:relative;overflow:hidden;}
.ct-form::before{content:'';position:absolute;top:0;right:0;width:120px;height:120px;background:rgba(216,255,48,.07);filter:blur(56px);border-radius:50%;pointer-events:none;}
.ct-form::after{content:'';position:absolute;left:28px;top:0;height:1px;width:150px;background:linear-gradient(to right,transparent,rgba(255,255,255,.28),transparent);}
.form-hdr{margin-bottom:22px;padding-bottom:18px;border-bottom:1px solid rgba(255,255,255,.06);}
.form-hdr .tag{margin-bottom:8px;}
.form-hdr h2{font-size:22px;font-weight:900;letter-spacing:-.04em;}
.frow{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-bottom:16px;}
.fg{margin-bottom:16px;}
.fg label{font-size:12px;font-weight:600;color:rgba(255,255,255,.38);display:block;margin-bottom:6px;margin-left:3px;}
.fg input,.fg textarea{width:100%;background:var(--bg);border:1px solid rgba(255,255,255,.07);border-radius:11px;padding:13px 14px;color:#fff;font-family:'Poppins',sans-serif;font-size:13px;outline:none;transition:border-color .25s;resize:none;}
.fg input::placeholder,.fg textarea::placeholder{color:rgba(255,255,255,.22);}
.fg input:focus,.fg textarea:focus{border-color:#d8ff30;box-shadow:0 0 0 1px rgba(216,255,48,.25);}
.ctags-row{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:18px;border-top:1px solid rgba(255,255,255,.06);padding-top:14px;}
.ctag2{padding:5px 11px;border-radius:9999px;border:1px solid rgba(255,255,255,.09);background:rgba(255,255,255,.03);font-size:9px;font-weight:600;letter-spacing:.18em;text-transform:uppercase;color:rgba(255,255,255,.5);}
.form-foot{display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:14px;}
.form-foot p{font-size:12px;color:rgba(255,255,255,.38);max-width:260px;line-height:1.6;}

/* ── RESPONSIVE ── */
@media(max-width:900px){
  .hero-grid,.about-grid,.ct-hero-grid,.ct-body,.footer-cols{grid-template-columns:1fr;}
  .hero-vis,.ct-vis{display:none;}
  .sg,.pg3,.port-grid-full,.svc-full-g,.price-cards,.wg,.ptrust{grid-template-columns:1fr 1fr;}
  footer::before{display:none;}
  .faq-g{grid-template-columns:1fr;}
  .fp-row{grid-template-columns:repeat(3,1fr);}
}
@media(max-width:560px){
  .sg,.pg3,.port-grid-full,.svc-full-g,.price-cards,.wg,.ptrust{grid-template-columns:1fr;}
  .frow{grid-template-columns:1fr;}
  .nav-links{display:none;}
  .fp-row{grid-template-columns:1fr 1fr;}
}
</style>
</head>
<body>

<div id="cur"></div>
<div id="cur-ring"></div>

<!-- NAV -->
<nav>
  <div class="nav-wrap">
    <a class="logo" href="#" onclick="go('home');return false;">
      <div class="logo-icon">WE</div>
      <span>Web<b>Enarly</b></span>
    </a>
    <div class="nav-links">
      <a class="nl on" id="nl-home" href="#" onclick="go('home');return false;">Home</a>
      <a class="nl" id="nl-portfolio" href="#" onclick="go('portfolio');return false;">Projects</a>
      <a class="nl" id="nl-services" href="#" onclick="go('services');return false;">Services</a>
      <a class="nl" id="nl-pricing" href="#" onclick="go('pricing');return false;">Pricing</a>
    </div>
    <a class="nav-cta" href="#" onclick="go('contact');return false;">
      <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M12 5v14m7-7H5"/></svg>
      <span style="display:flex;flex-direction:column;line-height:1.1;"><span style="font-size:10px;font-weight:900;">Start</span><span style="font-size:9px;font-weight:600;color:rgba(0,0,0,.6);">Project</span></span>
    </a>
  </div>
</nav>

<!-- ═══ HOME ═══ -->
<div class="pg on" id="pg-home">

  <section class="hero">
    <div class="h-g1"></div><div class="h-g2"></div>
    <div class="hero-grid">
      <div>
        <div class="hero-badge rv">
          <div class="ping"></div>
          <span style="font-size:10px;font-weight:700;letter-spacing:.28em;text-transform:uppercase;color:rgba(255,255,255,.36);">Available for new projects</span>
        </div>
        <h1 class="h1 rv">
          <span class="l1">DESIGN. BUILD.</span>
          <span class="l2">THAT CONVERTS.</span>
          <span class="l3">WEBENARLY</span>
        </h1>
        <p class="hero-desc rv">We engineer premium WordPress & WooCommerce experiences that transform your brand and accelerate revenue. No templates. No compromises. Pure performance.</p>
        <div class="hero-btns rv">
          <a class="btn-p" href="#" onclick="go('contact');return false;">Launch Your Project</a>
          <a class="btn-s" href="#" onclick="go('portfolio');return false;">View Case Studies</a>
        </div>
      </div>
      <div class="hero-vis rv">
        <div class="hcard"><img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=1470" alt="Studio"></div>
        <div class="sf l"><div class="n">98%</div><div class="lb">Project Success Rate</div><div style="display:flex;gap:3px;margin-top:7px;"><div style="width:3px;height:9px;background:#d8ff30;border-radius:3px;animation:bba 1s ease infinite;"></div><div style="width:3px;height:9px;background:#d8ff30;border-radius:3px;animation:bba 1s .1s ease infinite;"></div><div style="width:3px;height:9px;background:#d8ff30;border-radius:3px;animation:bba 1s .2s ease infinite;"></div><div style="width:3px;height:9px;background:#d8ff30;border-radius:3px;animation:bba 1s .3s ease infinite;"></div></div></div>
        <div class="sf r"><div style="display:flex;align-items:center;gap:10px;"><div style="display:flex;"><div style="width:26px;height:26px;border-radius:50%;border:2px solid #000;background:#333;display:flex;align-items:center;justify-content:center;font-size:8px;font-weight:700;margin-right:-5px;">U1</div><div style="width:26px;height:26px;border-radius:50%;border:2px solid #000;background:#444;display:flex;align-items:center;justify-content:center;font-size:8px;font-weight:700;margin-right:-5px;">U2</div><div style="width:26px;height:26px;border-radius:50%;border:2px solid #000;background:#555;display:flex;align-items:center;justify-content:center;font-size:8px;font-weight:700;">U3</div></div><div><div style="font-size:18px;font-weight:900;">25+</div><div style="font-size:8px;text-transform:uppercase;color:rgba(255,255,255,.38);letter-spacing:.15em;font-weight:700;">Happy Clients</div></div></div></div>
        <div class="badge">🚀 3+ YEARS EXPERTISE</div>
      </div>
    </div>
  </section>
  <style>@keyframes bba{0%,100%{transform:scaleY(1)}50%{transform:scaleY(1.9)}}</style>

  <!-- STATS BAR -->
  <div class="sbar">
    <div class="sbar-in">
      <div class="si"><span class="nv">25+</span><span class="lv">Satisfied Clients</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">98%</span><span class="lv">Delivery Rate</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">3+</span><span class="lv">Years Expertise</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">15+</span><span class="lv">Projects Shipped</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">24h</span><span class="lv">Response Time</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">4.9★</span><span class="lv">Fiverr Rating</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">25+</span><span class="lv">Satisfied Clients</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">98%</span><span class="lv">Delivery Rate</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">3+</span><span class="lv">Years Expertise</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">15+</span><span class="lv">Projects Shipped</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">24h</span><span class="lv">Response Time</span></div><div class="sdot">·</div>
      <div class="si"><span class="nv">4.9★</span><span class="lv">Fiverr Rating</span></div><div class="sdot">·</div>
    </div>
  </div>

  <!-- ABOUT -->
  <section class="about">
    <div class="about-grid">
      <div style="position:relative;" class="rvl">
        <div class="aim"><img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=1470" alt="Team"></div>
        <div class="ais"><img src="https://images.unsplash.com/photo-1600880292203-757bb62b4baf?q=80&w=1470" alt="Working"></div>
      </div>
      <div class="rvr">
        <span class="tag">WHO WE ARE</span>
        <h2 class="a-h2">We don't just build websites — we engineer digital growth engines.</h2>
        <p class="a-desc">WebEnarly is a premium web design & development studio based in Bangladesh, delivering for brands across the US, UK, Germany, and beyond. We specialise in WordPress, WooCommerce, Elementor, JetEngine, and conversion-first design — with a bias toward measurable outcomes.</p>
        <div class="stats3">
          <div><div class="s3n">5<span style="color:#d8ff30;">+</span></div><div class="s3l">Years in the Field</div></div>
          <div><div class="s3n" style="color:#d8ff30;">150<span style="color:#d8ff30;">+</span></div><div class="s3l">Projects Delivered</div></div>
          <div><div class="s3n" style="color:#cde95e;">250<span style="color:#d8ff30;">+</span></div><div class="s3l">Brands Served</div></div>
        </div>
        <a class="arr-link" href="#" onclick="go('contact');return false;">Start Working Together <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg></a>
      </div>
    </div>
  </section>

  <!-- SERVICES -->
  <section class="svc-sec">
    <div class="sec-h rv">
      <span class="tag">WHAT WE BUILD</span>
      <h2 class="sh2">Premium Digital Services</h2>
      <p class="sdesc">From concept to conversion — every deliverable engineered for performance, not just aesthetics.</p>
    </div>
    <div class="svc-wrap">
      <div class="sg">
        <div class="sc rvs"><img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">①</div><div class="sc-body"><span class="sc-num">01</span><div class="sc-n">WordPress Development</div><div class="sc-d">Bespoke WordPress builds using Elementor, JetEngine, and WooCommerce — architected for speed, SEO, and scale.</div></div></div>
        <div class="sc rvs" style="transition-delay:.08s"><img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">②</div><div class="sc-body"><span class="sc-num">02</span><div class="sc-n">WooCommerce Stores</div><div class="sc-d">Revenue-engineered eCommerce builds. Product filters, smart checkout, and UX that converts browsers into buyers.</div></div></div>
        <div class="sc rvs" style="transition-delay:.16s"><img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">③</div><div class="sc-body"><span class="sc-num">03</span><div class="sc-n">UI/UX Web Design</div><div class="sc-d">Conversion-optimised interfaces for Wix, Squarespace, and custom stacks. Every pixel earns its place.</div></div></div>
        <div class="sc rvs" style="transition-delay:.04s"><img src="https://images.unsplash.com/photo-1572177812156-58036aae439c?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">④</div><div class="sc-body"><span class="sc-num">04</span><div class="sc-n">Technical SEO</div><div class="sc-d">On-page, technical, and structured data optimisation that pushes your site to page one — and keeps it there.</div></div></div>
        <div class="sc rvs" style="transition-delay:.12s"><img src="https://images.unsplash.com/photo-1559028012-481c04fa702d?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">⑤</div><div class="sc-body"><span class="sc-num">05</span><div class="sc-n">High-Impact Landing Pages</div><div class="sc-d">Lead-gen pages engineered to capture intent and drive actions — built for campaigns, not vanity metrics.</div></div></div>
        <div class="sc rvs" style="transition-delay:.20s"><img src="https://images.unsplash.com/photo-1529336953121-ad5a0d43d0d2?q=80" alt=""><div class="sc-ov"></div><div class="sc-hov"></div><div class="sc-ico">⑥</div><div class="sc-body"><span class="sc-num">06</span><div class="sc-n">Brand Identity Systems</div><div class="sc-d">Visual identity built for authority. Logo, color systems, typography, and brand guidelines that command trust.</div></div></div>
      </div>
    </div>
  </section>

  <!-- WHY US -->
  <section class="why">
    <div style="max-width:1200px;margin:0 auto;" class="rv">
      <div style="text-align:center;margin-bottom:56px;position:relative;z-index:1;">
        <div class="pill" style="margin-bottom:14px;">Why WebEnarly</div>
        <h2 style="font-size:clamp(28px,5vw,52px);font-weight:900;letter-spacing:-.05em;margin-bottom:12px;">The Standard Others Benchmark Against</h2>
        <p style="color:rgba(255,255,255,.52);max-width:520px;margin:0 auto;font-size:15px;">We don't just deliver websites. We deliver outcomes — at a standard your clients will remember and your competitors will envy.</p>
      </div>
    </div>
    <div class="wg">
      <div class="wc rv"><div class="wi"><svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 3l7 3v5c0 4.2-2.7 7.8-7 10-4.3-2.2-7-5.8-7-10V6l7-3z"/><path stroke-linecap="round" stroke-linejoin="round" d="M9.5 12.5l1.7 1.7 3.8-4.2"/></svg></div><div class="wn">01</div><h3>Conversion-First Design</h3><p>Every layout decision backed by UX principles that turn visitors into buyers, not just admirers.</p></div>
      <div class="wc rv" style="transition-delay:.1s"><div class="wi"><svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M13 2L6 13h5l-1 9 7-11h-5l1-9z"/></svg></div><div class="wn">02</div><h3>Precision-Engineered Speed</h3><p>Sub-3-second loads as standard. Performance isn't an add-on — it's baked into every line we ship.</p></div>
      <div class="wc rv" style="transition-delay:.2s"><div class="wi"><svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M14.5 4.5c2.8.3 5.2 2.7 5.5 5.5-1 3.2-3.4 5.6-6.6 6.6l-3.3-3.3c1-3.2 3.4-5.6 6.6-6.6z"/><path stroke-linecap="round" stroke-linejoin="round" d="M9.8 14.2l-3.5 1 1-3.5M12.5 11.5l.01.01"/></svg></div><div class="wn">03</div><h3>On-Time, Every Time</h3><p>Deadlines aren't suggestions. Our system ensures delivery that respects your timeline and budget.</p></div>
      <div class="wc rv" style="transition-delay:.3s"><div class="wi"><svg viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M7 4h10l4 5-9 11L3 9l4-5z"/><path stroke-linecap="round" stroke-linejoin="round" d="M3 9h18M9 4l3 16M15 4l-3 16"/></svg></div><div class="wn">04</div><h3>Post-Delivery Support</h3><p>We don't disappear after launch. 30-day free support on every project, with ongoing retainer options.</p></div>
    </div>
  </section>

  <!-- PORTFOLIO PREVIEW -->
  <section class="pp">
    <div class="sec-h rv">
      <span class="tag">RECENT WORK</span>
      <h2 class="sh2">Built to Perform</h2>
      <p class="sdesc">A curated selection of projects where design met strategy and revenue followed.</p>
    </div>
    <div class="pg3">
      <div class="pi rvs"><img src="https://images.unsplash.com/photo-1600607686527-6fb886090705" alt=""><div class="pi-ov"></div><div class="pi-info"><div class="pi-cat">WordPress</div><div class="pi-t">eCommerce Revenue Engine</div></div></div>
      <div class="pi rvs" style="transition-delay:.1s"><img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71" alt=""><div class="pi-ov"></div><div class="pi-info"><div class="pi-cat">Web Design</div><div class="pi-t">Corporate Authority Site</div></div></div>
      <div class="pi rvs" style="transition-delay:.2s"><img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c" alt=""><div class="pi-ov"></div><div class="pi-info"><div class="pi-cat">WooCommerce</div><div class="pi-t">Premium Store Rebuild</div></div></div>
    </div>
    <div style="text-align:center;margin-top:44px;" class="rv">
      <a class="btn-s" href="#" onclick="go('portfolio');return false;">View All Case Studies →</a>
    </div>
  </section>

  <!-- TESTIMONIALS -->
  <section class="testi">
    <div class="sec-h rv">
      <span class="tag">CLIENT PROOF</span>
      <h2 class="sh2">Results, Not Just Reviews</h2>
      <p class="sdesc">Real outcomes from real clients. Here's what happens when quality meets execution.</p>
    </div>
    <div class="t-track">
      <div class="t-in">
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"WebWe had such a great experience working with Shihab on our website. He is easy to communicate with, patient with our ideas, and really took the time to make sure everything came together the way we wanted. The website turned out beautiful, clean, and easy to use. It feels like it truly represents our business, and we’re really happy with the final result. We’re grateful for all the time and care he put into it and would definitely recommend them to anyone looking for help with their website."</p><div class="ta"><h4>Sarah Johnson</h4><p>CEO, TechFlow Inc.</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"The WordPress site loads in under 2 seconds and looks premium on every device. Our bounce rate dropped by 40%. Genuinely best-in-class execution from start to finish."</p><div class="ta"><h4>Michael Weber</h4><p>Founder, StartUp X Germany</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"Best web investment we made in 2026. The SEO architecture they built got us ranking page one for 12 keywords within 90 days. No fluff — just measurable outcomes."</p><div class="ta"><h4>Emma Schreiber</h4><p>Marketing Director, EuroRetail</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"Exceptional Elementor & JetEngine work. They understood our brand vision, delivered ahead of schedule, and the communication was flawless. Truly premium service."</p><div class="ta"><h4>David Lee</h4><p>Product Manager, DataCorp</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"We hired 3 agencies before WebEnarly. None came close to this quality. They're now our permanent development partner for all web projects globally."</p><div class="ta"><h4>Lisa Müller</h4><p>Owner, FashionHub Berlin</p></div></div>
        <!-- duplicate for seamless loop -->
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"WebEnarly rebuilt our WooCommerce store from scratch. Within 60 days, our conversion rate tripled. The attention to UX detail was exceptional."</p><div class="ta"><h4>Sarah Johnson</h4><p>CEO, TechFlow Inc.</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"The WordPress site loads in under 2 seconds and looks premium on every device. Our bounce rate dropped by 40%. Genuinely best-in-class execution."</p><div class="ta"><h4>Michael Weber</h4><p>Founder, StartUp X Germany</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"Best web investment we made in 2026. The SEO architecture got us ranking page one for 12 keywords in 90 days. No fluff — just results."</p><div class="ta"><h4>Emma Schreiber</h4><p>Marketing Director, EuroRetail</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"Exceptional Elementor & JetEngine work. They understood our brand vision and delivered ahead of schedule. Truly premium service."</p><div class="ta"><h4>David Lee</h4><p>Product Manager, DataCorp</p></div></div>
        <div class="tc"><div class="tstars">★★★★★</div><p class="tq">"We hired 3 agencies before WebEnarly. None came close. They're now our permanent development partner for all projects."</p><div class="ta"><h4>Lisa Müller</h4><p>Owner, FashionHub Berlin</p></div></div>
      </div>
    </div>
  </section>

  <!-- FAQ -->
  <section class="faq">
    <div class="faq-g">
      <div class="rvl">
        <span class="tag">FAQ</span>
        <h2>Straight Answers to Smart Questions</h2>
        <p>No vague estimates. No hidden fees. Just clarity before you commit.</p>
        <a class="btn-s" style="display:inline-flex;align-items:center;gap:7px;padding:11px 22px;border-radius:9999px;font-size:13px;" href="#" onclick="go('contact');return false;">Book a Discovery Call →</a>
      </div>
      <div class="rvr">
        <div class="fi op"><div class="fh" onclick="tfaq(this)"><h3>How do we kick off a project together?</h3><div class="ft">+</div></div><div class="fb"><p>We start with a short discovery call to understand your goals, stack, and timeline. From there we scope the project, align expectations, and kick off within 48 hours of contract sign-off.</p></div></div>
        <div class="fi"><div class="fh" onclick="tfaq(this)"><h3>How is pricing structured?</h3><div class="ft">+</div></div><div class="fb"><p>Fixed-price packages for defined scopes and retainer-based models for ongoing work. Every quote is transparent — you'll see exactly what you're paying for before committing.</p></div></div>
        <div class="fi"><div class="fh" onclick="tfaq(this)"><h3>What's a realistic delivery timeline?</h3><div class="ft">+</div></div><div class="fb"><p>A standard WordPress build takes 1–2 weeks. Complex WooCommerce or custom projects run 3–4 weeks. We set milestones upfront and never move the goalposts without your approval.</p></div></div>
        <div class="fi"><div class="fh" onclick="tfaq(this)"><h3>Do you support the site after launch?</h3><div class="ft">+</div></div><div class="fb"><p>Every project includes 30 days of free post-launch support. For ongoing maintenance — updates, security, performance monitoring — we offer flexible monthly retainer plans.</p></div></div>
        <div class="fi"><div class="fh" onclick="tfaq(this)"><h3>Do you work with international clients?</h3><div class="ft">+</div></div><div class="fb"><p>Yes — we serve clients across the USA, UK, Germany, and beyond. We communicate fluently in English and German, and adapt to your timezone for key calls and deliveries.</p></div></div>
      </div>
    </div>
  </section>

  <!-- CTA -->
  <section class="cta-s">
    <div class="cta-in rv">
      <div class="pill" style="margin-bottom:12px;">READY TO BUILD?</div>
      <h2>Turn Your Vision Into a Revenue-Generating Website</h2>
      <p>Join 250+ brands that trusted WebEnarly to build their digital presence in 2026. Let's make yours next — and make it exceptional.</p>
      <div class="cta-btns">
        <a class="btn-p" href="#" onclick="go('contact');return false;">Start Your Project Today</a>
        <a class="btn-s" href="#" onclick="go('pricing');return false;">Explore Pricing Plans</a>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="fp-row">
      <div class="fpc"><div class="fn" style="color:#4285F4;">WordPress</div><div class="fr">Expert Developer</div></div>
      <div class="fpc"><div class="fn" style="color:#96588a;">WooCommerce</div><div class="fr">Certified Builder</div></div>
      <div class="fpc"><div class="fn" style="color:#ff4fa0;">Dribbble</div><div class="fr">Top Designer</div></div>
      <div class="fpc"><div class="fn" style="color:#2d7cff;">Fiverr</div><div class="fr">Level 2 Seller</div></div>
      <div class="fpc"><div class="fn" style="color:#d8ff30;">Elementor</div><div class="fr">Pro Expert</div></div>
      <div class="fpc"><div class="fn"><span style="color:#4285F4">G</span><span style="color:#EA4335">o</span><span style="color:#FBBC05">o</span><span style="color:#4285F4">g</span><span style="color:#34A853">l</span><span style="color:#EA4335">e</span></div><div class="fr">Reviewed ★★★★★</div></div>
    </div>
    <div class="footer-cols">
      <div class="fc fc-brand"><a href="#" onclick="go('home');return false;">WebEnarly</a><p>Transforming ambitious brands into premium digital experiences since 2019. WordPress, WooCommerce, and conversion-focused design — built to outperform.</p><div class="socials"><a class="sa" href="#"><svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"/></svg></a><a class="sa" href="#"><svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="2" width="20" height="20" rx="5"/><circle cx="12" cy="12" r="4"/></svg></a><a class="sa" href="#"><svg width="14" height="14" fill="none" stroke="currentColor" stroke-width="2"><path d="M16 8a6 6 0 0 1 6 6v7h-4"/><rect x="2" y="9" width="4" height="12"/><circle cx="4" cy="4" r="2"/></svg></a></div></div>
      <div class="fc"><h3>Navigation</h3><ul><li><a href="#" onclick="go('home');return false;">Home</a></li><li><a href="#" onclick="go('portfolio');return false;">Portfolio</a></li><li><a href="#" onclick="go('services');return false;">Services</a></li><li><a href="#" onclick="go('pricing');return false;">Pricing</a></li><li><a href="#" onclick="go('contact');return false;">Contact</a></li></ul></div>
      <div class="fc"><h3>Services</h3><ul><li><a href="#" onclick="go('services');return false;">WordPress Dev</a></li><li><a href="#" onclick="go('services');return false;">WooCommerce</a></li><li><a href="#" onclick="go('services');return false;">UI/UX Design</a></li><li><a href="#" onclick="go('services');return false;">Technical SEO</a></li><li><a href="#" onclick="go('services');return false;">Landing Pages</a></li></ul></div>
      <div class="fc fc-news"><h3>Stay Ahead</h3><p>Web design insights and exclusive offers, monthly.</p><input type="email" placeholder="your@email.com"><button>Subscribe Free</button></div>
    </div>
    <div class="f-bot"><p>© 2026 WebEnarly. All rights reserved.</p><div class="f-bot-links"><a href="#">Privacy Policy</a><a href="#">Terms</a></div><button class="stb" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button></div>
  </footer>
</div><!-- /home -->

<!-- ═══ PORTFOLIO ═══ -->
<div class="pg" id="pg-portfolio">
  <div class="port-page">
    <div class="port-hdr rv">
      <div class="pill" style="margin-bottom:14px;">REAL PROJECT SHOWCASE</div>
      <h1 style="font-size:clamp(34px,5vw,58px);font-weight:900;letter-spacing:-.04em;margin:14px 0 10px;">Work That Moves the Needle</h1>
      <p style="font-size:16px;color:rgba(255,255,255,.58);">Every project built with a singular focus: measurable performance, not just beautiful pixels.</p>
      <div class="port-filters">
        <button class="fbt on">All Projects</button>
        <button class="fbt">WordPress</button>
        <button class="fbt">WooCommerce</button>
        <button class="fbt">Web Design</button>
        <button class="fbt">Landing Pages</button>
        <button class="fbt">Branding</button>
      </div>
    </div>
    <div class="port-grid-full">
      <div class="pfc rvs"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1554224155-8d04cb21cd6c?q=80&w=1400" alt=""><span class="pb">WordPress</span><span class="py">2025</span></div><div class="pfc-body"><h3>eCommerce Revenue Engine</h3><p class="pcl">Confidential Retail Client</p><p>Full WooCommerce rebuild with JetSmartFilters, custom product architecture, and checkout optimisation.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">Retail / eCommerce</div></div><div class="pmi"><div class="k">Duration</div><div class="v">3 weeks</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">3x conversion rate</div></div><div class="pmi"><div class="k">Stack</div><div class="v">WP + WooCommerce</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>

      <div class="pfc rvs" style="transition-delay:.1s"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1460925895917-afdab827c52f?q=80&w=1400" alt=""><span class="pb">Web Design</span><span class="py">2025</span></div><div class="pfc-body"><h3>Corporate Authority Site</h3><p class="pcl">B2B Software Provider</p><p>A modular 12-page WordPress site with SEO foundations, campaign-ready pages, and strong conversion flow.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">SaaS / B2B</div></div><div class="pmi"><div class="k">Duration</div><div class="v">2 weeks</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">2.1x demo requests</div></div><div class="pmi"><div class="k">Stack</div><div class="v">WP + Elementor</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>

      <div class="pfc rvs" style="transition-delay:.2s"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1545239351-1141bd82e8a6?q=80&w=1400" alt=""><span class="pb">Branding</span><span class="py">2025</span></div><div class="pfc-body"><h3>Premium Brand Refresh</h3><p class="pcl">Interior & Lifestyle Co.</p><p>Full identity refresh across logo system, visual language, and brand communication for premium market positioning.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">Lifestyle / Retail</div></div><div class="pmi"><div class="k">Duration</div><div class="v">4 weeks</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">63% more inquiries</div></div><div class="pmi"><div class="k">Deliverables</div><div class="v">Full brand kit</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>

      <div class="pfc rvs"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80&w=1400" alt=""><span class="pb">WooCommerce</span><span class="py">2025</span></div><div class="pfc-body"><h3>Fashion Store Overhaul</h3><p class="pcl">European Fashion Brand</p><p>WooCommerce fashion store with custom filtering, multilingual support, and GDPR-compliant checkout.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">Fashion / EU Market</div></div><div class="pmi"><div class="k">Duration</div><div class="v">3 weeks</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">48% more sales</div></div><div class="pmi"><div class="k">Stack</div><div class="v">WooCommerce + WPML</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>

      <div class="pfc rvs" style="transition-delay:.1s"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1512941937669-90a1b58e7e9c?q=80&w=1400" alt=""><span class="pb">Landing Page</span><span class="py">2026</span></div><div class="pfc-body"><h3>Lead-Gen Landing Machine</h3>Lead-Gen Landing Machine</h3><p class="pcl">Health & Wellness Brand</p><p>High-intent landing page with video hero, social proof, and A/B-tested CTA structure. Built in 5 days.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">Health / Wellness</div></div><div class="pmi"><div class="k">Duration</div><div class="v">5 days</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">340 leads/week</div></div><div class="pmi"><div class="k">Stack</div><div class="v">Elementor Pro</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>

      <div class="pfc rvs" style="transition-delay:.2s"><div class="pfc-img"><img src="https://images.unsplash.com/photo-1552664730-d307ca884978?q=80&w=1400" alt=""><span class="pb">WordPress</span><span class="py">2026</span></div><div class="pfc-body"><h3>Legal Firm Digital Authority</h3><p class="pcl">Professional Legal Services</p><p>Trust-first website with comprehensive practice pages, attorney profiles, and Google Business optimisation.</p><div class="pmeta"><div class="pmi"><div class="k">Sector</div><div class="v">Professional Services</div></div><div class="pmi"><div class="k">Duration</div><div class="v">2 weeks</div></div><div class="pmi"><div class="k">Outcome</div><div class="v">3.2x profile views</div></div><div class="pmi"><div class="k">Stack</div><div class="v">WP + Yoast</div></div></div><div class="pcbtns"><button class="pcb1">View Case Study</button><button class="pcb2">Start Similar</button></div></div></div>
    </div>
    <div style="text-align:center;margin-top:52px;" class="rv"><a class="btn-p" href="#" onclick="go('contact');return false;">Start Your Project Now</a></div>
  </div>
  <footer><div class="footer-cols" style="max-width:1200px;margin:0 auto 32px;"><div class="fc fc-brand"><a href="#" onclick="go('home');return false;">WebEnarly</a><p>Premium web design & development — built for outcomes, not just aesthetics.</p></div><div class="fc"><h3>Pages</h3><ul><li><a href="#" onclick="go('home');return false;">Home</a></li><li><a href="#" onclick="go('portfolio');return false;">Portfolio</a></li><li><a href="#" onclick="go('services');return false;">Services</a></li><li><a href="#" onclick="go('pricing');return false;">Pricing</a></li></ul></div><div class="fc fc-news"><h3>Stay Updated</h3><p>Web tips monthly.</p><input type="email" placeholder="your@email.com"><button>Subscribe</button></div></div><div class="f-bot"><p>© 2026 WebEnarly. All rights reserved.</p><div class="f-bot-links"><a href="#">Privacy</a><a href="#">Terms</a></div><button class="stb" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button></div></footer>
</div><!-- /portfolio -->

<!-- SERVICES PAGE -->
<div class="pg" id="pg-services">
  <div class="svc-page">
    <div class="svc-p-hero rv">
      <div class="pill" style="margin-bottom:14px;">SERVICE ARCHITECTURE</div>
      <h1 style="font-size:clamp(36px,5vw,58px);font-weight:900;letter-spacing:-.05em;margin:14px 0 14px;">Build With <span style="background:linear-gradient(to right,#fff,#f7ffc5,#d8ff30);-webkit-background-clip:text;-webkit-text-fill-color:transparent;">Premium Services</span></h1>
      <p style="font-size:16px;color:rgba(255,255,255,.58);max-width:560px;margin:0 auto;">Innovative solutions for complex challenges — engineered to grow your brand in 2026 and beyond.</p>
    </div>
    <div class="svc-tabs">
      <button class="stab on"><div class="stn">WordPress & Dev</div><div class="stc">4 active services</div></button>
      <button class="stab"><div class="stn">Design & Brand</div><div class="stc">3 active services</div></button>
      <button class="stab"><div class="stn">Growth & SEO</div><div class="stc">3 active services</div></button>
    </div>
    <div class="svc-full-g">
      <div class="sfc rvs"><div class="sfc-img"><img src="https://images.unsplash.com/photo-1542744173-8e7e53415bb0?q=80&w=1200" alt=""><span class="stl">7–14 days to launch</span></div><div class="sfc-body"><h3>Custom WordPress Development</h3><p>Full-stack WordPress builds — custom theme, Elementor Pro, JetEngine, and performance optimisation baked in from day one.</p><div class="smg"><div class="smb"><div class="k">Best For</div><div class="v">Business & portfolio sites</div></div><div class="smb"><div class="k">Pricing</div><div class="v">Fixed per project</div></div></div><div class="scbtns"><button class="scb1">View Details</button><button class="scb2">Workflow Preview</button><button class="scb2" onclick="go('contact');return false;">Start This</button></div></div></div>
      <div class="sfc rvs" style="transition-delay:.08s"><div class="sfc-img"><img src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?q=80&w=1200" alt=""><span class="stl">10–21 days</span></div><div class="sfc-body"><h3>WooCommerce Store Build</h3><p>Revenue-engineered eCommerce builds with JetSmartFilters, custom checkout flows, and payment gateway integration.</p><div class="smg"><div class="smb"><div class="k">Best For</div><div class="v">eCommerce brands</div></div><div class="smb"><div class="k">Pricing</div><div class="v">Scoped per store</div></div></div><div class="scbtns"><button class="scb1">View Details</button><button class="scb2">Workflow Preview</button><button class="scb2" onclick="go('contact');return false;">Start This</button></div></div></div>
      <div class="sfc rvs"><div class="sfc-img"><img src="https://images.unsplash.com/photo-1559028012-481c04fa702d?q=80&w=1200" alt=""><span class="stl">3–7 days</span></div><div class="sfc-body"><h3>High-Conversion Landing Pages</h3><p>Campaign-specific pages built for a single purpose: generating qualified leads. CRO-optimised from headline to CTA button.</p><div class="smg"><div class="smb"><div class="k">Best For</div><div class="v">Ad campaigns & launches</div></div><div class="smb"><div class="k">Pricing</div><div class="v">Per page</div></div></div><div class="scbtns"><button class="scb1">View Details</button><button class="scb2">Workflow Preview</button><button class="scb2" onclick="go('contact');return false;">Start This</button></div></div></div>
      <div class="sfc rvs" style="transition-delay:.08s"><div class="sfc-img"><img src="https://images.unsplash.com/photo-1572177812156-58036aae439c?q=80&w=1200" alt=""><span class="stl">2–3 weeks sprint</span></div><div class="sfc-body"><h3>Technical SEO Sprint</h3><p>On-page architecture, technical audit, schema markup, and content structure — everything search engines reward in 2026.</p><div class="smg"><div class="smb"><div class="k">Best For</div><div class="v">Sites with low organic reach</div></div><div class="smb"><div class="k">Pricing</div><div class="v">Sprint-based</div></div></div><div class="scbtns"><button class="scb1">View Details</button><button class="scb2">Workflow Preview</button><button class="scb2" onclick="go('contact');return false;">Start This</button></div></div></div>
    </div>
    <div style="text-align:center;margin-top:52px;" class="rv"><a class="btn-p" href="#" onclick="go('contact');return false;">Book a Discovery Call</a></div>
  </div>
  <footer><div class="footer-cols" style="max-width:1200px;margin:0 auto 32px;"><div class="fc fc-brand"><a href="#" onclick="go('home');return false;">WebEnarly</a><p>Premium WordPress & WooCommerce development for growing brands worldwide.</p></div><div class="fc"><h3>Pages</h3><ul><li><a href="#" onclick="go('home');return false;">Home</a></li><li><a href="#" onclick="go('services');return false;">Services</a></li><li><a href="#" onclick="go('pricing');return false;">Pricing</a></li><li><a href="#" onclick="go('contact');return false;">Contact</a></li></ul></div><div class="fc fc-news"><h3>Updates</h3><p>Web insights monthly.</p><input type="email" placeholder="your@email.com"><button>Subscribe</button></div></div><div class="f-bot"><p>© 2026 WebEnarly.</p><div class="f-bot-links"><a href="#">Privacy</a><a href="#">Terms</a></div><button class="stb" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button></div></footer>
</div><!-- /services -->

<!-- PRICING PAGE -->
<div class="pg" id="pg-pricing">
  <section class="pricing-pg">
    <div class="price-hero rv">
      <span class="tag">PREMIUM PRICING PLANS</span>
      <h1>Choose the Plan That Matches Your Ambition</h1>
      <p style="font-size:15px;color:rgba(255,255,255,.58);max-width:520px;margin:0 auto 0;">No hidden costs. No vague estimates. Just transparent pricing that respects your time and business.</p>
      <div class="ptabs">
        <button class="ptb on">Website</button>
        <button class="ptb">WooCommerce</button>
        <button class="ptb">Landing Page</button>
        <button class="ptb">Brand Identity</button>
        <button class="ptb">SEO Sprint</button>
      </div>
    </div>
    <div class="price-cards">
      <div class="prcc rvs">
        <div class="prcc-glow"></div>
        <div class="pplan">Launch Package</div>
        <div class="pdesc">8-page website — clean design, core business pages, and everything to go live with confidence.</div>
        <div class="pbox"><div class="porig">$2,420</div><div class="pnrow"><span class="pnum">$1,450</span><span class="pbdge">40% OFF</span></div><div class="pper">one-time payment</div></div>
        <div class="pfeats">
          <div class="pfeat"><div class="pchk">✓</div><span>Custom UI/UX Design</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Fully Responsive Layout</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>8 Core Business Pages</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>On-Page SEO Foundation</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Google Analytics 4 Setup</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Contact Form + Map</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Speed Optimisation</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>30 Days Post-Launch Support</span></div>
        </div>
        <button class="pcta ghost" onclick="go('contact');return false;">Get Started →</button>
        <div class="pnote">Custom Scope Available</div>
      </div>
      <div class="prcc feat rvs" style="transition-delay:.1s">
        <div class="prcc-glow"></div>
        <div class="pop-badge">MOST POPULAR</div>
        <div class="pplan">Growth Package</div>
        <div class="pdesc">Design + development + conversion optimisation for brands that compete to win.</div>
        <div class="pbox"><div class="porig">$3,970</div><div class="pnrow"><span class="pnum">$2,380</span><span class="pbdge">40% OFF</span></div><div class="pper">one-time payment</div></div>
        <div class="pfeats">
          <div class="pfeat"><div class="pchk">✓</div><span>Everything in Launch</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Full CMS Integration</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Advanced Performance Tuning</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>eCommerce / WooCommerce</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Social Media Integration</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Security Hardening</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>2 Months Support</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Priority WhatsApp Access</span></div>
        </div>
        <button class="pcta main" onclick="go('contact');return false;">Start Free Consultation →</button>
        <div class="pnote">Custom Scope Available</div>
      </div>
      <div class="prcc rvs" style="transition-delay:.2s">
        <div class="prcc-glow"></div>
        <div class="pplan">Signature Package</div>
        <div class="pdesc">Premium architecture with scale-ready infrastructure — for brands that don't compromise.</div>
        <div class="pbox"><div class="porig">$5,535</div><div class="pnrow"><span class="pnum">$3,320</span><span class="pbdge">40% OFF</span></div><div class="pper">one-time payment</div></div>
        <div class="pfeats">
          <div class="pfeat"><div class="pchk">✓</div><span>Everything in Growth</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Advanced User Tracking</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Custom Animations & Micro-UX</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Multilingual (EN / DE / +)</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>A/B Testing Integration</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Cloudinary Media Optimisation</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>3 Months Maintenance</span></div>
          <div class="pfeat"><div class="pchk">✓</div><span>Dedicated Account Management</span></div>
        </div>
        <button class="pcta ghost" onclick="go('contact');return false;">Book Consultation →</button>
        <div class="pnote">Custom Scope Available</div>
      </div>
    </div>
    <div class="ptrust rv">
      <div class="trit"><span class="trck">✓</span><span>Fixed one-time pricing</span></div>
      <div class="trit"><span class="trck">✓</span><span>Clear project scope upfront</span></div>
      <div class="trit"><span class="trck">✓</span><span>Direct WhatsApp support</span></div>
      <div class="trit"><span class="trck">✓</span><span>Trusted by brands worldwide</span></div>
    </div>
    <div style="max-width:1200px;margin:24px auto 0;background:linear-gradient(to right,#102010,#163014,#214211);border:1px solid rgba(216,255,48,.16);border-radius:18px;padding:26px 28px;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:18px;position:relative;z-index:1;" class="rv">
      <div><p style="font-size:9px;font-weight:700;letter-spacing:.18em;text-transform:uppercase;color:#d8ff30;">Custom Quote</p><h3 style="font-size:20px;font-weight:700;margin:7px 0 5px;">Build Your Own Package</h3><p style="font-size:13px;color:rgba(255,255,255,.58);">Tell us exactly what you need — we'll price it precisely, with no guesswork.</p></div>
      <a class="btn-p" style="font-size:13px;padding:13px 26px;" href="#" onclick="go('contact');return false;">Get a Custom Quote</a>
    </div>
  </section>
  <footer><div class="footer-cols" style="max-width:1200px;margin:0 auto 32px;"><div class="fc fc-brand"><a href="#" onclick="go('home');return false;">WebEnarly</a><p>Premium web design & development — built for outcomes.</p></div><div class="fc"><h3>Pages</h3><ul><li><a href="#" onclick="go('home');return false;">Home</a></li><li><a href="#" onclick="go('services');return false;">Services</a></li><li><a href="#" onclick="go('contact');return false;">Contact</a></li></ul></div><div class="fc fc-news"><h3>Updates</h3><p>Latest offers monthly.</p><input type="email" placeholder="your@email.com"><button>Subscribe</button></div></div><div class="f-bot"><p>© 2026 WebEnarly.</p><div class="f-bot-links"><a href="#">Privacy</a><a href="#">Terms</a></div><button class="stb" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button></div></footer>
</div><!-- /pricing -->

<!-- CONTACT PAGE -->
<div class="pg" id="pg-contact">
  <section class="contact-pg">
    <div class="ct-hero">
      <div class="ct-hero-grid rv">
        <div>
          <div class="pill" style="margin-bottom:14px;">Contact WebEnarly</div>
          <h1 style="font-size:clamp(30px,4.2vw,50px);font-weight:900;letter-spacing:-.05em;margin:14px 0 14px;">A More Strategic Way to Start Your Project</h1>
          <p style="font-size:15px;color:rgba(255,255,255,.58);max-width:460px;line-height:1.7;">Share your goals and current blockers. We respond with a direction that is more strategic and more premium — from the very first message.</p>
          <div class="ct-tags">
            <span class="cttag">WordPress Sites</span>
            <span class="cttag">WooCommerce Stores</span>
            <span class="cttag">Landing Pages</span>
            <span class="cttag">Brand Systems</span>
          </div>
        </div>
        <div class="ct-vis">
          <div class="ct-orb">
            <div class="ct-orb-in"><div class="ctol">Premium Intake</div><div class="ctog">A+</div></div>
          </div>
          <div class="ctfl f1">Faster Replies</div>
          <div class="ctfl f2">Clearer Scope</div>
          <div class="ctfl f3">Premium Output</div>
        </div>
      </div>
    </div>
    <div class="ct-body">
      <div>
        <div class="ct-steps rvl">
          <div class="ct-step"><div class="csn">01</div><div><h3>Brief Review</h3><p>We study your current position, goals, and blockers before we reply.</p></div></div>
          <div class="ct-step"><div class="csn">02</div><div><h3>Fit Assessment</h3><p>We align scope, timeline, and output expectations around premium delivery standards.</p></div></div>
          <div class="ct-step"><div class="csn">03</div><div><h3>Fast Proposal</h3><p>You receive a clear strategic proposal — not a vague generic estimate.</p></div></div>
        </div>
        <div class="ci-items rvl">
          <div class="cii"><div class="cii-ico"><svg viewBox="0 0 24 24" fill="none" stroke="#d8ff30" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg></div><div><h4>Location</h4><p>Bangladesh — Serving brands globally</p></div></div>
          <div class="cii"><div class="cii-ico" style="background:rgba(33,66,17,.85);"><svg viewBox="0 0 24 24" fill="none" stroke="#d8ff30" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z"/></svg></div><div><h4>Fiverr / WhatsApp</h4><p>fiverr.com/webenarly — fastest for urgent queries</p></div></div>
          <div class="cii"><div class="cii-ico" style="background:rgba(216,255,48,.08);"><svg viewBox="0 0 24 24" fill="none" stroke="#d8ff30" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75"/></svg></div><div><h4>Email</h4><p>hello@webenarly.com</p></div></div>
        </div>
      </div>
      <div class="ct-form rvr">
        <div class="form-hdr">
          <span class="tag">PROJECT BRIEF</span>
          <h2>Tell us what you want to build.</h2>
        </div>
        <div class="frow">
          <div class="fg"><label>Your Name</label><input type="text" placeholder="John Doe"></div>
          <div class="fg"><label>Email Address</label><input type="email" placeholder="john@example.com"></div>
        </div>
        <div class="fg"><label>Subject</label><input type="text" placeholder="WordPress eCommerce rebuild"></div>
        <div class="fg"><label>Your Message</label><textarea rows="5" placeholder="Tell us your goals, timeline, and the kind of premium output you are after..."></textarea></div>
        <div class="ctags-row">
          <span class="ctag2">Strategy-Led</span>
          <span class="ctag2">Fast Response</span>
          <span class="ctag2">Premium Execution</span>
        </div>
        <div class="form-foot">
          <p>Include your current site URL and rough timeline for faster, more tailored responses.</p>
          <button class="btn-p" style="font-size:13px;padding:13px 26px;border-radius:11px;">Send Message</button>
        </div>
      </div>
    </div>
  </section>
  <footer>
    <div class="footer-cols" style="max-width:1200px;margin:0 auto 32px;">
      <div class="fc fc-brand"><a href="#" onclick="go('home');return false;">WebEnarly</a><p>Premium WordPress and WooCommerce development. Every project is a commitment to excellence.</p></div>
      <div class="fc"><h3>Pages</h3><ul><li><a href="#" onclick="go('home');return false;">Home</a></li><li><a href="#" onclick="go('portfolio');return false;">Portfolio</a></li><li><a href="#" onclick="go('services');return false;">Services</a></li><li><a href="#" onclick="go('pricing');return false;">Pricing</a></li></ul></div>
      <div class="fc fc-news"><h3>Updates</h3><p>Web tips monthly.</p><input type="email" placeholder="your@email.com"><button>Subscribe</button></div>
    </div>
    <div class="f-bot"><p>© 2026 WebEnarly. All rights reserved.</p><div class="f-bot-links"><a href="#">Privacy</a><a href="#">Terms</a></div><button class="stb" onclick="window.scrollTo({top:0,behavior:'smooth'})">↑</button></div>
  </footer>
</div><!-- /contact -->

<script>
// CURSOR
const cur=document.getElementById('cur'),ring=document.getElementById('cur-ring');
let mx=0,my=0,rx=0,ry=0;
document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;cur.style.left=mx+'px';cur.style.top=my+'px';});
(function animR(){rx+=(mx-rx)*.11;ry+=(my-ry)*.11;ring.style.left=rx+'px';ring.style.top=ry+'px';requestAnimationFrame(animR);})();
document.querySelectorAll('a,button').forEach(el=>{
  el.addEventListener('mouseenter',()=>{cur.style.width='18px';cur.style.height='18px';ring.style.width='56px';ring.style.height='56px';});
  el.addEventListener('mouseleave',()=>{cur.style.width='10px';cur.style.height='10px';ring.style.width='36px';ring.style.height='36px';});
});

// PAGE NAV
function go(id){
  document.querySelectorAll('.pg').forEach(p=>p.classList.remove('on'));
  document.getElementById('pg-'+id).classList.add('on');
  document.querySelectorAll('.nl').forEach(a=>a.classList.remove('on'));
  const nl=document.getElementById('nl-'+id);
  if(nl)nl.classList.add('on');
  window.scrollTo({top:0,behavior:'smooth'});
  setTimeout(initRev,80);
}

// SCROLL REVEAL
function initRev(){
  const io=new IntersectionObserver(entries=>{
    entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('in');io.unobserve(e.target);}});
  },{threshold:.1,rootMargin:'0px 0px -36px 0px'});
  document.querySelectorAll('.pg.on .rv,.pg.on .rvl,.pg.on .rvr,.pg.on .rvs').forEach(el=>{
    el.classList.remove('in');io.observe(el);
  });
}
window.addEventListener('DOMContentLoaded',initRev);

// FAQ
function tfaq(head){
  const item=head.closest('.fi');
  const was=item.classList.contains('op');
  document.querySelectorAll('.fi').forEach(f=>f.classList.remove('op'));
  if(!was)item.classList.add('op');
}

// FILTER TABS
document.querySelectorAll('.port-filters').forEach(w=>{
  w.querySelectorAll('.fbt').forEach(b=>{b.addEventListener('click',function(){w.querySelectorAll('.fbt').forEach(x=>x.classList.remove('on'));this.classList.add('on');});});
});
document.querySelectorAll('.ptabs').forEach(w=>{
  w.querySelectorAll('.ptb').forEach(b=>{b.addEventListener('click',function(){w.querySelectorAll('.ptb').forEach(x=>x.classList.remove('on'));this.classList.add('on');});});
});
document.querySelectorAll('.svc-tabs').forEach(w=>{
  w.querySelectorAll('.stab').forEach(b=>{b.addEventListener('click',function(){w.querySelectorAll('.stab').forEach(x=>x.classList.remove('on'));this.classList.add('on');});});
});
</script>
</body>
</html>
