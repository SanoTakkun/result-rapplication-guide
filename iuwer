<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover" />
  <meta name="theme-color" content="#d71920" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
  <meta name="mobile-web-app-capable" content="yes" />
  <title>Akiba Guild App Game</title>
  <style>
    :root {
      --red: #d71920;
      --deep-red: #9f1017;
      --pink: #ff7eb6;
      --soft-pink: #ffe3ef;
      --white: #fffafc;
      --gold: #ffd36e;
      --black: #2b1b20;
      --glass: rgba(255, 255, 255, 0.82);
      --shadow: 0 14px 34px rgba(110, 0, 25, 0.22);
      --toolbar-h: 58px;
      --bottom-h: 72px;
    }

    * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

    html, body {
      margin: 0;
      width: 100%;
      min-height: 100%;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color: var(--black);
      overflow-x: hidden;
      background: #fff1f7;
      touch-action: manipulation;
    }

    body {
      background-image:
        linear-gradient(135deg, rgba(255, 245, 249, .88), rgba(255, 229, 240, .82)),
        url("https://livedoor.blogimg.jp/akibaguild_front/imgs/c/d/cd20f7f5.png?v=20250819053007");
      background-size: cover;
      background-position: center;
      background-attachment: scroll;
    }

    button, a { font: inherit; }
    button { cursor: pointer; border: none; }
    a { color: inherit; text-decoration: none; }

    .app {
      width: 100%;
      min-height: 100svh;
      position: relative;
    }

    .screen {
      display: none;
      min-height: 100svh;
      animation: screenIn .34s ease both;
    }

    .screen.active { display: block; }

    @keyframes screenIn {
      from { opacity: 0; transform: translateY(12px); filter: blur(4px); }
      to { opacity: 1; transform: translateY(0); filter: blur(0); }
    }

    .tap-pop {
      position: fixed;
      width: 18px;
      height: 18px;
      border-radius: 999px;
      pointer-events: none;
      background: rgba(255, 126, 182, .45);
      border: 2px solid rgba(255, 255, 255, .9);
      transform: translate(-50%, -50%) scale(.2);
      animation: tapPop .5s ease-out forwards;
      z-index: 9999;
    }

    @keyframes tapPop {
      to { opacity: 0; transform: translate(-50%, -50%) scale(4); }
    }

    .start-screen {
      background-image:
        linear-gradient(180deg, rgba(61,0,14,.04), rgba(120,0,22,.20)),
        url("https://livedoor.blogimg.jp/akibaguild_front/imgs/6/5/6549560b.png?v=20260511121918");
      background-size: cover;
      background-position: center;
      min-height: 100svh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: calc(env(safe-area-inset-top) + 22px) 16px calc(env(safe-area-inset-bottom) + 22px);
      position: relative;
      overflow: hidden;
    }

    .start-screen::before,
    .start-screen::after {
      content: "♥ ♦ ♣ ♠";
      position: absolute;
      color: rgba(255,255,255,.24);
      font-size: clamp(54px, 18vw, 130px);
      font-weight: 900;
      letter-spacing: .16em;
      transform: rotate(-18deg);
      animation: floatCard 7s ease-in-out infinite alternate;
    }

    .start-screen::before { top: 8%; left: -38%; }
    .start-screen::after { bottom: 20%; right: -42%; animation-delay: -2.5s; }

    @keyframes floatCard {
      from { transform: translateY(-8px) rotate(-18deg); }
      to { transform: translateY(12px) rotate(-10deg); }
    }

    

    .start-card {
      width: min(430px, 96vw);
      min-height: min(780px, 96svh);
      padding: 18px 12px 8px;
      border-radius: 30px;
      background: transparent;
      box-shadow: none;
      backdrop-filter: none;
      text-align: center;
      border: none;
      z-index: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .logo-img {
      max-width: min(390px, 94vw);
      width: 100%;
      display: block;
      margin: 0 auto;
      filter: drop-shadow(0 12px 22px rgba(80,0,20,.34));
      transform: scale(1.08);
      transform-origin: center top;
    }

    .start-main {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: clamp(58px, 11svh, 108px);
      margin-top: clamp(36px, 7svh, 72px);
    }

    .start-button-img {
      width: min(304px, 80vw);
      display: block;
      filter: drop-shadow(0 0 12px rgba(255,255,255,.78)) drop-shadow(0 15px 28px rgba(80,0,20,.32));
      transition: transform .14s ease, filter .14s ease;
      animation: startFloat 2.4s ease-in-out infinite, startGlow 1.8s ease-in-out infinite alternate;
    }

    @keyframes startFloat {
      0%, 100% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-10px) scale(1.025); }
    }

    @keyframes startGlow {
      from { filter: drop-shadow(0 0 10px rgba(255,255,255,.62)) drop-shadow(0 14px 26px rgba(80,0,20,.30)); }
      to { filter: drop-shadow(0 0 24px rgba(255,255,255,.95)) drop-shadow(0 0 18px rgba(255,126,182,.72)) drop-shadow(0 18px 32px rgba(80,0,20,.36)); }
    }

    .start-button-img:active {
      transform: scale(.96);
      animation-play-state: paused;
      filter: drop-shadow(0 8px 16px rgba(80,0,20,.24));
    }

    .start-footer {
      width: 100%;
      display: grid;
      gap: 5px;
      margin-bottom: max(2px, env(safe-area-inset-bottom));
      color: rgba(255,255,255,.96);
      text-shadow: 0 2px 8px rgba(80,0,20,.48);
      font-weight: 800;
      font-size: 11px;
      letter-spacing: .02em;
      transform: translateY(4px);
    }

    .version-text {
      font-size: 10px;
      opacity: .92;
    }

    .start-title-note {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      margin: 6px auto 18px;
      padding: 7px 12px;
      border-radius: 999px;
      background: linear-gradient(90deg, #fff, #ffe4f0);
      color: var(--deep-red);
      font-size: 12px;
      font-weight: 900;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.16);
    }

    .primary-btn {
      width: 100%;
      min-height: 56px;
      padding: 15px 18px;
      border-radius: 999px;
      color: white;
      font-weight: 1000;
      font-size: 17px;
      letter-spacing: .08em;
      background: linear-gradient(135deg, var(--red), var(--pink));
      box-shadow: 0 13px 28px rgba(215, 25, 32, .32);
      transition: transform .14s ease, box-shadow .14s ease;
      position: relative;
      overflow: hidden;
    }

    .primary-btn::after {
      content: "";
      position: absolute;
      top: -60%;
      left: -40%;
      width: 40%;
      height: 220%;
      background: rgba(255,255,255,.34);
      transform: rotate(25deg);
      animation: shine 2.8s ease-in-out infinite;
    }

    @keyframes shine {
      0%, 45% { left: -55%; }
      70%, 100% { left: 120%; }
    }

    .image-start-btn {
      border: none;
      background: transparent;
      padding: 0;
      margin: 0;
      width: auto;
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .primary-btn:active,
    .menu-btn:active,
    .bottom-btn:active,
    .answer-btn:active { transform: scale(.97); }

    .diagnosis-wrap,
    .result-wrap {
      min-height: 100svh;
      padding: calc(env(safe-area-inset-top) + 18px) 14px calc(env(safe-area-inset-bottom) + 20px);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .panel {
      width: min(440px, 94vw);
      border-radius: 28px;
      padding: 18px;
      background: var(--glass);
      border: 2px solid rgba(255,255,255,.9);
      box-shadow: var(--shadow);
      backdrop-filter: blur(14px);
    }

    .badge {
      display: inline-flex;
      gap: 6px;
      align-items: center;
      padding: 7px 11px;
      border-radius: 999px;
      background: #fff;
      color: var(--deep-red);
      font-size: 12px;
      font-weight: 1000;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.14);
    }

    .progress {
      height: 9px;
      background: rgba(255,255,255,.92);
      border-radius: 999px;
      overflow: hidden;
      margin: 12px 0 18px;
    }

    .progress-bar {
      height: 100%;
      width: 0%;
      background: linear-gradient(90deg, var(--red), var(--pink), var(--gold));
      border-radius: inherit;
      transition: width .24s ease;
    }

    .question {
      font-size: clamp(20px, 6vw, 25px);
      line-height: 1.35;
      font-weight: 1000;
      margin: 0 0 16px;
      color: #5a1420;
    }

    .answers {
      display: grid;
      gap: 10px;
    }

    .answer-btn {
      display: grid;
      grid-template-columns: 48px 1fr;
      align-items: center;
      gap: 9px;
      width: 100%;
      min-height: 62px;
      padding: 9px 12px 9px 9px;
      border-radius: 18px;
      text-align: left;
      color: #301016;
      background: white;
      box-shadow: 0 9px 20px rgba(115,0,25,.10);
      border: 2px solid rgba(255,255,255,.86);
      transition: transform .14s ease, box-shadow .14s ease;
      font-weight: 900;
      font-size: 15px;
      line-height: 1.35;
    }

    .suit-icon {
      display: grid;
      place-items: center;
      width: 44px;
      height: 44px;
      border-radius: 15px;
      color: white;
      font-size: 25px;
      box-shadow: inset 0 -5px 10px rgba(0,0,0,.13);
    }

    .spade { background: linear-gradient(135deg, #2777ff, #66a4ff); }
    .heart { background: linear-gradient(135deg, #ff5aa8, #ff9ec9); }
    .diamond { background: linear-gradient(135deg, #20b56b, #8be7a8); }
    .club { background: linear-gradient(135deg, #f1b800, #ffe06f); color: #5c3c00; }

    .maid-emoji-big {
      width: 128px;
      height: 128px;
      display: grid;
      place-items: center;
      margin: 4px auto 8px;
      border-radius: 38px;
      background: radial-gradient(circle at 30% 20%, #fff, #ffe1ec 54%, #ff95bd);
      font-size: 74px;
      box-shadow: 0 16px 30px rgba(180,0,55,.22);
      border: 3px solid white;
    }

    .result-name {
      text-align: center;
      margin: 7px 0;
      color: var(--deep-red);
      font-size: clamp(24px, 7vw, 30px);
      font-weight: 1000;
      line-height: 1.28;
    }

    .result-lead {
      text-align: center;
      margin: 0 auto 14px;
      color: #6c2732;
      font-weight: 900;
      line-height: 1.6;
      font-size: 14px;
    }

    .info-grid {
      display: grid;
      gap: 8px;
      margin: 12px 0;
    }

    .info-row {
      padding: 10px 12px;
      border-radius: 15px;
      background: rgba(255,255,255,.84);
      display: grid;
      grid-template-columns: 66px 1fr;
      gap: 8px;
      font-size: 13px;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.08);
    }

    .info-row b { color: var(--deep-red); }

    .sub-actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 9px;
      margin-top: 13px;
    }

    .secondary-btn {
      min-height: 48px;
      padding: 12px 10px;
      border-radius: 17px;
      background: #fff;
      color: var(--deep-red);
      font-weight: 1000;
      box-shadow: 0 9px 18px rgba(100,0,24,.10);
      text-align: center;
      display: grid;
      place-items: center;
      font-size: 13px;
    }

    .home-screen {
      min-height: 100svh;
      padding: calc(var(--toolbar-h) + env(safe-area-inset-top) + 10px) 10px calc(var(--bottom-h) + env(safe-area-inset-bottom) + 12px);
    }

    .toolbar {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      height: calc(var(--toolbar-h) + env(safe-area-inset-top));
      padding: calc(env(safe-area-inset-top) + 7px) 9px 7px;
      display: grid;
      grid-template-columns: minmax(92px, 1fr) auto auto;
      gap: 7px;
      align-items: center;
      z-index: 20;
      background: rgba(255,255,255,.88);
      backdrop-filter: blur(16px);
      box-shadow: 0 9px 22px rgba(100,0,20,.13);
      border-bottom: 1px solid rgba(215,25,32,.14);
    }

    .toolbar-logo {
      height: 38px;
      width: min(132px, 36vw);
      object-fit: contain;
      object-position: left center;
      cursor: pointer;
    }

    .quest-btn,
    .hamburger-btn {
      height: 40px;
      border-radius: 999px;
      padding: 0 11px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 5px;
      font-weight: 1000;
      font-size: 11px;
      box-shadow: 0 7px 16px rgba(80,0,25,.13);
      white-space: nowrap;
    }

    .quest-btn { background: linear-gradient(135deg, var(--red), var(--pink)); color: #fff; }
    .hamburger-btn { width: 42px; background: #fff; color: var(--deep-red); font-size: 21px; padding: 0; }

    .home-layout {
      display: grid;
      grid-template-columns: 38% 1fr;
      gap: 9px;
      max-width: 430px;
      margin: 0 auto;
      align-items: stretch;
    }

    .guide-card {
      min-height: 380px;
      position: relative;
      border-radius: 26px;
      padding: 12px 7px;
      overflow: hidden;
      background: rgba(255,255,255,.76);
      box-shadow: var(--shadow);
      border: 2px solid rgba(255,255,255,.9);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .guide-card::before {
      content: "♡";
      position: absolute;
      top: 5px;
      right: 8px;
      font-size: 62px;
      color: rgba(255,126,182,.18);
      font-weight: 900;
    }

    .guide-emoji {
      width: min(138px, 32vw);
      height: min(260px, 45vh);
      min-width: 108px;
      min-height: 220px;
      display: grid;
      place-items: center;
      border-radius: 999px 999px 36px 36px;
      background: radial-gradient(circle at 35% 20%, #fff, #ffe1ec 44%, #ff95bd 86%);
      font-size: clamp(70px, 18vw, 118px);
      box-shadow: 0 15px 28px rgba(200, 0, 55, .2);
      border: 4px solid white;
      animation: guideFloat 2.8s ease-in-out infinite alternate;
      z-index: 1;
    }

    @keyframes guideFloat {
      from { transform: translateY(-4px); }
      to { transform: translateY(8px); }
    }

    .guide-name {
      margin-top: 11px;
      padding: 7px 11px;
      border-radius: 999px;
      background: #fff;
      color: var(--deep-red);
      font-weight: 1000;
      font-size: 13px;
      box-shadow: 0 7px 16px rgba(120,0,26,.12);
      z-index: 1;
      max-width: 100%;
      text-align: center;
    }

    .menu-area {
      display: grid;
      gap: 8px;
      align-content: start;
    }

    .menu-btn {
      min-height: 66px;
      border-radius: 20px;
      padding: 11px;
      background: rgba(255,255,255,.88);
      color: var(--deep-red);
      box-shadow: 0 10px 22px rgba(100,0,25,.11);
      border: 2px solid rgba(255,255,255,.94);
      font-weight: 1000;
      text-align: left;
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 2px;
      transition: transform .14s ease;
    }

    .menu-btn span:first-child {
      font-size: clamp(15px, 4.4vw, 18px);
      line-height: 1.2;
    }

    .menu-btn small {
      color: #85505a;
      font-weight: 900;
      font-size: 10.5px;
      line-height: 1.25;
    }

    .half-row { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
    .half-row .menu-btn { min-height: 62px; padding: 9px; }
    .half-row .menu-btn span:first-child { font-size: 14px; }

    .speech {
      max-width: 430px;
      margin: 10px auto 0;
      padding: 13px 15px;
      border-radius: 23px;
      background: rgba(255,255,255,.88);
      box-shadow: var(--shadow);
      border: 2px solid white;
      position: relative;
      font-weight: 900;
      line-height: 1.55;
      color: #5a1420;
      font-size: 13.5px;
    }

    .speech::before {
      content: "";
      position: absolute;
      left: 48px;
      top: -10px;
      width: 22px;
      height: 22px;
      background: rgba(255,255,255,.88);
      transform: rotate(45deg);
      border-left: 2px solid white;
      border-top: 2px solid white;
    }

    .bottom-nav {
      position: fixed;
      left: 0;
      right: 0;
      bottom: 0;
      height: calc(var(--bottom-h) + env(safe-area-inset-bottom));
      padding: 7px 7px calc(env(safe-area-inset-bottom) + 7px);
      background: rgba(255,255,255,.9);
      backdrop-filter: blur(16px);
      z-index: 20;
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 5px;
      box-shadow: 0 -10px 26px rgba(100,0,30,.14);
      border-top: 1px solid rgba(215,25,32,.14);
    }

    .bottom-btn {
      border-radius: 16px;
      background: #fff;
      color: #6d2230;
      font-size: 10px;
      font-weight: 1000;
      display: grid;
      place-items: center;
      gap: 1px;
      padding: 5px 1px;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.08);
      min-width: 0;
    }

    .bottom-btn.active {
      background: linear-gradient(135deg, var(--red), var(--pink));
      color: #fff;
      box-shadow: 0 7px 16px rgba(215,25,32,.23);
    }

    .bottom-btn b { font-size: 19px; line-height: 1; }

    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(40,0,12,.38);
      z-index: 40;
      opacity: 0;
      pointer-events: none;
      transition: opacity .2s ease;
    }

    .overlay.open { opacity: 1; pointer-events: auto; }

    .sidebar {
      position: fixed;
      top: 0;
      right: 0;
      width: min(310px, 86vw);
      height: 100svh;
      padding: calc(env(safe-area-inset-top) + 18px) 16px 16px;
      background: rgba(255,255,255,.96);
      z-index: 50;
      transform: translateX(105%);
      transition: transform .22s ease;
      box-shadow: -16px 0 36px rgba(60,0,20,.22);
      backdrop-filter: blur(14px);
    }

    .sidebar.open { transform: translateX(0); }

    .sidebar h2 { color: var(--deep-red); margin: 8px 0 16px; }

    .side-link {
      width: 100%;
      min-height: 52px;
      display: block;
      padding: 14px;
      border-radius: 17px;
      background: #fff3f8;
      color: var(--deep-red);
      font-weight: 1000;
      margin-bottom: 9px;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.10);
      text-align: left;
    }

    .close-btn {
      width: 100%;
      min-height: 50px;
      margin-top: 16px;
      padding: 13px;
      border-radius: 17px;
      background: var(--red);
      color: #fff;
      font-weight: 1000;
    }

    .modal {
      position: fixed;
      left: 50%;
      top: 50%;
      width: min(430px, 92vw);
      max-height: min(720px, 82svh);
      overflow: auto;
      transform: translate(-50%, -50%) scale(.96);
      background: rgba(255,255,255,.97);
      border-radius: 26px;
      padding: 18px;
      z-index: 60;
      box-shadow: 0 20px 60px rgba(50,0,20,.35);
      border: 2px solid white;
      opacity: 0;
      pointer-events: none;
      transition: .2s ease;
      -webkit-overflow-scrolling: touch;
    }

    .modal.open { opacity: 1; pointer-events: auto; transform: translate(-50%, -50%) scale(1); }
    .modal h2 { margin: 0 0 10px; color: var(--deep-red); font-size: 22px; }
    .modal p, .modal li { line-height: 1.65; font-size: 14px; }

    .maid-list {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 8px;
      margin-top: 12px;
    }

    .maid-card-mini {
      background: #fff4f8;
      border-radius: 17px;
      padding: 11px 7px;
      text-align: center;
      font-weight: 1000;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.08);
      font-size: 13px;
    }

    .maid-card-mini .mini-emoji { font-size: 34px; display: block; }

    @media (max-width: 374px) {
      .start-card { min-height: min(690px, 96svh); padding-left: 8px; padding-right: 8px; padding-bottom: 6px; }
      .start-main { margin-top: clamp(24px, 5svh, 42px); gap: clamp(56px, 12svh, 92px); }
      .logo-img { max-width: min(340px, 94vw); transform: scale(1.06); }
      .start-button-img { width: min(270px, 78vw); }
      .start-footer { font-size: 10px; transform: translateY(3px); }
      .version-text { font-size: 9px; }
      :root { --toolbar-h: 54px; --bottom-h: 66px; }
      .toolbar-logo { width: 104px; height: 34px; }
      .quest-btn { font-size: 0; width: 40px; padding: 0; }
      .quest-btn::before { content: "🎰"; font-size: 18px; }
      .hamburger-btn { width: 40px; height: 38px; }
      .home-layout { grid-template-columns: 36% 1fr; gap: 7px; }
      .guide-card { min-height: 342px; border-radius: 23px; }
      .guide-emoji { min-width: 92px; width: 29vw; min-height: 198px; font-size: 64px; }
      .guide-name { font-size: 12px; padding: 6px 9px; }
      .menu-area { gap: 7px; }
      .menu-btn { min-height: 60px; border-radius: 18px; padding: 9px; }
      .menu-btn span:first-child { font-size: 14px; }
      .menu-btn small { font-size: 9.5px; }
      .half-row { gap: 7px; }
      .half-row .menu-btn { min-height: 56px; padding: 8px; }
      .half-row .menu-btn span:first-child { font-size: 12.5px; }
      .speech { font-size: 12.5px; padding: 12px 13px; }
      .bottom-btn { font-size: 9px; border-radius: 14px; }
      .bottom-btn b { font-size: 17px; }
      .question { font-size: 19px; }
      .answer-btn { font-size: 14px; min-height: 58px; grid-template-columns: 44px 1fr; }
      .suit-icon { width: 40px; height: 40px; font-size: 23px; }
    }

    @media (min-width: 700px) {
      .home-layout, .speech { max-width: 520px; }
      .guide-card { min-height: 420px; }
      .guide-emoji { width: 170px; }
    }
  

    .story-wrap {
      min-height: 100svh;
      padding: calc(env(safe-area-inset-top) + 18px) 14px calc(env(safe-area-inset-bottom) + 20px);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .story-panel {
      width: min(440px, 94vw);
      min-height: min(620px, 88svh);
      border-radius: 30px;
      padding: 18px;
      background: rgba(255,255,255,.84);
      border: 2px solid rgba(255,255,255,.92);
      box-shadow: var(--shadow);
      backdrop-filter: blur(14px);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 16px;
      position: relative;
      overflow: hidden;
    }

    .story-panel::before {
      content: "♥ ♦ ♣ ♠";
      position: absolute;
      top: 14px;
      right: -18px;
      font-size: 44px;
      color: rgba(215,25,32,.10);
      font-weight: 1000;
      transform: rotate(16deg);
      pointer-events: none;
    }

    .story-maid {
      display: grid;
      place-items: center;
      width: 138px;
      height: 138px;
      margin: 4px auto 0;
      border-radius: 44px;
      background: radial-gradient(circle at 30% 20%, #fff, #ffe1ec 54%, #ff95bd);
      font-size: 76px;
      box-shadow: 0 16px 30px rgba(180,0,55,.20);
      border: 3px solid white;
      animation: guideFloat 2.8s ease-in-out infinite alternate;
      z-index: 1;
    }

    .story-box {
      position: relative;
      padding: 18px 16px;
      border-radius: 24px;
      background: #fff;
      box-shadow: inset 0 0 0 1px rgba(215,25,32,.10), 0 10px 22px rgba(100,0,24,.10);
      color: #5a1420;
      font-weight: 900;
      line-height: 1.72;
      font-size: 15px;
      z-index: 1;
      min-height: 150px;
      white-space: pre-line;
    }

    .story-nameplate {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      margin-bottom: 8px;
      padding: 6px 11px;
      border-radius: 999px;
      background: linear-gradient(135deg, var(--red), var(--pink));
      color: #fff;
      font-size: 12px;
      font-weight: 1000;
      box-shadow: 0 8px 16px rgba(215,25,32,.22);
    }

    .story-options {
      display: grid;
      gap: 10px;
      z-index: 1;
    }

    .story-choice {
      min-height: 56px;
      border-radius: 18px;
      padding: 13px 14px;
      background: rgba(255,255,255,.95);
      color: var(--deep-red);
      font-weight: 1000;
      text-align: left;
      box-shadow: 0 10px 22px rgba(100,0,24,.10);
      border: 2px solid rgba(255,255,255,.96);
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .story-choice::after {
      content: "›";
      font-size: 24px;
      line-height: 1;
      opacity: .65;
    }

    .story-choice:active { transform: scale(.97); }

    .story-progress {
      display: flex;
      justify-content: center;
      gap: 6px;
      margin-top: 4px;
      z-index: 1;
    }

    .story-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: rgba(215,25,32,.22);
    }

    .story-dot.active { background: var(--red); transform: scale(1.25); }

    @media (max-width: 374px) {
      .story-panel { min-height: min(590px, 88svh); padding: 15px; }
      .story-maid { width: 120px; height: 120px; font-size: 66px; }
      .story-box { font-size: 14px; min-height: 138px; padding: 15px 14px; }
      .story-choice { min-height: 52px; font-size: 14px; padding: 12px; }
    }
  </style>
</head>
<body>
  <div id="app" class="app">
    

    <section id="startScreen" class="screen active">
      <div class="start-screen">
        <div class="start-card">
          <div class="start-main">
            <img class="logo-img" src="https://livedoor.blogimg.jp/akibaguild_front/imgs/3/3/33b7ebb9.png?v=20260513202134" alt="Akiba Guild" />
            <button class="image-start-btn" id="startBtn" aria-label="START">
              <img class="start-button-img" src="https://livedoor.blogimg.jp/akibaguild_front/imgs/c/6/c6233720.png?v=20260513202159" alt="START" />
            </button>
          </div>
          <div class="start-footer">
            <div>©ハンターサイト株式会社</div>
            <div class="version-text">Ver.1.001.03</div>
          </div>
        </div>
      </div>
    </section>

    <section id="storyScreen" class="screen">
      <div class="story-wrap">
        <div class="story-panel">
          <div>
            <div class="story-maid" id="storyMaid">🎀</div>
            <div class="story-box">
              <div class="story-nameplate">案内メイド</div>
              <div id="storyText"></div>
            </div>
          </div>
          <div>
            <div class="story-options" id="storyOptions"></div>
            <div class="story-progress" id="storyProgress"></div>
          </div>
        </div>
      </div>
    </section>

    <section id="diagnosisScreen" class="screen">
      <div class="diagnosis-wrap">
        <div class="panel">
          <div class="badge" id="questionCount">Q1 / 10</div>
          <div class="progress"><div class="progress-bar" id="progressBar"></div></div>
          <h1 class="question" id="questionText"></h1>
          <div class="answers" id="answers"></div>
        </div>
      </div>
    </section>

    <section id="resultScreen" class="screen">
      <div class="result-wrap">
        <div class="panel">
          <div class="badge">診断結果</div>
          <div class="maid-emoji-big" id="resultEmoji">🎀</div>
          <h1 class="result-name" id="resultName"></h1>
          <p class="result-lead" id="resultLead"></p>
          <div class="info-grid">
            <div class="info-row"><b>MBTI</b><span id="resultMbti"></span></div>
            <div class="info-row"><b>趣味</b><span id="resultHobby"></span></div>
            <div class="info-row"><b>X</b><a id="resultX" href="https://x.com/AkibaGuild" target="_blank" rel="noopener">公式Xを見る</a></div>
          </div>
          <button class="primary-btn" id="goHomeBtn">ホームへ進む</button>
          <div class="sub-actions">
            <button class="secondary-btn" id="retryBtn">もう一度診断</button>
            <a class="secondary-btn" href="https://x.com/AkibaGuild" target="_blank" rel="noopener">Xを見る</a>
          </div>
        </div>
      </div>
    </section>

    <section id="homeScreen" class="screen">
      <div class="home-screen">
        <header class="toolbar">
          <img class="toolbar-logo" id="toolbarLogo" src="https://livedoor.blogimg.jp/akibaguild_front/imgs/0/8/0895fa31.png?v=20250728060438" alt="Akiba Guild" />
          <a class="quest-btn" href="https://akiba-casino.jp/" target="_blank" rel="noopener">カジノクエスト</a>
          <button class="hamburger-btn" id="openSidebar">☰</button>
        </header>

        <main class="home-layout">
          <section class="guide-card">
            <div class="guide-emoji" id="homeEmoji">🎀</div>
            <div class="guide-name" id="homeName">メイド</div>
          </section>

          <section class="menu-area">
            <button class="menu-btn" data-modal="maids"><span>📖 メイド図鑑</span><small>27人のメイドをチェック</small></button>
            <button class="menu-btn" data-modal="games"><span>🎲 各ゲーム紹介</span><small>ポーカー・カジノゲーム案内</small></button>
            <button class="menu-btn" data-modal="price"><span>💰 料金表</span><small>入場料・遊び方の確認</small></button>
            <div class="half-row">
              <button class="menu-btn" data-modal="coupon"><span>🎁 クーポン</span><small>LINE連携想定</small></button>
              <button class="menu-btn" data-modal="wifi"><span>📶 Wi-Fi</span><small>店内接続情報</small></button>
            </div>
          </section>
        </main>

        <div class="speech" id="homeSpeech">こんにちは。今日は私が店内をご案内します。</div>

        <nav class="bottom-nav">
          <button class="bottom-btn" data-modal="minigame"><b>🎮</b>ミニゲーム</button>
          <button class="bottom-btn" data-modal="tournament"><b>🏆</b>トーナメント</button>
          <button class="bottom-btn active"><b>🏠</b>ホーム</button>
          <button class="bottom-btn" data-modal="event"><b>🎪</b>イベント</button>
          <button class="bottom-btn" data-modal="sns"><b>📱</b>SNS</button>
        </nav>
      </div>
    </section>
  </div>

  <div class="overlay" id="overlay"></div>
  <aside class="sidebar" id="sidebar">
    <h2>メニュー</h2>
    <button class="side-link" data-modal="contact">お問い合わせ</button>
    <button class="side-link" data-modal="terms">利用規約</button>
    <button class="side-link" id="sidebarResetBtn">リセット</button>
    <button class="close-btn" id="closeSidebar">閉じる</button>
  </aside>

  <div class="modal" id="modal">
    <h2 id="modalTitle"></h2>
    <div id="modalBody"></div>
    <button class="close-btn" id="closeModal">閉じる</button>
  </div>

  <script>
    const STORAGE_KEY = "ag_store_game_result_v1";
    const PROFILE_KEY = "ag_store_game_profile_v1";

    const maidNames = [
      "はずみ", "るり", "ぶどう", "ゴロ美", "星凪", "ぐみ", "あさひ", "ひらり", "あしゅ",
      "柘榴", "あかね", "のら", "かれん", "ゆあ", "ねあ", "たね", "びび", "れる",
      "みすず", "ゆま", "もぬ", "がぶ", "ライラ", "すずめ", "ミラ", "レヴィ", "まるち"
    ];

    const emojis = ["🎀", "💎", "🍇", "🃏", "🌙", "🍀", "☀️", "🪽", "✨", "🌺", "🍎", "🐾", "💐", "🫧", "🌸", "🌱", "⚡", "🎧", "🔔", "🧸", "🍰", "🦇", "🪄", "🐦", "🔮", "♠️", "🤖"];
    const mbtis = ["ENFP", "ISFJ", "INFP", "ESTP", "INTJ", "ESFP", "ENFJ", "ISFP", "ENTP", "INFJ", "ESFJ", "ISTP", "ENFP", "INFP", "ISFJ", "ISTJ", "ENTJ", "ISFP", "ESFJ", "ENFJ", "INTP", "ESTP", "INFJ", "ISTP", "INTJ", "ENTP", "INTP"];
    const hobbies = [
      "新作スイーツ探し", "アクセサリー集め", "音楽とカフェ巡り", "ボードゲーム", "星空観察", "アニメ鑑賞",
      "朝活と散歩", "かわいい雑貨探し", "ゲーム実況を見ること", "和風小物集め", "写真を撮ること", "猫動画を見ること",
      "紅茶と読書", "コスメ研究", "ぬいぐるみ集め", "観葉植物", "ダンス", "音楽プレイリスト作り",
      "喫茶店巡り", "お菓子作り", "イラスト", "ミステリー作品", "占い", "街歩き", "カードゲーム", "映画鑑賞", "便利ツール探し"
    ];
    const leads = [
      "今日のラッキーゲームまで、にこにこ案内します♡", "落ち着いて遊びたいあなたにぴったりです。", "ゆるっと楽しい時間を一緒に作ります。",
      "勝負のドキドキを全力で盛り上げます！", "静かに燃える作戦派のあなたと好相性。", "初めてでも楽しく過ごせるように案内します。",
      "明るく元気に店内をご案内します！", "ふわっと軽やかにおすすめを紹介します。", "ワクワクする遊び方を一緒に探しましょう。"
    ];

    const maids = maidNames.map((name, index) => ({
      id: index,
      name,
      emoji: emojis[index],
      mbti: mbtis[index],
      hobby: hobbies[index],
      x: "https://x.com/AkibaGuild",
      lead: leads[index % leads.length]
    }));

    const questionPool = [
      { q: "お店で最初に惹かれるのは？", a: ["勝負感のあるゲーム", "かわいい雰囲気", "新しい体験", "落ち着く接客"] },
      { q: "理想の案内役はどんなタイプ？", a: ["クールに導く", "甘く応援してくれる", "明るく盛り上げる", "丁寧に教えてくれる"] },
      { q: "好きな席の雰囲気は？", a: ["集中できる席", "華やかな席", "みんなで楽しめる席", "ゆったり話せる席"] },
      { q: "ゲームで大事にしたいことは？", a: ["読み合い", "かわいい演出", "逆転のチャンス", "安心して遊べること"] },
      { q: "今日の気分に近い色は？", a: ["青", "ピンク", "緑", "黄色"] },
      { q: "初めてのゲームなら？", a: ["戦略性重視", "見た目がかわいい", "直感で遊べる", "説明がわかりやすい"] },
      { q: "メイドに言われたい一言は？", a: ["次の一手、いいですね", "一緒に楽しみましょう♡", "今のすごいです！", "ゆっくりで大丈夫です"] },
      { q: "休日の過ごし方は？", a: ["一人で趣味に集中", "かわいい場所に行く", "友達と盛り上がる", "のんびり休む"] },
      { q: "トランプで好きなマークは？", a: ["スペード", "ハート", "ダイヤ", "クラブ"] },
      { q: "あなたの勝負スタイルは？", a: ["冷静に判断", "気持ちで押す", "流れを読む", "堅実に進める"] },
      { q: "好きなイベントは？", a: ["真剣勝負系", "衣装テーマ系", "参加型企画", "初心者歓迎系"] },
      { q: "お店で欲しい体験は？", a: ["上達した実感", "写真を撮りたくなる空間", "非日常感", "居心地の良さ"] }
    ];

    const suits = [
      { mark: "♠", cls: "spade", score: 0 },
      { mark: "♥", cls: "heart", score: 1 },
      { mark: "♦", cls: "diamond", score: 2 },
      { mark: "♣", cls: "club", score: 3 }
    ];

    let questions = [];
    let current = 0;
    let scores = [0, 0, 0, 0];
    let storyStep = 0;
    let playerProfile = { visit: null, understood: null, title: "ご主人様" };

    const storySteps = [
      {
        maid: "🎀",
        text: "お帰りなさいませ。
アキバギルドへようこそ。

本日は、アキバギルドのご利用は初めてですか？",
        options: [
          { label: "初めてです", value: "first" },
          { label: "来たことがあります", value: "again" }
        ],
        action: (value) => { playerProfile.visit = value; }
      },
      {
        maid: "🎰",
        text: "アキバギルドは、ポーカーやカジノゲームを楽しめるアミューズメントカジノです。

本物のお金を賭ける場所ではなく、チップを使ってゲームの雰囲気や駆け引きを楽しむお店です。

ルールが分からなくても、メイドがそばでご案内しますのでご安心ください。",
        options: [
          { label: "理解しました", value: "yes" },
          { label: "もう一度説明を見たい", value: "repeat" }
        ],
        action: (value) => { playerProfile.understood = value === "yes"; }
      },
      {
        maid: "💌",
        text: "ありがとうございます。

それでは、店内をご案内するために、あなたのことを少しだけ教えてください。

メイドからはどのようにお呼びしましょうか？",
        options: [
          { label: "ご主人様", value: "ご主人様" },
          { label: "お嬢様", value: "お嬢様" }
        ],
        action: (value) => { playerProfile.title = value; }
      },
      {
        maid: "🃏",
        text: "かしこまりました。

では、あなたにぴったりの案内メイドをお探しします。

いくつかの質問から、相性のよいメイドを選ばせていただきますね。",
        options: [
          { label: "相性診断を始める", value: "start" }
        ],
        action: () => {}
      }
    ];

    const $ = (id) => document.getElementById(id);

    function shuffle(array) {
      return [...array].sort(() => Math.random() - 0.5);
    }

    function showScreen(id) {
      document.querySelectorAll(".screen").forEach(screen => screen.classList.remove("active"));
      $(id).classList.add("active");
      window.scrollTo({ top: 0, behavior: "smooth" });
    }

    function requestFullscreen() {
      const el = document.documentElement;
      if (el.requestFullscreen) el.requestFullscreen().catch(() => {});
      window.scrollTo(0, 1);
    }

    function startFlow() {
      requestFullscreen();
      const saved = getSavedResult();
      if (saved) {
        renderHome(saved);
        showScreen("homeScreen");
      } else {
        startStory();
      }
    }

    function startStory() {
      storyStep = 0;
      playerProfile = { visit: null, understood: null, title: "ご主人様" };
      renderStory();
      showScreen("storyScreen");
    }

    function renderStory() {
      const step = storySteps[storyStep];
      $("storyMaid").textContent = step.maid;
      $("storyText").textContent = step.text;
      $("storyOptions").innerHTML = "";
      $("storyProgress").innerHTML = "";

      storySteps.forEach((_, index) => {
        const dot = document.createElement("span");
        dot.className = `story-dot ${index === storyStep ? "active" : ""}`;
        $("storyProgress").appendChild(dot);
      });

      step.options.forEach(option => {
        const btn = document.createElement("button");
        btn.className = "story-choice";
        btn.textContent = option.label;
        btn.addEventListener("click", () => handleStoryChoice(option.value));
        $("storyOptions").appendChild(btn);
      });
    }

    function handleStoryChoice(value) {
      const step = storySteps[storyStep];
      step.action(value);

      if (value === "repeat") {
        renderStory();
        return;
      }

      if (storyStep >= storySteps.length - 1) {
        saveProfile();
        startDiagnosis();
        return;
      }

      storyStep += 1;
      renderStory();
    }

    function startDiagnosis() {
      questions = shuffle(questionPool).slice(0, 10);
      current = 0;
      scores = [0, 0, 0, 0];
      renderQuestion();
      showScreen("diagnosisScreen");
    }

    function renderQuestion() {
      const item = questions[current];
      $("questionCount").textContent = `Q${current + 1} / 10`;
      $("progressBar").style.width = `${(current / 10) * 100}%`;
      $("questionText").textContent = item.q;
      $("answers").innerHTML = "";

      item.a.forEach((text, index) => {
        const suit = suits[index];
        const btn = document.createElement("button");
        btn.className = "answer-btn";
        btn.innerHTML = `<span class="suit-icon ${suit.cls}">${suit.mark}</span><span>${text}</span>`;
        btn.addEventListener("click", () => answerQuestion(index));
        $("answers").appendChild(btn);
      });
    }

    function answerQuestion(index) {
      scores[index] += 1;
      current += 1;
      if (current >= 10) {
        $("progressBar").style.width = "100%";
        setTimeout(showResult, 220);
      } else {
        renderQuestion();
      }
    }

    function showResult() {
      const weighted = scores.reduce((sum, value, index) => sum + value * (index + 3), 0);
      const spice = questions.map(q => q.q.length).reduce((a, b) => a + b, 0);
      const maidIndex = (weighted * 7 + spice + scores[1] * 5 + scores[2] * 3) % maids.length;
      const maid = maids[maidIndex];
      saveResult(maid);
      renderResult(maid);
      showScreen("resultScreen");
    }

    function renderResult(maid) {
      $("resultEmoji").textContent = maid.emoji;
      $("resultName").textContent = `${maid.name} と相性ぴったり！`;
      $("resultLead").textContent = maid.lead;
      $("resultMbti").textContent = maid.mbti;
      $("resultHobby").textContent = maid.hobby;
      $("resultX").href = maid.x;
    }

    function saveResult(maid) {
      localStorage.setItem(STORAGE_KEY, JSON.stringify({ maidId: maid.id, savedAt: Date.now() }));
    }

    function saveProfile() {
      localStorage.setItem(PROFILE_KEY, JSON.stringify(playerProfile));
    }

    function getSavedProfile() {
      try {
        const raw = localStorage.getItem(PROFILE_KEY);
        if (!raw) return { title: "ご主人様" };
        return { title: "ご主人様", ...JSON.parse(raw) };
      } catch (_) {
        return { title: "ご主人様" };
      }
    }

    function getSavedResult() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (!raw) return null;
        const data = JSON.parse(raw);
        return maids[data.maidId] || null;
      } catch (_) {
        return null;
      }
    }

    function resetGame() {
      localStorage.removeItem(STORAGE_KEY);
      localStorage.removeItem(PROFILE_KEY);
      closeAll();
      showScreen("startScreen");
    }

    function renderHome(maid) {
      const profile = getSavedProfile();
      const title = profile.title || "ご主人様";
      $("homeEmoji").textContent = maid.emoji;
      $("homeName").textContent = maid.name;
      $("homeSpeech").textContent = `「${title}、${maid.lead} 右のメニューから、気になる内容を選んでくださいね。」`;
    }

    function openSidebar() {
      $("overlay").classList.add("open");
      $("sidebar").classList.add("open");
    }

    function closeAll() {
      $("overlay").classList.remove("open");
      $("sidebar").classList.remove("open");
      $("modal").classList.remove("open");
    }

    function openModal(type) {
      const contents = getModalContent(type);
      $("modalTitle").textContent = contents.title;
      $("modalBody").innerHTML = contents.body;
      $("overlay").classList.add("open");
      $("sidebar").classList.remove("open");
      $("modal").classList.add("open");
    }

    function getModalContent(type) {
      const maidListHtml = `<div class="maid-list">${maids.map(m => `<div class="maid-card-mini"><span class="mini-emoji">${m.emoji}</span>${m.name}<br><small>${m.mbti}</small></div>`).join("")}</div>`;
      const map = {
        maids: { title: "メイド図鑑", body: `<p>診断に登場する27人のメイド一覧です。画像は仮の絵文字です。</p>${maidListHtml}` },
        games: { title: "各ゲーム紹介", body: `<ul><li>ポーカー：読み合いと駆け引きを楽しむ定番ゲーム。</li><li>ブラックジャック：数字の判断が楽しいカジノゲーム。</li><li>ルーレット：直感でも遊びやすい華やかなゲーム。</li><li>その他：店内スタッフが遊び方をご案内します。</li></ul>` },
        price: { title: "料金表", body: `<p>ここに入場料、チップ購入、ドリンク、各種サービス料金を掲載できます。</p><p><b>仮表示：</b>入場料 / ゲームチップ / ドリンク / イベント参加費</p>` },
        coupon: { title: "クーポン", body: `<p>LINEクーポンや来店特典への誘導を想定した画面です。</p><p><button class="primary-btn" onclick="window.open('https://x.com/AkibaGuild','_blank')">クーポンを見る</button></p>` },
        wifi: { title: "Wi-Fi", body: `<p>店内Wi-Fi情報をここに掲載できます。</p><p><b>SSID：</b>AkibaGuild_Guest<br><b>PASS：</b>staffにお尋ねください</p>` },
        minigame: { title: "ミニゲーム", body: `<p>ここに簡単なカードめくり、ルーレット、スタンプ演出などを追加できます。</p>` },
        tournament: { title: "トーナメント", body: `<p>トーナメント予定、参加方法、開始時間、レイトレジストなどを掲載できます。</p>` },
        event: { title: "イベント", body: `<p>周年、季節イベント、限定衣装、キャンペーン情報などを掲載できます。</p>` },
        sns: { title: "SNS", body: `<p>公式SNSへの導線です。</p><p><a class="secondary-btn" href="https://x.com/AkibaGuild" target="_blank" rel="noopener">公式Xを開く</a></p>` },
        contact: { title: "お問い合わせ", body: `<p>お問い合わせ先、営業時間、アクセス、予約方法などを掲載できます。</p>` },
        terms: { title: "利用規約", body: `<p>本コンテンツは店舗紹介を目的としたブラウザアプリ風コンテンツです。</p><ul><li>診断結果は端末内に保存されます。</li><li>Cookie削除、シークレットモード終了、ブラウザデータ削除により消える場合があります。</li><li>実際のキャンペーン内容は店頭案内を優先します。</li></ul>` }
      };
      return map[type] || { title: "準備中", body: "<p>このページは準備中です。</p>" };
    }

    document.addEventListener("click", (event) => {
      const pop = document.createElement("span");
      pop.className = "tap-pop";
      pop.style.left = `${event.clientX}px`;
      pop.style.top = `${event.clientY}px`;
      document.body.appendChild(pop);
      setTimeout(() => pop.remove(), 600);
    });

    $("startBtn").addEventListener("click", startFlow);
    $("goHomeBtn").addEventListener("click", () => {
      const maid = getSavedResult();
      renderHome(maid);
      showScreen("homeScreen");
    });
    $("retryBtn").addEventListener("click", () => {
      localStorage.removeItem(STORAGE_KEY);
      startStory();
    });
    
    $("toolbarLogo").addEventListener("click", () => location.reload());
    $("openSidebar").addEventListener("click", openSidebar);
    $("closeSidebar").addEventListener("click", closeAll);
    $("sidebarResetBtn").addEventListener("click", () => {
      resetGame();
    });
    $("overlay").addEventListener("click", closeAll);
    $("closeModal").addEventListener("click", closeAll);

    document.querySelectorAll("[data-modal]").forEach(el => {
      el.addEventListener("click", () => openModal(el.dataset.modal));
    });

    window.addEventListener("DOMContentLoaded", () => {
      const saved = getSavedResult();
      if (saved) {
        renderHome(saved);
      }
    });
  </script>
</body>
</html>
