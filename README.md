<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Lets Learn</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

body{
    font-family:"Comic Sans MS","Trebuchet MS",sans-serif;
    background:linear-gradient(135deg,#8ed8ff,#c9f7ff,#fff3a8);
    min-height:100vh;
    overflow-x:hidden;
    color:#25324a;
}

button{
    font-family:inherit;
    cursor:pointer;
    border:none;
}

.screen{
    display:none;
    min-height:100vh;
    padding:25px;
    position:relative;
    overflow:hidden;
}

.screen.active{
    display:flex;
    flex-direction:column;
    align-items:center;
}

.cloud{
    position:absolute;
    font-size:65px;
    opacity:.75;
    animation:floatCloud 12s linear infinite;
    pointer-events:none;
}

.cloud.c1{top:7%;left:-80px}
.cloud.c2{top:22%;right:-90px;animation-delay:4s}
.cloud.c3{top:55%;left:-100px;animation-delay:7s}

@keyframes floatCloud{
    0%{transform:translateX(0)}
    50%{transform:translateX(50vw)}
    100%{transform:translateX(110vw)}
}

.star{
    position:absolute;
    font-size:25px;
    animation:twinkle 1.5s infinite alternate;
}

@keyframes twinkle{
    from{transform:scale(.7) rotate(0deg);opacity:.5}
    to{transform:scale(1.25) rotate(20deg);opacity:1}
}

.logo{
    margin-top:25px;
    text-align:center;
    animation:bounce 2s infinite;
    z-index:2;
}

.logo-icon{
    font-size:80px;
}

.logo h1{
    font-size:54px;
    color:#ff6b6b;
    text-shadow:4px 4px #fff;
}

.logo p{
    font-size:20px;
    font-weight:bold;
}

@keyframes bounce{
    0%,100%{transform:translateY(0)}
    50%{transform:translateY(-8px)}
}

.mascots{
    display:flex;
    gap:18px;
    margin:30px 0;
    z-index:2;
    flex-wrap:wrap;
    justify-content:center;
}

.mascot{
    width:110px;
    height:110px;
    background:#fff;
    border-radius:30px;
    box-shadow:0 8px 20px #0002;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:65px;
    animation:mascotFloat 2s infinite ease-in-out;
}

.mascot:nth-child(2){animation-delay:.2s}
.mascot:nth-child(3){animation-delay:.4s}
.mascot:nth-child(4){animation-delay:.6s}
.mascot:nth-child(5){animation-delay:.8s}
.mascot:nth-child(6){animation-delay:1s}

@keyframes mascotFloat{
    50%{transform:translateY(-10px) rotate(3deg)}
}

.main-btn{
    background:#ff8a3d;
    color:white;
    padding:17px 42px;
    border-radius:50px;
    font-size:22px;
    font-weight:bold;
    box-shadow:0 7px 0 #d85c20;
    transition:.15s;
    z-index:2;
}

.main-btn:hover{
    transform:translateY(-3px);
}

.main-btn:active{
    transform:translateY(4px);
    box-shadow:0 3px 0 #d85c20;
}

.secondary-btn{
    background:white;
    padding:12px 25px;
    border-radius:30px;
    font-weight:bold;
    font-size:16px;
    box-shadow:0 4px 12px #0002;
}

.panel{
    background:#ffffffdd;
    backdrop-filter:blur(10px);
    width:min(1000px,95%);
    padding:25px;
    border-radius:35px;
    box-shadow:0 10px 30px #0002;
    z-index:2;
    margin-top:20px;
}

.title{
    text-align:center;
    font-size:32px;
    color:#ff6b6b;
    margin-bottom:20px;
}

.settings-row{
    display:flex;
    flex-wrap:wrap;
    gap:15px;
    justify-content:center;
}

.setting{
    background:#f4fbff;
    border-radius:20px;
    padding:18px;
    min-width:220px;
    text-align:center;
}

.setting h3{
    margin-bottom:10px;
}

select,input[type="range"]{
    width:100%;
    padding:10px;
}

.char-grid{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:15px;
}

.char-card{
    background:white;
    border-radius:25px;
    padding:18px 10px;
    text-align:center;
    box-shadow:0 6px 15px #0002;
    transition:.2s;
}

.char-card:hover{
    transform:translateY(-8px) rotate(1deg);
}

.char-icon{
    font-size:65px;
}

.char-card h3{
    color:#ff6b6b;
    margin:8px 0;
}

.char-card p{
    font-size:13px;
    min-height:40px;
}

.level-grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:20px;
}

.level-card{
    background:white;
    padding:30px 20px;
    border-radius:30px;
    text-align:center;
    box-shadow:0 7px 20px #0002;
    transition:.2s;
}

