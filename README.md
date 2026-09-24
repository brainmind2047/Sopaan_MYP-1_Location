<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Location</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Grade 6 Mathematics · Chapter 15</div>
  <div class="chapter-title">Location</div>
  <div class="chapter-sub">Exercises 15A–15E · Review Sets · Step-by-Step Practice</div><div class="chapter-credit">Follows Haese Mathematics 6 (MYP 1), Chapter 15</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Grade 6 Mathematics<br>Exercises follow the structure of <i>Mathematics 6 (MYP 1), 3rd edition</i>, Haese Mathematics. Questions, steps and solutions written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')') && (a.k==='n'||a.k==='v'||a.k==='(')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/[−–—]/g,'-').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(\d+)(?: |\+|-)(\d+)\/(\d+)$/))){ if(+m[3]===0) return null; return {v:+m[1]+m[2]/m[3],form:'mixed',w:+m[1],n:+m[2],d:+m[3]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ return wordsNorm(a)===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='glist'){ var gn=function(x){ return String(x).toUpperCase().split(/[\s,;]+/).filter(Boolean).sort().join(','); }; return [answer].concat(accept||[]).some(function(a){ return gn(a)===gn(input); }); }
  if(expr==='coord'){ var cn=function(x){ return String(x).replace(/[\u2212\u2013\u2014]/g,'-').replace(/[\s()\[\]]/g,''); }; return [answer].concat(accept||[]).some(function(a){ return cn(a)===cn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null) return Math.abs(n1-n2)<1e-3;
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var SECTIONS = [{"id": "s1", "label": "Ex 15A", "sub": "Grid references", "slides": [{"kind": "blank", "p": "Use this city map. A grid reference gives the column letter, then the row number.", "tag": "", "marks": "", "flat": [{"t": "a) Which feature is at F1? __B1__", "a": {"B1": "Temple"}, "expr": "words"}, {"t": "b) Which feature is at E4? __B1__", "a": {"B1": "Market"}, "expr": "words"}, {"t": "c) Which feature is at A1? __B1__", "a": {"B1": "Station"}, "expr": "words", "accept": ["railway station"]}, {"t": "d) Grid reference of the Zoo: __B1__", "a": {"B1": "F5"}}, {"t": "e) Grid reference of the Museum: __B1__", "a": {"B1": "C2"}}, {"t": "f) Through which squares does the Lake stretch? (separate with commas) __B1__", "a": {"B1": "D2, D3, E3"}, "expr": "glist"}, {"t": "g) How many squares does the Fort cover? __B1__", "a": {"B1": "2"}}], "sol": "Read the column letter along the bottom, then the row number up the side.\na) Temple\nb) Market\nc) Station\nd) F5\ne) C2\nf) D2, D3 and E3\ng) 2 (B5 and C5)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 304 256\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" x=\"26\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"184\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"8\" width=\"44\" height=\"44\"/><text class=\"po\" x=\"48.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><text class=\"po\" x=\"92.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><text class=\"po\" x=\"136.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><text class=\"po\" x=\"180.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><text class=\"po\" x=\"224.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><text class=\"po\" x=\"268.0\" y=\"242.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><text class=\"po\" x=\"16.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"16.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"16.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"16.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"16.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"185\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"48.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Station</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"71\" y=\"9\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"114.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Fort</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"97\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"97\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"194.7\" y=\"132.7\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Lake</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"268.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Zoo</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"136.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Museum</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"53\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"97\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"48.0\" y=\"96.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Park</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"185\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"268.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Temple</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"224.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Market</text></svg>"}, {"kind": "blank", "p": "A map of a zoo:", "tag": "", "marks": "", "flat": [{"t": "a) Which animal is at A3? __B1__", "a": {"B1": "Tigers"}, "expr": "words"}, {"t": "b) Which animal is at E1? __B1__", "a": {"B1": "Giraffes"}, "expr": "words"}, {"t": "c) Grid reference of the Aquarium: __B1__", "a": {"B1": "D2"}}, {"t": "d) Grid reference of the Snakes: __B1__", "a": {"B1": "F3"}}, {"t": "e) Which animal is in the square directly below the Pandas? __B1__", "a": {"B1": "Snakes"}, "expr": "words"}], "sol": "a) Tigers\nb) Giraffes\nc) D2\nd) F3\ne) Pandas are at F4, so the square below is F3: Snakes", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 304 212\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" x=\"26\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"8\" width=\"44\" height=\"44\"/><text class=\"po\" x=\"48.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><text class=\"po\" x=\"92.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><text class=\"po\" x=\"136.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><text class=\"po\" x=\"180.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><text class=\"po\" x=\"224.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><text class=\"po\" x=\"268.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><text class=\"po\" x=\"16.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"16.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"16.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"16.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"48.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Tigers</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"9\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"158.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:8.5px\">Elephants</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"224.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:8.5px\">Giraffes</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"71\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"92.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:8.5px\">Penguins</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"97\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"180.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:8.5px\">Aquarium</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"268.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Snakes</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"136.0\" y=\"68.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Bus</text><text class=\"lb\" x=\"136.0\" y=\"79.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">stop</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"268.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Pandas</text></svg>"}]}, {"id": "s2", "label": "Ex 15B", "sub": "Locating points", "slides": [{"kind": "blank", "p": "In this food market the letters and numbers label the grid lines, so each stall is at a point.", "tag": "", "marks": "", "flat": [{"t": "a) Position of Chaat: __B1__", "a": {"B1": "B8"}}, {"t": "b) Position of Books: __B1__", "a": {"B1": "E4"}}, {"t": "c) Position of Cakes: __B1__", "a": {"B1": "G2"}}, {"t": "d) Which stall is at A5? __B1__", "a": {"B1": "Juice"}, "expr": "words"}, {"t": "e) Which stall is at G4? __B1__", "a": {"B1": "Kulfi"}, "expr": "words"}, {"t": "f) Which stall is at E6? __B1__", "a": {"B1": "Toys"}, "expr": "words"}], "sol": "Read the letter below the point, then the number beside it.\na) B8\nb) E4\nc) G2\nd) Juice\ne) Kulfi\nf) Toys", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 264 258\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"26\" y2=\"10\"/><text class=\"po\" x=\"26.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><line style=\"stroke:var(--rule)\" x1=\"54\" y1=\"206\" x2=\"54\" y2=\"10\"/><text class=\"po\" x=\"54.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><line style=\"stroke:var(--rule)\" x1=\"82\" y1=\"206\" x2=\"82\" y2=\"10\"/><text class=\"po\" x=\"82.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><line style=\"stroke:var(--rule)\" x1=\"110\" y1=\"206\" x2=\"110\" y2=\"10\"/><text class=\"po\" x=\"110.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><line style=\"stroke:var(--rule)\" x1=\"138\" y1=\"206\" x2=\"138\" y2=\"10\"/><text class=\"po\" x=\"138.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><line style=\"stroke:var(--rule)\" x1=\"166\" y1=\"206\" x2=\"166\" y2=\"10\"/><text class=\"po\" x=\"166.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><line style=\"stroke:var(--rule)\" x1=\"194\" y1=\"206\" x2=\"194\" y2=\"10\"/><text class=\"po\" x=\"194.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">G</text><line style=\"stroke:var(--rule)\" x1=\"222\" y1=\"206\" x2=\"222\" y2=\"10\"/><text class=\"po\" x=\"222.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">H</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"222\" y2=\"206\"/><text class=\"po\" x=\"14.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"178\" x2=\"222\" y2=\"178\"/><text class=\"po\" x=\"14.0\" y=\"178.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"150\" x2=\"222\" y2=\"150\"/><text class=\"po\" x=\"14.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"122\" x2=\"222\" y2=\"122\"/><text class=\"po\" x=\"14.0\" y=\"122.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"94\" x2=\"222\" y2=\"94\"/><text class=\"po\" x=\"14.0\" y=\"94.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"66\" x2=\"222\" y2=\"66\"/><text class=\"po\" x=\"14.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"38\" x2=\"222\" y2=\"38\"/><text class=\"po\" x=\"14.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"10\" x2=\"222\" y2=\"10\"/><text class=\"po\" x=\"14.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8</text><circle class=\"dr\" cx=\"54\" cy=\"10\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"1.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Chaat</text><circle class=\"dr\" cx=\"194\" cy=\"10\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"1.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Dosa</text><circle class=\"dr\" cx=\"26\" cy=\"94\" r=\"4\"/><text class=\"al\" x=\"30.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Juice</text><circle class=\"dr\" cx=\"138\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"142.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Books</text><circle class=\"dr\" cx=\"138\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"142.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Toys</text><circle class=\"dr\" cx=\"194\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Kulfi</text><circle class=\"dr\" cx=\"54\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Pizza</text><circle class=\"dr\" cx=\"194\" cy=\"178\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"169.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Cakes</text></svg>"}, {"kind": "blank", "p": "The points A4, C7, F4, C1 are joined in order and back to A4.", "tag": "", "marks": "", "flat": [{"t": "What shape is formed? __B1__", "a": {"B1": "kite"}, "expr": "words"}], "sol": "Joining the points in order\nA4 to C7 and A4 to C1 are equal; C7 to F4 and C1 to F4 are equal.\nTwo pairs of equal adjacent sides: a kite.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 236 258\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"26\" y2=\"10\"/><text class=\"po\" x=\"26.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><line style=\"stroke:var(--rule)\" x1=\"54\" y1=\"206\" x2=\"54\" y2=\"10\"/><text class=\"po\" x=\"54.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><line style=\"stroke:var(--rule)\" x1=\"82\" y1=\"206\" x2=\"82\" y2=\"10\"/><text class=\"po\" x=\"82.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><line style=\"stroke:var(--rule)\" x1=\"110\" y1=\"206\" x2=\"110\" y2=\"10\"/><text class=\"po\" x=\"110.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><line style=\"stroke:var(--rule)\" x1=\"138\" y1=\"206\" x2=\"138\" y2=\"10\"/><text class=\"po\" x=\"138.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><line style=\"stroke:var(--rule)\" x1=\"166\" y1=\"206\" x2=\"166\" y2=\"10\"/><text class=\"po\" x=\"166.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><line style=\"stroke:var(--rule)\" x1=\"194\" y1=\"206\" x2=\"194\" y2=\"10\"/><text class=\"po\" x=\"194.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">G</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"194\" y2=\"206\"/><text class=\"po\" x=\"14.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"178\" x2=\"194\" y2=\"178\"/><text class=\"po\" x=\"14.0\" y=\"178.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"150\" x2=\"194\" y2=\"150\"/><text class=\"po\" x=\"14.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"122\" x2=\"194\" y2=\"122\"/><text class=\"po\" x=\"14.0\" y=\"122.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"94\" x2=\"194\" y2=\"94\"/><text class=\"po\" x=\"14.0\" y=\"94.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"66\" x2=\"194\" y2=\"66\"/><text class=\"po\" x=\"14.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"38\" x2=\"194\" y2=\"38\"/><text class=\"po\" x=\"14.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"10\" x2=\"194\" y2=\"10\"/><text class=\"po\" x=\"14.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8</text><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"26\" y1=\"122\" x2=\"82\" y2=\"38\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"82\" y1=\"38\" x2=\"166\" y2=\"122\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"166\" y1=\"122\" x2=\"82\" y2=\"206\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"82\" y1=\"206\" x2=\"26\" y2=\"122\"/><circle class=\"dr\" cx=\"26\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"30.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">A4</text><circle class=\"dr\" cx=\"82\" cy=\"38\" r=\"4\"/><text class=\"al\" x=\"86.0\" y=\"29.0\" text-anchor=\"start\" dominant-baseline=\"middle\">C7</text><circle class=\"dr\" cx=\"166\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"170.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">F4</text><circle class=\"dr\" cx=\"82\" cy=\"206\" r=\"4\"/><text class=\"al\" x=\"86.0\" y=\"197.0\" text-anchor=\"start\" dominant-baseline=\"middle\">C1</text></svg>"}]}, {"id": "s3", "label": "Ex 15C", "sub": "Coordinates", "slides": [{"kind": "blank", "p": "Coordinates are written (x-coordinate, y-coordinate).", "tag": "", "marks": "", "flat": [{"t": "a) x-coordinate of P: __B1__", "a": {"B1": "4"}}, {"t": "b) x-coordinate of R: __B1__", "a": {"B1": "6"}}, {"t": "c) y-coordinate of S: __B1__", "a": {"B1": "3"}}, {"t": "d) y-coordinate of T: __B1__", "a": {"B1": "0"}}, {"t": "e) coordinates of P: __B1__", "a": {"B1": "(4, 2)"}, "expr": "coord"}, {"t": "f) coordinates of Q: __B1__", "a": {"B1": "(1, 4)"}, "expr": "coord"}, {"t": "g) coordinates of U: __B1__", "a": {"B1": "(0, 4)"}, "expr": "coord"}, {"t": "h) coordinates of T: __B1__", "a": {"B1": "(3, 0)"}, "expr": "coord"}, {"t": "i) coordinates of the origin O: __B1__", "a": {"B1": "(0, 0)"}, "expr": "coord"}], "sol": "Go across first (x), then up (y).\nP = (4, 2)\nQ = (1, 4)\nR = (6, 5)\nS = (3, 3)\nT = (3, 0)\nU = (0, 4)\nO = (0, 0)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 206 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"144\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"144\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"144\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"144\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"144\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"144\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"184\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"184\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"184\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"184\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"184\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"184\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"192.0\" y2=\"144.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"28.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"54.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"80.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"106.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"132.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"158.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"184.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"19.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"19.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"19.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"19.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"19.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"194.0\" y=\"136.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"38.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"132\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"136.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">P</text><circle class=\"dr\" cx=\"54\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Q</text><circle class=\"dr\" cx=\"184\" cy=\"14\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"5.0\" text-anchor=\"start\" dominant-baseline=\"middle\">R</text><circle class=\"dr\" cx=\"106\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">S</text><circle class=\"dr\" cx=\"106\" cy=\"144\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"135.0\" text-anchor=\"start\" dominant-baseline=\"middle\">T</text><circle class=\"dr\" cx=\"28\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"32.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">U</text></svg>"}, {"kind": "blank", "p": "Decode the message using the grid:", "tag": "", "marks": "", "flat": [{"t": "word 1: (2, 3), (3, 4), (4, 3), (1, 2) → __B1__", "a": {"B1": "HAVE"}, "expr": "words"}, {"t": "word 2: (3, 4) → __B1__", "a": {"B1": "A"}, "expr": "words"}, {"t": "word 3: (1, 5), (0, 0), (0, 0), (6, 1) → __B1__", "a": {"B1": "GOOD"}, "expr": "words"}, {"t": "word 4: (6, 1), (3, 4), (5, 4) → __B1__", "a": {"B1": "DAY"}, "expr": "words"}], "sol": "Find each point on the grid and read its letter.\nHAVE A GOOD DAY", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 206 170\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"144\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"144\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"144\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"144\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"144\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"144\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"184\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"184\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"184\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"184\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"184\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"184\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"192.0\" y2=\"144.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"28.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"54.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"80.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"106.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"132.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"158.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"184.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"19.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"19.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"19.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"19.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"19.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"194.0\" y=\"136.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"38.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"54\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">E</text><circle class=\"dr\" cx=\"106\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">A</text><circle class=\"dr\" cx=\"132\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"136.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">V</text><circle class=\"dr\" cx=\"80\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">H</text><circle class=\"dr\" cx=\"54\" cy=\"14\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"5.0\" text-anchor=\"start\" dominant-baseline=\"middle\">G</text><circle class=\"dr\" cx=\"184\" cy=\"118\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"109.0\" text-anchor=\"start\" dominant-baseline=\"middle\">D</text><circle class=\"dr\" cx=\"158\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"162.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Y</text></svg>"}, {"kind": "blank", "p": "A map of an athletics stadium:", "tag": "", "marks": "", "flat": [{"t": "a) coordinates of the high jump: __B1__", "a": {"B1": "(4, 3)"}, "expr": "coord"}, {"t": "b) coordinates of the long jump: __B1__", "a": {"B1": "(5, 5)"}, "expr": "coord"}, {"t": "c) Which event is at (1, 4)? __B1__", "a": {"B1": "sprints"}, "expr": "words"}, {"t": "d) Which event has the same x-coordinate as the javelin, and is highest up? __B1__", "a": {"B1": "shot put"}, "expr": "words"}, {"t": "e) Which event has the same y-coordinate as the pole vault, on its left? __B1__", "a": {"B1": "shot put"}, "expr": "words"}], "sol": "a) (4, 3)\nb) (5, 5)\nc) sprints\nd) javelin x = 1: sprints (1, 4) and shot put (1, 5); the highest is the shot put\ne) pole vault y = 5: shot put (1, 5) is on its left", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 206 196\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"170\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"170\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"170\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"170\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"170\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"170\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"184\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"184\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"184\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"184\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"184\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"184\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"184\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"170.0\" x2=\"192.0\" y2=\"170.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"28.0\" y1=\"170.0\" x2=\"28.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"54.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"80.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"106.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"132.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"158.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"184.0\" y=\"181.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><text class=\"po\" x=\"19.0\" y=\"144.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"19.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"19.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"19.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"19.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"19.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><text class=\"lb\" x=\"194.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"38.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"132\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"136.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">high jump</text><circle class=\"dr\" cx=\"158\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"162.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">long jump</text><circle class=\"dr\" cx=\"54\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">shot put</text><circle class=\"dr\" cx=\"106\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">pole vault</text><circle class=\"dr\" cx=\"54\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">sprints</text><circle class=\"dr\" cx=\"158\" cy=\"118\" r=\"4\"/><text class=\"al\" x=\"162.0\" y=\"109.0\" text-anchor=\"start\" dominant-baseline=\"middle\">hurdles</text><circle class=\"dr\" cx=\"54\" cy=\"118\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"109.0\" text-anchor=\"start\" dominant-baseline=\"middle\">javelin</text></svg>"}, {"kind": "blank", "p": "Points on the axes:", "tag": "", "marks": "", "flat": [{"t": "a) A point on the x-axis always has y-coordinate __B1__", "a": {"B1": "0"}}, {"t": "b) A point on the y-axis always has x-coordinate __B1__", "a": {"B1": "0"}}], "sol": "a) 0\nb) 0"}, {"kind": "mcq", "text": "Are (1, 6) and (6, 1) the same point?", "opts": ["No: (1, 6) is 1 across and 6 up; (6, 1) is 6 across and 1 up", "Yes, they use the same numbers", "Only on the x-axis", "Only if x = y"], "correct": 0, "tag": "", "sol": "The order matters: the first number is always the x-coordinate."}]}, {"id": "s4", "label": "Ex 15D", "sub": "Positive and negative coordinates", "slides": [{"kind": "blank", "p": "The axes now extend in both directions: left of O and below O are negative.", "tag": "", "marks": "", "flat": [{"t": "a) x-coordinate of Z: __B1__", "a": {"B1": "4"}}, {"t": "b) x-coordinate of S: __B1__", "a": {"B1": "-5"}}, {"t": "c) y-coordinate of T: __B1__", "a": {"B1": "0"}}, {"t": "d) y-coordinate of Q: __B1__", "a": {"B1": "-4"}}, {"t": "e) coordinates of P: __B1__", "a": {"B1": "(-2, 1)"}, "expr": "coord"}, {"t": "f) coordinates of V: __B1__", "a": {"B1": "(1, -5)"}, "expr": "coord"}, {"t": "g) coordinates of U: __B1__", "a": {"B1": "(-4, -1)"}, "expr": "coord"}, {"t": "h) Which point has x-coordinate −3? __B1__", "a": {"B1": "Q"}}, {"t": "i) Which point has the same x- and y-coordinate? __B1__", "a": {"B1": "none"}, "accept": ["no point", "nothing"]}], "sol": "x first (left is negative), then y (down is negative).\nW = (2, 4)\nS = (−5, 3)\nR = (4, 2)\nP = (−2, 1)\nT = (−4, 0)\nU = (−4, −1)\nZ = (4, −2)\nQ = (−3, −4)\nV = (1, −5)\nh) Q\ni) none of the points has x = y", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 290\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"53\" y1=\"264\" x2=\"53\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"78\" y1=\"264\" x2=\"78\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"103\" y1=\"264\" x2=\"103\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"128\" y1=\"264\" x2=\"128\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"153\" y1=\"264\" x2=\"153\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"178\" y1=\"264\" x2=\"178\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"203\" y1=\"264\" x2=\"203\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"228\" y1=\"264\" x2=\"228\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"253\" y1=\"264\" x2=\"253\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"278\" y1=\"264\" x2=\"278\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"278\" y2=\"264\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"239\" x2=\"278\" y2=\"239\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"214\" x2=\"278\" y2=\"214\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"189\" x2=\"278\" y2=\"189\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"164\" x2=\"278\" y2=\"164\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"139\" x2=\"278\" y2=\"139\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"114\" x2=\"278\" y2=\"114\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"89\" x2=\"278\" y2=\"89\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"64\" x2=\"278\" y2=\"64\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"39\" x2=\"278\" y2=\"39\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"278\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"139.0\" x2=\"286.0\" y2=\"139.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"153.0\" y1=\"264.0\" x2=\"153.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"53.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"78.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"103.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"128.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"178.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"203.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"228.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"253.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"278.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"144.0\" y=\"264.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"144.0\" y=\"239.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"144.0\" y=\"214.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"144.0\" y=\"189.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"144.0\" y=\"164.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"144.0\" y=\"114.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"144.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"144.0\" y=\"64.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"144.0\" y=\"39.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"144.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"288.0\" y=\"131.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"163.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"203\" cy=\"39\" r=\"4\"/><text class=\"al\" x=\"207.0\" y=\"30.0\" text-anchor=\"start\" dominant-baseline=\"middle\">W</text><circle class=\"dr\" cx=\"28\" cy=\"64\" r=\"4\"/><text class=\"al\" x=\"32.0\" y=\"55.0\" text-anchor=\"start\" dominant-baseline=\"middle\">S</text><circle class=\"dr\" cx=\"253\" cy=\"89\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">R</text><circle class=\"dr\" cx=\"103\" cy=\"114\" r=\"4\"/><text class=\"al\" x=\"107.0\" y=\"105.0\" text-anchor=\"start\" dominant-baseline=\"middle\">P</text><circle class=\"dr\" cx=\"53\" cy=\"139\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"130.0\" text-anchor=\"start\" dominant-baseline=\"middle\">T</text><circle class=\"dr\" cx=\"53\" cy=\"164\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"155.0\" text-anchor=\"start\" dominant-baseline=\"middle\">U</text><circle class=\"dr\" cx=\"253\" cy=\"189\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"180.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Z</text><circle class=\"dr\" cx=\"78\" cy=\"239\" r=\"4\"/><text class=\"al\" x=\"82.0\" y=\"230.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Q</text><circle class=\"dr\" cx=\"178\" cy=\"264\" r=\"4\"/><text class=\"al\" x=\"182.0\" y=\"255.0\" text-anchor=\"start\" dominant-baseline=\"middle\">V</text></svg>"}, {"kind": "blank", "p": "Friends meet at a pizza shop, which is at the origin.", "tag": "", "marks": "", "flat": [{"t": "a) coordinates of Riya's house: __B1__", "a": {"B1": "(4, 1)"}, "expr": "coord"}, {"t": "b) coordinates of Sahil's house: __B1__", "a": {"B1": "(-2, 4)"}, "expr": "coord"}, {"t": "c) Who lives at (−5, −4)? __B1__", "a": {"B1": "Divya"}, "expr": "words"}, {"t": "d) Who lives closest to the pizza shop (fewest grid units along the lines)? __B1__", "a": {"B1": "Gaurav"}, "expr": "words", "accept": ["Riya"]}], "sol": "a) (4, 1)\nb) (−2, 4)\nc) Divya\nd) Gaurav (4 across, 1 down) and Riya (4 across, 1 up) are both 5 units away, so either answer is accepted.", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 290\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"53\" y1=\"264\" x2=\"53\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"78\" y1=\"264\" x2=\"78\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"103\" y1=\"264\" x2=\"103\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"128\" y1=\"264\" x2=\"128\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"153\" y1=\"264\" x2=\"153\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"178\" y1=\"264\" x2=\"178\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"203\" y1=\"264\" x2=\"203\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"228\" y1=\"264\" x2=\"228\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"253\" y1=\"264\" x2=\"253\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"278\" y1=\"264\" x2=\"278\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"278\" y2=\"264\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"239\" x2=\"278\" y2=\"239\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"214\" x2=\"278\" y2=\"214\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"189\" x2=\"278\" y2=\"189\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"164\" x2=\"278\" y2=\"164\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"139\" x2=\"278\" y2=\"139\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"114\" x2=\"278\" y2=\"114\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"89\" x2=\"278\" y2=\"89\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"64\" x2=\"278\" y2=\"64\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"39\" x2=\"278\" y2=\"39\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"278\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"139.0\" x2=\"286.0\" y2=\"139.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"153.0\" y1=\"264.0\" x2=\"153.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"53.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"78.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"103.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"128.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"178.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"203.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"228.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"253.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"278.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"144.0\" y=\"264.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"144.0\" y=\"239.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"144.0\" y=\"214.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"144.0\" y=\"189.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"144.0\" y=\"164.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"144.0\" y=\"114.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"144.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"144.0\" y=\"64.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"144.0\" y=\"39.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"144.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"288.0\" y=\"131.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"163.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"253\" cy=\"114\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"105.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Riya</text><circle class=\"dr\" cx=\"103\" cy=\"39\" r=\"4\"/><text class=\"al\" x=\"107.0\" y=\"30.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Sahil</text><circle class=\"dr\" cx=\"53\" cy=\"164\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"155.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Gaurav</text><circle class=\"dr\" cx=\"28\" cy=\"239\" r=\"4\"/><text class=\"al\" x=\"32.0\" y=\"230.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Divya</text><circle class=\"dr\" cx=\"203\" cy=\"239\" r=\"4\"/><text class=\"al\" x=\"207.0\" y=\"230.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Jordan</text><circle class=\"dr\" cx=\"153\" cy=\"139\" r=\"4\"/><text class=\"al\" x=\"157.0\" y=\"130.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Pizza</text></svg>"}, {"kind": "blank", "p": "Train stations in a city. The main station A is at the origin.", "tag": "", "marks": "", "flat": [{"t": "a) coordinates of station F: __B1__", "a": {"B1": "(-1, 3)"}, "expr": "coord"}, {"t": "b) coordinates of station L: __B1__", "a": {"B1": "(2, -2)"}, "expr": "coord"}, {"t": "c) Which station is at (−5, 1)? __B1__", "a": {"B1": "H"}, "expr": "words"}, {"t": "d) Which station is at (−4, −5)? __B1__", "a": {"B1": "K"}, "expr": "words"}, {"t": "e) Tanya lives at (−3, −2). Which station is closest? __B1__", "a": {"B1": "J"}, "expr": "words"}], "sol": "a) (−1, 3)\nb) (2, −2)\nc) H\nd) K\ne) J at (−3, −1) is just 1 unit away", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 290\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"53\" y1=\"264\" x2=\"53\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"78\" y1=\"264\" x2=\"78\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"103\" y1=\"264\" x2=\"103\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"128\" y1=\"264\" x2=\"128\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"153\" y1=\"264\" x2=\"153\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"178\" y1=\"264\" x2=\"178\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"203\" y1=\"264\" x2=\"203\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"228\" y1=\"264\" x2=\"228\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"253\" y1=\"264\" x2=\"253\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"278\" y1=\"264\" x2=\"278\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"278\" y2=\"264\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"239\" x2=\"278\" y2=\"239\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"214\" x2=\"278\" y2=\"214\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"189\" x2=\"278\" y2=\"189\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"164\" x2=\"278\" y2=\"164\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"139\" x2=\"278\" y2=\"139\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"114\" x2=\"278\" y2=\"114\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"89\" x2=\"278\" y2=\"89\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"64\" x2=\"278\" y2=\"64\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"39\" x2=\"278\" y2=\"39\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"278\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"139.0\" x2=\"286.0\" y2=\"139.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"153.0\" y1=\"264.0\" x2=\"153.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"53.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"78.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"103.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"128.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"178.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"203.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"228.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"253.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"278.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"144.0\" y=\"264.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"144.0\" y=\"239.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"144.0\" y=\"214.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"144.0\" y=\"189.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"144.0\" y=\"164.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"144.0\" y=\"114.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"144.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"144.0\" y=\"64.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"144.0\" y=\"39.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"144.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"288.0\" y=\"131.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"163.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"153\" cy=\"139\" r=\"4\"/><text class=\"al\" x=\"157.0\" y=\"130.0\" text-anchor=\"start\" dominant-baseline=\"middle\">A</text><circle class=\"dr\" cx=\"203\" cy=\"89\" r=\"4\"/><text class=\"al\" x=\"207.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">B</text><circle class=\"dr\" cx=\"253\" cy=\"39\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"30.0\" text-anchor=\"start\" dominant-baseline=\"middle\">C</text><circle class=\"dr\" cx=\"103\" cy=\"114\" r=\"4\"/><text class=\"al\" x=\"107.0\" y=\"105.0\" text-anchor=\"start\" dominant-baseline=\"middle\">E</text><circle class=\"dr\" cx=\"128\" cy=\"64\" r=\"4\"/><text class=\"al\" x=\"132.0\" y=\"55.0\" text-anchor=\"start\" dominant-baseline=\"middle\">F</text><circle class=\"dr\" cx=\"78\" cy=\"39\" r=\"4\"/><text class=\"al\" x=\"82.0\" y=\"30.0\" text-anchor=\"start\" dominant-baseline=\"middle\">G</text><circle class=\"dr\" cx=\"28\" cy=\"114\" r=\"4\"/><text class=\"al\" x=\"32.0\" y=\"105.0\" text-anchor=\"start\" dominant-baseline=\"middle\">H</text><circle class=\"dr\" cx=\"128\" cy=\"164\" r=\"4\"/><text class=\"al\" x=\"132.0\" y=\"155.0\" text-anchor=\"start\" dominant-baseline=\"middle\">I</text><circle class=\"dr\" cx=\"78\" cy=\"164\" r=\"4\"/><text class=\"al\" x=\"82.0\" y=\"155.0\" text-anchor=\"start\" dominant-baseline=\"middle\">J</text><circle class=\"dr\" cx=\"53\" cy=\"264\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"255.0\" text-anchor=\"start\" dominant-baseline=\"middle\">K</text><circle class=\"dr\" cx=\"203\" cy=\"189\" r=\"4\"/><text class=\"al\" x=\"207.0\" y=\"180.0\" text-anchor=\"start\" dominant-baseline=\"middle\">L</text><circle class=\"dr\" cx=\"253\" cy=\"214\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"205.0\" text-anchor=\"start\" dominant-baseline=\"middle\">M</text><circle class=\"dr\" cx=\"253\" cy=\"264\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"255.0\" text-anchor=\"start\" dominant-baseline=\"middle\">N</text></svg>"}, {"kind": "blank", "p": "On this map 1 grid unit represents 10 km.", "tag": "", "marks": "", "flat": [{"t": "a) distance from Beachport (−4, 4) to Hilltown (2, 4): __B1__ km", "a": {"B1": "60"}}, {"t": "b) distance from Cedarville (3, −1) to Dev at (−2, −1): __B1__ km", "a": {"B1": "50"}}, {"t": "c) distance from Stanley (−3, −2) to Belinda at (−3, 3): __B1__ km", "a": {"B1": "50"}}], "sol": "Count the grid units along the line, then × 10.\na) 6 units = 60 km\nb) 5 units = 50 km\nc) 5 units = 50 km", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 310 274\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"248\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"248\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"248\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"248\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"248\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"248\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"248\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"210\" y1=\"248\" x2=\"210\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"236\" y1=\"248\" x2=\"236\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"262\" y1=\"248\" x2=\"262\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"288\" y1=\"248\" x2=\"288\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"248\" x2=\"288\" y2=\"248\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"222\" x2=\"288\" y2=\"222\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"288\" y2=\"196\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"288\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"288\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"288\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"288\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"288\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"288\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"288\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"296.0\" y2=\"144.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"158.0\" y1=\"248.0\" x2=\"158.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"54.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"80.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"106.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"132.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"184.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"210.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"236.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"262.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"288.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"149.0\" y=\"248.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"149.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"149.0\" y=\"196.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"149.0\" y=\"170.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"149.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"149.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"149.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"149.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"149.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"298.0\" y=\"136.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"168.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"54\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Beachport</text><circle class=\"dr\" cx=\"210\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"214.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Hilltown</text><circle class=\"dr\" cx=\"236\" cy=\"170\" r=\"4\"/><text class=\"al\" x=\"240.0\" y=\"161.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Cedarville</text><circle class=\"dr\" cx=\"106\" cy=\"170\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"161.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Dev</text><circle class=\"dr\" cx=\"80\" cy=\"196\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"187.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Stanley</text><circle class=\"dr\" cx=\"80\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Belinda</text></svg>"}]}, {"id": "s5", "label": "Ex 15E", "sub": "Compass points", "slides": [{"kind": "blank", "p": "North points up the page. In which direction must we travel to go from (type e.g. north, southeast or SE):", "tag": "", "marks": "", "flat": [{"t": "a) D to B → __B1__", "a": {"B1": "north"}, "accept": ["N", "n"]}, {"t": "b) C to A → __B1__", "a": {"B1": "east"}, "accept": ["E", "e"]}], "sol": "a) D(−2, −3) to B(−2, 4): straight up → north\nb) C(−1, 2) to A(3, 2): straight right → east", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 258 274\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"248\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"248\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"248\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"248\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"248\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"248\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"248\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"210\" y1=\"248\" x2=\"210\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"236\" y1=\"248\" x2=\"236\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"248\" x2=\"236\" y2=\"248\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"222\" x2=\"236\" y2=\"222\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"236\" y2=\"196\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"236\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"236\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"236\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"236\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"236\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"236\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"236\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"244.0\" y2=\"144.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"132.0\" y1=\"248.0\" x2=\"132.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"54.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"80.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"106.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"158.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"184.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"210.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"236.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"123.0\" y=\"248.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"123.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"123.0\" y=\"196.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"123.0\" y=\"170.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"123.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"123.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"123.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"123.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"123.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"246.0\" y=\"136.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"142.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"210\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"214.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">A</text><circle class=\"dr\" cx=\"80\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">B</text><circle class=\"dr\" cx=\"106\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">C</text><circle class=\"dr\" cx=\"80\" cy=\"222\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"213.0\" text-anchor=\"start\" dominant-baseline=\"middle\">D</text><line class=\"ln\" x1=\"240.0\" y1=\"34.0\" x2=\"240.0\" y2=\"10.0\" marker-end=\"url(#ah)\"/><text class=\"lb\" x=\"240.0\" y=\"4.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">N</text></svg>"}, {"kind": "blank", "p": "Which of these points is south of P(−4, 3)?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "(−4, −2)"}, "expr": "coord"}], "sol": "South means directly below: the same x-coordinate (−4) and a smaller y. Of (−2, 5), (−4, −2) and (3, 3), only (−4, −2)."}, {"kind": "blank", "p": "Which of these points is northwest of Q(3, −2): (1, 0), (5, 0) or (1, −4)?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "(1, 0)"}, "expr": "coord"}], "sol": "Northwest: left 2 and up 2 → (1, 0)"}, {"kind": "blank", "p": "A playground map. 1 grid unit represents 1 m.", "tag": "", "marks": "", "flat": [{"t": "a) distance from the spider net to the monkey bars: __B1__ m", "a": {"B1": "5"}}, {"t": "b) direction from the spider net to the slide: __B1__", "a": {"B1": "west"}, "accept": ["W", "w"]}, {"t": "c) The swings are 5 m south of the slide. Coordinates: __B1__", "a": {"B1": "(-3, -2)"}, "expr": "coord"}, {"t": "d) distance from the swings to the monkey bars: __B1__ m", "a": {"B1": "5"}}], "sol": "a) (2, 3) to (2, −2): 5 m\nb) the slide is directly left of the spider net: west\nc) (−3, 3 − 5) = (−3, −2)\nd) (−3, −2) to (2, −2): 5 m", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 258 222\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"196\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"196\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"196\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"196\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"196\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"196\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"210\" y1=\"196\" x2=\"210\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"236\" y1=\"196\" x2=\"236\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"236\" y2=\"196\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"236\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"236\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"236\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"236\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"236\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"236\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"236\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"118.0\" x2=\"244.0\" y2=\"118.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"132.0\" y1=\"196.0\" x2=\"132.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"54.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"80.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"106.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"158.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"184.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"210.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"236.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"123.0\" y=\"196.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"123.0\" y=\"170.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"123.0\" y=\"144.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"123.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"123.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"123.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"123.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"lb\" x=\"246.0\" y=\"110.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"142.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"54\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Slide</text><circle class=\"dr\" cx=\"184\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Spider net</text><circle class=\"dr\" cx=\"210\" cy=\"144\" r=\"4\"/><text class=\"al\" x=\"214.0\" y=\"135.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Entrance</text><circle class=\"dr\" cx=\"184\" cy=\"170\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"161.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Monkey bars</text><line class=\"ln\" x1=\"240.0\" y1=\"34.0\" x2=\"240.0\" y2=\"10.0\" marker-end=\"url(#ah)\"/><text class=\"lb\" x=\"240.0\" y=\"4.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">N</text></svg>"}, {"kind": "blank", "p": "Erin hikes from S to T, T to U, U to V and V to W. North is up; 1 unit represents 2 km.", "tag": "", "marks": "", "flat": [{"t": "a) direction on day 1 (S to T): __B1__", "a": {"B1": "northeast"}, "accept": ["NE", "ne"]}, {"t": "b) distance on day 2 (T to U): __B1__ km", "a": {"B1": "6"}}, {"t": "c) direction on day 3 (U to V): __B1__", "a": {"B1": "southwest"}, "accept": ["SW", "sw"]}, {"t": "d) distance on day 4 (V to W): __B1__ km", "a": {"B1": "6"}}, {"t": "e) direction from W back to S: __B1__", "a": {"B1": "southwest"}, "accept": ["SW", "sw"]}], "sol": "a) right 5, up 5: northeast\nb) 3 units × 2 = 6 km\nc) left 3, down 3: southwest\nd) 3 units × 2 = 6 km\ne) left 2, down 2: southwest", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 310 222\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"196\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"196\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"196\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"196\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"196\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"196\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"210\" y1=\"196\" x2=\"210\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"236\" y1=\"196\" x2=\"236\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"262\" y1=\"196\" x2=\"262\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"288\" y1=\"196\" x2=\"288\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"288\" y2=\"196\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"288\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"288\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"288\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"288\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"288\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"288\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"288\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"144.0\" x2=\"296.0\" y2=\"144.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"158.0\" y1=\"196.0\" x2=\"158.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"54.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"80.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"106.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"132.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"184.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"210.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"236.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"262.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"288.0\" y=\"155.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"149.0\" y=\"196.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"149.0\" y=\"170.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"149.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"149.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"149.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"149.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"149.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"298.0\" y=\"136.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"168.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"54\" y1=\"170\" x2=\"184\" y2=\"40\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"184\" y1=\"40\" x2=\"262\" y2=\"40\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"262\" y1=\"40\" x2=\"184\" y2=\"118\"/><line style=\"stroke:var(--danger);stroke-width:2\" x1=\"184\" y1=\"118\" x2=\"106\" y2=\"118\"/><circle class=\"dr\" cx=\"54\" cy=\"170\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"161.0\" text-anchor=\"start\" dominant-baseline=\"middle\">S</text><circle class=\"dr\" cx=\"184\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">T</text><circle class=\"dr\" cx=\"262\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"266.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">U</text><circle class=\"dr\" cx=\"184\" cy=\"118\" r=\"4\"/><text class=\"al\" x=\"188.0\" y=\"109.0\" text-anchor=\"start\" dominant-baseline=\"middle\">V</text><circle class=\"dr\" cx=\"106\" cy=\"118\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"109.0\" text-anchor=\"start\" dominant-baseline=\"middle\">W</text><line class=\"ln\" x1=\"292.0\" y1=\"34.0\" x2=\"292.0\" y2=\"10.0\" marker-end=\"url(#ah)\"/><text class=\"lb\" x=\"292.0\" y=\"4.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">N</text></svg>"}]}, {"id": "s6", "label": "Review 15A", "sub": "Review set 15A", "slides": [{"kind": "blank", "p": "A swimming centre map:", "tag": "", "marks": "", "flat": [{"t": "a) What is at A3? __B1__", "a": {"B1": "Change rooms"}, "expr": "words"}, {"t": "b) How many squares does the main pool cover? __B1__", "a": {"B1": "6"}}, {"t": "c) Grid reference of the diving area: __B1__", "a": {"B1": "F2"}}, {"t": "d) Grid reference of the canteen: __B1__", "a": {"B1": "C1"}}], "sol": "a) Change rooms\nb) 6\nc) F2\nd) C1", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 304 212\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" x=\"26\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"140\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"96\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"52\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"26\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"70\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"114\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"158\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"202\" y=\"8\" width=\"44\" height=\"44\"/><rect class=\"cell\" x=\"246\" y=\"8\" width=\"44\" height=\"44\"/><text class=\"po\" x=\"48.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><text class=\"po\" x=\"92.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><text class=\"po\" x=\"136.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><text class=\"po\" x=\"180.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><text class=\"po\" x=\"224.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><text class=\"po\" x=\"268.0\" y=\"198.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><text class=\"po\" x=\"16.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"16.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"16.0\" y=\"74.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"16.0\" y=\"30.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"136.0\" y=\"24.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Kids</text><text class=\"lb\" x=\"136.0\" y=\"35.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">pool</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"9\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"9\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"246.0\" y=\"24.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Water</text><text class=\"lb\" x=\"246.0\" y=\"35.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">slides</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"48.0\" y=\"68.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Change</text><text class=\"lb\" x=\"48.0\" y=\"79.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">rooms</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"97\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"97\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"97\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"53\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"159\" y=\"53\" width=\"42\" height=\"42\"/><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"203\" y=\"53\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"180.0\" y=\"90.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Main</text><text class=\"lb\" x=\"180.0\" y=\"101.5\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">pool</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"247\" y=\"97\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"268.0\" y=\"118.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Diving</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"27\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"48.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:8.5px\">Entrance</text><rect class=\"shd\" style=\"fill-opacity:.25\" x=\"115\" y=\"141\" width=\"42\" height=\"42\"/><text class=\"lb\" x=\"136.0\" y=\"162.0\" text-anchor=\"middle\" dominant-baseline=\"middle\" style=\"font-size:9.5px\">Canteen</text></svg>"}, {"kind": "blank", "p": "Look at the plane:", "tag": "", "marks": "", "flat": [{"t": "a) coordinates of H: __B1__", "a": {"B1": "(-2, 3)"}, "expr": "coord"}, {"t": "b) coordinates of F: __B1__", "a": {"B1": "(3, 2)"}, "expr": "coord"}, {"t": "c) coordinates of K: __B1__", "a": {"B1": "(-4, 1)"}, "expr": "coord"}, {"t": "d) coordinates of G: __B1__", "a": {"B1": "(-3, -2)"}, "expr": "coord"}, {"t": "e) Which point has x-coordinate 4? __B1__", "a": {"B1": "I"}}, {"t": "f) Which points have y-coordinate 2? (separate with commas) __B1__", "a": {"B1": "E, F"}, "expr": "glist"}], "sol": "H = (−2, 3)\nF = (3, 2)\nK = (−4, 1)\nJ = (−1, −1)\nG = (−3, −2)\nI = (4, −3)\nE = (2, 2)", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 310 248\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"222\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"54\" y1=\"222\" x2=\"54\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"80\" y1=\"222\" x2=\"80\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"106\" y1=\"222\" x2=\"106\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"132\" y1=\"222\" x2=\"132\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"158\" y1=\"222\" x2=\"158\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"184\" y1=\"222\" x2=\"184\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"210\" y1=\"222\" x2=\"210\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"236\" y1=\"222\" x2=\"236\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"262\" y1=\"222\" x2=\"262\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"288\" y1=\"222\" x2=\"288\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"222\" x2=\"288\" y2=\"222\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"196\" x2=\"288\" y2=\"196\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"170\" x2=\"288\" y2=\"170\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"144\" x2=\"288\" y2=\"144\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"118\" x2=\"288\" y2=\"118\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"92\" x2=\"288\" y2=\"92\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"66\" x2=\"288\" y2=\"66\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"40\" x2=\"288\" y2=\"40\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"288\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"118.0\" x2=\"296.0\" y2=\"118.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"158.0\" y1=\"222.0\" x2=\"158.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"54.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"80.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"106.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"132.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"184.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"210.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"236.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"262.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"288.0\" y=\"129.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"149.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"149.0\" y=\"196.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"149.0\" y=\"170.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"149.0\" y=\"144.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"149.0\" y=\"92.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"149.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"149.0\" y=\"40.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"149.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"lb\" x=\"298.0\" y=\"110.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"168.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"106\" cy=\"40\" r=\"4\"/><text class=\"al\" x=\"110.0\" y=\"31.0\" text-anchor=\"start\" dominant-baseline=\"middle\">H</text><circle class=\"dr\" cx=\"236\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"240.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">F</text><circle class=\"dr\" cx=\"54\" cy=\"92\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"83.0\" text-anchor=\"start\" dominant-baseline=\"middle\">K</text><circle class=\"dr\" cx=\"132\" cy=\"144\" r=\"4\"/><text class=\"al\" x=\"136.0\" y=\"135.0\" text-anchor=\"start\" dominant-baseline=\"middle\">J</text><circle class=\"dr\" cx=\"80\" cy=\"170\" r=\"4\"/><text class=\"al\" x=\"84.0\" y=\"161.0\" text-anchor=\"start\" dominant-baseline=\"middle\">G</text><circle class=\"dr\" cx=\"262\" cy=\"196\" r=\"4\"/><text class=\"al\" x=\"266.0\" y=\"187.0\" text-anchor=\"start\" dominant-baseline=\"middle\">I</text><circle class=\"dr\" cx=\"210\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"214.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">E</text></svg>"}, {"kind": "blank", "p": "Directions (north is up):", "tag": "", "marks": "", "flat": [{"t": "a) from K(−4, 1) to H(−2, 3): __B1__", "a": {"B1": "northeast"}, "accept": ["NE", "ne"]}, {"t": "b) from E(2, 2) to F(3, 2): __B1__", "a": {"B1": "east"}, "accept": ["E", "e"]}], "sol": "a) right 2, up 2: northeast\nb) right: east"}]}, {"id": "s7", "label": "Review 15B", "sub": "Review set 15B", "slides": [{"kind": "blank", "p": "Map of a food fair:", "tag": "", "marks": "", "flat": [{"t": "a) Grid reference of the Chaat stall: __B1__", "a": {"B1": "B8"}}, {"t": "b) Which stall is at E4? __B1__", "a": {"B1": "Books"}, "expr": "words"}], "sol": "a) B8\nb) Books", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 264 258\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"26\" y2=\"10\"/><text class=\"po\" x=\"26.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><line style=\"stroke:var(--rule)\" x1=\"54\" y1=\"206\" x2=\"54\" y2=\"10\"/><text class=\"po\" x=\"54.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><line style=\"stroke:var(--rule)\" x1=\"82\" y1=\"206\" x2=\"82\" y2=\"10\"/><text class=\"po\" x=\"82.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><line style=\"stroke:var(--rule)\" x1=\"110\" y1=\"206\" x2=\"110\" y2=\"10\"/><text class=\"po\" x=\"110.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text><line style=\"stroke:var(--rule)\" x1=\"138\" y1=\"206\" x2=\"138\" y2=\"10\"/><text class=\"po\" x=\"138.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">E</text><line style=\"stroke:var(--rule)\" x1=\"166\" y1=\"206\" x2=\"166\" y2=\"10\"/><text class=\"po\" x=\"166.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">F</text><line style=\"stroke:var(--rule)\" x1=\"194\" y1=\"206\" x2=\"194\" y2=\"10\"/><text class=\"po\" x=\"194.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">G</text><line style=\"stroke:var(--rule)\" x1=\"222\" y1=\"206\" x2=\"222\" y2=\"10\"/><text class=\"po\" x=\"222.0\" y=\"222.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">H</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"206\" x2=\"222\" y2=\"206\"/><text class=\"po\" x=\"14.0\" y=\"206.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"178\" x2=\"222\" y2=\"178\"/><text class=\"po\" x=\"14.0\" y=\"178.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"150\" x2=\"222\" y2=\"150\"/><text class=\"po\" x=\"14.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"122\" x2=\"222\" y2=\"122\"/><text class=\"po\" x=\"14.0\" y=\"122.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"94\" x2=\"222\" y2=\"94\"/><text class=\"po\" x=\"14.0\" y=\"94.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"66\" x2=\"222\" y2=\"66\"/><text class=\"po\" x=\"14.0\" y=\"66.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">6</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"38\" x2=\"222\" y2=\"38\"/><text class=\"po\" x=\"14.0\" y=\"38.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">7</text><line style=\"stroke:var(--rule)\" x1=\"26\" y1=\"10\" x2=\"222\" y2=\"10\"/><text class=\"po\" x=\"14.0\" y=\"10.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">8</text><circle class=\"dr\" cx=\"54\" cy=\"10\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"1.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Chaat</text><circle class=\"dr\" cx=\"194\" cy=\"10\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"1.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Dosa</text><circle class=\"dr\" cx=\"26\" cy=\"94\" r=\"4\"/><text class=\"al\" x=\"30.0\" y=\"85.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Juice</text><circle class=\"dr\" cx=\"138\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"142.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Books</text><circle class=\"dr\" cx=\"138\" cy=\"66\" r=\"4\"/><text class=\"al\" x=\"142.0\" y=\"57.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Toys</text><circle class=\"dr\" cx=\"194\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Kulfi</text><circle class=\"dr\" cx=\"54\" cy=\"122\" r=\"4\"/><text class=\"al\" x=\"58.0\" y=\"113.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Pizza</text><circle class=\"dr\" cx=\"194\" cy=\"178\" r=\"4\"/><text class=\"al\" x=\"198.0\" y=\"169.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Cakes</text></svg>"}, {"kind": "blank", "p": "Look at the plane:", "tag": "", "marks": "", "flat": [{"t": "a) coordinates of P: __B1__", "a": {"B1": "(-2, 1)"}, "expr": "coord"}, {"t": "b) coordinates of Z: __B1__", "a": {"B1": "(4, -2)"}, "expr": "coord"}, {"t": "c) Which point is at (−4, 0)? __B1__", "a": {"B1": "T"}}], "sol": "a) (−2, 1)\nb) (4, −2)\nc) T", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 290\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"28\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"53\" y1=\"264\" x2=\"53\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"78\" y1=\"264\" x2=\"78\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"103\" y1=\"264\" x2=\"103\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"128\" y1=\"264\" x2=\"128\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"153\" y1=\"264\" x2=\"153\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"178\" y1=\"264\" x2=\"178\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"203\" y1=\"264\" x2=\"203\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"228\" y1=\"264\" x2=\"228\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"253\" y1=\"264\" x2=\"253\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"278\" y1=\"264\" x2=\"278\" y2=\"14\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"264\" x2=\"278\" y2=\"264\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"239\" x2=\"278\" y2=\"239\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"214\" x2=\"278\" y2=\"214\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"189\" x2=\"278\" y2=\"189\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"164\" x2=\"278\" y2=\"164\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"139\" x2=\"278\" y2=\"139\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"114\" x2=\"278\" y2=\"114\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"89\" x2=\"278\" y2=\"89\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"64\" x2=\"278\" y2=\"64\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"39\" x2=\"278\" y2=\"39\"/><line style=\"stroke:var(--rule);stroke-width:1\" x1=\"28\" y1=\"14\" x2=\"278\" y2=\"14\"/><line class=\"ln\" x1=\"28.0\" y1=\"139.0\" x2=\"286.0\" y2=\"139.0\" marker-end=\"url(#ah)\"/><line class=\"ln\" x1=\"153.0\" y1=\"264.0\" x2=\"153.0\" y2=\"6.0\" marker-end=\"url(#ah)\"/><text class=\"po\" x=\"28.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"53.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"78.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"103.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"128.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"178.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"203.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"228.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"253.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"278.0\" y=\"150.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"po\" x=\"144.0\" y=\"264.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−5</text><text class=\"po\" x=\"144.0\" y=\"239.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−4</text><text class=\"po\" x=\"144.0\" y=\"214.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−3</text><text class=\"po\" x=\"144.0\" y=\"189.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−2</text><text class=\"po\" x=\"144.0\" y=\"164.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">−1</text><text class=\"po\" x=\"144.0\" y=\"114.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">1</text><text class=\"po\" x=\"144.0\" y=\"89.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">2</text><text class=\"po\" x=\"144.0\" y=\"64.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">3</text><text class=\"po\" x=\"144.0\" y=\"39.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">4</text><text class=\"po\" x=\"144.0\" y=\"14.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">5</text><text class=\"lb\" x=\"288.0\" y=\"131.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">x</text><text class=\"lb\" x=\"163.0\" y=\"8.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">y</text><circle class=\"dr\" cx=\"203\" cy=\"39\" r=\"4\"/><text class=\"al\" x=\"207.0\" y=\"30.0\" text-anchor=\"start\" dominant-baseline=\"middle\">W</text><circle class=\"dr\" cx=\"28\" cy=\"64\" r=\"4\"/><text class=\"al\" x=\"32.0\" y=\"55.0\" text-anchor=\"start\" dominant-baseline=\"middle\">S</text><circle class=\"dr\" cx=\"253\" cy=\"89\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"80.0\" text-anchor=\"start\" dominant-baseline=\"middle\">R</text><circle class=\"dr\" cx=\"103\" cy=\"114\" r=\"4\"/><text class=\"al\" x=\"107.0\" y=\"105.0\" text-anchor=\"start\" dominant-baseline=\"middle\">P</text><circle class=\"dr\" cx=\"53\" cy=\"139\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"130.0\" text-anchor=\"start\" dominant-baseline=\"middle\">T</text><circle class=\"dr\" cx=\"53\" cy=\"164\" r=\"4\"/><text class=\"al\" x=\"57.0\" y=\"155.0\" text-anchor=\"start\" dominant-baseline=\"middle\">U</text><circle class=\"dr\" cx=\"253\" cy=\"189\" r=\"4\"/><text class=\"al\" x=\"257.0\" y=\"180.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Z</text><circle class=\"dr\" cx=\"78\" cy=\"239\" r=\"4\"/><text class=\"al\" x=\"82.0\" y=\"230.0\" text-anchor=\"start\" dominant-baseline=\"middle\">Q</text><circle class=\"dr\" cx=\"178\" cy=\"264\" r=\"4\"/><text class=\"al\" x=\"182.0\" y=\"255.0\" text-anchor=\"start\" dominant-baseline=\"middle\">V</text></svg>"}, {"kind": "blank", "p": "On this map 1 grid unit represents 1 km. Sanjay's house is at (2, 3) and Deepa's house is at (−3, −2).", "tag": "", "marks": "", "flat": [{"t": "a) Vani lives 5 km south of Sanjay. Coordinates: __B1__", "a": {"B1": "(2, -2)"}, "expr": "coord"}, {"t": "b) How far is Vani's house from Deepa's? __B1__ km", "a": {"B1": "5"}}, {"t": "c) Direction from Deepa's house to Sanjay's: __B1__", "a": {"B1": "northeast"}, "accept": ["NE", "ne"]}], "sol": "a) (2, 3 − 5) = (2, −2)\nb) (−3, −2) to (2, −2): 5 km\nc) right 5 and up 5: northeast"}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-g6-ch15';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Location</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('');
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { h += fr(esc(slide.p)); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist'||qstep.expr==='glist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist'||step.expr==='glist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — revisit it anytime from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+(item.status!=='unanswered'?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick);
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };

renderLogin();
})();
</script>
</body>
</html>
