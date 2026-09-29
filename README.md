# enma
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>NEXUS // Academic OS</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Orbitron:wght@500;600;700;800;900&display=swap');

:root{
    --red:#ff1738;
    --red2:#ff3150;
    --dark:#030305;
    --panel:#0b0b10;
    --panel2:#101016;
    --line:#24242d;
    --text:#f5f5f7;
    --muted:#858592;
    --green:#31f59b;
    --yellow:#ffd23f;
    --blue:#54a8ff;
}

*{box-sizing:border-box;margin:0;padding:0}

html{scroll-behavior:smooth}

body{
    background:
    radial-gradient(circle at 80% 0%,rgba(255,20,55,.15),transparent 28%),
    radial-gradient(circle at 0% 100%,rgba(255,20,55,.09),transparent 30%),
    #030305;
    color:var(--text);
    font-family:Inter,sans-serif;
    min-height:100vh;
    overflow-x:hidden;
}

/* futuristic background */

body:before{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:-2;
    background-image:
        linear-gradient(rgba(255,255,255,.025) 1px,transparent 1px),
        linear-gradient(90deg,rgba(255,255,255,.025) 1px,transparent 1px);
    background-size:45px 45px;
    mask-image:linear-gradient(to bottom,#000,transparent);
}

body:after{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;
    z-index:-1;
    background:radial-gradient(circle,transparent 30%,rgba(0,0,0,.7));
}

button,input,textarea,select{font-family:inherit}

/* =========================
INTRO
========================= */

#intro{
    position:fixed;
    inset:0;
    background:#020203;
    display:flex;
    align-items:center;
    justify-content:center;
    z-index:9999;
    transition:.7s;
}

#intro.hide{
    opacity:0;
    pointer-events:none;
}

.intro-box{
    width:min(570px,92%);
    padding:55px 42px;
    text-align:center;
    background:rgba(9,9,13,.95);
    border:1px solid rgba(255,23,56,.35);
    box-shadow:0 0 100px rgba(255,20,55,.1);
    position:relative;
}

.intro-box:before{
    content:"";
    position:absolute;
    top:0;
    left:0;
    right:0;
    height:2px;
    background:linear-gradient(90deg,transparent,var(--red),transparent);
}

.logo{
    font-family:Orbitron;
    font-size:clamp(32px,7vw,55px);
    font-weight:900;
    letter-spacing:7px;
}

.logo span{color:var(--red)}

.intro-tag{
    margin-top:13px;
    color:var(--muted);
    font-size:11px;
    letter-spacing:3px;
}

.boot{
    margin-top:35px;
    text-align:left;
    color:#6d6d78;
    font-family:monospace;
    font-size:11px;
    line-height:2;
}

.boot span{color:var(--green)}

.name-input{
    width:100%;
    margin-top:20px;
    padding:17px;
    background:#050507;
    border:1px solid var(--line);
    outline:none;
    color:white;
    font-size:15px;
}

.name-input:focus{
    border-color:var(--red);
    box-shadow:0 0 25px rgba(255,23,56,.15);
}

.launch{
    width:100%;
    margin-top:12px;
    padding:16px;
    border:0;
    background:var(--red);
    color:white;
    font-weight:800;
    letter-spacing:2px;
    cursor:pointer;
    transition:.25s;
}

.launch:hover{
    transform:translateY(-2px);
    box-shadow:0 0 35px rgba(255,23,56,.4);
}

/* =========================
APP
========================= */

#app{display:none}

#app.active{display:block}

/* =========================
NAV
========================= */

.nav{
    position:sticky;
    top:0;
    z-index:500;
    height:72px;
    padding:0 28px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    background:rgba(4,4,7,.85);
    backdrop-filter:blur(18px);
    border-bottom:1px solid var(--line);
}

.nav-logo{
    font-family:Orbitron;
    font-weight:800;
    letter-spacing:4px;
}

.nav-logo span{color:var(--red)}

.nav-right{
    display:flex;
    align-items:center;
    gap:18px;
}

.clock{
    font-family:Orbitron;
    font-size:11px;
    color:var(--muted);
}

.avatar{
    width:36px;
    height:36px;
    display:flex;
    align-items:center;
    justify-content:center;
    background:var(--red);
    font-weight:900;
    box-shadow:0 0 20px rgba(255,23,56,.35);
}

/* =========================
LAYOUT
========================= */

.layout{
    display:flex;
    max-width:1600px;
    margin:auto;
}

/* sidebar */

.sidebar{
    width:250px;
    min-height:calc(100vh - 72px);
    border-right:1px solid var(--line);
    padding:25px 16px;
    position:sticky;
    top:72px;
    height:calc(100vh - 72px);
}

.side-label{
    color:#555560;
    font-size:9px;
    letter-spacing:2px;
    margin:10px 12px;
}

.side-btn{
    width:100%;
    border:1px solid transparent;
    background:transparent;
    color:#858590;
    padding:12px;
    text-align:left;
    cursor:pointer;
    margin-bottom:5px;
    transition:.2s;
    font-size:12px;
}

.side-btn:hover{
    background:#101014;
    color:white;
}

.side-btn.active{
    background:rgba(255,23,56,.1);
    color:white;
    border-color:rgba(255,23,56,.25);
}

.side-btn.active:before{
    content:"";
    display:inline-block;
    width:3px;
    height:13px;
    background:var(--red);
    margin-right:9px;
    vertical-align:-2px;
}

.course-mini{
    margin-top:25px;
    padding-top:20px;
    border-top:1px solid var(--line);
}

.course-mini button{
    width:100%;
    padding:10px;
    background:transparent;
    border:0;
    color:#777782;
    text-align:left;
    cursor:pointer;
    font-size:11px;
}

.course-mini button:hover{color:white}

/* main */

.main{
    flex:1;
    padding:38px;
    min-width:0;
}

.view{display:none}

.view.active{
    display:block;
    animation:viewIn .35s ease;
}

@keyframes viewIn{
    from{opacity:0;transform:translateY(8px)}
    to{opacity:1;transform:translateY(0)}
}

/* =========================
HEADERS
========================= */

.page-head{
    display:flex;
    justify-content:space-between;
    align-items:flex-end;
    gap:20px;
    margin-bottom:30px;
}

.page-head h1{
    font-family:Orbitron;
    font-size:clamp(26px,4vw,44px);
}

.page-head h1 span{color:var(--red)}

.page-head p{
    color:var(--muted);
    margin-top:8px;
    font-size:12px;
}