.level-card:hover{
    transform:scale(1.04);
}
.level-card.locked{
    opacity:.58;
    filter:grayscale(.55);
    cursor:not-allowed;
    box-shadow:0 5px 12px #0001;
}
.level-card.locked:hover{transform:none}
.level-lock-label{display:block;margin-top:10px;font-size:14px;font-weight:bold;color:#6d7280}
.level-card.unlocked{border:3px solid #79d79a}


.level-number{
    font-size:55px;
}

.game-top{
    width:min(1100px,100%);
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:10px;
    z-index:2;
}

.game-title{
    font-size:28px;
    color:#ff6b6b;
}

.question-box{
    width:min(1000px,100%);
    background:#ffffffee;
    border-radius:35px;
    padding:25px;
    margin-top:15px;
    box-shadow:0 10px 30px #0002;
    text-align:center;
    z-index:2;
    position:relative;
}

.question-box:before{
    content:"☁️";
    position:absolute;
    top:-25px;
    left:7%;
    font-size:55px;
    animation:bounce 2s infinite;
}

.question{
    font-size:27px;
    font-weight:bold;
    margin-bottom:20px;
}

.speak-btn{
    background:#65c466;
    color:white;
    padding:10px 20px;
    border-radius:30px;
    font-weight:bold;
    margin-bottom:20px;
}

.match-layout{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:70px;
    position:relative;
}

.match-column{
    display:flex;
    flex-direction:column;
    gap:15px;
}

.option{
    min-height:75px;
    background:white;
    border:4px solid #dcecff;
    border-radius:22px;
    padding:10px;
    font-size:24px;
    box-shadow:0 5px 12px #0002;
    transition:.2s;
}

.option:hover{
    transform:scale(1.03);
}

.option.correct{
    background:#b9f6bd;
    border-color:#52c45a;
}

.option.wrong{
    animation:shake .4s;
    background:#ffd0d0;
}

@keyframes shake{
    25%{transform:translateX(-8px)}
    75%{transform:translateX(8px)}
}

.picture{
    font-size:42px;
    display:block;
}

.special-area{
    margin-top:10px;
}

.memory-status{
    font-size:20px;
    font-weight:bold;
    margin-bottom:10px;
}

.memory-progress{
    height:14px;
    background:#e5e5e5;
    border-radius:20px;
    overflow:hidden;
    margin-bottom:20px;
}

.memory-progress-bar{
    height:100%;
    width:0%;
    background:#65c466;
    transition:.4s;
}

.memory-grid{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:10px;
}

.memory-card{
    aspect-ratio:1/1;
    min-width:0;
    border-radius:18px;
    background:#ff9f68;
    box-shadow:0 5px 10px #0002;
    position:relative;
    overflow:hidden;
    transition:.3s;
}

.memory-card:hover{
    transform:translateY(-4px);
}

.question-mark{
    font-size:32px;
}

.memory-content{
    display:none;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    height:100%;
    background:white;
    border-radius:18px;
}

.memory-card.open .question-mark,
.memory-card.matched .question-mark{
    display:none;
}

.memory-card.open .memory-content,
.memory-card.matched .memory-content{
    display:flex;
}

.memory-card.matched{
    background:#a9eeb0;
    border:4px solid #48b957;
    pointer-events:none;
}

.memory-emoji{
    font-size:42px;
}

.memory-name{
    font-size:13px;
    font-weight:bold;
    margin-top:3px;
}

.choice-grid{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:18px;
}

.choice-btn{
    background:white;
    border-radius:25px;
    padding:20px;
    font-size:23px;
    box-shadow:0 6px 15px #0002;
}

.sequence-grid{
    display:flex;
    gap:15px;
    justify-content:center;
    flex-wrap:wrap;
}

.sequence-item{
    background:white;
    border-radius:20px;
    padding:25px;
    font-size:40px;
    box-shadow:0 5px 12px #0002;
}

.bimo-picture-row{
    display:flex;
    justify-content:center;
    flex-wrap:wrap;
    gap:8px;
    margin:12px auto;
}
.bimo-picture{
    display:inline-flex;
    align-items:center;
    justify-content:center;
    min-width:48px;
    min-height:48px;
    border-radius:14px;
    background:#fff;
    font-size:clamp(30px,6vw,48px);
    box-shadow:0 3px 8px #0001;
}
.bimo-picture-row.removed .bimo-picture{
    position:relative;
    opacity:.65;
}
.bimo-picture-row.removed .bimo-picture::after{
    content:"";
    position:absolute;
    width:115%;
    height:4px;
    border-radius:4px;
    background:#e65b5b;
    transform:rotate(-45deg);
}
.bimo-addition{
    display:flex;
    align-items:center;
    justify-content:center;
    flex-wrap:wrap;
    gap:10px;
}
.bimo-operator{
    font-size:34px;
    font-weight:bold;
    color:#ff8a3d;
}
.bimo-order-grid,
.bimo-groups{
    display:grid;
    grid-template-columns:repeat(3,minmax(0,1fr));
    gap:12px;
    margin-top:14px;
}
.bimo-order-card,
.bimo-group{
    min-width:0;
    border:3px solid #e6f4ff;
    border-radius:18px;
    background:#fff;
    padding:10px;
    box-shadow:0 4px 10px #0001;
}
.bimo-order-card{
    position:relative;
    cursor:pointer;
}
.bimo-order-card.selected{
    border-color:#ffb347;
    background:#fff8e7;
}
.bimo-order-card:disabled{
    cursor:default;
}
.bimo-order-badge{
    display:inline-flex;
    align-items:center;
    justify-content:center;
    width:30px;
    height:30px;
    border-radius:50%;
    background:#ff8a3d;
    color:#fff;
    font-size:17px;
    font-weight:bold;
}
.bimo-groups{
    grid-template-columns:repeat(auto-fit,minmax(105px,1fr));
}
.bimo-group .bimo-picture-row{
    gap:4px;
    margin:4px auto;
}
.bimo-group .bimo-picture{
    min-width:32px;
    min-height:34px;
    background:#f3fbff;
    font-size:clamp(23px,4vw,34px);
    box-shadow:none;
}
.writing-exercise{
    display:flex;
    flex-direction:column;
    align-items:center;
    gap:14px;
    width:min(100%,520px);
    margin:20px auto;
}
.writing-picture{
    font-size:clamp(64px,14vw,100px);
    line-height:1.1;
}
.writing-model{
    padding:10px 18px;
    border-radius:14px;
    background:#fff4cb;
    font-size:clamp(24px,6vw,38px);
    font-weight:bold;
    letter-spacing:2px;
}
.writing-clues{
    display:grid;
    gap:10px;
    width:100%;
}
.writing-clues div{
    padding:12px 16px;
    border-radius:14px;
    background:#fff4cb;
    font-size:clamp(18px,4vw,24px);
    font-weight:bold;
}
.writing-input{
    width:100%;
    min-height:58px;
    padding:12px 16px;
    border:3px solid #b9e7ee;
    border-radius:16px;
    background:#fff;
    color:#25324a;
    font-size:24px;
    text-align:center;
}
.writing-submit{
    min-width:170px;
}


.game-stats{
    display:flex;
    align-items:center;
    justify-content:center;
    gap:8px;
    flex-wrap:wrap;
}
.stat-pill{
    background:white;
    padding:10px 14px;
    border-radius:25px;
    box-shadow:0 4px 12px #0002;
    font-weight:bold;
    min-width:82px;
}
.lives-pill{
    transition:.2s;
}
.lives-pill.life-lost{
    animation:lifeLost .45s;
}
@keyframes lifeLost{
    25%{transform:scale(1.18) rotate(-4deg)}
    50%{transform:scale(.92) rotate(4deg)}
    100%{transform:scale(1) rotate(0)}
}

.animated-scene{
    width:min(1000px,100%);
    min-height:135px;
    margin-top:16px;
    border-radius:30px;
    background:linear-gradient(180deg,#dff8ff,#fff8cf);
    box-shadow:0 8px 24px #0002;
    position:relative;
    overflow:hidden;
    display:flex;
    align-items:flex-end;
    justify-content:center;
    padding-bottom:8px;
}
.animated-scene:before{
    content:"";
    position:absolute;
    left:0;
    right:0;
    bottom:0;
    height:42px;
    background:#9be27d;
    border-radius:50% 50% 0 0;
}
.scene-character{
    position:relative;
    z-index:2;
    font-size:76px;
    line-height:1;
    filter:drop-shadow(0 5px 4px #0002);
}
.scene-item{
    position:absolute;
    z-index:1;
    font-size:32px;
}
.scene-item.i1{left:12%;bottom:35px}
.scene-item.i2{right:14%;bottom:38px}
.scene-item.i3{left:43%;bottom:20px;font-size:26px}
.scene-cloud{
    position:absolute;
    top:12px;
    font-size:35px;
    opacity:.7;
    animation:sceneCloud 8s linear infinite;
}
.scene-cloud.c1{left:-50px}
.scene-cloud.c2{left:55%;animation-delay:3s}
@keyframes sceneCloud{
    from{transform:translateX(0)}
    to{transform:translateX(110%)}
}
.scene-lumi{animation:hop 1s ease-in-out infinite}
.scene-nara{animation:run 1.2s ease-in-out infinite}
.scene-bimo{animation:bimoBounce 1.4s ease-in-out infinite}
.scene-sky{animation:fly 1.8s ease-in-out infinite}
.scene-luna{animation:walk 2s ease-in-out infinite}
.scene-pippo{animation:walk 2s ease-in-out infinite}
@keyframes hop{
    0%,100%{transform:translateY(0) rotate(0)}
    45%{transform:translateY(-25px) rotate(-5deg)}
    70%{transform:translateY(-8px) rotate(5deg)}
}
@keyframes run{
    0%,100%{transform:translateX(-18px) scaleX(1)}
    50%{transform:translateX(18px) scaleX(1.08)}
}
@keyframes bimoBounce{
    0%,100%{transform:translateY(0)}
    50%{transform:translateY(-15px) scale(1.05)}
}
@keyframes fly{
    0%,100%{transform:translate(-18px,-3px) rotate(-4deg)}
    50%{transform:translate(18px,-25px) rotate(5deg)}
}
@keyframes walk{
    0%,100%{transform:translateX(-20px)}
    50%{transform:translateX(20px)}
}

.match-layout.lumi-match{
    grid-template-columns:1fr 1fr;
    gap:45px;
}
.lumi-column-title{
    font-size:18px;
    font-weight:bold;
    margin-bottom:2px;
}
.lumi-name-option{
    min-height:68px;
}
.lumi-name-option.selected{
    border-color:#ffb347;
    background:#fff2cc;
    transform:scale(1.03);
}
.lumi-name-option.matched,
.lumi-picture-option.matched{
    background:#b9f6bd;
    border-color:#52c45a;
    pointer-events:none;
    animation:matchPop .45s;
}
.lumi-picture-option{
    display:flex;
    align-items:center;
    justify-content:center;
    gap:10px;
}
.lumi-picture-option .picture{
    font-size:45px;
}
.lumi-picture-option.selected-wrong,
.lumi-name-option.selected-wrong{
    background:#ffd0d0;
    border-color:#ff6b6b;
    animation:shake .4s;
}
@keyframes matchPop{
    50%{transform:scale(1.08)}
}

.life-warning{
    animation:lifeWarning .5s;
}
@keyframes lifeWarning{
    25%{transform:scale(1.08)}
    50%{transform:scale(.95)}
    100%{transform:scale(1)}
}

.game-over-box{
    padding:15px;
}

.feedback{
    margin-top:18px;
    font-size:23px;
    font-weight:bold;
    min-height:32px;
}

.back-btn{
    margin-top:20px;
}

.hidden{
    display:none!important;
}

.confetti{
    position:fixed;
    top:-20px;
    font-size:25px;
    animation:fall 2s linear forwards;
    z-index:999;
    pointer-events:none;
}

@keyframes fall{
    to{
        transform:translateY(110vh) rotate(720deg);
        opacity:0;
    }
}

.balloon{
    position:absolute;
    font-size:45px;
    animation:balloon 4s ease-in-out infinite;
}

@keyframes balloon{
    0%,100%{transform:translateY(0)}
    50%{transform:translateY(-25px)}
}

@media(max-width:800px){
    .char-grid{
        grid-template-columns:repeat(2,1fr);
    }

    .level-grid{
        grid-template-columns:1fr;
    }

    .memory-grid{
        grid-template-columns:repeat(5,1fr);
    }

    .memory-name{
        font-size:10px;
    }

    .memory-emoji{
        font-size:30px;
    }

    .question{
        font-size:22px;
    }

    .game-top{
        flex-wrap:wrap;
    }
}

@media(max-width:500px){
    .game-stats{gap:5px}
    .stat-pill{padding:8px 10px;min-width:72px;font-size:14px}
    .animated-scene{min-height:110px}
    .scene-character{font-size:60px}
    .scene-item{font-size:25px}
    .match-layout.lumi-match{gap:10px}
    .lumi-column-title{font-size:15px}
    .screen{
        padding:12px;
    }

    .logo h1{
        font-size:40px;
    }

    .logo-icon{
        font-size:65px;
    }

    .mascot{
        width:65px;
        height:65px;
        font-size:40px;
        border-radius:20px;
    }

    .panel,
    .question-box{
        padding:16px;
        border-radius:25px;
    }

    .match-layout{
        gap:12px;
    }

    .option{
        min-height:65px;
        font-size:17px;
    }

    .picture{
        font-size:32px;
    }

    .memory-grid{
        grid-template-columns:repeat(4,1fr);
        gap:8px;
    }

    .memory-card{
        border-radius:13px;
    }

    .memory-emoji{
        font-size:27px;
    }

    .memory-name{
        font-size:8px;
    }

    .question-mark{
        font-size:25px;
    }

    .choice-grid{
        grid-template-columns:1fr;
    }
}


/* ================= MATERI SOSIAL ================= */
.game-menu-btn{margin-top:14px;color:white;padding:16px 30px;border-radius:30px;font-size:19px;font-weight:bold;box-shadow:0 6px 0 #5a72c8;min-width:280px}
.academic-menu-btn{background:#6d83e8;box-shadow:0 6px 0 #4d63b0}
.social-menu-btn{background:#62c78b;box-shadow:0 6px 0 #3f9c64}
.game-menu-btn:hover{transform:translateY(-3px)}
.social-material-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px;max-width:900px;margin:18px auto}
.social-card{background:white;border:3px solid #e8f7ed;border-radius:25px;padding:18px 10px;text-align:center;box-shadow:0 6px 15px #0002;transition:.2s;cursor:pointer}
.social-card:hover{transform:translateY(-5px) rotate(1deg);border-color:#8ed8a8}
.social-card.active{border-color:#55b878;background:#f1fff5;transform:translateY(-4px)}
.social-icon{font-size:48px;margin-bottom:7px}.social-card h3{color:#55a974;margin:0;font-size:17px}
.social-world-banner{height:132px;max-width:850px;margin:0 auto 18px;padding:0 8%;display:flex;align-items:center;justify-content:space-around;gap:10px;position:relative;overflow:hidden;border:3px solid #fff;border-radius:20px;background:linear-gradient(180deg,#a9e6ff 0%,#e5f8ff 68%,#a8df82 68%,#8cc96e 100%);box-shadow:0 5px 0 #26384a18}
.social-world-banner:before{content:"☁️";position:absolute;top:4px;left:12%;font-size:30px;opacity:.8}
.social-world-banner:after{content:"☀️";position:absolute;top:4px;right:12%;font-size:30px}
.world-stop{position:relative;z-index:1;font-size:38px;white-space:nowrap;filter:drop-shadow(0 3px 2px #26384a20);animation:mascotFloat 2.8s ease-in-out infinite}
.world-stop:nth-of-type(3){animation-delay:.25s}.world-stop:nth-of-type(4){animation-delay:.5s}.world-stop:nth-of-type(5){animation-delay:.75s}
.social-map{max-width:900px;margin:0 auto 18px;background:#fff8d8;border-radius:22px;padding:13px;font-size:17px;font-weight:bold;text-align:center;box-shadow:0 4px 12px #0001}
.social-start-note{font-size:16px;font-weight:bold;margin:8px 0 16px}
.social-question-card{max-width:820px;margin:auto;background:white;border-radius:28px;padding:20px;text-align:center;box-shadow:0 6px 16px #0002}
.social-scene{font-size:78px;min-height:95px;display:flex;align-items:center;justify-content:center;gap:12px;background:#f2fbff;border-radius:22px;margin-bottom:15px}
.social-situation{font-size:21px;font-weight:bold;line-height:1.35;margin-bottom:16px}
.social-hint{font-size:16px;margin-bottom:14px;font-weight:bold}
.social-options{display:grid;grid-template-columns:repeat(2,1fr);gap:13px}
.social-option{background:#f7fbff;border:3px solid transparent;border-radius:20px;padding:15px;font-size:17px;font-weight:bold;min-height:70px;transition:.2s}
.social-option:hover{transform:translateY(-3px);border-color:#8ed8ff}.social-option.correct{background:#b9f6bd;border-color:#52c45a;animation:correct .5s}.social-option.wrong{background:#ffd0d0;border-color:#ff6b6b;animation:shake .4s}
@keyframes correct{50%{transform:scale(1.06)}}
.social-map-title{font-size:20px;font-weight:bold;text-align:center;margin:8px 0 16px}
.social-map-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;max-width:850px;margin:auto}
.social-place{border:4px solid transparent;background:#fff;border-radius:24px;padding:16px 10px;cursor:pointer;box-shadow:0 5px 12px #0002;transition:.2s;font-weight:bold;font-size:17px}
.social-place:hover{transform:translateY(-4px)}
.social-place.active{border-color:#62c78b;background:#effff3;transform:translateY(-3px)}
.social-place .place-icon{font-size:48px;display:block;margin-bottom:5px}
.social-place .place-illustration{height:96px;position:relative;overflow:hidden;border-radius:16px;margin-bottom:10px;font-size:initial;box-shadow:inset 0 -7px #65bb6870}
.place-illustration:before{content:"☀️";position:absolute;top:6px;left:10px;font-size:20px}
.place-building{position:absolute;left:19%;bottom:5px;font-size:48px;filter:drop-shadow(0 3px 2px #26384a20)}
.place-friend{position:absolute;right:10%;bottom:2px;font-size:34px;filter:drop-shadow(0 3px 2px #26384a20)}
.place-detail{position:absolute;left:8%;bottom:4px;font-size:20px}
.social-place[data-topic="home"] .place-illustration{background:linear-gradient(180deg,#bdeaff 0 66%,#a8dc83 66%)}
.social-place[data-topic="school"] .place-illustration{background:linear-gradient(180deg,#c9efff 0 66%,#91d077 66%)}
.social-place[data-topic="play"] .place-illustration{background:linear-gradient(180deg,#b7eaff 0 63%,#a6df82 63% 80%,#f7d78b 80%)}
.social-place[data-topic="friends"] .place-illustration{background:linear-gradient(180deg,#c8edff 0 66%,#a8df8c 66%)}
.social-place[data-topic="play"] .place-building{left:13%;font-size:53px}
.social-place[data-topic="friends"] .place-building{left:13%;font-size:42px}
.social-place.active .place-illustration{filter:saturate(1.18)}
.social-mini-card{max-width:760px;margin:auto;background:#fff;border-radius:28px;padding:22px;box-shadow:0 6px 16px #0002;text-align:center}
.social-mini-scene{font-size:78px;min-height:145px;position:relative;isolation:isolate;overflow:hidden;display:flex;align-items:center;justify-content:center;gap:12px;margin-bottom:14px;border:3px solid #fff;border-radius:22px;box-shadow:inset 0 -7px #26384a12,0 4px 0 #26384a12}
.social-mini-scene:before{content:"☁️";position:absolute;z-index:-1;top:8px;left:8%;font-size:32px;opacity:.78}
.social-mini-scene:after{content:"";position:absolute;z-index:-1;left:0;right:0;bottom:0;height:30%;background:#8dd275;clip-path:ellipse(70% 75% at 50% 100%)}
.social-scene-topic-home{background:linear-gradient(180deg,#bdeaff 0 72%,#eaf7c6 72%)}
.social-scene-topic-school{background:linear-gradient(180deg,#b9e8fa 0 72%,#b6d9a1 72%)}
.social-scene-topic-play{background:linear-gradient(180deg,#b9eaff 0 66%,#a5df82 66% 82%,#f6d887 82%)}
.social-scene-topic-friends{background:linear-gradient(180deg,#c6eaff 0 72%,#b9e7a0 72%)}
.social-mini-scene>*{filter:drop-shadow(0 4px 2px #26384a20)}
.social-mini-question{font-size:24px;font-weight:bold;margin:8px 0 18px}
.social-mini-options{display:grid;grid-template-columns:repeat(2,1fr);gap:14px}
.social-mini-option{border:3px solid #e5edf5;background:#f8fbff;border-radius:20px;padding:18px 12px;font-size:18px;font-weight:bold;min-height:72px;cursor:pointer;transition:.2s}
.social-mini-option:hover{transform:translateY(-3px);border-color:#8ed8ff}
.social-mini-option.correct{background:#b9f6bd;border-color:#52c45a;animation:correct .5s}
.social-mini-option.wrong{background:#ffd0d0;border-color:#ff6b6b;animation:shake .4s}
.social-type-phrase .social-mini-scene{background:#fff7df}.social-type-choice .social-mini-scene{background:#f4efff}.social-type-situation .social-mini-scene{background:#eef9f2}.social-type-phrase .social-mini-question{letter-spacing:.2px}
.social-progress{font-size:15px;margin-bottom:10px;opacity:.75}
@media(max-width:700px){.social-map-grid{grid-template-columns:repeat(2,1fr)}.social-mini-options{grid-template-columns:1fr}.social-mini-scene{font-size:62px;min-height:120px}.social-mini-question{font-size:20px}.social-world-banner{height:106px;padding:0 5%}.world-stop{font-size:29px}}

@media(max-width:800px){.social-material-grid{grid-template-columns:repeat(2,1fr)}}
@media(max-width:500px){.social-material-grid,.social-options{grid-template-columns:1fr}.social-situation{font-size:18px}.social-scene{font-size:62px}}



/* Responsive layout: phone, tablet, laptop and desktop */
* { box-sizing: border-box; }
html { width: 100%; min-height: 100%; -webkit-text-size-adjust: 100%; }
body {
  width: 100%;
  min-width: 0;
  min-height: 100vh;
  min-height: 100dvh;
  margin: 0;
  overflow-x: hidden;
  -webkit-tap-highlight-color: transparent;
}
button, input, select, textarea { max-width: 100%; font: inherit; }
button { touch-action: manipulation; }
img, video, canvas, svg { max-width: 100%; }
.screen, .panel, .question-box, .game-top, .game-stats {
  min-width: 0;
  max-width: 100%;
}
.screen { width: 100%; }
.panel { width: min(100% - 24px, 1100px); margin-left: auto; margin-right: auto; }
.game-top { flex-wrap: wrap; gap: 10px; }
.game-stats { display: flex; flex-wrap: wrap; justify-content: center; gap: 8px; }
.question-box { width: min(100% - 20px, 1000px); margin-left: auto; margin-right: auto; }
.game-area, #gameArea, #socialGameArea, .social-options, .social-material-grid {
  min-width: 0;
  max-width: 100%;
}
.social-material-grid { grid-template-columns: repeat(auto-fit, minmax(min(180px, 100%), 1fr)); }
.social-options { grid-template-columns: repeat(2, minmax(0, 1fr)); }
button, .main-btn, .secondary-btn, .game-menu-btn { min-height: 44px; }
@media (max-width: 700px) {
  body { font-size: 16px; }
  .panel { padding: 18px 14px; border-radius: 22px; }
  .title { font-size: clamp(23px, 6vw, 34px); }
  .game-title { font-size: clamp(18px, 4.5vw, 26px); }
  .game-menu-btn, .main-btn, .secondary-btn { width: min(100%, 360px); }
  .game-top { justify-content: center; }
  .game-stats { width: 100%; }
  .stat-pill { font-size: 14px; padding: 8px 10px; }
  .question-box { padding: 16px 12px; border-radius: 22px; }
  .social-material-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 10px; }
  .social-card { padding: 14px 9px; }
  .social-icon { font-size: 36px; }
  .social-situation { font-size: clamp(17px, 4vw, 22px); }
  .social-options { gap: 10px; }
  .social-option { padding: 12px 8px; font-size: 15px; min-height: 64px; overflow-wrap: anywhere; }
  .memory-grid { grid-template-columns: repeat(5, minmax(0, 1fr)); gap: 6px; }
  .memory-card { min-width: 0; padding: 6px; }
  .memory-card .memory-content { font-size: clamp(20px, 6vw, 34px); }
  .animated-scene { max-width: 100%; overflow: hidden; }
}
@media (max-width: 420px) {
  .social-material-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .social-options { grid-template-columns: 1fr; }
  .memory-grid { grid-template-columns: repeat(5, minmax(0, 1fr)); gap: 4px; }
  .memory-card { border-width: 2px; border-radius: 12px; }
  .memory-card .memory-content { font-size: 20px; }
  .question { font-size: 21px; }
  .stat-pill { font-size: 12px; }
}
@media (orientation: landscape) and (max-height: 520px) {
  .panel { padding-top: 10px; padding-bottom: 10px; }
  .title { margin-top: 6px; margin-bottom: 8px; }
  .game-top { gap: 6px; }
  .question-box { padding: 10px; }
  .animated-scene { max-height: 100px; overflow: hidden; }
  .social-material-grid { grid-template-columns: repeat(4, minmax(0, 1fr)); }
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; scroll-behavior: auto !important; }
}

/* Playful storybook theme */
:root {
    --ink: #26384a;
    --coral: #f26558;
    --sunshine: #ffc83d;
    --leaf: #35ad79;
    --sky: #368acb;
    --paper: #fffdf4;
}

body {
    color: var(--ink);
    font-family: "Trebuchet MS", "Comic Sans MS", sans-serif;
    background-color: #9bdff2;
    background-image:
        radial-gradient(circle, #ffffffa0 1.2px, transparent 1.8px),
        repeating-linear-gradient(125deg, transparent 0 74px, #ffffff18 74px 77px),
        linear-gradient(175deg, transparent 0 76%, #80c96a55 76% 79%, #b1e48d70 79% 100%),
        linear-gradient(145deg, #76c9ef 0%, #b4eddb 51%, #fff0ad 100%);
    background-size: 36px 36px, 100% 100%, 100% 100%, cover;
    background-attachment: fixed;
}

.screen {
    padding: clamp(16px, 3vw, 34px);
}

.logo {
    margin-top: clamp(12px, 3vh, 28px);
}

.logo-icon {
    display: inline-block;
    filter: drop-shadow(0 5px 0 #ffffffa8);
}

.logo h1 {
    color: var(--coral);
    text-shadow: 2px 3px 0 #fff, 4px 6px 0 #26384a20;
}

.logo p {
    display: inline-block;
    margin-top: 7px;
    padding: 7px 15px;
    background: var(--paper);
    border: 2px solid #fff;
    border-radius: 999px;
    box-shadow: 0 3px 0 #26384a18;
}

.mascot {
    width: clamp(76px, 12vw, 108px);
    height: clamp(76px, 12vw, 108px);
    border: 4px solid #fff;
    border-radius: 28px 28px 22px 28px;
    box-shadow: 0 6px 0 #26384a20;
}

.mascot:nth-child(4n + 1) { background: #fff0c2; }
.mascot:nth-child(4n + 2) { background: #d9f4ff; }
.mascot:nth-child(4n + 3) { background: #ffe0dc; }
.mascot:nth-child(4n) { background: #ddf5d8; }

.game-menu-btn,
.main-btn,
.secondary-btn {
    border: 2px solid #fff;
    transition: transform .18s ease, box-shadow .18s ease, filter .18s ease;
}

.game-menu-btn {
    min-width: min(300px, 100%);
    border-radius: 18px;
    font-size: 20px;
    box-shadow: 0 5px 0 #26384a2b;
}

.academic-menu-btn {
    background: #f5a928;
    box-shadow: 0 5px 0 #bd7413;
}

.social-menu-btn {
    background: #2eae83;
    box-shadow: 0 5px 0 #197654;
}

.main-btn {
    border-radius: 16px;
    background: var(--coral);
    box-shadow: 0 5px 0 #bd493f;
}

.secondary-btn {
    border-radius: 14px;
    color: var(--ink);
    box-shadow: 0 4px 0 #26384a20;
}

.game-menu-btn:hover,
.main-btn:hover,
.secondary-btn:hover,
.char-card:hover,
.level-card:hover,
.social-card:hover,
.social-place:hover {
    filter: saturate(1.08);
    transform: translateY(-3px);
}

.panel,
.question-box {
    border: 4px solid #fff;
    border-radius: 22px;
    background: var(--paper);
    box-shadow: 0 8px 0 #26384a20, 0 16px 36px #26384a18;
}

.title,
.game-title {
    color: var(--coral);
}

.setting,
.social-map,
.social-scene,
.social-mini-scene {
    border-radius: 14px;
}

.char-grid {
    grid-template-columns: repeat(auto-fit, minmax(min(150px, 100%), 1fr));
    gap: 12px;
}

.char-card,
.level-card,
.social-card,
.social-place {
    border: 3px solid #fff;
    border-radius: 14px;
    box-shadow: 0 4px 0 #26384a18;
}

.char-card:nth-child(5n + 1) { background: #fff0c2; }
.char-card:nth-child(5n + 2) { background: #e1f4ff; }
.char-card:nth-child(5n + 3) { background: #ffe3de; }
.char-card:nth-child(5n + 4) { background: #e5f5d8; }
.char-card:nth-child(5n) { background: #f0e8ff; }

.char-card h3 { color: var(--sky); }
.level-grid { grid-template-columns: repeat(auto-fit, minmax(min(160px, 100%), 1fr)); }
.level-card.unlocked { border-color: #61c98a; }
.question-box { padding: clamp(18px, 3vw, 30px); }
.question { color: var(--ink); line-height: 1.35; }

.option,
.choice-btn,
.sequence-item,
.memory-card {
    border-radius: 14px;
    box-shadow: 0 4px 0 #26384a18;
}

.option { border-color: #b9e7ee; }
.option:hover,
.choice-btn:hover { border-color: var(--sunshine); }
.stat-pill { border: 2px solid #fff; box-shadow: 0 3px 0 #26384a1c; }

button:focus-visible,
select:focus-visible,
input:focus-visible {
    outline: 3px solid #26384a;
    outline-offset: 3px;
}

@media (max-width: 700px) {
    .mascots { gap: 10px; margin: 20px 0; }
    .logo h1 { font-size: clamp(36px, 10vw, 48px); }
    .panel { padding: 18px 14px; }
    .social-material-grid { gap: 9px; }
}

</style>
</head>

<body>

<!-- HOME -->
<section id="home" class="screen active">

<div class="cloud c1">☁️</div>
<div class="cloud c2">☁️</div>
<div class="cloud c3">☁️</div>

<div class="star" style="left:10%;top:15%">⭐</div>
<div class="star" style="right:12%;top:12%">✨</div>
<div class="star" style="left:15%;bottom:15%">🌟</div>
<div class="balloon" style="right:8%;bottom:20%">🎈</div>

<div class="logo">
    <div class="logo-icon">📚✨</div>
    <h1 data-i18n="appName">Mari Belajar</h1>
    <p data-i18n="tagline">Belajar sambil bermain! 🌈</p>
</div>

<div class="mascots">
    <div class="mascot">🐰</div>
    <div class="mascot">🐿️</div>
    <div class="mascot">🐻</div>
    <div class="mascot">🦅</div>
    <div class="mascot">🐱</div>
    <div class="mascot">🐧</div>
</div>

<button class="game-menu-btn academic-menu-btn" onclick="showScreen('characters')">
    🎓 <span data-i18n="academicGame">Game Akademik</span>
</button>

<button class="game-menu-btn social-menu-btn" onclick="showScreen('social')">
    🤝 <span data-i18n="socialGame">Game Sosial</span>
</button>

<button class="secondary-btn back-btn" onclick="showScreen('settings')">
    ⚙️ <span data-i18n="settings">Pengaturan</span>
</button>

</section>

<!-- SETTINGS -->
<section id="settings" class="screen">

<div class="panel">

<h2 class="title">⚙️ <span data-i18n="settings">Pengaturan</span></h2>

<div class="settings-row">

<div class="setting">
<h3>🌐 <span data-i18n="language">Bahasa</span></h3>
<select id="language" onchange="changeLanguage()">
<option value="id">🇮🇩 Indonesia</option>
<option value="en">🇬🇧 English</option>
</select>
</div>

<div class="setting">
<h3>🎵 <span data-i18n="music">Musik</span></h3>
<input id="volume" type="range" min="0" max="100" value="80"
oninput="musicVolume=this.value/100">
<p id="volumeText">80%</p>
</div>

<div class="setting">
<h3>📱 <span data-i18n="orientation">Orientasi</span></h3>
<select onchange="changeOrientation(this.value)">
<option value="auto" data-i18n="auto">🔄 Otomatis</option>
<option value="portrait" data-i18n="portrait">📱 Potret</option>
<option value="landscape" data-i18n="landscape">🖥️ Lanskap</option>
</select>
</div>

</div>

<br>

<button class="main-btn" onclick="showScreen('home')">
⬅️ <span data-i18n="back">Kembali</span>
</button>

</div>
</section>

<!-- MATERI SOSIAL -->
<section id="social" class="screen">
<div class="panel">
<h2 class="title">🤝 <span data-i18n="socialGame">Game Sosial</span></h2>
<div class="social-map-title" data-i18n="socialChoose">📍 Pilih tempat</div>
<div class="social-world-banner" aria-hidden="true">
<span class="world-stop">🏠🐰</span>
<span class="world-stop">🏫🐿️</span>
<span class="world-stop">🛝🐻</span>
<span class="world-stop">🌼👫</span>
</div>
<div class="social-map-grid">
<button class="social-place" data-topic="home"><span class="place-icon place-illustration" aria-hidden="true"><span class="place-building">🏠</span><span class="place-friend">🐰</span><span class="place-detail">🌷</span></span><span data-i18n="homeTopic">Rumah</span></button>
<button class="social-place" data-topic="school"><span class="place-icon place-illustration" aria-hidden="true"><span class="place-building">🏫</span><span class="place-friend">🐿️</span><span class="place-detail">📚</span></span><span data-i18n="schoolTopic">Sekolah</span></button>
<button class="social-place" data-topic="play"><span class="place-icon place-illustration" aria-hidden="true"><span class="place-building">🛝</span><span class="place-friend">🐻</span><span class="place-detail">⚽</span></span><span data-i18n="playTopic">Bermain</span></button>
<button class="social-place" data-topic="friends"><span class="place-icon place-illustration" aria-hidden="true"><span class="place-building">👫</span><span class="place-friend">🐱</span><span class="place-detail">💛</span></span><span data-i18n="friendTopic">Teman</span></button>
</div>
<br>
<button class="main-btn" onclick="startSocialGame()" data-i18n="socialPractice">🎮 Mulai</button>
<br><br>
<button class="secondary-btn back-btn" onclick="showScreen('home')" data-i18n="back">⬅️ Kembali</button>
</div>
</section>

<!-- CHARACTERS -->
<section id="characters" class="screen">

<div class="panel">

<h2 class="title">🎓 <span data-i18n="academicGame">Game Akademik</span></h2>
<div class="social-start-note" data-i18n="chooseFriend">Pilih teman belajar</div>

<div class="char-grid">

<button class="char-card" onclick="selectCharacter('lumi')">
<div class="char-icon">🐰</div>
<h3>Lumi</h3>
<p>🧠 <span data-i18n="smartEnergetic">Pintar & Enerjik</span></p>
</button>

<button class="char-card" onclick="selectCharacter('nara')">
<div class="char-icon">🐿️</div>
<h3>Nara</h3>
<p>🎨 <span data-i18n="creative">Kreatif</span></p>
</button>

<button class="char-card" onclick="selectCharacter('bimo')">
<div class="char-icon">🐻</div>
<h3>Bimo</h3>
<p>💪 <span data-i18n="calmStable">Sabar & Stabil</span></p>
</button>

<button class="char-card" onclick="selectCharacter('sky')">
<div class="char-icon">🦅</div>
<h3>Sky</h3>
<p>🔥 <span data-i18n="braveFocused">Berani & Fokus</span></p>
</button>

<button class="char-card" onclick="selectCharacter('luna')">
<div class="char-icon">🐱</div>
<h3>Luna</h3>
<p>🎯 <span data-i18n="carefulConsistent">Teliti & Konsisten</span></p>
</button>

<button class="char-card" onclick="selectCharacter('pippo')">
<div class="char-icon">🐧</div>
<h3>Pippo</h3>
<p>✍️ <span data-i18n="writingPractice">Latihan Menulis</span></p>
</button>

</div>

<button class="secondary-btn back-btn" onclick="showScreen('home')">
⬅️ Kembali
</button>

</div>
</section>

<!-- LEVEL -->
<section id="levels" class="screen">

<div class="panel">

<h2 class="title">🎓 <span data-i18n="academicLevel">Game Akademik • Pilih Level</span></h2>

<div class="level-grid">

<button id="levelCard1" class="level-card unlocked" data-level="1" onclick="startGame(1)">
<div class="level-number">🌱</div>
<h2>Level 1</h2>
<p><span data-i18n="level1Desc">Mudah<br>Belajar dengan santai.</span></p>
</button>

<button id="levelCard2" class="level-card locked" data-level="2" onclick="startGame(2)">
<div class="level-number">🌿</div>
<h2>Level 2</h2>
<p><span data-i18n="level2Desc">Sedang<br>Mulai lebih menantang.</span></p>
<span id="levelLock2" class="level-lock-label">🔒 Selesaikan Level 1</span>
</button>

<button id="levelCard3" class="level-card locked" data-level="3" onclick="startGame(3)">
<div class="level-number">🌳</div>
<h2>Level 3</h2>
<p><span data-i18n="level3Desc">Menengah<br>Lebih banyak pilihan.</span></p>
<span id="levelLock3" class="level-lock-label">🔒 Selesaikan Level 2</span>
</button>

<button id="levelCard4" class="level-card locked" data-level="4" onclick="startGame(4)">
<div class="level-number">🌲</div>
<h2>Level 4</h2>
<p><span data-i18n="level4Desc">Sulit<br>Latihan lebih panjang.</span></p>
<span id="levelLock4" class="level-lock-label">🔒 Selesaikan Level 3</span>
</button>

<button id="levelCard5" class="level-card locked" data-level="5" onclick="startGame(5)">
<div class="level-number">🏆</div>
<h2>Level 5</h2>
<p><span data-i18n="level5Desc">Ahli<br>Tantangan paling seru!</span></p>
<span id="levelLock5" class="level-lock-label">🔒 Selesaikan Level 4</span>
</button>

</div>

<button class="secondary-btn back-btn" onclick="showScreen('characters')">
⬅️ <span data-i18n="back">Kembali</span>
</button>

</div>
</section>

<!-- SOCIAL GAME -->
<section id="socialGame" class="screen">
<div class="game-top">
<button class="secondary-btn" onclick="showScreen('social')">⬅️ <span data-i18n="choosePlace">Pilih Tempat</span></button>
<h2 class="game-title">🤝 <span data-i18n="socialGame">Game Sosial</span></h2>
<div class="game-stats">
<div class="stat-pill">⭐ <span id="socialScore">0</span></div>
<div class="stat-pill">🎯 <span id="socialTarget">50</span></div>
<div class="stat-pill lives-pill" id="socialLivesPill">❤️ <span id="socialLives">5</span></div>
</div>
</div>
<div class="question-box">
<div style="font-size:55px">🤝</div>
<div id="socialQuestion" class="question"></div>
<button class="speak-btn" onclick="speakSocialQuestion()">🔊 <span data-i18n="readQuestion">Bacakan Soal</span></button>
<div id="socialGameArea"></div>
<div id="socialFeedback" class="feedback"></div>
<div class="animated-scene" style="margin-top:16px">
<div class="scene-cloud c1">☁️</div>
<div class="scene-cloud c2">☁️</div>
<div class="scene-item i1">🌼</div>
<div class="scene-item i2">🌸</div>
<div class="scene-item i3">⭐</div>
<div class="scene-character scene-bimo">🤝</div>
</div>
</div>
</section>

<!-- GAME -->
<section id="game" class="screen">

<div class="game-top">

<button class="secondary-btn" onclick="showScreen('levels')">
⬅️ <span data-i18n="exit">Keluar</span>
</button>

<h2 class="game-title">🎓 <span data-i18n="academicGame">Game Akademik</span></h2>

<div class="game-stats">
    <div class="stat-pill">⭐ <span id="score">0</span></div>
    <div class="stat-pill">🎯 <span id="targetScore">50</span></div>
    <div class="stat-pill lives-pill">❤️ <span id="lives">5</span></div>
</div>

</div>

<div class="question-box">

<div id="characterDisplay" style="font-size:55px"></div>

<div id="question" class="question"></div>

<button class="speak-btn" onclick="speakCurrentQuestion()">
🔊 <span data-i18n="readQuestion">Bacakan Soal</span>
</button>

<div id="gameArea"></div>

<div id="feedback" class="feedback"></div>

<div id="animatedScene" class="animated-scene"></div>

</div>

</section>

<script>
/* =========================
   DATA
========================= */

const words=[
["Apel","🍎"],
["Pisang","🍌"],
["Jeruk","🍊"],
["Semangka","🍉"],
["Anggur","🍇"],
["Kucing","🐱"],
["Anjing","🐶"],
["Ikan","🐟"],
["Ayam","🐔"],
["Sapi","🐮"],
["Mobil","🚗"],
["Bus","🚌"],
["Sepeda","🚲"],
["Pesawat","✈️"],
["Kapal","🚢"],
["Buku","📚"],
["Pensil","✏️"],
["Tas","🎒"],
["Bola","⚽"],
["Rumah","🏠"],
["Pohon","🌳"],
["Bunga","🌷"],
["Matahari","☀️"],
["Bulan","🌙"],
["Bintang","⭐"],
["Kue","🍰"],
["Susu","🥛"],
["Es Krim","🍦"],
["Topi","🧢"],
["Sepatu","👟"]
];

const englishWords=[
["Apple","🍎"],
["Banana","🍌"],
["Orange","🍊"],
["Watermelon","🍉"],
["Grapes","🍇"],
["Cat","🐱"],
["Dog","🐶"],
["Fish","🐟"],
["Chicken","🐔"],
["Cow","🐮"],
["Car","🚗"],
["Bus","🚌"],
["Bicycle","🚲"],
["Airplane","✈️"],
["Ship","🚢"],
["Book","📚"],
["Pencil","✏️"],
["Bag","🎒"],
["Ball","⚽"],
["House","🏠"],
["Tree","🌳"],
["Flower","🌷"],
["Sun","☀️"],
["Moon","🌙"],
["Star","⭐"],
["Cake","🍰"],
["Milk","🥛"],
["Ice Cream","🍦"],
["Hat","🧢"],
["Shoes","👟"]
];

const characters={
lumi:"🐰",
nara:"🐿️",
bimo:"🐻",
sky:"🦅",
luna:"🐱",
pippo:"🐧"
};

let selectedCharacter="lumi";
let selectedLevel=1;
let questionNumber=0;
let score=0;
let lives=5;
let gameFinished=false;
const TARGET_SCORE=50;
const QUESTIONS_PER_GAME=5;
let academicQuestionSeen=Object.create(null);
let musicVolume=.8;
let currentQuestionText="";
let audioContext=null;
let musicTimer=null;
let speechQueue=[];
let activeSpeech=null;
let speechGeneration=0;
let scheduledSpeechTimer=null;

/* =========================
   SCREEN
========================= */

const LEVEL_PROGRESS_KEY = "mariBelajarMaxUnlockedLevel";
function getMaxUnlockedLevel(){
    const key = `${LEVEL_PROGRESS_KEY}:${selectedCharacter}`;
    try { return Math.max(1, Math.min(5, Number(localStorage.getItem(key)) || 1)); }
    catch(e) { return (window.__maxUnlockedLevels || {})[selectedCharacter] || 1; }
}
function saveMaxUnlockedLevel(level){
    const next = Math.max(getMaxUnlockedLevel(), Math.min(5, level));
    const progress = window.__maxUnlockedLevels || (window.__maxUnlockedLevels = {});
    progress[selectedCharacter] = next;
    try { localStorage.setItem(`${LEVEL_PROGRESS_KEY}:${selectedCharacter}`, String(next)); } catch(e) {}
  updateLevelLocks();
}
function updateLevelLocks(){
  const maxLevel = getMaxUnlockedLevel();
    for(let level=1; level<=5; level++){
    const card=document.getElementById("levelCard"+level);
    if(!card) continue;
    const unlocked=level<=maxLevel;
    card.classList.toggle("locked", !unlocked);
    card.classList.toggle("unlocked", unlocked);
    card.setAttribute("aria-disabled", String(!unlocked));
    const lockLabel=document.getElementById("levelLock"+level);
    if(lockLabel){
      lockLabel.style.display=unlocked?"none":"block";
      lockLabel.textContent=lang==="id" ? `🔒 Selesaikan Level ${level-1} dulu` : `🔒 Complete Level ${level-1} first`;
    }
    const number=card.querySelector(".level-number");
    if(number){
    const icons={1:"🌱",2:"🌿",3:"🌳",4:"🌲",5:"🏆"};
      number.textContent=unlocked?icons[level]:"🔒";
    }
  }
}

function showScreen(id){

document.querySelectorAll(".screen").forEach(s=>{
s.classList.remove("active");
});

document.getElementById(id).classList.add("active");
if(id==="levels") updateLevelLocks();

if(id==="home" || id==="levels" || id==="characters"){
stopSpeech();
}
if(id==="home"){
stopMusic();
}

}

/* =========================
   CHARACTER
========================= */

function selectCharacter(character){

selectedCharacter=character;

showScreen("levels");

}

/* =========================
   START GAME
========================= */

function startGame(level){
if(level > getMaxUnlockedLevel()){
  updateLevelLocks();
  const msg = lang==="id" ? `Selesaikan Level ${level-1} terlebih dahulu!` : `Complete Level ${level-1} first!`;
    if(typeof speak === "function") speak(msg,true);
  const feedback=document.getElementById("feedback");
  if(feedback) feedback.textContent="🔒 "+msg;
  return;
}
selectedLevel=level;
academicQuestionSeen=Object.create(null);
questionNumber=0;
score=0;
lives=5;
gameFinished=false;

document.getElementById("score").textContent=score;
document.getElementById("targetScore").textContent=TARGET_SCORE;
document.getElementById("lives").textContent=lives;
document.getElementById("characterDisplay").textContent=
characters[selectedCharacter];

showScreen("game");
startMusic();
renderAnimatedScene();
nextQuestion();
}

/* =========================
   RANDOM
========================= */

function shuffle(array){
const result=[...array];
for(let index=result.length-1;index>0;index--){
const swapIndex=Math.floor(Math.random()*(index+1));
[result[index],result[swapIndex]]=[result[swapIndex],result[index]];
}
return result;
}

function randomItems(data,count){

return shuffle(data).slice(0,count);

}

function pickUnseen(key,items,getKey){
const seen=academicQuestionSeen[key]||(academicQuestionSeen[key]=new Set());
let available=items.filter(item=>!seen.has(getKey(item)));
if(!available.length){
seen.clear();
available=items;
}
const selected=available[Math.floor(Math.random()*available.length)];
seen.add(getKey(selected));
return selected;
}

function randomUnseenItems(key,data,count){
const seen=academicQuestionSeen[key]||(academicQuestionSeen[key]=new Set());
let items,signature,attempts=0;
do{
items=randomItems(data,count);
signature=items.map(item=>item[0]).sort().join("|");
attempts++;
}while(seen.has(signature)&&attempts<20);
seen.add(signature);
return items;
}

/* =========================
   QUESTIONS
========================= */

function nextQuestion(){
if(gameFinished || lives<=0)return;
if(questionNumber>=QUESTIONS_PER_GAME){
finishGame();
return;
}

questionNumber++;

document.getElementById("feedback").textContent="";
const area=document.getElementById("gameArea");
area.innerHTML="";

if(selectedCharacter==="lumi"){
renderMatch(area);
}
else if(selectedCharacter==="nara"){
renderShadow(area);
}
else if(selectedCharacter==="bimo"){
renderSequence(area);
}
else if(selectedCharacter==="sky"){
renderChoice(area);
}
else if(selectedCharacter==="luna"){
renderMemory(area);
}
else if(selectedCharacter==="pippo"){
renderWriting(area);
}

scheduleSpeech(currentQuestionText,350);
}

/* =========================
   LUMI MATCHING
========================= */

function renderMatch(area){
const dataCount=[2,3,4,5,6][selectedLevel-1]||2;
const data=randomUnseenItems("lumi",langData(),dataCount);
const shuffledPictures=shuffle(data);

currentQuestionText=
lang==="id"
?"Jodohkan nama di kiri dengan gambar yang tepat di kanan!"
:"Match the names on the left with the correct pictures on the right!";

document.getElementById("question").textContent=currentQuestionText;

const layout=document.createElement("div");
layout.className="match-layout lumi-match";

const left=document.createElement("div");
left.className="match-column";

const right=document.createElement("div");
right.className="match-column";

const leftTitle=document.createElement("div");
leftTitle.className="lumi-column-title";
leftTitle.textContent=lang==="id"?"📝 Nama":"📝 Names";
left.appendChild(leftTitle);

const rightTitle=document.createElement("div");
rightTitle.className="lumi-column-title";
rightTitle.textContent=lang==="id"?"🖼️ Gambar":"🖼️ Pictures";
right.appendChild(rightTitle);

let selectedNameBtn=null;
let selectedItem=null;
let matchedCount=0;
let checking=false;

data.forEach(item=>{
const btn=document.createElement("button");
btn.className="option lumi-name-option";
btn.textContent=item[0];
btn.dataset.name=item[0];

btn.onclick=()=>{
if(checking || btn.classList.contains("matched"))return;

if(selectedNameBtn===btn){
btn.classList.remove("selected");
selectedNameBtn=null;
selectedItem=null;
return;
}

if(selectedNameBtn){
selectedNameBtn.classList.remove("selected");
}

selectedNameBtn=btn;
selectedItem=item;
btn.classList.add("selected");
    speak(item[0],true);
feedback(lang==="id"?"Sekarang pilih gambarnya!":"Now choose the picture!");
};

left.appendChild(btn);
});

shuffledPictures.forEach(item=>{
const btn=document.createElement("button");
btn.className="option lumi-picture-option";
btn.dataset.name=item[0];
btn.innerHTML=`<span class="picture">${item[1]}</span>`;

btn.onclick=()=>{
if(checking || btn.classList.contains("matched"))return;

if(!selectedNameBtn){
feedback(lang==="id"?"Pilih nama di kiri dulu!":"Choose a name on the left first!");
    speak(lang==="id"?"Pilih nama di kiri dulu!":"Choose a name on the left first!",true);
return;
}

checking=true;
speak(item[0],true);

if(selectedItem[0]===item[0]){
selectedNameBtn.classList.remove("selected");
selectedNameBtn.classList.add("matched");
btn.classList.add("matched");
matchedCount++;
selectedNameBtn=null;
selectedItem=null;

feedback(lang==="id"?"🎉 Pasangan benar!":"🎉 Correct pair!");
celebrateSmall();

if(matchedCount===data.length){
score+=10;
updateScore();
setTimeout(nextQuestion,1000);
}else{
setTimeout(()=>{checking=false;},300);
}
}else{
selectedNameBtn.classList.add("selected-wrong");
btn.classList.add("selected-wrong");
loseLife();

feedback(lang==="id"?"❌ Belum cocok, coba lagi!":"❌ Not a match, try again!");
speak(lang==="id"?"Salah, coba lagi!":"Wrong, try again!");

setTimeout(()=>{
selectedNameBtn?.classList.remove("selected-wrong","selected");
btn.classList.remove("selected-wrong");
selectedNameBtn=null;
selectedItem=null;
checking=false;
},650);
}
};

right.appendChild(btn);
});

layout.appendChild(left);
layout.appendChild(right);
area.appendChild(layout);
}

/* =========================
   NARA
========================= */

function renderShadow(area){
const allData=langData();
const target=pickUnseen("nara",allData,item=>item[0]);
const choiceCount=selectedLevel+2;
const data=[target,...randomItems(allData.filter(item=>item[0]!==target[0]),choiceCount-1)];

currentQuestionText=
lang==="id"
?`Manakah gambar ${target[0]}?`
:`Which picture is ${target[0]}?`;

document.getElementById("question").textContent=currentQuestionText;

const grid=document.createElement("div");
grid.className="choice-grid";

shuffle(data).forEach(item=>{
const btn=document.createElement("button");
btn.className="choice-btn";
btn.innerHTML=`
<div style="font-size:65px">${item[1]}</div>
<div>${item[0]}</div>
`;

btn.onclick=()=>{
if(btn.disabled)return;
speak(item[0],true);

if(item[0]===target[0]){
btn.classList.add("correct");
btn.disabled=true;
feedback("🎨 "+(lang==="id"?"Keren! Benar!":"Awesome! Correct!"));
celebrateSmall();
score+=10;
updateScore();
setTimeout(nextQuestion,900);
}else{
btn.classList.add("wrong");
loseLife();
feedback("💭 "+(lang==="id"?"Coba lagi!":"Try again!"));
speak(lang==="id"?"Salah, coba lagi!":"Wrong, try again!");
setTimeout(()=>btn.classList.remove("wrong"),500);
}
};

grid.appendChild(btn);
});

area.appendChild(grid);
}

/* =========================
   BIMO
========================= */

function renderSequence(area){
const pictures=["🍎","🍌","🍊","🍇","🍓","🍐","⭐","🌼","⚽","🐟"];
const pictureRow=(emoji,count)=>{
const row=document.createElement("div");
row.className="bimo-picture-row";
row.setAttribute("role","img");
row.setAttribute("aria-label",lang==="id"?`${count} gambar ${emoji}`:`${count} pictures ${emoji}`);
for(let index=0;index<count;index++){
const picture=document.createElement("span");
picture.className="bimo-picture";
picture.textContent=emoji;
picture.setAttribute("aria-hidden","true");
row.appendChild(picture);
}
return row;
};
const setQuestion=text=>{
currentQuestionText=text;
document.getElementById("question").textContent=text;
};
const markCorrect=()=>{
score+=10;
updateScore();
feedback("🐻 "+(lang==="id"?"Hebat! Jawabanmu benar!":"Great! Your answer is correct!"));
celebrateSmall();
setTimeout(nextQuestion,900);
};
const renderNumberChoices=answer=>{
const choices=new Set([answer]);
for(let offset=1;choices.size<4;offset++){
const lower=answer-offset;
const higher=answer+offset;
if(lower>0)choices.add(lower);
if(choices.size<4)choices.add(higher);
}
const grid=document.createElement("div");
grid.className="choice-grid";
shuffle([...choices]).forEach(number=>{
const button=document.createElement("button");
button.className="choice-btn";
button.textContent=number;
button.onclick=()=>{
if(button.disabled)return;
speak(String(number),true);
if(number===answer){
button.classList.add("correct");
button.disabled=true;
markCorrect();
}else{
button.classList.add("wrong");
loseLife();
feedback("💭 "+(lang==="id"?"Coba hitung lagi!":"Try counting again!"));
speak(lang==="id"?"Belum tepat, coba lagi!":"Not quite, try again!");
setTimeout(()=>button.classList.remove("wrong"),500);
}
};
grid.appendChild(button);
});
area.appendChild(grid);
};

if(selectedLevel===1){
const count=1+Math.floor(Math.random()*10);
const emoji=pictures[Math.floor(Math.random()*pictures.length)];
setQuestion(lang==="id"?"Ada berapa jumlah gambar? Pilih angkanya.":"How many pictures are there? Choose the number.");
area.appendChild(pictureRow(emoji,count));
renderNumberChoices(count);
return;
}

if(selectedLevel===2){
const isSubtraction=questionNumber%2===0;
const firstIndex=Math.floor(Math.random()*pictures.length);
const firstCount=isSubtraction?2+Math.floor(Math.random()*7):1+Math.floor(Math.random()*5);
const secondCount=isSubtraction?1+Math.floor(Math.random()*(firstCount-1)):1+Math.floor(Math.random()*5);
const equation=document.createElement("div");
equation.className="bimo-addition";
equation.appendChild(pictureRow(pictures[firstIndex],firstCount));
const operator=document.createElement("span");
operator.className="bimo-operator";
operator.textContent=isSubtraction?"−":"+";
equation.appendChild(operator);
const secondRow=pictureRow(isSubtraction?pictures[firstIndex]:pictures[(firstIndex+1+Math.floor(Math.random()*(pictures.length-1)))%pictures.length],secondCount);
if(isSubtraction){
secondRow.classList.add("removed");
secondRow.setAttribute("aria-label",lang==="id"?`${secondCount} gambar diambil`:`${secondCount} pictures taken away`);
}
equation.appendChild(secondRow);
const equals=document.createElement("span");
equals.className="bimo-operator";
equals.textContent="=";
equation.appendChild(equals);
const questionMark=document.createElement("span");
questionMark.className="bimo-operator";
questionMark.textContent="?";
equation.appendChild(questionMark);
setQuestion(isSubtraction
?lang==="id"?"Ada beberapa gambar, lalu sebagian diambil. Berapa gambar yang tersisa?":"Some pictures are taken away. How many are left?"
:lang==="id"?"Berapa jumlah semua gambar?":"How many pictures are there altogether?");
area.appendChild(equation);
renderNumberChoices(isSubtraction?firstCount-secondCount:firstCount+secondCount);
return;
}

if(selectedLevel===3){
const counts=shuffle([1,2,3,4,5,6,7,8,9,10]).slice(0,3);
const emojis=randomItems(pictures,3);
const items=counts.map((count,index)=>({count,emoji:emojis[index]}));
const selection=[];
let checking=false;
setQuestion(lang==="id"?"Urutkan kelompok gambar dari jumlah terbesar ke terkecil!":"Order the picture groups from the largest amount to the smallest!");
const grid=document.createElement("div");
grid.className="bimo-order-grid";
shuffle(items).forEach(item=>{
const button=document.createElement("button");
button.className="bimo-order-card";
button.appendChild(pictureRow(item.emoji,item.count));
const badge=document.createElement("span");
badge.className="bimo-order-badge";
badge.textContent="•";
button.appendChild(badge);
button.onclick=()=>{
if(checking||button.disabled)return;
selection.push(item);
button.classList.add("selected");
button.disabled=true;
badge.textContent=selection.length;
speak(String(item.count),true);
if(selection.length===items.length){
checking=true;
const expected=[...items].sort((first,second)=>second.count-first.count);
if(selection.every((selected,index)=>selected.count===expected[index].count)){
markCorrect();
}else{
loseLife();
feedback("🔄 "+(lang==="id"?"Belum tepat, coba urutkan lagi!":"Not quite, try ordering them again!"));
speak(lang==="id"?"Coba urutkan lagi!":"Try ordering them again!");
setTimeout(()=>{
selection.length=0;
checking=false;
grid.querySelectorAll("button").forEach(card=>{
card.disabled=false;
card.classList.remove("selected");
card.querySelector(".bimo-order-badge").textContent="•";
});
},700);
}
}
};
grid.appendChild(button);
});
area.appendChild(grid);
return;
}

const isAdvanced=selectedLevel===5;
const groupCount=isAdvanced?4+Math.floor(Math.random()*3):2+Math.floor(Math.random()*3);
const countPerGroup=isAdvanced?3+Math.floor(Math.random()*4):2+Math.floor(Math.random()*4);
const emoji=pictures[Math.floor(Math.random()*pictures.length)];
setQuestion(isAdvanced
?lang==="id"?"Tantangan perkalian! Berapa jumlah semua gambar di dalam kelompok?":"Multiplication challenge! How many pictures are there in all the groups?"
:lang==="id"?"Kalikan jumlah kelompok dengan gambar di tiap kelompok. Berapa semuanya?":"Multiply the number of groups by the pictures in each group. How many are there?");
const groups=document.createElement("div");
groups.className="bimo-groups";
for(let group=0;group<groupCount;group++){
const card=document.createElement("div");
card.className="bimo-group";
card.setAttribute("aria-label",lang==="id"?"Satu kelompok gambar":"One group of pictures");
card.appendChild(pictureRow(emoji,countPerGroup));
groups.appendChild(card);
}
area.appendChild(groups);
renderNumberChoices(groupCount*countPerGroup);
}

/* =========================
   SKY
========================= */

function renderChoice(area){
const allData=langData();
const target=pickUnseen("sky",allData,item=>item[0]);
const choiceCount=selectedLevel+2;
const data=[target,...randomItems(allData.filter(item=>item[0]!==target[0]),choiceCount-1)];

currentQuestionText=
lang==="id"
?`Apa nama benda ini? ${target[1]}`
:`What is this? ${target[1]}`;

document.getElementById("question").textContent=currentQuestionText;

const grid=document.createElement("div");
grid.className="choice-grid";

shuffle(data).forEach(item=>{
const btn=document.createElement("button");
btn.className="choice-btn";
btn.textContent=item[0];

btn.onclick=()=>{
if(btn.disabled)return;
speak(item[0],true);

if(item[0]===target[0]){
btn.classList.add("correct");
btn.disabled=true;
score+=10;
updateScore();
feedback("🦅 "+(lang==="id"?"Tepat sekali!":"Exactly right!"));
celebrateSmall();
setTimeout(nextQuestion,900);
}else{
btn.classList.add("wrong");
loseLife();
feedback("🦅 "+(lang==="id"?"Belum benar!":"Not correct yet!"));
speak(lang==="id"?"Salah, coba lagi!":"Wrong, try again!");
setTimeout(()=>btn.classList.remove("wrong"),500);
}
};

grid.appendChild(btn);
});

area.appendChild(grid);
}

/* =========================
   LUNA MEMORY
   5 PAIRS / 10 CARDS
========================= */

function renderMemory(area){
const availableData=langData();
const pairCount=selectedLevel+1;
const pairs=randomUnseenItems("luna",availableData,pairCount);

let cards=[];
pairs.forEach((item,index)=>{
cards.push({id:index,name:item[0],emoji:item[1]});
cards.push({id:index,name:item[0],emoji:item[1]});
});
cards=shuffle(cards);

const box=document.createElement("div");
box.className="special-area";

const status=document.createElement("div");
status.className="memory-status";

let matchedPairs=0;

function updateStatus(){
status.textContent=
lang==="id"
?`⭐ Pasangan ditemukan: ${matchedPairs} / ${pairCount}`
:`⭐ Pairs found: ${matchedPairs} / ${pairCount}`;
}

const progress=document.createElement("div");
progress.className="memory-progress";

const progressBar=document.createElement("div");
progressBar.className="memory-progress-bar";

progress.appendChild(progressBar);

const grid=document.createElement("div");
grid.className="memory-grid";

let firstCard=null;
let secondCard=null;
let locked=true;

updateStatus();

cards.forEach((item,index)=>{
const card=document.createElement("button");
card.className="memory-card";
card.dataset.id=item.id;
card.dataset.index=index;

card.innerHTML=`
<span class="question-mark">❓</span>
<span class="memory-content">
<span class="memory-emoji">${item.emoji}</span>
<span class="memory-name">${item.name}</span>
</span>
`;

card.onclick=()=>{
if(locked || card.classList.contains("matched") || card===firstCard)return;

card.classList.add("open");
speak(item.name,true);

if(!firstCard){
firstCard=card;
return;
}

secondCard=card;
locked=true;

if(firstCard.dataset.id===secondCard.dataset.id){
firstCard.classList.add("matched");
secondCard.classList.add("matched");

matchedPairs++;
updateStatus();
progressBar.style.width=(matchedPairs/pairCount*100)+"%";

feedback(lang==="id"?"🎉 Pasangan benar!":"🎉 Correct pair!");

firstCard=null;
secondCard=null;
locked=false;

if(matchedPairs===pairCount){
score+=10;
updateScore();
celebrateSmall();

setTimeout(()=>{
speak(lang==="id"
?"Hebat! Semua pasangan sudah ditemukan!"
:"Amazing! You found all the pairs!");
},250);

setTimeout(nextQuestion,1200);
}
}else{
loseLife();
feedback(lang==="id"?"❌ Belum cocok. Coba lagi!":"❌ Not a match. Try again!");
speak(lang==="id"?"Salah, coba lagi!":"Wrong, try again!");

setTimeout(()=>{
firstCard.classList.remove("open");
secondCard.classList.remove("open");
firstCard=null;
secondCard=null;
locked=false;
},900);
}
};

grid.appendChild(card);
});

// Preview singkat agar permainan Luna lebih mudah untuk dipahami.
// Lama preview mengikuti tingkat kesulitan: level 1 paling lama.
const previewTime = [5000,4000,3200,2400,1700][selectedLevel-1]||5000;
const previewText = lang==="id"
    ? "👀 Perhatikan semua gambar dan ingat pasangannya!"
    : "👀 Look carefully and remember the pairs!";
const preview=document.createElement("div");
preview.className="memory-preview";
preview.textContent=previewText;
box.appendChild(preview);

// Semua kartu dibuka sebentar di awal setiap babak.
cards.forEach((_,i)=>{
    grid.children[i].classList.add("open");
});
speak(lang==="id" ? "Perhatikan gambarnya baik-baik!" : "Look at the pictures carefully!",true);

setTimeout(()=>{
    if(gameFinished || lives<=0)return;
    cards.forEach((_,i)=>{
        const c=grid.children[i];
        if(!c.classList.contains("matched")) c.classList.remove("open");
    });
    preview.remove();
    locked=false;
},previewTime);

box.appendChild(status);
box.appendChild(progress);
box.appendChild(grid);
area.appendChild(box);
}

/* =========================
   PIPPO WRITING PRACTICE
========================= */

const writingRiddles={
"🍎":{id:["Warnanya merah dan tumbuh di pohon.","Buah ini sering dijadikan jus."],en:["It is red and grows on a tree.","This fruit is often made into juice."]},
"🍌":{id:["Kulitnya berwarna kuning saat matang.","Bentuknya panjang dan melengkung."],en:["Its peel is yellow when ripe.","It is long and curved."]},
"🍊":{id:["Kulitnya mudah dikupas.","Buah ini berbentuk bulat dan berwarna oranye."],en:["Its peel is easy to remove.","This round fruit is orange."]},
"🍉":{id:["Kulitnya hijau, tetapi bagian dalamnya merah.","Buah besar ini banyak mengandung air."],en:["Its skin is green, but the inside is red.","This large fruit has lots of water."]},
"🍇":{id:["Buah-buah kecil ini tumbuh bergerombol.","Warnanya bisa ungu atau hijau."],en:["These small fruits grow in clusters.","They can be purple or green."]},
"🐱":{id:["Hewan ini mengeong.","Ia suka mengejar tikus."],en:["This animal meows.","It likes to chase mice."]},
"🐶":{id:["Hewan ini menggonggong.","Ia sering disebut sahabat manusia."],en:["This animal barks.","It is often called man's best friend."]},
"🐟":{id:["Hewan ini hidup dan berenang di air.","Ia bernapas menggunakan insang."],en:["This animal lives and swims in water.","It breathes through gills."]},
"🐔":{id:["Hewan ini berkokok pada pagi hari.","Betinanya dapat menghasilkan telur."],en:["This animal crows in the morning.","The female can lay eggs."]},
"🐮":{id:["Hewan ini berbunyi moo.","Susu dapat diperoleh dari hewan ini."],en:["This animal says moo.","Milk comes from this animal."]},
"🚗":{id:["Kendaraan ini memiliki empat roda.","Biasanya digunakan keluarga untuk bepergian."],en:["This vehicle has four wheels.","Families often use it to travel."]},
"🚌":{id:["Kendaraan besar ini mengangkut banyak penumpang.","Kendaraan ini biasanya berhenti di halte."],en:["This large vehicle carries many passengers.","It usually stops at bus stops."]},
"🚲":{id:["Kendaraan ini memiliki dua roda dan pedal.","Kamu mengayuhnya agar bisa berjalan."],en:["This vehicle has two wheels and pedals.","You pedal it to make it move."]},
"✈️":{id:["Kendaraan ini memiliki sayap.","Ia membawa penumpang terbang di langit."],en:["This vehicle has wings.","It carries passengers through the sky."]},
"🚢":{id:["Kendaraan besar ini berlayar di laut.","Penumpang atau barang bisa dibawa di atasnya."],en:["This large vehicle sails on the sea.","It can carry passengers or cargo."]},
"📚":{id:["Benda ini memiliki banyak halaman.","Kamu bisa membaca cerita atau belajar darinya."],en:["This item has many pages.","You can read stories or learn from it."]},
"✏️":{id:["Benda ini digunakan untuk menulis.","Ujungnya bisa diraut jika sudah tumpul."],en:["This item is used for writing.","Its tip can be sharpened when dull."]},
"🎒":{id:["Benda ini dipakai di punggung.","Buku dan alat sekolah bisa dibawa di dalamnya."],en:["This item is worn on your back.","Books and school supplies can be carried inside."]},
"⚽":{id:["Benda ini berbentuk bulat.","Kamu bisa menendangnya saat bermain."],en:["This item is round.","You can kick it when playing."]},
"🏠":{id:["Tempat ini memiliki pintu dan jendela.","Keluarga tinggal dan beristirahat di sini."],en:["This place has doors and windows.","Families live and rest here."]},
"🌳":{id:["Tumbuhan ini memiliki batang dan banyak daun.","Kita bisa berteduh di bawahnya."],en:["This plant has a trunk and many leaves.","We can rest in its shade."]},
"🌷":{id:["Tumbuhan ini memiliki kelopak yang cantik.","Banyak orang menaruhnya di dalam vas."],en:["This plant has beautiful petals.","People often put it in a vase."]},
"☀️":{id:["Benda langit ini tampak pada siang hari.","Cahayanya membuat bumi terasa hangat."],en:["This object appears in the daytime sky.","Its light makes Earth feel warm."]},
"🌙":{id:["Benda langit ini tampak pada malam hari.","Bentuknya kadang terlihat seperti sabit."],en:["This object appears in the night sky.","Sometimes it looks like a crescent."]},
"⭐":{id:["Benda langit ini tampak berkelap-kelip.","Kita bisa melihat banyak benda ini pada malam cerah."],en:["This object twinkles in the sky.","We can see many of them on a clear night."]},
"🍰":{id:["Makanan ini rasanya manis.","Biasanya makanan ini dipotong dan disajikan saat ulang tahun."],en:["This food tastes sweet.","It is often sliced and served at birthdays."]},
"🥛":{id:["Minuman ini berwarna putih.","Minuman ini sering dituangkan ke dalam gelas."],en:["This drink is white.","It is often poured into a glass."]},
"🍦":{id:["Makanan penutup ini disajikan dingin.","Makanan ini mudah meleleh jika dibiarkan."],en:["This dessert is served cold.","It melts if left out."]},
"🧢":{id:["Benda ini dipakai di kepala.","Benda ini bisa melindungi kepala dari sinar matahari."],en:["This item is worn on the head.","It can protect your head from the sun."]},
"👟":{id:["Benda ini dipakai di kaki.","Kamu memakainya saat berjalan atau berolahraga."],en:["This item is worn on your feet.","You wear it when walking or exercising."]}
};

function renderWriting(area){
const target=pickUnseen("pippo-writing",langData(),item=>item[0]);
const word=target[0];
let incorrectAttempts=0;
let answer=word;
let prompt;
let modelText="";
let riddleClues=null;

if(selectedLevel===1){
answer=word.charAt(0);
prompt=lang==="id"?"Tulislah huruf pertama dari nama gambar ini.":"Write the first letter of this picture's name.";
modelText=word;
}else if(selectedLevel===2){
const letterIndexes=[...word].map((letter,index)=>letter===" "?-1:index).filter(index=>index>=0);
const missingIndex=letterIndexes[Math.floor(Math.random()*letterIndexes.length)];
answer=word[missingIndex];
modelText=[...word].map((letter,index)=>index===missingIndex?"_":letter).join("");
prompt=lang==="id"?"Lengkapi kata dengan menulis huruf yang hilang.":"Complete the word by writing the missing letter.";
}else if(selectedLevel===3){
prompt=lang==="id"?"Salin kata pada contoh ke dalam kotak.":"Copy the word from the example into the box.";
modelText=word;
}else if(selectedLevel===4){
prompt=lang==="id"?"Lihat gambarnya, lalu tulis nama benda itu.":"Look at the picture, then write the object's name.";
}else if(selectedLevel===5){
answer=word;
riddleClues=writingRiddles[target[1]][lang];
prompt=lang==="id"?"Tebak bendanya dari dua petunjuk, lalu tulis namanya!":"Guess the object from two clues, then write its name!";
}else{
answer=word;
}

currentQuestionText=riddleClues?`${prompt} ${riddleClues.join(" ")}`:prompt;
document.getElementById("question").textContent=prompt;

const exercise=document.createElement("form");
exercise.className="writing-exercise";
if(riddleClues){
const clues=document.createElement("div");
clues.className="writing-clues";
riddleClues.forEach((clue,index)=>{
const clueElement=document.createElement("div");
clueElement.textContent=`🔎 ${lang==="id"?"Petunjuk":"Clue"} ${index+1}: ${clue}`;
clues.appendChild(clueElement);
});
exercise.appendChild(clues);
}else{
const picture=document.createElement("div");
picture.className="writing-picture";
picture.textContent=target[1];
picture.setAttribute("role","img");
picture.setAttribute("aria-label",word);
exercise.appendChild(picture);
}

if(modelText){
const model=document.createElement("div");
model.className="writing-model";
model.textContent=modelText;
exercise.appendChild(model);
}

const input=document.createElement("input");
input.className="writing-input";
input.type="text";
input.autocomplete="off";
input.autocapitalize="off";
input.spellcheck=false;
input.setAttribute("aria-label",prompt);
input.placeholder=lang==="id"?"Tulis jawabanmu di sini":"Write your answer here";
exercise.appendChild(input);

const submit=document.createElement("button");
submit.className="main-btn writing-submit";
submit.type="submit";
submit.textContent=lang==="id"?"Periksa":"Check";
exercise.appendChild(submit);

exercise.addEventListener("submit",event=>{
event.preventDefault();
if(input.disabled)return;
const normalize=value=>value.trim().toLocaleLowerCase().normalize("NFC").replace(/\s+/g," ");
if(normalize(input.value)===normalize(answer)){
input.disabled=true;
submit.disabled=true;
score+=10;
updateScore();
feedback("🐧 "+(lang==="id"?"Bagus! Tulisanmu benar!":"Great! Your writing is correct!"));
celebrateSmall();
setTimeout(nextQuestion,900);
}else{
incorrectAttempts++;
if(lives>1)loseLife();
if(incorrectAttempts>=3){
input.disabled=true;
submit.disabled=true;
feedback("✍️ "+(lang==="id"?`Kunci jawaban: ${answer}. Lanjut ke soal berikutnya!`:`Answer: ${answer}. Moving to the next question!`));
setTimeout(nextQuestion,1800);
}else{
feedback("✍️ "+(lang==="id"?"Belum tepat, coba tulis lagi!":"Not quite, try writing it again!"));
input.focus();
input.select();
}
}
});

area.appendChild(exercise);
input.focus();
}


/* =========================
   MATERI SOSIAL - LATIHAN
========================= */

const socialQuestions=[
{topic:"home",scene:"🏠👋",type:"action",q:{id:"Pulang ke rumah. Apa yang sebaiknya kamu lakukan?",en:"You arrive home. What should you do?"},a:{id:"Menyapa keluarga",en:"Greet your family"},o:{id:["Menyapa keluarga","Berteriak","Langsung masuk kamar"],en:["Greet your family","Shout","Go straight to your room"]}},
{topic:"home",scene:"🍽️😊",type:"phrase",q:{id:"Keluarga memberi kamu makanan. Apa yang kamu katakan?",en:"Your family gives you food. What do you say?"},a:{id:"Terima kasih",en:"Thank you"},o:{id:["Terima kasih","Pergi sana","Aku tidak mau!"],en:["Thank you","Go away","I don’t want it!"]}},
{topic:"home",scene:"🥤🙋",type:"choice",q:{id:"Kamu ingin minum. Pilihan mana yang sopan?",en:"You want a drink. Which choice is polite?"},a:{id:"Boleh minta minum?",en:"May I have a drink?"},o:{id:["Boleh minta minum?","Berikan sekarang!","Aku ambil sendiri!"],en:["May I have a drink?","Give it to me now!","I’ll just take it!"]}},
{topic:"home",scene:"🚪🙋",type:"situation",q:{id:"Mau masuk kamar orang lain. Apa yang harus dilakukan dulu?",en:"You want to enter someone else’s room. What should you do first?"},a:{id:"Minta izin",en:"Ask permission"},o:{id:["Minta izin","Langsung masuk","Berteriak"],en:["Ask permission","Enter directly","Shout"]}},
{topic:"home",scene:"🧸🧹",type:"action",q:{id:"Setelah bermain, apa yang sebaiknya dilakukan?",en:"After playing, what should you do?"},a:{id:"Merapikan mainan",en:"Tidy up the toys"},o:{id:["Merapikan mainan","Meninggalkan mainan","Melempar mainan"],en:["Tidy up the toys","Leave the toys","Throw the toys"]}},
{topic:"home",scene:"🗣️👂",type:"phrase",q:{id:"Orang tua sedang berbicara. Sikap yang baik adalah...",en:"A parent is talking. A good thing to do is..."},a:{id:"Mendengarkan",en:"Listen"},o:{id:["Mendengarkan","Memotong pembicaraan","Berteriak"],en:["Listen","Interrupt","Shout"]}},
{topic:"home",scene:"🧺🤝",type:"choice",q:{id:"Keluarga sedang membersihkan rumah. Kamu bisa...",en:"Your family is cleaning the house. You can..."},a:{id:"Membantu",en:"Help"},o:{id:["Membantu","Mengganggu","Bermain sendiri"],en:["Help","Bother them","Play by yourself"]}},
{topic:"home",scene:"📺⏰",type:"situation",q:{id:"Sudah waktunya mematikan TV. Apa yang sebaiknya kamu lakukan?",en:"It is time to turn off the TV. What should you do?"},a:{id:"Mematikan TV",en:"Turn off the TV"},o:{id:["Mematikan TV","Berteriak","Menyalakan lebih keras"],en:["Turn off the TV","Shout","Turn it louder"]}},
{topic:"home",scene:"🍪🙋",type:"action",q:{id:"Kamu ingin mengambil makanan. Apa yang sebaiknya kamu lakukan?",en:"You want to take some food. What should you do?"},a:{id:"Meminta izin",en:"Ask permission"},o:{id:["Meminta izin","Mengambil tanpa bertanya","Merebut"],en:["Ask permission","Take it without asking","Grab it"]}},
{topic:"home",scene:"😔👨‍👩‍👧",type:"phrase",q:{id:"Kamu membuat kesalahan di rumah. Apa yang sebaiknya kamu katakan?",en:"You make a mistake at home. What should you say?"},a:{id:"Maaf",en:"Sorry"},o:{id:["Maaf","Bukan salahku!","Diam saja"],en:["Sorry","It’s not my fault!","Say nothing"]}},
{topic:"home",scene:"🧹🏠",type:"choice",q:{id:"Melihat lantai kotor. Apa yang bisa kamu lakukan?",en:"You see a dirty floor. What can you do?"},a:{id:"Membantu membersihkan",en:"Help clean it"},o:{id:["Membantu membersihkan","Membiarkannya","Mengotori lagi"],en:["Help clean it","Leave it","Make it dirtier"]}},
{topic:"home",scene:"😴🌙",type:"situation",q:{id:"Waktunya tidur. Apa yang sebaiknya kamu lakukan?",en:"It is bedtime. What should you do?"},a:{id:"Bersiap tidur",en:"Get ready for bed"},o:{id:["Bersiap tidur","Bermain terus","Berteriak"],en:["Get ready for bed","Keep playing","Shout"]}},
{topic:"school",scene:"🏫👋",type:"action",q:{id:"Bertemu guru di pagi hari. Apa yang kamu lakukan?",en:"You meet your teacher in the morning. What do you do?"},a:{id:"Menyapa guru",en:"Greet the teacher"},o:{id:["Menyapa guru","Berjalan pergi","Berteriak"],en:["Greet the teacher","Walk away","Shout"]}},
{topic:"school",scene:"📚❓",type:"phrase",q:{id:"Tidak mengerti tugas. Apa pilihan yang tepat?",en:"You do not understand the task. What is the right choice?"},a:{id:"Bertanya dengan sopan",en:"Ask politely"},o:{id:["Bertanya dengan sopan","Marah","Meninggalkan kelas"],en:["Ask politely","Get angry","Leave the class"]}},
{topic:"school",scene:"✏️🤝",type:"choice",q:{id:"Teman lupa membawa pensil. Apa yang bisa kamu lakukan?",en:"A friend forgot a pencil. What can you do?"},a:{id:"Meminjamkan pensil",en:"Lend a pencil"},o:{id:["Meminjamkan pensil","Menertawakan","Menyembunyikan pensil"],en:["Lend a pencil","Laugh","Hide the pencil"]}},
{topic:"school",scene:"🧑‍🤝‍🧑⏳",type:"situation",q:{id:"Teman sedang mendapat giliran. Apa yang kamu lakukan?",en:"Your friend is having a turn. What do you do?"},a:{id:"Menunggu giliran",en:"Wait your turn"},o:{id:["Menunggu giliran","Merebut","Mendorong"],en:["Wait your turn","Take it","Push"]}},
{topic:"school",scene:"👩‍🏫📖",type:"action",q:{id:"Guru sedang menjelaskan. Sikap yang tepat adalah...",en:"The teacher is explaining. The right thing to do is..."},a:{id:"Mendengarkan",en:"Listen"},o:{id:["Mendengarkan","Mengobrol","Berteriak"],en:["Listen","Chat","Shout"]}},
{topic:"school",scene:"🗑️🏫",type:"phrase",q:{id:"Melihat sampah di kelas. Apa yang sebaiknya dilakukan?",en:"You see trash in the classroom. What should you do?"},a:{id:"Membuangnya ke tempat sampah",en:"Put it in the trash"},o:{id:["Membuangnya ke tempat sampah","Melempar ke lantai","Menendangnya"],en:["Put it in the trash","Throw it on the floor","Kick it"]}},
{topic:"school",scene:"👋🚪",type:"choice",q:{id:"Waktu pulang sekolah. Apa yang baik dilakukan?",en:"It is time to go home. What is a good thing to do?"},a:{id:"Berpamitan",en:"Say goodbye"},o:{id:["Berpamitan","Pergi tanpa bicara","Berteriak"],en:["Say goodbye","Leave without speaking","Shout"]}},
{topic:"school",scene:"🙋‍♂️📖",type:"situation",q:{id:"Ingin bertanya di kelas. Apa yang kamu lakukan?",en:"You want to ask a question in class. What do you do?"},a:{id:"Angkat tangan",en:"Raise your hand"},o:{id:["Angkat tangan","Berteriak dari tempat duduk","Memotong pembicaraan"],en:["Raise your hand","Shout from your seat","Interrupt"]}},
{topic:"school",scene:"🚶‍♀️🚪",type:"action",q:{id:"Kamu terlambat masuk kelas. Apa yang sebaiknya dikatakan?",en:"You are late to class. What should you say?"},a:{id:"Maaf",en:"Sorry"},o:{id:["Maaf","Minggir!","Tidak perlu bicara"],en:["Sorry","Move!","No need to speak"]}},
{topic:"school",scene:"🎒🪑",type:"phrase",q:{id:"Selesai belajar, apa yang sebaiknya dilakukan?",en:"After studying, what should you do?"},a:{id:"Merapikan alat belajar",en:"Put your school things away"},o:{id:["Merapikan alat belajar","Melempar buku","Meninggalkan barang"],en:["Put your school things away","Throw books","Leave things behind"]}},
{topic:"school",scene:"🤫📖",type:"choice",q:{id:"Teman sedang membaca. Apa yang sebaiknya kamu lakukan?",en:"A friend is reading. What should you do?"},a:{id:"Menjaga suara tetap pelan",en:"Keep your voice low"},o:{id:["Menjaga suara tetap pelan","Berteriak","Mengganggu"],en:["Keep your voice low","Shout","Bother them"]}},
{topic:"school",scene:"🪑👫",type:"situation",q:{id:"Kursi teman menghalangi jalan. Apa yang bisa kamu katakan?",en:"A friend’s chair blocks the way. What can you say?"},a:{id:"Permisi",en:"Excuse me"},o:{id:["Permisi","Minggir!","Aku lewat!"],en:["Excuse me","Move!","I’m coming through!"]}},
{topic:"play",scene:"🛝⏳",type:"action",q:{id:"Teman sedang bermain di perosotan. Apa yang kamu lakukan?",en:"A friend is playing on the slide. What do you do?"},a:{id:"Menunggu giliran",en:"Wait your turn"},o:{id:["Menunggu giliran","Merebut","Mendorong"],en:["Wait your turn","Take it","Push"]}},
{topic:"play",scene:"⚽🤝",type:"phrase",q:{id:"Bola teman jatuh. Apa yang bisa kamu lakukan?",en:"Your friend’s ball falls. What can you do?"},a:{id:"Mengambilkan bola",en:"Pick up the ball"},o:{id:["Mengambilkan bola","Menendang jauh","Menertawakan"],en:["Pick up the ball","Kick it away","Laugh"]}},
{topic:"play",scene:"🎲👫",type:"choice",q:{id:"Teman mengajak bermain. Apa yang bisa kamu katakan?",en:"A friend asks you to play. What can you say?"},a:{id:"Ayo bermain bersama!",en:"Let’s play together!"},o:{id:["Ayo bermain bersama!","Pergi sana!","Aku tidak mau bicara"],en:["Let’s play together!","Go away!","I don’t want to talk"]}},
{topic:"play",scene:"🧸🙋",type:"situation",q:{id:"Ingin memakai mainan teman. Apa yang kamu katakan?",en:"You want to use a friend’s toy. What do you say?"},a:{id:"Boleh aku pinjam?",en:"May I borrow it?"},o:{id:["Boleh aku pinjam?","Berikan!","Aku ambil ya!"],en:["May I borrow it?","Give it to me!","I’ll take it!"]}},
{topic:"play",scene:"🎮⏱️",type:"action",q:{id:"Teman sedang memakai permainan. Apa yang kamu lakukan?",en:"Your friend is using the game. What do you do?"},a:{id:"Menunggu giliran",en:"Wait your turn"},o:{id:["Menunggu giliran","Merebut","Mematikan permainan"],en:["Wait your turn","Take it","Turn it off"]}},
{topic:"play",scene:"🏆😊",type:"phrase",q:{id:"Teman menang. Apa yang sebaiknya kamu katakan?",en:"Your friend wins. What should you say?"},a:{id:"Selamat!",en:"Congratulations!"},o:{id:["Selamat!","Kamu curang!","Aku marah!"],en:["Congratulations!","You cheated!","I’m angry!"]}},
{topic:"play",scene:"😌🎯",type:"choice",q:{id:"Kamu kalah dalam permainan. Apa yang sebaiknya dilakukan?",en:"You lose a game. What should you do?"},a:{id:"Menerima dengan tenang",en:"Accept it calmly"},o:{id:["Menerima dengan tenang","Marah","Melempar barang"],en:["Accept it calmly","Get angry","Throw things"]}},
{topic:"play",scene:"🧩🤝",type:"situation",q:{id:"Teman kesulitan bermain. Apa yang bisa kamu lakukan?",en:"A friend is having trouble playing. What can you do?"},a:{id:"Membantu",en:"Help"},o:{id:["Membantu","Menertawakan","Meninggalkan"],en:["Help","Laugh","Leave"]}},
{topic:"play",scene:"🎨👫",type:"action",q:{id:"Teman sedang menggambar. Apa yang sebaiknya kamu lakukan?",en:"A friend is drawing. What should you do?"},a:{id:"Memberi ruang",en:"Give them space"},o:{id:["Memberi ruang","Mengambil gambarnya","Mengganggu"],en:["Give them space","Take their drawing","Bother them"]}},
{topic:"play",scene:"🧸🔄",type:"phrase",q:{id:"Sudah selesai memakai mainan. Apa yang sebaiknya dilakukan?",en:"You are done using a toy. What should you do?"},a:{id:"Mengembalikan mainan",en:"Put the toy back"},o:{id:["Mengembalikan mainan","Menyembunyikan","Melempar"],en:["Put the toy back","Hide it","Throw it"]}},
{topic:"play",scene:"👫💬",type:"choice",q:{id:"Teman mengusulkan permainan yang berbeda. Apa yang sebaiknya dilakukan?",en:"A friend suggests a different game. What should you do?"},a:{id:"Mendengarkan dan berdiskusi",en:"Listen and discuss"},o:{id:["Mendengarkan dan berdiskusi","Memaksa pilihanmu","Marah"],en:["Listen and discuss","Force your choice","Get angry"]}},
{topic:"friends",scene:"🤝😊",type:"situation",q:{id:"Teman membantumu. Apa yang kamu katakan?",en:"A friend helps you. What do you say?"},a:{id:"Terima kasih",en:"Thank you"},o:{id:["Terima kasih","Pergi sana","Diam saja"],en:["Thank you","Go away","Say nothing"]}},
{topic:"friends",scene:"📚🤝",type:"action",q:{id:"Teman membawa banyak buku. Apa yang bisa kamu lakukan?",en:"A friend carries many books. What can you do?"},a:{id:"Membantu",en:"Help"},o:{id:["Membantu","Menertawakan","Pergi saja"],en:["Help","Laugh","Walk away"]}},
{topic:"friends",scene:"👂💬",type:"phrase",q:{id:"Teman sedang berbicara. Apa yang kamu lakukan?",en:"A friend is talking. What do you do?"},a:{id:"Mendengarkan",en:"Listen"},o:{id:["Mendengarkan","Memotong pembicaraan","Berteriak"],en:["Listen","Interrupt","Shout"]}},
{topic:"friends",scene:"😟👫",type:"choice",q:{id:"Teman terlihat sedih. Apa yang bisa kamu lakukan?",en:"A friend looks sad. What can you do?"},a:{id:"Menanyakan kabarnya",en:"Ask how they are"},o:{id:["Menanyakan kabarnya","Menertawakan","Mengabaikan"],en:["Ask how they are","Laugh","Ignore"]}},
{topic:"friends",scene:"🎒🤝",type:"situation",q:{id:"Teman menjatuhkan tas. Apa yang kamu lakukan?",en:"A friend drops their bag. What do you do?"},a:{id:"Membantu mengambil",en:"Help pick it up"},o:{id:["Membantu mengambil","Menendang tas","Menertawakan"],en:["Help pick it up","Kick the bag","Laugh"]}},
{topic:"friends",scene:"💬❤️",type:"action",q:{id:"Teman punya pendapat berbeda. Apa yang sebaiknya kamu lakukan?",en:"A friend has a different opinion. What should you do?"},a:{id:"Menghargai pendapat",en:"Respect the opinion"},o:{id:["Menghargai pendapat","Memaksa","Marah"],en:["Respect the opinion","Force them","Get angry"]}},
{topic:"friends",scene:"🙋‍♂️👫",type:"phrase",q:{id:"Ingin bergabung bermain dengan teman. Apa yang kamu katakan?",en:"You want to join your friends. What do you say?"},a:{id:"Boleh ikut bermain?",en:"May I join?"},o:{id:["Boleh ikut bermain?","Aku ikut saja!","Minggir!"],en:["May I join?","I’m joining!","Move!"]}},
{topic:"friends",scene:"❤️😊",type:"choice",q:{id:"Teman melakukan kesalahan. Apa yang sebaiknya kamu lakukan?",en:"A friend makes a mistake. What should you do?"},a:{id:"Menyemangati",en:"Encourage them"},o:{id:["Menyemangati","Menertawakan","Memarahi"],en:["Encourage them","Laugh","Scold them"]}},
{topic:"friends",scene:"🙌👋",type:"situation",q:{id:"Teman datang. Apa yang bisa kamu katakan?",en:"A friend arrives. What can you say?"},a:{id:"Halo!",en:"Hello!"},o:{id:["Halo!","Jangan datang!","Pergi!"],en:["Hello!","Don’t come!","Go away!"]}},
{topic:"friends",scene:"🗣️🤫",type:"action",q:{id:"Teman sedang berbicara dengan orang lain. Apa yang sebaiknya dilakukan?",en:"A friend is talking to someone else. What should you do?"},a:{id:"Menunggu sampai selesai",en:"Wait until they finish"},o:{id:["Menunggu sampai selesai","Memotong pembicaraan","Berteriak"],en:["Wait until they finish","Interrupt","Shout"]}},
{topic:"friends",scene:"🍎🤲",type:"phrase",q:{id:"Teman menawarkan makanan. Jika kamu mau, apa yang kamu katakan?",en:"A friend offers you food. If you want it, what do you say?"},a:{id:"Terima kasih",en:"Thank you"},o:{id:["Terima kasih","Berikan!","Aku ambil!"],en:["Thank you","Give it!","I’ll take it!"]}},
{topic:"friends",scene:"🧑‍🤝‍🧑🌟",type:"choice",q:{id:"Teman berhasil melakukan sesuatu. Apa yang bisa kamu katakan?",en:"A friend succeeds at something. What can you say?"},a:{id:"Bagus!",en:"Great job!"},o:{id:["Bagus!","Kamu tidak bisa!","Aku tidak peduli"],en:["Great job!","You can’t do it!","I don’t care"]}},
{topic:"friends",scene:"😕💬",type:"situation",q:{id:"Kamu tidak setuju dengan teman. Apa yang sebaiknya kamu lakukan?",en:"You disagree with a friend. What should you do?"},a:{id:"Berbicara dengan sopan",en:"Speak politely"},o:{id:["Berbicara dengan sopan","Berteriak","Memaksa"],en:["Speak politely","Shout","Force them"]}}
];

let socialScore=0;
let socialLives=5;
let socialQuestionNumber=0;
let socialGameFinished=false;
let currentSocialQuestion="";
let selectedSocialTopic="all";
let socialQuestionOrder=[];

function setupSocialTopics(){
 document.querySelectorAll('.social-place[data-topic]').forEach(card=>{
  card.onclick=()=>{
   document.querySelectorAll('.social-place[data-topic]').forEach(c=>c.classList.remove('active'));
   card.classList.add('active');
   selectedSocialTopic=card.dataset.topic;
   const name=card.querySelector('[data-i18n]').textContent;
    speak(name,true);
  };
 });
}


function startSocialGame(){
 if(!selectedSocialTopic) selectedSocialTopic="all";
 socialScore=0; socialLives=5; socialQuestionNumber=0; socialGameFinished=false;
 let pool=selectedSocialTopic==='all'?socialQuestions:socialQuestions.filter(x=>x.topic===selectedSocialTopic);
 if(!pool.length) pool=socialQuestions;
 socialQuestionOrder=shuffle([...pool]);
 document.getElementById('socialScore').textContent=0;
 document.getElementById('socialTarget').textContent=50;
 document.getElementById('socialLives').textContent=5;
 showScreen('socialGame'); nextSocialQuestion();
}

function nextSocialQuestion(){
 if(socialGameFinished || socialLives<=0)return;
 if(socialQuestionNumber>=5){finishSocialGame();return;}
 let pool=selectedSocialTopic==='all'?socialQuestions:socialQuestions.filter(x=>x.topic===selectedSocialTopic);
 if(!pool.length) pool=socialQuestions;
 const data=socialQuestionOrder[socialQuestionNumber];
 if(!data){ finishSocialGame(); return; }
 socialQuestionNumber++;
 const q=data.q[lang], answer=data.a[lang], optionsList=data.o[lang];
 currentSocialQuestion=q;
 document.getElementById('socialQuestion').textContent=q;
 document.getElementById('socialFeedback').textContent='';
 document.getElementById('socialFeedback').className='feedback';
 const area=document.getElementById('socialGameArea');
 area.innerHTML=''; area.classList.remove('slide-in'); void area.offsetWidth; area.classList.add('slide-in');
 const card=document.createElement('div'); card.className='social-mini-card social-type-'+(data.type||'action');
 const progress=document.createElement('div'); progress.className='social-progress';
 progress.textContent=(lang==='id'?'Soal ':'Question ')+socialQuestionNumber+' / 5';
 card.appendChild(progress);
 const scene=document.createElement('div'); scene.className='social-mini-scene social-scene-topic-'+data.topic; scene.textContent=data.scene; scene.setAttribute('aria-hidden','true'); card.appendChild(scene);
 const title=document.createElement('div'); title.className='social-mini-question';
 const prompts={action:{id:'👉 Apa yang sebaiknya dilakukan?',en:'👉 What should you do?'},phrase:{id:'💬 Pilih ucapan yang tepat',en:'💬 Choose the right phrase'},choice:{id:'🧠 Mana jawaban yang tepat?',en:'🧠 Which answer is right?'},situation:{id:'⭐ Pilih tindakan yang baik',en:'⭐ Choose the kind action'}};
 title.textContent=(prompts[data.type]||prompts.action)[lang]; card.appendChild(title);
 const options=document.createElement('div'); options.className='social-mini-options';
 shuffle(optionsList).forEach(option=>{
  const btn=document.createElement('button'); btn.className='social-mini-option'; btn.textContent=option;
  btn.onclick=()=>{
   if(btn.dataset.used || socialGameFinished)return;
    speak(option,true);
   if(option===answer){
    btn.dataset.used='1'; btn.classList.add('correct'); socialScore+=10;
    document.getElementById('socialScore').textContent=socialScore;
    socialFeedback('🎉 '+(lang==='id'?'Benar!':'Correct!'),true);
    celebrateSmall(); options.querySelectorAll('button').forEach(b=>b.disabled=true);
    setTimeout(nextSocialQuestion,850);
   }else{
    btn.classList.add('wrong'); socialLives--;
    document.getElementById('socialLives').textContent=socialLives;
    const pill=document.getElementById('socialLivesPill'); pill.classList.remove('life-lost'); void pill.offsetWidth; pill.classList.add('life-lost');
    socialFeedback('❌ '+(lang==='id'?'Coba lagi!':'Try again!'),false);
    speak(lang==='id'?'Salah, coba lagi!':'Wrong, try again!');
    if(socialLives<=0){socialGameFinished=true; setTimeout(gameOverSocial,500);} else setTimeout(()=>btn.classList.remove('wrong'),450);
   }
  }; options.appendChild(btn);
 });
 card.appendChild(options); area.appendChild(card); scheduleSpeech(currentSocialQuestion,350);
}

function socialFeedback(text,good){
 const el=document.getElementById("socialFeedback");
 el.textContent=text;
 el.className="feedback "+(good?"good":"bad");
}

function speakSocialQuestion(){
speak(currentSocialQuestion,true);
}

function finishSocialGame(){
 socialGameFinished=true;
 stopSpeech();
 document.getElementById("question").textContent="";
 document.getElementById("gameArea").innerHTML="";
 document.getElementById("feedback").textContent="";
 const area=document.getElementById("socialGameArea");
 area.innerHTML=`
 <div style="text-align:center;padding:25px">
 <div style="font-size:85px">🏆🤝</div>
 <h2 style="margin:15px">${lang==="id"?"Hebat!":"Amazing!"}</h2>
 <p style="font-size:22px">⭐ ${lang==="id"?"Nilai kamu":"Your score"}: <strong>${socialScore}</strong> / 50</p>
 <br>
 <button class="main-btn" onclick="startSocialGame()">🔄 ${lang==="id"?"Main Lagi":"Play Again"}</button>
 <br><br>
 <button class="secondary-btn" onclick="showScreen('social')">⬅️ ${lang==="id"?"Kembali ke Materi":"Back to Material"}</button>
 </div>`;
 document.getElementById("socialQuestion").textContent=lang==="id"?"🎉 Latihan Selesai!":"🎉 Practice Complete!";
}

function gameOverSocial(){
 socialGameFinished=true;
 stopSpeech();
 const area=document.getElementById("socialGameArea");
 area.innerHTML=`
 <div style="text-align:center;padding:25px">
 <div style="font-size:85px">💪🤝</div>
 <h2 style="margin:15px">${lang==="id"?"Coba Lagi!":"Try Again!"}</h2>
 <p style="font-size:21px">❤️ ${lang==="id"?"Nyawa kamu habis":"You ran out of lives"}</p>
 <p style="font-size:22px">⭐ ${lang==="id"?"Nilai":"Score"}: <strong>${socialScore}</strong> / 50</p>
 <br>
 <button class="main-btn" onclick="startSocialGame()">🔄 ${lang==="id"?"Coba Lagi":"Try Again"}</button>
 <br><br>
 <button class="secondary-btn" onclick="showScreen('social')">⬅️ ${lang==="id"?"Kembali ke Materi":"Back to Material"}</button>
 </div>`;
 document.getElementById("socialQuestion").textContent=lang==="id"?"💔 Latihan Berakhir":"💔 Practice Over";
}

/* =========================
   SCORE & LIVES
========================= */
function updateScore(){
const scoreEl=document.getElementById("score");
scoreEl.textContent=score;
scoreEl.parentElement.classList.add("life-warning");
setTimeout(()=>scoreEl.parentElement.classList.remove("life-warning"),400);
}

function loseLife(){
if(lives<=0)return;

lives--;
const lifeEl=document.getElementById("lives");
lifeEl.textContent=lives;

const pill=lifeEl.closest(".lives-pill");
pill.classList.remove("life-lost");
void pill.offsetWidth;
pill.classList.add("life-lost");

if(lives<=0 && !gameFinished){
gameFinished=true;
setTimeout(gameOver,500);
}
}

function gameOver(){
if(lives>0)return;
gameFinished=true;
stopSpeech();
stopMusic();

document.getElementById("question").textContent=
lang==="id"?"💔 Permainan Berakhir":"💔 Game Over";

document.getElementById("gameArea").innerHTML=`
<div class="game-over-box">
    <div style="font-size:80px">💔${characters[selectedCharacter]}</div>
    <h2 style="margin:15px">
        ${lang==="id"?"Nyawamu sudah habis!":"You ran out of lives!"}
    </h2>
    <p style="font-size:21px">
        ⭐ ${lang==="id"?"Skor kamu":"Your score"}:
        <strong>${score}</strong> / ${TARGET_SCORE}
    </p>
    <br>
    <button class="main-btn" onclick="startGame(selectedLevel)">
        🔄 ${lang==="id"?"Coba Lagi":"Try Again"}
    </button>
    <br><br>
    <button class="secondary-btn" onclick="showScreen('levels')">
        ⬅️ ${lang==="id"?"Pilih Level":"Choose Level"}
    </button>
</div>
`;
renderAnimatedScene();
}


/* =========================
   UI LANGUAGE
========================= */
const translations={
 id:{
  appName:"Mari Belajar", tagline:"Belajar sambil bermain! 🌈", start:"Mulai Bermain", academicGame:"Game Akademik", socialGame:"Game Sosial", academicLevel:"Game Akademik • Pilih Level", choosePlace:"Pilih Tempat", settings:"Pengaturan", language:"Bahasa", music:"Musik", orientation:"Orientasi", auto:"Otomatis", portrait:"Potret", landscape:"Lanskap", back:"Kembali",
  socialTitle:"Game Sosial", socialMenu:"Game Sosial", socialChoose:"📍 Pilih tempat", socialStartNote:"", homeTopic:"Rumah", schoolTopic:"Sekolah", playTopic:"Bermain", friendTopic:"Teman", socialPractice:"🎮 Latihan", material:"Materi", socialPracticeTitle:"Latihan Interaksi", readQuestion:"Bacakan Soal", chooseFriend:"Pilih Teman Belajarmu!", chooseLevel:"Pilih Level", exit:"Keluar",
  smartEnergetic:"Pintar & Enerjik", creative:"Kreatif", calmStable:"Sabar & Stabil", braveFocused:"Berani & Fokus", carefulConsistent:"Teliti & Konsisten", writingPractice:"Latihan Menulis",
    level1Desc:"Pemula<br>Mulai dengan santai.", level2Desc:"Mudah<br>Mulai tambah tantangan.", level3Desc:"Menengah<br>Lebih banyak pilihan.", level4Desc:"Sulit<br>Latihan lebih panjang.", level5Desc:"Ahli<br>Tantangan paling seru!",
  greet:"Menyapa", help:"Meminta Tolong", thanks:"Berterima Kasih", permission:"Meminta Izin", turn:"Menunggu Giliran", helpFriend:"Membantu Teman", listen:"Mendengarkan", polite:"Berbicara Sopan", respect:"Menghargai"
 },
 en:{
  appName:"Let's Learn", tagline:"Learn while playing! 🌈", start:"Start Playing", academicGame:"Academic Game", socialGame:"Social Game", academicLevel:"Academic Game • Choose Level", choosePlace:"Choose Place", settings:"Settings", language:"Language", music:"Music", orientation:"Orientation", auto:"Auto", portrait:"Portrait", landscape:"Landscape", back:"Back",
  socialTitle:"Social Game", socialMenu:"Social Game", socialChoose:"📍 Choose a place", socialStartNote:"", homeTopic:"Home", schoolTopic:"School", playTopic:"Play", friendTopic:"Friends", socialPractice:"🎮 Practice", material:"Material", socialPracticeTitle:"Social Practice", readQuestion:"Read Question", chooseFriend:"Choose Your Learning Friend!", chooseLevel:"Choose Level", exit:"Exit",
  smartEnergetic:"Smart & Energetic", creative:"Creative", calmStable:"Calm & Steady", braveFocused:"Brave & Focused", carefulConsistent:"Careful & Consistent", writingPractice:"Writing Practice",
    level1Desc:"Beginner<br>Start at an easy pace.", level2Desc:"Easy<br>A little more challenge.", level3Desc:"Medium<br>More choices to explore.", level4Desc:"Hard<br>Longer challenges.", level5Desc:"Expert<br>The biggest challenge!",
  greet:"Say Hello", help:"Ask for Help", thanks:"Say Thank You", permission:"Ask Permission", turn:"Take Turns", helpFriend:"Help a Friend", listen:"Listen", polite:"Speak Politely", respect:"Show Respect"
 }
};

function applyTranslations(){
 const t=translations[lang]||translations.id;
 document.querySelectorAll('[data-i18n]').forEach(el=>{
   const key=el.dataset.i18n;
   if(t[key]!==undefined) el.innerHTML=t[key];
 });
 document.title=t.appName;
}

/* =========================
   DATA LANGUAGE
========================= */

let lang=localStorage.getItem("mariBelajarLang")||"id";

function langData(){

return lang==="id"?words:englishWords;

}

function changeLanguage(){
 lang=document.getElementById("language").value;
 localStorage.setItem("mariBelajarLang",lang);
 applyTranslations();
 // Refresh the current question in the selected language without resetting score/lives.
 const active=document.querySelector(".screen.active")?.id;
 if(active==="game"){
   questionNumber=Math.max(0,questionNumber-1);
   nextQuestion();
 }else if(active==="socialGame"){
   socialQuestionNumber=Math.max(0,socialQuestionNumber-1);
   nextSocialQuestion();
 }
}

/* =========================
   FEEDBACK
========================= */

function feedback(text){

document.getElementById("feedback").textContent=text;

}

/* =========================
   SPEECH
========================= */

function stopSpeech(){
clearTimeout(scheduledSpeechTimer);
scheduledSpeechTimer=null;
speechQueue=[];
speechGeneration++;
activeSpeech=null;
if("speechSynthesis" in window) speechSynthesis.cancel();
}

function playNextSpeech(){
if(activeSpeech || !speechQueue.length || !("speechSynthesis" in window))return;
const utter=speechQueue.shift();
const generation=speechGeneration;
activeSpeech=utter;
const finish=()=>{
if(generation!==speechGeneration || activeSpeech!==utter)return;
activeSpeech=null;
playNextSpeech();
};
utter.onend=finish;
utter.onerror=finish;
speechSynthesis.speak(utter);
}

function speak(text,interrupt=false){
if(!("speechSynthesis" in window) || !String(text||"").trim())return;
if(interrupt){
clearTimeout(scheduledSpeechTimer);
scheduledSpeechTimer=null;
speechQueue=[];
speechGeneration++;
activeSpeech=null;
speechSynthesis.cancel();
}
const utter=new SpeechSynthesisUtterance(String(text));
const targetLanguage=lang==="id"?"id-ID":"en-US";
const languageCode=targetLanguage.slice(0,2).toLowerCase();
const voices=speechSynthesis.getVoices();
utter.lang=targetLanguage;
utter.voice=voices.find(voice=>voice.lang.toLowerCase()===targetLanguage.toLowerCase()&&voice.localService)
    ||voices.find(voice=>voice.lang.toLowerCase()===targetLanguage.toLowerCase())
    ||voices.find(voice=>voice.lang.toLowerCase().startsWith(languageCode));
utter.rate=.9;
utter.pitch=1.05;
utter.volume=1;
speechQueue.push(utter);
playNextSpeech();
}

function scheduleSpeech(text,delay=350){
clearTimeout(scheduledSpeechTimer);
scheduledSpeechTimer=setTimeout(()=>{
scheduledSpeechTimer=null;
speak(text);
},delay);
}

function speakCurrentQuestion(){
speak(currentQuestionText,true);
}

/* =========================
   MUSIC
   Original WebAudio melody
========================= */

function startMusic(){

if(audioContext)return;

audioContext=
new(window.AudioContext||window.webkitAudioContext)();

const notes=[
261.63,
293.66,
329.63,
392,
329.63,
293.66,
261.63,
392,
440,
392,
329.63,
293.66
];

let i=0;

function playNote(){

if(!audioContext)return;

const osc=audioContext.createOscillator();
const gain=audioContext.createGain();

osc.type="sine";
osc.frequency.value=notes[i%notes.length];

gain.gain.value=.045*musicVolume;

osc.connect(gain);
gain.connect(audioContext.destination);

osc.start();

gain.gain.exponentialRampToValueAtTime(
.001,
audioContext.currentTime+.45
);

osc.stop(audioContext.currentTime+.45);

i++;

musicTimer=setTimeout(playNote,500);

}

playNote();

}

function stopMusic(){

if(musicTimer){
clearTimeout(musicTimer);
musicTimer=null;
}

if(audioContext){

audioContext.close();
audioContext=null;

}

}

/* =========================
   VOLUME
========================= */

document.getElementById("volume").addEventListener("input",function(){

musicVolume=this.value/100;
document.getElementById("volumeText").textContent=
this.value+"%";

});

/* =========================
   ORIENTATION
========================= */

async function changeOrientation(value){

if(!screen.orientation)return;

try{

if(value==="portrait"){
await screen.orientation.lock("portrait");
}

else if(value==="landscape"){
await screen.orientation.lock("landscape");
}

else{
await screen.orientation.unlock();
}

}catch(e){

console.log("Orientation lock tidak didukung.");

}

}

/* =========================
   CONFETTI
========================= */

function celebrateSmall(){

const icons=["🎉","⭐","✨","🌟","🎈","🎊","💫"];

for(let i=0;i<25;i++){

const c=document.createElement("div");

c.className="confetti";

c.textContent=
icons[Math.floor(Math.random()*icons.length)];

c.style.left=Math.random()*100+"vw";
c.style.animationDelay=Math.random()*.4+"s";

document.body.appendChild(c);

setTimeout(()=>{
c.remove();
},2500);

}

}


/* =========================
   ANIMATED GAME SCENE
========================= */
function renderAnimatedScene(){
const scene=document.getElementById("animatedScene");
if(!scene)return;

const scenes={
lumi:{char:"🐰",cls:"scene-lumi",items:["🥕","🌼","⭐"]},
nara:{char:"🐿️",cls:"scene-nara",items:["🌰","🍂","⭐"]},
bimo:{char:"🐻",cls:"scene-bimo",items:["🍯","🌳","⭐"]},
sky:{char:"🦅",cls:"scene-sky",items:["☁️","🪶","⭐"]},
luna:{char:"🐱",cls:"scene-luna",items:["🌿","🌸","⭐"]},
pippo:{char:"🐧",cls:"scene-pippo",items:["✏️","📖","⭐"]}
};

const s=scenes[selectedCharacter]||scenes.lumi;

scene.innerHTML=`
<div class="scene-cloud c1">☁️</div>
<div class="scene-cloud c2">☁️</div>
<div class="scene-item i1">${s.items[0]}</div>
<div class="scene-item i2">${s.items[1]}</div>
<div class="scene-item i3">${s.items[2]}</div>
<div class="scene-character ${s.cls}">${s.char}</div>
`;
}


/* =========================
   FINISH
========================= */

function finishGame(){
// Menyelesaikan satu level membuka level berikutnya.
saveMaxUnlockedLevel(Math.min(5, selectedLevel + 1));
stopSpeech();
stopMusic();

document.getElementById("question").textContent=
lang==="id"
?"🏆 Permainan Selesai!"
:"🏆 Game Complete!";

document.getElementById("gameArea").innerHTML=`

<div style="font-size:90px">🎉🏆🎉</div>

<h2 style="margin:15px">
${lang==="id"?"Hebat! Kamu sudah menyelesaikan permainan!":"Amazing! You completed the game!"}
</h2>

<p style="font-size:22px">
⭐ ${lang==="id"?"Skor kamu":"Your score"}:
<strong>${score}</strong> / ${TARGET_SCORE}
</p>

<br>

<button class="main-btn" onclick="startGame(selectedLevel)">
🔄 ${lang==="id"?"Main Lagi":"Play Again"}
</button>

<br><br>

<button class="secondary-btn" onclick="showScreen('levels')">
⬅️ ${lang==="id"?"Pilih Level":"Choose Level"}
</button>

`;

celebrateSmall();

}

// Apply saved language and initialize social topics when the page opens.
window.addEventListener("DOMContentLoaded",()=>{
 const sel=document.getElementById("language");
 if(sel){sel.value=lang;}
 setupSocialTopics();
 applyTranslations();
});

</script>

</body>
</html>