.status{
    border:1px solid rgba(49,245,155,.2);
    color:var(--green);
    padding:9px 12px;
    font-family:monospace;
    font-size:10px;
    white-space:nowrap;
}

/* =========================
CARDS
========================= */

.grid{
    display:grid;
    gap:15px;
}

.stats{
    grid-template-columns:repeat(4,1fr);
    margin-bottom:25px;
}

.card{
    background:linear-gradient(145deg,#101015,#08080b);
    border:1px solid var(--line);
}

.stat-card{
    padding:20px;
    position:relative;
    overflow:hidden;
}

.stat-card:after{
    content:"";
    position:absolute;
    width:100px;
    height:100px;
    right:-40px;
    bottom:-50px;
    border-radius:50%;
    background:var(--red);
    opacity:.06;
    filter:blur(10px);
}

.stat-name{
    color:var(--muted);
    font-size:10px;
    letter-spacing:1px;
}

.stat-num{
    font-family:Orbitron;
    font-size:30px;
    margin-top:9px;
}

.stat-num.red{color:var(--red)}
.stat-num.green{color:var(--green)}

/* =========================
DASHBOARD
========================= */

.dashboard-grid{
    display:grid;
    grid-template-columns:1.5fr 1fr;
    gap:15px;
}

.panel{
    padding:23px;
    background:linear-gradient(145deg,#101015,#08080b);
    border:1px solid var(--line);
}

.panel-title{
    display:flex;
    justify-content:space-between;
    margin-bottom:20px;
    font-family:Orbitron;
    font-size:13px;
}

.panel-title small{
    color:#555560;
    font-family:Inter;
    font-size:9px;
}

/* progress */

.progress-item{
    margin-bottom:20px;
}

.progress-head{
    display:flex;
    justify-content:space-between;
    font-size:11px;
    margin-bottom:7px;
}

.progress-head span:last-child{color:var(--muted)}

.progress{
    height:6px;
    background:#18181e;
    overflow:hidden;
}

.progress-bar{
    height:100%;
    background:linear-gradient(90deg,var(--red),#ff6379);
    box-shadow:0 0 12px rgba(255,23,56,.5);
}

/* =========================
MISSIONS
========================= */

.mission{
    padding:14px;
    background:#08080b;
    border:1px solid #1b1b21;
    margin-bottom:9px;
}

.mission:hover{border-color:#383842}

.mission-name{
    font-weight:700;
    font-size:12px;
}

.mission-meta{
    display:flex;
    justify-content:space-between;
    margin-top:8px;
    font-size:9px;
    color:var(--muted);
}

.mission-time{color:var(--red)}

/* =========================
COURSES
========================= */

.course-grid{
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
}

.course-card{
    padding:24px;
    cursor:pointer;
    position:relative;
    overflow:hidden;
    transition:.25s;
}

.course-card:hover{
    transform:translateY(-4px);
    border-color:rgba(255,23,56,.4);
    box-shadow:0 15px 40px rgba(0,0,0,.3);
}

.course-icon{font-size:30px}

.course-card h3{
    margin-top:18px;
    font-size:15px;
}

.course-code{
    margin-top:5px;
    color:var(--muted);
    font-size:9px;
    letter-spacing:1px;
}

.course-progress{
    margin-top:20px;
}

/* =========================
COURSE PAGE
========================= */

.course-tabs{
    display:flex;
    gap:8px;
    overflow-x:auto;
    margin-bottom:22px;
}

.course-tab{
    padding:11px 14px;
    background:#08080b;
    border:1px solid var(--line);
    color:#777782;
    cursor:pointer;
    white-space:nowrap;
    font-size:10px;
}

.course-tab.active{
    background:var(--red);
    color:white;
    border-color:var(--red);
}

.course-tools{
    display:flex;
    justify-content:space-between;
    gap:10px;
    margin-bottom:18px;
}

.search{
    flex:1;
    max-width:450px;
    padding:12px;
    background:#08080b;
    color:white;
    border:1px solid var(--line);
    outline:none;
}

.search:focus{border-color:var(--red)}

.primary{
    background:var(--red);
    border:0;
    color:white;
    padding:12px 17px;
    font-weight:800;
    cursor:pointer;
}

/* assignments */

.assignment-grid{
    grid-template-columns:repeat(auto-fill,minmax(300px,1fr));
}

.assignment{
    padding:20px;
    position:relative;
    overflow:hidden;
}

.assignment:before{
    content:"";
    position:absolute;
    left:0;
    top:0;
    bottom:0;
    width:3px;
    background:var(--red);
}

.assignment.completed:before{background:var(--green)}

.assignment.overdue:before{background:#ff375f}

.assignment-top{
    display:flex;
    justify-content:space-between;
    gap:10px;
}

.assignment h3{
    font-size:15px;
    line-height:1.4;
}

.badge{
    padding:4px 7px;
    border:1px solid;
    height:max-content;
    font-size:8px;
}

.badge.high{color:var(--red);border-color:rgba(255,23,56,.35)}
.badge.medium{color:var(--yellow);border-color:rgba(255,210,63,.35)}
.badge.low{color:var(--green);border-color:rgba(49,245,155,.35)}

.description{
    color:var(--muted);
    font-size:11px;
    line-height:1.6;
    margin:13px 0 16px;
}

.due-box{
    padding:12px;
    background:#070709;
    border:1px solid #18181e;
}

.due-label{
    color:#555560;
    font-size:8px;
    letter-spacing:1px;
}

.due-date{
    font-family:Orbitron;
    font-size:10px;
    margin-top:5px;
}

.countdown{
    color:var(--red);
    font-family:Orbitron;
    font-size:10px;
    margin-top:11px;
}

.completed .countdown{color:var(--green)}

.actions{
    display:flex;
    gap:7px;
    margin-top:14px;
}

.action{
    flex:1;
    padding:9px;
    border:1px solid var(--line);
    background:transparent;
    color:#888892;
    cursor:pointer;
    font-size:9px;
}

.action:hover{
    color:white;
    border-color:#44444e;
}

.action.complete:hover{
    color:var(--green);
    border-color:var(--green);
}

.action.delete:hover{
    color:var(--red);
    border-color:var(--red);
}

/* =========================
CALENDAR
========================= */

.calendar-head{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:18px;
}

.calendar-head button{
    background:#0b0b0f;
    color:white;
    border:1px solid var(--line);
    padding:9px 13px;
    cursor:pointer;
}

.calendar-title{
    font-family:Orbitron;
    font-size:16px;
}

.calendar{
    display:grid;
    grid-template-columns:repeat(7,1fr);
    border-left:1px solid var(--line);
    border-top:1px solid var(--line);
}

.day-name{
    padding:12px;
    color:#656570;
    font-size:9px;
    border-right:1px solid var(--line);
    border-bottom:1px solid var(--line);
    text-align:center;
}

.day{
    min-height:120px;
    padding:8px;
    border-right:1px solid var(--line);
    border-bottom:1px solid var(--line);
    background:#08080b;
}

.day-number{
    color:#777782;
    font-size:9px;
}

.day.today{
    background:rgba(255,23,56,.05);
}

.day.today .day-number{
    color:var(--red);
}

.calendar-event{
    margin-top:7px;
    padding:6px;
    background:rgba(255,23,56,.12);
    border-left:2px solid var(--red);
    font-size:8px;
    cursor:pointer;
}

/* =========================
WEEK
========================= */

.week-grid{
    display:grid;
    grid-template-columns:repeat(7,1fr);
    gap:8px;
}

.week-day{
    min-height:350px;
    padding:12px;
    background:#08080b;
    border:1px solid var(--line);
}

.week-day h3{
    font-size:10px;
    font-family:Orbitron;
}

.week-day small{
    color:#555560;
}

.week-event{
    margin-top:12px;
    padding:10px;
    border:1px solid #25252d;
    background:#101015;
}

.week-event strong{
    font-size:9px;
}

.week-event p{
    color:var(--red);
    font-size:8px;
    margin-top:5px;
}

/* =========================
ACHIEVEMENTS
========================= */

.achievement-grid{
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
}

.achievement{
    padding:22px;
    text-align:center;
    opacity:.35;
}

.achievement.unlocked{
    opacity:1;
    border-color:rgba(255,23,56,.3);
    box-shadow:0 0 30px rgba(255,23,56,.06);
}

.achievement-icon{font-size:34px}

.achievement h3{
    font-size:12px;
    margin-top:13px;
}

.achievement p{
    color:var(--muted);
    font-size:9px;
    margin-top:7px;
}

/* =========================
PROFILE
========================= */

.profile-panel{
    max-width:700px;
}

.level{
    font-family:Orbitron;
    color:var(--red);
    font-size:24px;
}

.xp-bar{
    height:8px;
    background:#17171d;
    margin-top:12px;
}

.xp-fill{
    height:100%;
    background:linear-gradient(90deg,var(--red),#ff6a7e);
}

/* =========================
MODAL
========================= */

.modal{
    position:fixed;
    inset:0;
    z-index:1000;
    display:none;
    align-items:center;
    justify-content:center;
    background:rgba(0,0,0,.78);
    backdrop-filter:blur(12px);
}

.modal.show{display:flex}

.modal-box{
    width:min(560px,92%);
    padding:28px;
    background:#0a0a0d;
    border:1px solid rgba(255,23,56,.4);
    box-shadow:0 30px 100px #000;
}

.modal-head{
    display:flex;
    justify-content:space-between;
    margin-bottom:23px;
}

.modal-head h2{
    font-family:Orbitron;
    font-size:16px;
}

.close{
    background:none;
    border:0;
    color:#777;
    font-size:20px;
    cursor:pointer;
}

.form-group{margin-bottom:14px}

.form-group label{
    display:block;
    color:#777782;
    font-size:9px;
    letter-spacing:1px;
    margin-bottom:6px;
}

.form-group input,
.form-group textarea,
.form-group select{
    width:100%;
    background:#050507;
    border:1px solid var(--line);
    color:white;
    padding:12px;
    outline:none;
}

.form-group textarea{
    min-height:80px;
    resize:vertical;
}

.form-group input:focus,
.form-group textarea:focus,
.form-group select:focus{
    border-color:var(--red);
}

.form-row{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:10px;
}

.save{
    width:100%;
    padding:14px;
    border:0;
    background:var(--red);
    color:white;
    font-weight:800;
    cursor:pointer;
}

/* =========================
TOAST
========================= */

#toast{
    position:fixed;
    right:25px;
    bottom:25px;
    padding:14px 18px;
    background:#0c0c10;
    border:1px solid rgba(255,23,56,.4);
    box-shadow:0 10px 40px #000;
    transform:translateY(100px);
    opacity:0;
    transition:.3s;
    z-index:2000;
    font-size:11px;
}

#toast.show{
    transform:translateY(0);
    opacity:1;
}

/* =========================
RESPONSIVE
========================= */

@media(max-width:1000px){

    .sidebar{
        display:none;
    }

    .main{
        padding:25px 18px;
    }

    .stats{
        grid-template-columns:repeat(2,1fr);
    }

    .dashboard-grid{
        grid-template-columns:1fr;
    }

    .week-grid{
        grid-template-columns:1fr;
    }

    .week-day{
        min-height:auto;
    }

}

@media(max-width:650px){

    .nav{
        padding:0 15px;
    }

    .clock{
        display:none;
    }

    .page-head{
        display:block;
    }

    .status{
        display:inline-block;
        margin-top:15px;
    }

    .stats{
        grid-template-columns:1fr 1fr;
    }

    .course-tools{
        flex-direction:column;
    }

    .search{
        max-width:none;
    }

    .form-row{
        grid-template-columns:1fr;
    }

    .calendar{
        min-width:700px;
    }

    .calendar-wrap{
        overflow-x:auto;
    }

}
</style>
</head>

<body>

<!-- ==========================================
INTRO
========================================== -->

<section id="intro">

    <div class="intro-box">

        <div class="logo">
            NEXUS<span>//</span>OS
        </div>

        <div class="intro-tag">
            PERSONAL ACADEMIC COMMAND CENTER
        </div>

        <div class="boot">
            <div>> INITIALIZING ACADEMIC CORE... <span>OK</span></div>
            <div>> LOADING COURSE DATABASE... <span>OK</span></div>
            <div>> DEADLINE ENGINE... <span>ONLINE</span></div>
            <div>> MISSION CONTROL... <span>ONLINE</span></div>
        </div>

        <input
            id="nameInput"
            class="name-input"
            placeholder="ENTER YOUR NAME"
            maxlength="30"
        >

        <button class="launch" onclick="launch()">
            INITIALIZE NEXUS →
        </button>

    </div>

</section>


<!-- ==========================================
APP
========================================== -->

<div id="app">

<nav class="nav">

    <div class="nav-logo">
        NEXUS<span>//</span>OS
    </div>

    <div class="nav-right">

        <div class="clock" id="clock">
            00:00:00
        </div>

        <div class="avatar" id="avatar">
            ?
        </div>

    </div>

</nav>


<div class="layout">

<!-- ==========================================
SIDEBAR
========================================== -->

<aside class="sidebar">

    <div class="side-label">
        COMMAND
    </div>

    <button class="side-btn active" onclick="showView('dashboard',this)">
        ◈ Dashboard
    </button>

    <button class="side-btn" onclick="showView('courses',this)">
        ▣ Courses
    </button>

    <button class="side-btn" onclick="showView('missions',this)">
        ⚡ All Missions
    </button>

    <button class="side-btn" onclick="showView('calendar',this)">
        ◫ Calendar
    </button>

    <button class="side-btn" onclick="showView('week',this)">
        ◷ Weekly View
    </button>

    <button class="side-btn" onclick="showView('achievements',this)">
        🏆 Achievements
    </button>

    <button class="side-btn" onclick="showView('profile',this)">
        ◎ Profile
    </button>

    <div class="course-mini">

        <div class="side-label">
            COURSES
        </div>

        <button onclick="openCourse('technical')">
            ✏️ Technical Drawing
        </button>

        <button onclick="openCourse('ia')">
            🧠 Information Architecture
        </button>

        <button onclick="openCourse('interactive')">
            ⚡ Interactive Systems
        </button>

        <button onclick="openCourse('visualization')">
            🎨 2D Visualization
        </button>

        <button onclick="openCourse('visual')">
            👁️ Visual Design
        </button>

    </div>

</aside>


<!-- ==========================================
MAIN
========================================== -->

<main class="main">


<!-- DASHBOARD -->

<section id="dashboard" class="view active">

    <div class="page-head">

        <div>
            <h1>
                SYSTEM <span>ONLINE</span>
            </h1>

            <p>
                Welcome back, <b id="dashName">Student</b>.
                Your academic command center is ready.
            </p>
        </div>

        <div class="status">
            ● ALL SYSTEMS OPERATIONAL
        </div>

    </div>


    <div class="grid stats">

        <div class="card stat-card">
            <div class="stat-name">TOTAL MISSIONS</div>
            <div class="stat-num" id="statTotal">0</div>
        </div>

        <div class="card stat-card">
            <div class="stat-name">DUE SOON</div>
            <div class="stat-num red" id="statSoon">0</div>
        </div>

        <div class="card stat-card">
            <div class="stat-name">COMPLETED</div>
            <div class="stat-num green" id="statCompleted">0</div>
        </div>

        <div class="card stat-card">
            <div class="stat-name">OVERDUE</div>
            <div class="stat-num red" id="statOverdue">0</div>
        </div>

    </div>


    <div class="dashboard-grid">

        <div class="panel">

            <div class="panel-title">
                COURSE PROGRESS
                <small>LIVE DATA</small>
            </div>

            <div id="courseProgress"></div>

        </div>


        <div class="panel">

            <div class="panel-title">
                NEXT MISSIONS
                <small>48 HOURS</small>
            </div>

            <div id="nextMissions"></div>

        </div>

    </div>

</section>


<!-- COURSES -->

<section id="courses" class="view">

    <div class="page-head">

        <div>
            <h1>
                COURSE <span>NETWORK</span>
            </h1>

            <p>
                Select an academic sector.
            </p>
        </div>

    </div>

    <div class="grid course-grid" id="courseGrid"></div>

</section>


<!-- ALL MISSIONS -->

<section id="missions" class="view">

    <div class="page-head">

        <div>
            <h1>
                ALL <span>MISSIONS</span>
            </h1>

            <p>
                Every assignment across every course.
            </p>

        </div>

        <button class="primary" onclick="openModal()">
            + NEW MISSION
        </button>

    </div>

    <div class="course-tools">

        <input
            class="search"
            id="globalSearch"
            placeholder="⌕ Search assignments..."
            oninput="renderAllMissions()"
        >

    </div>

    <div class="grid assignment-grid" id="allMissionGrid"></div>

</section>


<!-- COURSE ASSIGNMENTS -->

<section id="courseView" class="view">

    <div class="page-head">

        <div>
            <h1 id="coursePageTitle">
                COURSE
            </h1>

            <p id="coursePageSub">
                Assignment database.
            </p>
        </div>

        <button class="primary" onclick="openModal()">
            + NEW MISSION
        </button>

    </div>

    <div class="course-tabs" id="courseTabs"></div>

    <div class="course-tools">

        <input
            class="search"
            id="courseSearch"
            placeholder="⌕ Search this course..."
            oninput="renderCourseAssignments()"
        >

    </div>

    <div
        class="grid assignment-grid"
        id="courseAssignmentGrid"
    ></div>

</section>


<!-- CALENDAR -->

<section id="calendar" class="view">

    <div class="page-head">

        <div>
            <h1>
                DEADLINE <span>CALENDAR</span>
            </h1>

            <p>
                Visualize your academic timeline.
            </p>

        </div>

    </div>

    <div class="panel">

        <div class="calendar-head">

            <button onclick="changeMonth(-1)">
                ←
            </button>

            <div class="calendar-title" id="calendarTitle"></div>

            <button onclick="changeMonth(1)">
                →
            </button>

        </div>

        <div class="calendar-wrap">

            <div class="calendar" id="calendarGrid"></div>

        </div>

    </div>

</section>


<!-- WEEK -->

<section id="week" class="view">

    <div class="page-head">

        <div>
            <h1>
                WEEKLY <span>MISSION MAP</span>
            </h1>

            <p>
                Your next seven days.
            </p>

        </div>

    </div>

    <div class="week-grid" id="weekGrid"></div>

</section>


<!-- ACHIEVEMENTS -->

<section id="achievements" class="view">

    <div class="page-head">

        <div>
            <h1>
                ACHIEVEMENT <span>CORE</span>
            </h1>

            <p>
                Complete missions and unlock system achievements.
            </p>

        </div>

    </div>

    <div class="grid achievement-grid" id="achievementGrid"></div>

</section>


<!-- PROFILE -->

<section id="profile" class="view">

    <div class="page-head">

        <div>
            <h1>
                USER <span>PROFILE</span>
            </h1>

            <p>
                Your NEXUS identity and academic statistics.
            </p>

        </div>

    </div>

    <div class="panel profile-panel">

        <div class="level" id="profileLevel">
            LEVEL 01
        </div>

        <p style="margin-top:8px;color:#888;font-size:12px">
            <span id="profileFullName">Student</span>
        </p>

        <div style="margin-top:25px;color:#777;font-size:9px">
            EXPERIENCE PROGRESS
        </div>

        <div class="xp-bar">
            <div class="xp-fill" id="xpFill"></div>
        </div>

        <div style="margin-top:9px;color:#777;font-size:9px" id="xpText">
            0 XP
        </div>

        <div style="margin-top:30px">

            <button class="primary" onclick="exportData()">
                ↓ EXPORT DATA
            </button>

            <button
                class="action"
                onclick="resetSystem()"
                style="margin-left:7px"
            >
                RESET SYSTEM
            </button>

        </div>

    </div>

</section>


</main>

</div>

</div>


<!-- ==========================================
MODAL
========================================== -->

<div class="modal" id="modal">

    <div class="modal-box">

        <div class="modal-head">

            <h2>
                NEW ACADEMIC MISSION
            </h2>

            <button class="close" onclick="closeModal()">×</button>

        </div>

        <form onsubmit="saveAssignment(event)">

            <div class="form-group">

                <label>Course</label>

                <select id="assignmentCourse"></select>

            </div>


            <div class="form-group">

                <label>Assignment Name</label>

                <input
                    id="assignmentName"
                    required
                    placeholder="e.g. Visual Territories & Prompt Craft"
                >

            </div>


            <div class="form-group">

                <label>Description</label>

                <textarea
                    id="assignmentDescription"
                    placeholder="What do you need to complete?"
                ></textarea>

            </div>


            <div class="form-row">

                <div class="form-group">

                    <label>Due Date</label>

                    <input
                        type="date"
                        id="assignmentDate"
                        required
                    >

                </div>

                <div class="form-group">

                    <label>Due Time</label>

                    <input
                        type="time"
                        id="assignmentTime"
                        required
                    >

                </div>

            </div>


            <div class="form-group">

                <label>Priority</label>

                <select id="assignmentPriority">

                    <option value="high">
                        🔴 HIGH
                    </option>

                    <option value="medium">
                        🟡 MEDIUM
                    </option>

                    <option value="low">
                        🟢 LOW
                    </option>

                </select>

            </div>


            <button class="save">
                + DEPLOY MISSION
            </button>

        </form>

    </div>

</div>


<div id="toast"></div>


<script>

/* =========================================================
NEXUS // CORE DATABASE
========================================================= */

const courses = [

    {
        id:"technical",
        name:"Technical Drawing",
        emoji:"✏️",
        code:"TD"
    },

    {
        id:"ia",
        name:"Information Architecture",
        emoji:"🧠",
        code:"IA"
    },

    {
        id:"interactive",
        name:"Interactive Systems",
        emoji:"⚡",
        code:"IS"
    },

    {
        id:"visualization",
        name:"2D Visualization",
        emoji:"🎨",
        code:"2DV"
    },

    {
        id:"visual",
        name:"Visual Design",
        emoji:"👁️",
        code:"VD"
    }

];


let assignments =
    JSON.parse(
        localStorage.getItem("NEXUS_ASSIGNMENTS")
    ) || [];

let user =
    localStorage.getItem("NEXUS_USER") || "";

let currentCourse =
    localStorage.getItem("NEXUS_COURSE") ||
    "technical";

let calendarDate =
    new Date();


/* =========================================================
START
========================================================= */

window.addEventListener("DOMContentLoaded",()=>{

    if(user){

        document
        .getElementById("intro")
        .classList.add("hide");

        document
        .getElementById("app")
        .classList.add("active");

        updateIdentity();

    }

    buildCourseSelect();
    buildCourseCards();
    buildCourseTabs();

    refresh();

    setInterval(refreshClock,1000);

    refreshClock();

});


/* =========================================================
LAUNCH
========================================================= */

function launch(){

    const input =
        document.getElementById("nameInput");

    const name =
        input.value.trim();

    if(!name){

        input.focus();

        toast("ENTER YOUR NAME FIRST");

        return;

    }

    user=name;

    localStorage.setItem(
        "NEXUS_USER",
        user
    );

    document
    .getElementById("intro")
    .classList.add("hide");

    document
    .getElementById("app")
    .classList.add("active");

    updateIdentity();

    toast("NEXUS INITIALIZED ⚡");

}


/* =========================================================
IDENTITY
========================================================= */

function updateIdentity(){

    document
    .getElementById("dashName")
    .textContent=user;

    document
    .getElementById("profileFullName")
    .textContent=user;

    document
    .getElementById("avatar")
    .textContent=
        user.charAt(0).toUpperCase();

}


/* =========================================================
CLOCK
========================================================= */

function refreshClock(){

    const now=new Date();

    document
    .getElementById("clock")
    .textContent=
        now.toLocaleTimeString(
            [],
            {
                hour:"2-digit",
                minute:"2-digit",
                second:"2-digit"
            }
        );

}


/* =========================================================
NAVIGATION
========================================================= */

function showView(id,button){

    document
    .querySelectorAll(".view")
    .forEach(v=>v.classList.remove("active"));

    document
    .getElementById(id)
    .classList.add("active");

    document
    .querySelectorAll(".side-btn")
    .forEach(b=>b.classList.remove("active"));

    if(button)
        button.classList.add("active");

    if(id==="dashboard")
        renderDashboard();

    if(id==="courses")
        buildCourseCards();

    if(id==="missions")
        renderAllMissions();

    if(id==="calendar")
        renderCalendar();

    if(id==="week")
        renderWeek();

    if(id==="achievements")
        renderAchievements();

    if(id==="profile")
        renderProfile();

}


function openCourse(id){

    currentCourse=id;

    localStorage.setItem(
        "NEXUS_COURSE",
        id
    );

    document
    .querySelectorAll(".view")
    .forEach(v=>v.classList.remove("active"));

    document
    .getElementById("courseView")
    .classList.add("active");

    document
    .querySelectorAll(".side-btn")
    .forEach(b=>b.classList.remove("active"));

    buildCourseTabs();

    renderCourseAssignments();

}


/* =========================================================
REFRESH EVERYTHING
========================================================= */

function refresh(){

    renderDashboard();
    renderCourseAssignments();
    renderAllMissions();
    renderCalendar();
    renderWeek();
    renderAchievements();
    renderProfile();

}


/* =========================================================
COURSE SELECT
========================================================= */

function buildCourseSelect(){

    const select =
        document.getElementById(
            "assignmentCourse"
        );

    select.innerHTML="";

    courses.forEach(c=>{

        const option=
            document.createElement("option");

        option.value=c.id;

        option.textContent=
            `${c.emoji} ${c.name}`;

        select.appendChild(option);

    });

}


/* =========================================================
COURSE CARDS
========================================================= */

function buildCourseCards(){

    const grid=
        document.getElementById("courseGrid");

    grid.innerHTML="";

    courses.forEach(c=>{

        const list=
            assignments.filter(
                a=>a.course===c.id
            );

        const completed=
            list.filter(
                a=>a.completed
            ).length;

        const percent=
            list.length
            ? Math.round(
                completed/list.length*100
            )
            : 0;

        const card=
            document.createElement("div");

        card.className="card course-card";

        card.onclick=
            ()=>openCourse(c.id);

        card.innerHTML=`

            <div class="course-icon">
                ${c.emoji}
            </div>

            <h3>${c.name}</h3>

            <div class="course-code">
                ${c.code} // ${list.length} MISSIONS
            </div>

            <div class="course-progress">

                <div class="progress-head">
                    <span>COMPLETION</span>
                    <span>${percent}%</span>
                </div>

                <div class="progress">
                    <div
                        class="progress-bar"
                        style="width:${percent}%"
                    ></div>
                </div>

            </div>

        `;

        grid.appendChild(card);

    });

}


/* =========================================================
COURSE TABS
========================================================= */

function buildCourseTabs(){

    const tabs=
        document.getElementById(
            "courseTabs"
        );

    tabs.innerHTML="";

    courses.forEach(c=>{

        const button=
            document.createElement("button");

        button.className=
            "course-tab "+
            (
                c.id===currentCourse
                ?"active"
                :""
            );

        button.textContent=
            `${c.emoji} ${c.name}`;

        button.onclick=()=>{

            currentCourse=c.id;

            localStorage.setItem(
                "NEXUS_COURSE",
                c.id
            );

            buildCourseTabs();
            renderCourseAssignments();

        };

        tabs.appendChild(button);

    });

}


/* =========================================================
DASHBOARD
========================================================= */

function renderDashboard(){

    const total=assignments.length;

    const completed=
        assignments.filter(
            a=>a.completed
        ).length;

    const now=new Date();

    const overdue=
        assignments.filter(
            a=>
                !a.completed &&
                new Date(a.due)<now
        ).length;

    const soon=
        assignments.filter(a=>{

            if(a.completed)return false;

            const diff=
                new Date(a.due)-now;

            return diff>0 &&
                diff<=48*60*60*1000;

        }).length;

    document.getElementById("statTotal")
        .textContent=total;

    document.getElementById("statCompleted")
        .textContent=completed;

    document.getElementById("statOverdue")
        .textContent=overdue;

    document.getElementById("statSoon")
        .textContent=soon;


    /* course progress */

    const progress=
        document.getElementById(
            "courseProgress"
        );

    progress.innerHTML="";

    courses.forEach(c=>{

        const list=
            assignments.filter(
                a=>a.course===c.id
            );

        const done=
            list.filter(
                a=>a.completed
            ).length;

        const percent=
            list.length
            ?Math.round(done/list.length*100)
            :0;

        progress.innerHTML+=`

            <div class="progress-item">

                <div class="progress-head">

                    <span>
                        ${c.emoji} ${c.name}
                    </span>

                    <span>
                        ${done}/${list.length}
                    </span>

                </div>

                <div class="progress">
                    <div
                        class="progress-bar"
                        style="width:${percent}%"
                    ></div>
                </div>

            </div>

        `;

    });


    /* next missions */

    const next=
        document.getElementById(
            "nextMissions"
        );

    next.innerHTML="";

    const upcoming=
        assignments
        .filter(
            a=>
                !a.completed &&
                new Date(a.due)>=now
        )
        .sort(
            (a,b)=>
                new Date(a.due)-
                new Date(b.due)
        )
        .slice(0,5);

    if(!upcoming.length){

        next.innerHTML=`

            <div style="
                color:#666;
                font-size:11px;
                padding:15px 0;
            ">
                🎉 NO UPCOMING MISSIONS.
            </div>

        `;

    }else{

        upcoming.forEach(a=>{

            const c=
                courses.find(
                    x=>x.id===a.course
                );

            next.innerHTML+=`

                <div class="mission">

                    <div class="mission-name">
                        ${c.emoji}
                        ${escapeHTML(a.name)}
                    </div>

                    <div class="mission-meta">

                        <span>
                            ${c.name}
                        </span>

                        <span class="mission-time">
                            ${countdown(a)}
                        </span>

                    </div>

                </div>

            `;

        });

    }

}


/* =========================================================
ASSIGNMENT CARD
========================================================= */

function assignmentCard(a){

    const c=
        courses.find(
            x=>x.id===a.course
        );

    const overdue=
        !a.completed &&
        new Date(a.due)<new Date();

    const el=
        document.createElement("div");

    el.className=
        "card assignment "+
        (a.completed?"completed ":"")+
        (overdue?"overdue":"");

    el.innerHTML=`

        <div class="assignment-top">

            <h3>
                ${escapeHTML(a.name)}
            </h3>

            <span class="badge ${a.priority}">
                ${a.priority.toUpperCase()}
            </span>

        </div>

        <div class="description">
            ${
                escapeHTML(
                    a.description||
                    "No mission briefing provided."
                )
            }
        </div>

        <div class="due-box">

            <div class="due-label">
                DEADLINE
            </div>

            <div class="due-date">
                ${formatDate(new Date(a.due))}
            </div>

        </div>

        <div class="countdown">
            ${countdown(a)}
        </div>

        <div class="actions">

            <button
                class="action complete"
                onclick="toggleComplete('${a.id}')"
            >
                ${a.completed?"↩ UNDO":"✓ COMPLETE"}
            </button>

            <button
                class="action delete"
                onclick="deleteAssignment('${a.id}')"
            >
                DELETE
            </button>

        </div>

    `;

    return el;

}


/* =========================================================
COURSE ASSIGNMENTS
========================================================= */

function renderCourseAssignments(){

    const grid=
        document.getElementById(
            "courseAssignmentGrid"
        );

    if(!grid)return;

    const c=
        courses.find(
            x=>x.id===currentCourse
        );

    document.getElementById(
        "coursePageTitle"
    ).innerHTML=
        `${c.emoji} ${c.name}`;

    document.getElementById(
        "coursePageSub"
    ).textContent=
        `${c.code} // Assignment database`;

    const search=
        (
            document.getElementById(
                "courseSearch"
            )?.value||""
        ).toLowerCase();

    const list=
        assignments
        .filter(a=>a.course===currentCourse)
        .filter(
            a=>
                a.name
                .toLowerCase()
                .includes(search)
        )
        .sort(
            (a,b)=>
                new Date(a.due)-
                new Date(b.due)
        );

    grid.innerHTML="";

    if(!list.length){

        grid.innerHTML=
            emptyState(
                "🛰️",
                "NO MISSIONS",
                "This course has no matching assignments."
            );

        return;

    }

    list.forEach(a=>
        grid.appendChild(
            assignmentCard(a)
        )
    );

}


/* =========================================================
ALL MISSIONS
========================================================= */

function renderAllMissions(){

    const grid=
        document.getElementById(
            "allMissionGrid"
        );

    if(!grid)return;

    const search=
        (
            document.getElementById(
                "globalSearch"
            )?.value||""
        ).toLowerCase();

    const list=
        assignments
        .filter(a=>
            a.name
            .toLowerCase()
            .includes(search)
        )
        .sort(
            (a,b)=>
                new Date(a.due)-
                new Date(b.due)
        );

    grid.innerHTML="";

    if(!list.length){

        grid.innerHTML=
            emptyState(
                "📡",
                "NO MISSIONS FOUND",
                "Your search returned no assignments."
            );

        return;

    }

    list.forEach(a=>
        grid.appendChild(
            assignmentCard(a)
        )
    );

}


/* =========================================================
MODAL
========================================================= */

function openModal(){

    document
    .getElementById("modal")
    .classList.add("show");

    document
    .getElementById("assignmentCourse")
    .value=currentCourse;

    document
    .getElementById("assignmentName")
    .focus();

}

function closeModal(){

    document
    .getElementById("modal")
    .classList.remove("show");

}


/* =========================================================
SAVE ASSIGNMENT
========================================================= */

function saveAssignment(e){

    e.preventDefault();

    const assignment={

        id:
            Date.now().toString(),

        course:
            document.getElementById(
                "assignmentCourse"
            ).value,

        name:
            document.getElementById(
                "assignmentName"
            ).value.trim(),

        description:
            document.getElementById(
                "assignmentDescription"
            ).value.trim(),

        due:
            document.getElementById(
                "assignmentDate"
            ).value+
            "T"+
            document.getElementById(
                "assignmentTime"
            ).value,

        priority:
            document.getElementById(
                "assignmentPriority"
            ).value,

        completed:false,

        created:
            new Date().toISOString()

    };

    assignments.push(assignment);

    save();

    closeModal();

    e.target.reset();

    refresh();

    toast("MISSION DEPLOYED 🚀");

}


/* =========================================================
COMPLETE
========================================================= */

function toggleComplete(id){

    const a=
        assignments.find(
            x=>x.id===id
        );

    if(!a)return;

    a.completed=!a.completed;

    save();

    refresh();

    if(a.completed){

        toast("+100 XP // MISSION COMPLETE ⚡");

    }

}


/* =========================================================
DELETE
========================================================= */

function deleteAssignment(id){

    const a=
        assignments.find(
            x=>x.id===id
        );

    if(!a)return;

    if(
        !confirm(
            `Delete "${a.name}"?`
        )
    )return;

    assignments=
        assignments.filter(
            x=>x.id!==id
        );

    save();

    refresh();

    toast("MISSION DELETED");

}


/* =========================================================
SAVE DATABASE
========================================================= */

function save(){

    localStorage.setItem(
        "NEXUS_ASSIGNMENTS",
        JSON.stringify(assignments)
    );

}


/* =========================================================
COUNTDOWN
========================================================= */

function countdown(a){

    if(a.completed)
        return "✓ MISSION COMPLETE";

    let diff=
        new Date(a.due)-new Date();

    if(diff<=0)
        return "⚠ OVERDUE";

    const days=
        Math.floor(
            diff/86400000
        );

    diff%=86400000;

    const hours=
        Math.floor(
            diff/3600000
        );

    diff%=3600000;

    const mins=
        Math.floor(
            diff/60000
        );

    const secs=
        Math.floor(
            (diff%60000)/1000
        );

    if(days)
        return `⏳ ${days}D ${hours}H ${mins}M`;

    return `🔥 ${hours}H ${mins}M ${secs}S`;

}


/* =========================================================
CALENDAR
========================================================= */

function renderCalendar(){

    const grid=
        document.getElementById(
            "calendarGrid"
        );

    if(!grid)return;

    const year=
        calendarDate.getFullYear();

    const month=
        calendarDate.getMonth();

    document.getElementById(
        "calendarTitle"
    ).textContent=
        calendarDate.toLocaleDateString(
            undefined,
            {
                month:"long",
                year:"numeric"
            }
        ).toUpperCase();

    grid.innerHTML="";

    [
        "MON","TUE","WED",
        "THU","FRI","SAT","SUN"
    ].forEach(day=>{

        grid.innerHTML+=
            `<div class="day-name">${day}</div>`;

    });

    const first=
        new Date(year,month,1);

    let start=
        first.getDay();

    start=
        start===0?6:start-1;

    const days=
        new Date(
            year,
            month+1,
            0
        ).getDate();

    for(let i=0;i<start;i++){

        grid.innerHTML+=
            `<div class="day"></div>`;

    }

    for(let d=1;d<=days;d++){

        const date=
            new Date(year,month,d);

        const today=
            date.toDateString()===
            new Date().toDateString();

        const cell=
            document.createElement("div");

        cell.className=
            "day "+
            (today?"today":"");

        cell.innerHTML=
            `<div class="day-number">${d}</div>`;

        assignments
        .filter(a=>{

            const due=
                new Date(a.due);

            return(
                due.getFullYear()===year &&
                due.getMonth()===month &&
                due.getDate()===d
            );

        })
        .forEach(a=>{

            const event=
                document.createElement("div");

            event.className=
                "calendar-event";

            event.textContent=
                a.completed
                ?"✓ "+a.name
                :"⚡ "+a.name;

            cell.appendChild(event);

        });

        grid.appendChild(cell);

    }

}


function changeMonth(direction){

    calendarDate.setMonth(
        calendarDate.getMonth()+
        direction
    );

    renderCalendar();

}


/* =========================================================
WEEK VIEW
========================================================= */

function renderWeek(){

    const grid=
        document.getElementById(
            "weekGrid"
        );

    if(!grid)return;

    grid.innerHTML="";

    const today=
        new Date();

    for(let i=0;i<7;i++){

        const date=
            new Date(today);

        date.setDate(
            today.getDate()+i
        );

        const day=
            document.createElement("div");

        day.className="week-day";

        day.innerHTML=`

            <h3>
                ${date.toLocaleDateString(
                    undefined,
                    {weekday:"long"}
                ).toUpperCase()}
            </h3>

            <small>
                ${date.toLocaleDateString(
                    undefined,
                    {
                        month:"short",
                        day:"numeric"
                    }
                )}
            </small>

        `;

        assignments
        .filter(a=>{

            const due=
                new Date(a.due);

            return(
                due.getFullYear()===
                    date.getFullYear() &&
                due.getMonth()===
                    date.getMonth() &&
                due.getDate()===
                    date.getDate()
            );

        })
        .forEach(a=>{

            const c=
                courses.find(
                    x=>x.id===a.course
                );

            day.innerHTML+=`

                <div class="week-event">

                    <strong>
                        ${c.emoji}
                        ${escapeHTML(a.name)}
                    </strong>

                    <p>
                        ${new Date(a.due)
                            .toLocaleTimeString(
                                [],
                                {
                                    hour:"numeric",
                                    minute:"2-digit"
                                }
                            )}
                    </p>

                </div>

            `;

        });

        grid.appendChild(day);

    }

}


/* =========================================================
ACHIEVEMENTS
========================================================= */

function renderAchievements(){

    const grid=
        document.getElementById(
            "achievementGrid"
        );

    if(!grid)return;

    const completed=
        assignments.filter(
            a=>a.completed
        ).length;

    const total=
        assignments.length;

    const noOverdue=
        assignments.length>0 &&
        assignments.every(
            a=>
                a.completed ||
                new Date(a.due)>=new Date()
        );

    const achievements=[

        {
            icon:"🚀",
            title:"FIRST MISSION",
            text:"Complete your first assignment.",
            unlocked:completed>=1
        },

        {
            icon:"⚡",
            title:"SPEEDRUNNER",
            text:"Complete 3 assignments.",
            unlocked:completed>=3
        },

        {
            icon:"🔥",
            title:"MISSION MACHINE",
            text:"Complete 10 assignments.",
            unlocked:completed>=10
        },

        {
            icon:"🎯",
            title:"PERFECT WEEK",
            text:"Have no overdue missions.",
            unlocked:noOverdue
        },

        {
            icon:"🧠",
            title:"FULL NETWORK",
            text:"Add work to all 5 courses.",
            unlocked:
                courses.every(
                    c=>
                        assignments.some(
                            a=>a.course===c.id
                        )
                )
        },

        {
            icon:"🏆",
            title:"ACADEMIC LEGEND",
            text:"Complete 25 assignments.",
            unlocked:completed>=25
        },

        {
            icon:"💀",
            title:"FINAL BOSS",
            text:"Complete every assignment.",
            unlocked:
                total>0 &&
                completed===total
        },

        {
            icon:"🌌",
            title:"NEXUS MASTER",
            text:"Complete 50 assignments.",
            unlocked:completed>=50
        }

    ];

    grid.innerHTML="";

    achievements.forEach(a=>{

        const card=
            document.createElement("div");

        card.className=
            "card achievement "+
            (a.unlocked?"unlocked":"");

        card.innerHTML=`

            <div class="achievement-icon">
                ${a.icon}
            </div>

            <h3>
                ${a.unlocked?"✓ ":"🔒 "}
                ${a.title}
            </h3>

            <p>
                ${a.text}
            </p>

        `;

        grid.appendChild(card);

    });

}


/* =========================================================
XP / PROFILE
========================================================= */

function renderProfile(){

    const completed=
        assignments.filter(
            a=>a.completed
        ).length;

    const xp=
        completed*100;

    const level=
        Math.floor(xp/500)+1;

    const progress=
        (xp%500)/5;

    document.getElementById(
        "profileLevel"
    ).textContent=
        `LEVEL ${String(level).padStart(2,"0")}`;

    document.getElementById(
        "xpFill"
    ).style.width=
        progress+"%";

    document.getElementById(
        "xpText"
    ).textContent=
        `${xp} XP // ${500-(xp%500)} XP TO NEXT LEVEL`;

}


/* =========================================================
EXPORT
========================================================= */

function exportData(){

    const data={
        user,
        assignments,
        exported:new Date().toISOString()
    };

    const blob=
        new Blob(
            [JSON.stringify(data,null,2)],
            {type:"application/json"}
        );

    const url=
        URL.createObjectURL(blob);

    const link=
        document.createElement("a");

    link.href=url;

    link.download=
        "NEXUS-Academic-Backup.json";

    link.click();

    URL.revokeObjectURL(url);

    toast("DATABASE EXPORTED 💾");

}


/* =========================================================
RESET
========================================================= */

function resetSystem(){

    if(
        !confirm(
            "RESET NEXUS? ALL ASSIGNMENTS WILL BE DELETED."
        )
    )return;

    localStorage.removeItem(
        "NEXUS_ASSIGNMENTS"
    );

    localStorage.removeItem(
        "NEXUS_USER"
    );

    assignments=[];
    user="";

    location.reload();

}


/* =========================================================
EMPTY STATE
========================================================= */

function emptyState(icon,title,text){

    return `

        <div
            class="card"
            style="
                grid-column:1/-1;
                padding:70px;
                text-align:center;
            "
        >

            <div style="
                font-size:40px;
                margin-bottom:15px;
            ">
                ${icon}
            </div>

            <h3>${title}</h3>

            <p style="
                color:#777;
                font-size:11px;
                margin-top:8px;
            ">
                ${text}
            </p>

        </div>

    `;

}


/* =========================================================
TOAST
========================================================= */

let toastTimer;

function toast(message){

    const el=
        document.getElementById("toast");

    el.textContent=message;

    el.classList.add("show");

    clearTimeout(toastTimer);

    toastTimer=
        setTimeout(
            ()=>el.classList.remove("show"),
            2500
        );

}


/* =========================================================
DATE FORMAT
========================================================= */

function formatDate(date){

    return date.toLocaleString(
        undefined,
        {
            month:"short",
            day:"numeric",
            year:"numeric",
            hour:"numeric",
            minute:"2-digit"
        }
    );

}


/* =========================================================
SECURITY
========================================================= */

function escapeHTML(value){

    return String(value)
        .replace(/&/g,"&amp;")
        .replace(/</g,"&lt;")
        .replace(/>/g,"&gt;")
        .replace(/"/g,"&quot;")
        .replace(/'/g,"&#039;");

}


/* =========================================================
MODAL OUTSIDE CLICK
========================================================= */

document
.getElementById("modal")
.addEventListener("click",e=>{

    if(
        e.target===
        document.getElementById("modal")
    ){

        closeModal();

    }

});


/* =========================================================
LIVE REFRESH
========================================================= */

setInterval(()=>{

    renderDashboard();
    renderCourseAssignments();
    renderAllMissions();
    renderProfile();

},1000);

</script>

</body>
</html>
