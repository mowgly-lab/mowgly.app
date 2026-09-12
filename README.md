# mowgly.app
App de apoyo para personas con discapacidad cognitiva: rutinas diarias, juegos de aprendizaje, seguimiento para cuidadores y comunicación familiar.
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mowgly Nueva</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,Helvetica,sans-serif;background:#f5f7fb;color:#20253a}
button,input,select{font:inherit}
button{cursor:pointer;border:0}
.hidden{display:none!important}

/* LOGIN */
#loginScreen{min-height:100vh;display:flex;align-items:center;justify-content:center;padding:24px;background:linear-gradient(135deg,#eef2ff,#f8fbff)}
.login-card{width:min(460px,100%);background:white;border-radius:28px;padding:34px;box-shadow:0 18px 50px #26315a20;text-align:center}
.logo{width:76px;height:76px;border-radius:24px;background:#6c63ff;color:white;display:grid;place-items:center;font-size:38px;margin:0 auto 15px}
.login-card h1{font-size:34px;color:#5148d9}
.login-card p{color:#70758a;margin:8px 0 26px}
.role-title{text-align:left;font-weight:bold;margin-bottom:10px}
.roles{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:18px}
.role{padding:18px;border:2px solid #e5e7f5;border-radius:18px;background:white}
.role.active{border-color:#6c63ff;background:#f1f0ff}
.role strong{display:block;margin-top:7px}
.form-group{text-align:left;margin:12px 0}
.form-group label{display:block;font-size:14px;font-weight:bold;margin-bottom:6px}
.form-group input{width:100%;padding:13px 14px;border:1px solid #dfe2ee;border-radius:12px;outline:none}
.form-group input:focus{border-color:#6c63ff}
.primary{width:100%;padding:14px;border-radius:14px;background:#6c63ff;color:white;font-weight:bold;margin-top:8px}
.secondary{padding:11px 15px;border-radius:12px;background:#eef0ff;color:#5148d9;font-weight:bold}
.demo-note{font-size:12px!important;margin-top:14px!important;color:#999!important}

/* APP */
#app{min-height:100vh}
.header{height:72px;background:white;border-bottom:1px solid #e8eaf2;display:flex;align-items:center;justify-content:space-between;padding:0 28px;position:sticky;top:0;z-index:5}
.brand{font-size:23px;font-weight:800;color:#5148d9}
.user-mini{display:flex;align-items:center;gap:10px}
.avatar{width:40px;height:40px;border-radius:50%;background:#ecebff;display:grid;place-items:center}
.layout{display:flex;min-height:calc(100vh - 72px)}
.sidebar{width:245px;background:#fff;border-right:1px solid #e8eaf2;padding:20px 14px}
.nav-btn{width:100%;text-align:left;padding:13px 15px;margin:4px 0;border-radius:12px;background:transparent;color:#555b70}
.nav-btn:hover,.nav-btn.active{background:#f0efff;color:#5148d9;font-weight:bold}
.content{flex:1;padding:30px;max-width:1250px}
.section{display:none}
.section.active{display:block}
.title-row{display:flex;justify-content:space-between;align-items:center;gap:15px;margin-bottom:22px}
.title-row h2{font-size:28px}
.subtitle{color:#74798c;margin-top:5px}

/* CARDS */
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}
.card{background:white;border-radius:18px;padding:20px;box-shadow:0 5px 18px #2730520b;border:1px solid #eceef5}
.sensor-icon{font-size:28px;margin-bottom:12px}
.card h3{font-size:16px;margin-bottom:8px}
.status{font-weight:bold;color:#2c9a64}
.status.warning{color:#e49b24}
.status.danger{color:#d9534f}
.info-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:18px;margin-top:20px}
.panel{background:white;border-radius:18px;padding:20px;border:1px solid #eceef5}
.panel h3{margin-bottom:13px}
.list-item{display:flex;justify-content:space-between;align-items:center;padding:13px 0;border-bottom:1px solid #eef0f5}
.list-item:last-child{border-bottom:0}
.badge{padding:5px 9px;border-radius:20px;background:#eef0ff;color:#5148d9;font-size:12px;font-weight:bold}

/* ACTIVITIES */
.activity-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.activity{background:white;border-radius:18px;padding:20px;border:1px solid #eceef5}
.activity .emoji{font-size:34px}
.activity h3{margin:12px 0 7px}
.activity p{color:#70758a;font-size:14px;line-height:1.5}
.activity button{margin-top:14px;padding:10px 13px;border-radius:11px;background:#6c63ff;color:white}

/* LINK */
.link-box{background:#f5f3ff;border:1px solid #ddd9ff;border-radius:18px;padding:20px;margin-bottom:20px}
.link-code{font-size:25px;font-weight:bold;letter-spacing:4px;color:#5148d9;margin:10px 0}
.link-row{display:flex;gap:10px}
.link-row input{flex:1;padding:12px;border:1px solid #ddd;border-radius:11px}

/* CAREGIVERS */
.caregiver-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.caregiver{background:white;border:1px solid #e7e9f2;border-radius:20px;padding:20px}
.caregiver-top{display:flex;align-items:center;gap:12px}
.caregiver-avatar{width:55px;height:55px;border-radius:50%;background:#ecebff;display:grid;place-items:center;font-size:25px}
.stars{color:#e7a51e;margin:9px 0}
.score{font-weight:bold}
.caregiver p{color:#70758a;font-size:14px;line-height:1.5;margin:8px 0}
.tags{display:flex;flex-wrap:wrap;gap:6px;margin:12px 0}
.tag{background:#f0f1f7;padding:5px 8px;border-radius:8px;font-size:11px}
.hire{width:100%;padding:11px;border-radius:11px;background:#6c63ff;color:#fff;font-weight:bold}

/* ALERT */
.alert{padding:15px;border-radius:13px;background:#fff6e7;border-left:4px solid #f0a52b;margin:10px 0}
.success{padding:15px;border-radius:13px;background:#eaf9f0;color:#24764c;margin:10px 0}


.learning-hero{background:linear-gradient(135deg,#f0efff,#f8fbff);text-align:center}
.progress-wrap{height:13px;background:#e5e6f1;border-radius:20px;overflow:hidden;margin-top:18px}
.progress-bar{height:100%;width:0;background:#6c63ff;border-radius:20px;transition:.4s}
.mini-game{display:flex;justify-content:center;gap:18px;font-size:34px;padding:12px}
.color-options,.number-options,.quick-options{display:flex;justify-content:center;gap:9px;flex-wrap:wrap;margin:12px 0}
.color-options button,.number-options button,.quick-options button{background:#f0f1f7;padding:10px 14px;border-radius:10px}
.word-box{background:#f5f3ff;border-radius:13px;padding:12px;margin:12px 0;line-height:1.5}
.badges{display:flex;flex-wrap:wrap;gap:7px;margin-top:12px}
.badges span{background:#f0f1f7;padding:8px 10px;border-radius:10px;font-size:12px}
.learning-card{transition:.2s;position:relative}
.learning-card:hover{transform:translateY(-4px);box-shadow:0 12px 25px #27305218}

.game-modal{position:fixed;inset:0;background:#20253a99;display:flex;align-items:center;justify-content:center;padding:18px;z-index:20}
.game-window{background:white;width:min(520px,100%);border-radius:25px;padding:26px;text-align:center;position:relative;box-shadow:0 20px 60px #0003}
.close-game{position:absolute;right:15px;top:12px;background:#f0f1f7;border-radius:50%;width:34px;height:34px}
.memory-board{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin:20px 0}
.memory-card{height:70px;border-radius:14px;background:#ecebff;font-size:30px;display:grid;place-items:center;color:transparent}
.memory-card.revealed,.memory-card.matched{color:initial;background:#f5f3ff}
.game-message{padding:12px;border-radius:12px;background:#f5f3ff;margin-top:12px;font-weight:bold}
.big-emoji{font-size:62px;margin:10px}


.learning-categories{display:grid;grid-template-columns:repeat(6,1fr);gap:10px;margin-bottom:18px}
.learn-category{padding:14px 9px;background:white;border:1px solid #e5e7f0;border-radius:14px;color:#555b70;font-weight:bold}
.learn-category.active,.learn-category:hover{background:#f0efff;color:#5148d9;border-color:#d8d5ff}
.topic-hero{display:flex;align-items:center;gap:16px;background:linear-gradient(135deg,#f0efff,#f8fbff);border-radius:20px;padding:22px;margin-bottom:18px}
.topic-icon{font-size:48px}
.explore-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.explore-card{background:white;border:1px solid #e7e9f2;border-radius:18px;padding:20px;text-align:center;transition:.2s}
.explore-card:hover{transform:translateY(-4px);box-shadow:0 12px 25px #27305218}
.explore-card .big-icon{font-size:52px}
.explore-card h3{margin:10px 0 7px}
.explore-card p{color:#70758a;font-size:14px;line-height:1.5}
.learn-more{margin-top:12px;padding:10px 14px;border-radius:11px;background:#6c63ff;color:white;font-weight:bold}
.fact{background:#f5f3ff;border-radius:12px;padding:10px;margin-top:10px;font-size:13px}
.quiz-panel{margin-top:20px;text-align:center}
.explore-answers{display:flex;justify-content:center;gap:10px;flex-wrap:wrap;margin-top:15px}
.explore-answers button{padding:12px 18px;border-radius:12px;background:#f0f1f7}
.explore-answers button:hover{background:#ecebff;color:#5148d9}

@media(max-width:900px){
.grid{grid-template-columns:repeat(2,1fr)}
.activity-grid,.caregiver-grid{grid-template-columns:1fr 1fr}
.sidebar{width:205px}
}
@media(max-width:650px){
.header{padding:0 15px}.layout{display:block}.sidebar{width:100%;display:flex;overflow:auto;padding:8px}.nav-btn{min-width:max-content;margin:0 3px}.content{padding:18px}.grid,.info-grid,.activity-grid,.caregiver-grid{grid-template-columns:1fr}.roles{grid-template-columns:1fr 1fr}.title-row{align-items:flex-start;flex-direction:column}
}

.routine-list{display:grid;gap:10px;margin-top:16px}.routine-item{display:flex;align-items:center;gap:12px;padding:14px;border:1px solid #e5e8f0;border-radius:14px;background:#fff}.routine-item input{width:20px;height:20px}.routine-item.done span{text-decoration:line-through;opacity:.55}.progress-row{display:flex;justify-content:space-between;margin-bottom:8px}.stats-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin-bottom:18px}.stat-card{background:#fff;border-radius:18px;padding:20px;text-align:center;box-shadow:0 8px 24px rgba(0,0,0,.06)}.stat-card b{display:block;font-size:30px}.stat-card span{display:block;margin-top:6px}.chat-head{display:flex;align-items:center;gap:12px;padding-bottom:14px;border-bottom:1px solid #e5e8f0}.avatar{font-size:32px}.chat-head small{display:block;margin-top:3px;opacity:.7}.chat-messages{min-height:260px;display:flex;flex-direction:column;gap:10px;padding:18px 0}.message{max-width:75%;padding:11px 14px;border-radius:16px}.message.received{background:#eef1f8;align-self:flex-start}.message.sent{background:#6c63ff;color:white;align-self:flex-end}.chat-compose{display:flex;gap:8px}.chat-compose input,.form-row input{flex:1;padding:12px;border:1px solid #dfe3ec;border-radius:12px}.form-row{display:flex;gap:8px;margin-top:12px}.caregiver-card{padding:18px}.rating{font-weight:700}.tag{display:inline-block;padding:5px 9px;background:#f0f2f8;border-radius:10px;margin:4px 4px 0 0;font-size:12px}@media(max-width:700px){.stats-grid{grid-template-columns:1fr}.form-row,.chat-compose{flex-direction:column}}
</style>
</head>
<body>

<!-- LOGIN -->
<div id="loginScreen">
  <div class="login-card">
    <div class="logo">🐾</div>
    <h1>Mowgly</h1>
    <p>Tecnología que cuida, protege e incluye</p>

    <div class="role-title">¿Cómo deseas entrar?</div>
    <div class="roles">
      <button class="role active" id="userRole" onclick="selectRole('usuario')">👦<strong>Usuario</strong><small>Aprender y participar</small></button>
      <button class="role" id="parentRole" onclick="selectRole('padre')">👨‍👩‍👧<strong>Padre/Madre</strong><small>Acompañar y supervisar</small></button>
      <button class="role" id="careRole" onclick="selectRole('cuidador')">👨‍⚕️<strong>Cuidador</strong><small>Apoyo y seguimiento</small></button>
    </div>

    <div class="form-group">
      <label>Correo electrónico</label>
      <input id="email" type="email" placeholder="correo@ejemplo.com">
    </div>
    <div class="form-group">
      <label>Contraseña</label>
      <input id="password" type="password" placeholder="••••••••">
    </div>
    <button class="primary" onclick="login()">Entrar a Mowgly</button>
    <button class="secondary" style="margin-top:10px;width:100%" onclick="register()">Crear cuenta</button>
    <p class="demo-note">Esta versión usa datos de demostración. La conexión real con Supabase se agregará en el siguiente paso.</p>
  </div>
</div>

<!-- APP -->
<div id="app" class="hidden">
<header class="header">
  <div class="brand">🐾 Mowgly</div>
  <div class="user-mini"><span id="roleLabel">Usuario</span><div class="avatar" id="topAvatar">👤</div></div>
</header>

<div class="layout">
<aside class="sidebar" id="sidebar"></aside>

<main class="content">

<!-- INICIO -->
<section id="inicio" class="section active">
  <div class="title-row"><div><h2>Hola, bienvenido a Mowgly 👋</h2><p class="subtitle">Aquí puedes consultar el estado del sistema.</p></div></div>
  <div class="grid">
    <div class="card"><div class="sensor-icon">🚶</div><h3>Movimiento PIR</h3><div class="status">Sin movimiento</div></div>
    <div class="card"><div class="sensor-icon">💧</div><h3>Sensor de agua</h3><div class="status">Normal</div></div>
    <div class="card"><div class="sensor-icon">🚪</div><h3>Reed Switch</h3><div class="status">Cerrado</div></div>
    <div class="card"><div class="sensor-icon">🌡️</div><h3>DHT11</h3><div class="status">-- °C / -- %</div></div>
  </div>
  <div class="info-grid">
    <div class="panel"><h3>🎯 Actividades recientes</h3><div class="list-item"><span>Ejercicios de memoria</span><span class="badge">Completada</span></div><div class="list-item"><span>Reconocimiento de colores</span><span class="badge">Pendiente</span></div></div>
    <div class="panel"><h3>🔔 Estado de seguridad</h3><div class="success">✓ No hay alertas activas en este momento.</div></div>
  </div>
</section>

<!-- SENSORES -->
<section id="sensores" class="section">
  <div class="title-row"><div><h2>📊 Sensores</h2><p class="subtitle">Información recibida desde el prototipo Mowgly.</p></div></div>
  <div class="grid">
    <div class="card"><div class="sensor-icon">🚶</div><h3>PIR</h3><p>Movimiento</p><h2 id="pirValue">Sin movimiento</h2></div>
    <div class="card"><div class="sensor-icon">💧</div><h3>Agua</h3><p>Lectura</p><h2 id="waterValue">Normal</h2></div>
    <div class="card"><div class="sensor-icon">🚪</div><h3>Reed Switch</h3><p>Puerta</p><h2 id="reedValue">Cerrado</h2></div>
    <div class="card"><div class="sensor-icon">🌡️</div><h3>DHT11</h3><p>Temperatura / humedad</p><h2>-- °C / -- %</h2></div>
  </div>
</section>

<!-- ACTIVIDADES -->
<section id="actividadesAntiguo" class="section">
  <div class="title-row"><div><h2>🎯 Actividades</h2><p class="subtitle">Actividades para el usuario y herramientas para el cuidador.</p></div></div>
  <div id="activityIntro" class="panel" style="margin-bottom:18px"></div>
  <div class="activity-grid">
    <div class="activity"><span class="emoji">🧠</span><h3>Memoria</h3><p>Ejercicios sencillos para trabajar atención y memoria.</p><button onclick="completeActivity(this)">Iniciar actividad</button></div>
    <div class="activity"><span class="emoji">🎨</span><h3>Colores</h3><p>Identificación y asociación de colores.</p><button onclick="completeActivity(this)">Iniciar actividad</button></div>
    <div class="activity"><span class="emoji">🔢</span><h3>Números</h3><p>Ejercicios básicos de reconocimiento y conteo.</p><button onclick="completeActivity(this)">Iniciar actividad</button></div>
    <div class="activity"><span class="emoji">🗣️</span><h3>Comunicación</h3><p>Actividades para fortalecer comunicación y expresión.</p><button onclick="completeActivity(this)">Iniciar actividad</button></div>
    <div class="activity"><span class="emoji">🏃</span><h3>Movimiento</h3><p>Rutinas sencillas de movimiento y coordinación.</p><button onclick="completeActivity(this)">Iniciar actividad</button></div>
    <div class="activity"><span class="emoji">📝</span><h3>Registro del cuidador</h3><p>El cuidador podrá registrar observaciones y avances.</p><button onclick="caregiverNote()">Agregar observación</button></div>
  </div>
</section>

<!-- APRENDER -->
<section id="aprender" class="section">
  <div class="title-row">
    <div><h2>🌟 ¡Vamos a aprender!</h2><p class="subtitle">Aprende jugando, completa retos y gana estrellas.</p></div>
    <div class="badge" id="starCounter">⭐ 0 estrellas</div>
  </div>

  <div class="panel learning-hero">
    <div style="font-size:48px">🚀</div>
    <h3 style="font-size:23px;margin:8px 0">Tu misión de hoy</h3>
    <p class="subtitle">Completa 3 retos cortos para desbloquear una nueva insignia.</p>
    <div class="progress-wrap"><div id="learningProgress" class="progress-bar"></div></div>
    <p id="progressText" style="font-weight:bold;margin-top:8px">0 de 3 retos completados</p>
  </div>

  <div class="activity-grid" style="margin-top:18px">
    <div class="activity learning-card">
      <span class="emoji">🧠</span><h3>Reto de memoria</h3>
      <p>Observa 3 elementos y recuerda cuál falta.</p>
      <div class="mini-game" id="memoryGame"></div>
      <button onclick="startMemoryGame()">¡Jugar memoria!</button>
    </div>

    <div class="activity learning-card">
      <span class="emoji">🎨</span><h3>Detective de colores</h3>
      <p>Encuentra el color correcto y gana una estrella.</p>
      <div id="colorGame">
        <strong id="colorTargetText">Pulsa "Comenzar"</strong>
        <div class="color-options">
          <button onclick="chooseColor('rojo')">🔴</button>
          <button onclick="chooseColor('azul')">🔵</button>
          <button onclick="chooseColor('verde')">🟢</button>
        </div>
        <button onclick="startColorGame()" style="margin-top:4px">Comenzar</button>
      </div>
    </div>

    <div class="activity learning-card">
      <span class="emoji">🔢</span><h3>Desafío de números</h3>
      <p>¿Cuál número sigue?</p>
      <h2 id="numberQuestion" style="margin:13px 0">2 → 4 → 6 → ?</h2>
      <div class="number-options" id="numberOptions">
        <button onclick="chooseNumber(this,8)">8</button>
        <button onclick="chooseNumber(this,9)">9</button>
        <button onclick="chooseNumber(this,10)">10</button>
      </div>
      <button onclick="newNumberGame()" style="margin-top:4px;padding:9px 12px;border-radius:10px;background:#eef0ff;color:#5148d9">Nuevo reto</button>
    </div>

    <div class="activity learning-card">
      <span class="emoji">🗣️</span><h3>Palabra del día</h3>
      <p>Aprende una palabra nueva y escucha su significado.</p>
      <div class="word-box"><strong>INCLUSIÓN</strong><br><small>Todos tenemos un lugar y podemos participar.</small></div>
      <button onclick="wordChallenge(this)">✨ Aprender</button>
    </div>

    <div class="activity learning-card">
      <span class="emoji">🌈</span><h3>Pregunta rápida</h3>
      <p>¿Qué debes hacer si necesitas ayuda?</p>
      <div class="quick-options">
        <button onclick="quickAnswer(this,false)">Quedarme callado</button>
        <button onclick="quickAnswer(this,true)">Pedir ayuda</button>
      </div>
    </div>

    <div class="activity learning-card">
      <span class="emoji">🏆</span><h3>Mis logros</h3>
      <p>Cada reto completado te acerca a una nueva insignia.</p>
      <div class="badges"><span>🌱 Inicio</span><span>🧠 Aprendiz</span><span>🏆 Experto</span></div>
    </div>
  </div>
</section>


<!-- EXPLORAR Y APRENDER -->
<section id="explorar" class="section">
  <div class="title-row">
    <div>
      <h2>🌎 Explorar y aprender</h2>
      <p class="subtitle">Descubre animales, ciudades, naturaleza y muchas cosas nuevas.</p>
    </div>
  </div>

  <div class="learning-categories">
    <button class="learn-category active" onclick="openTopic('animales',this)">🐾 Animales</button>
    <button class="learn-category" onclick="openTopic('ciudades',this)">🏙️ Ciudades</button>
    <button class="learn-category" onclick="openTopic('naturaleza',this)">🌿 Naturaleza</button>
    <button class="learn-category" onclick="openTopic('cuerpo',this)">🧍 Mi cuerpo</button>
    <button class="learn-category" onclick="openTopic('espacio',this)">🚀 Espacio</button>
    <button class="learn-category" onclick="openTopic('oficios',this)">👩‍🚒 Oficios</button>
  </div>

  <div class="topic-hero" id="topicHero">
    <div class="topic-icon">🐾</div>
    <div>
      <h3 id="topicTitle">Mundo de los animales</h3>
      <p id="topicDescription">Conoce animales y descubre datos curiosos.</p>
    </div>
  </div>

  <div class="explore-grid" id="exploreCards"></div>

  <div class="panel quiz-panel">
    <h3>🎯 Mini reto</h3>
    <p id="exploreQuestion">¿Cuál de estos animales puede volar?</p>
    <div id="exploreAnswers" class="explore-answers"></div>
    <div id="exploreFeedback" class="game-message hidden"></div>
    <button class="secondary" onclick="newExploreQuiz()" style="margin-top:12px">🔄 Nueva pregunta</button>
  </div>
</section>

<!-- ACTIVIDADES CUIDADOR -->
<section id="actividadesCuidador" class="section">
  <div class="title-row"><div><h2>🎯 Actividades</h2><p class="subtitle">Planifica, registra y consulta actividades de usuarios vinculados.</p></div></div>
  <div class="panel" style="margin-bottom:18px"><strong>🧑‍⚕️ Panel del cuidador:</strong> aquí podrás revisar avances, asignar actividades y escribir observaciones.</div>
  <div class="activity-grid">
    <div class="activity"><span class="emoji">🧠</span><h3>Memoria</h3><p>Actividad para atención y memoria.</p><button onclick="assignActivity('Memoria')">Asignar</button></div>
    <div class="activity"><span class="emoji">🎨</span><h3>Colores</h3><p>Actividad de identificación y asociación.</p><button onclick="assignActivity('Colores')">Asignar</button></div>
    <div class="activity"><span class="emoji">🔢</span><h3>Números</h3><p>Reconocimiento y conteo básico.</p><button onclick="assignActivity('Números')">Asignar</button></div>
    <div class="activity"><span class="emoji">📝</span><h3>Observaciones</h3><p>Registra avances, dificultades y recomendaciones.</p><button onclick="caregiverNote()">Agregar observación</button></div>
  </div>
</section>

<!-- INICIO PADRE/MADRE -->
<section id="inicioPadre" class="section">
  <div class="title-row"><div><h2>Hola, familia 👋</h2><p class="subtitle">Consulta de forma sencilla cómo va el usuario vinculado.</p></div></div>
  <div class="stats-grid">
    <div class="stat-card"><b>82%</b><span>📈 Progreso semanal</span></div>
    <div class="stat-card"><b>8</b><span>🎯 Actividades</span></div>
    <div class="stat-card"><b>24</b><span>⭐ Estrellas</span></div>
  </div>
  <div class="info-grid">
    <div class="panel"><h3>👦 Mi hijo / usuario</h3><div class="list-item"><span>Estado</span><span class="badge">🟢 Activo</span></div><div class="list-item"><span>Rutina de hoy</span><strong>3/5</strong></div></div>
    <div class="panel"><h3>🔔 Resumen</h3><div class="success">✓ No hay alertas importantes.</div></div>
  </div>
</section>

<!-- PROGRESO PADRE/MADRE -->
<section id="progresoPadre" class="section">
  <div class="title-row"><div><h2>📊 Progreso</h2><p class="subtitle">Resumen del aprendizaje y las actividades del usuario.</p></div></div>
  <div class="panel">
    <div class="list-item"><span>🎯 Actividades completadas</span><strong>8</strong></div>
    <div class="list-item"><span>⭐ Estrellas obtenidas</span><strong>24</strong></div>
    <div class="list-item"><span>📈 Progreso semanal</span><strong>82%</strong></div>
    <div class="progress"><div class="progress-fill" style="width:82%"></div></div>
  </div>
  <div class="cards-grid" style="margin-top:18px"><div class="card"><h3>💪 Fortalezas</h3><p>Buen desempeño en memoria y reconocimiento de colores.</p></div><div class="card"><h3>🌱 Para seguir practicando</h3><p>Continuar con números, comunicación y rutina diaria.</p></div></div>
</section>

<!-- RUTINAS PADRE/MADRE -->
<section id="rutinasPadre" class="section">
  <div class="title-row"><div><h2>📅 Rutinas</h2><p class="subtitle">Revisa la rutina del usuario vinculado.</p></div></div>
  <div class="panel"><div class="list-item"><span>🌅 Levantarse y organizarse</span><span class="badge">✓</span></div><div class="list-item"><span>🪥 Cepillarse los dientes</span><span class="badge">✓</span></div><div class="list-item"><span>🍽️ Desayunar</span><span class="badge">✓</span></div><div class="list-item"><span>📚 Actividad educativa</span><span class="badge">Pendiente</span></div><div class="list-item"><span>🧘 Descanso</span><span class="badge">Pendiente</span></div></div>
</section>

<!-- LOGROS PADRE/MADRE -->
<section id="logrosPadre" class="section">
  <div class="title-row"><div><h2>🏆 Puntaje y logros</h2><p class="subtitle">Mira los avances y reconocimientos obtenidos.</p></div></div>
  <div class="stats-grid"><div class="stat-card"><b>24</b><span>⭐ Estrellas</span></div><div class="stat-card"><b>3</b><span>🏅 Insignias</span></div><div class="stat-card"><b>1</b><span>🌟 Nivel</span></div></div>
  <div class="panel"><h3>🏅 Insignias</h3><div class="badges"><span>🌱 Inicio</span><span>🧠 Aprendiz</span><span>🎯 Constancia</span></div></div>
</section>

<!-- ALERTAS PADRE/MADRE -->
<section id="alertasPadre" class="section">
  <div class="title-row"><div><h2>🚨 Alertas</h2><p class="subtitle">Avisos importantes sobre el usuario vinculado.</p></div></div>
  <div class="panel"><div class="success">✓ No hay alertas importantes en este momento.</div><div class="alert">ℹ️ Si Mowgly detecta una situación configurada como alerta, podrás consultarla aquí.</div></div>
</section>

<!-- BUSCAR CUIDADOR PADRE/MADRE -->
<section id="buscarCuidadoresPadre" class="section">
  <div class="section-title"><h2>👨‍⚕️ Buscar cuidador</h2><p>Consulta perfiles, experiencia y calificaciones para elegir un cuidador.</p></div>
  <div class="cards-grid" id="caregiverCardsPadre"></div>
</section>

<!-- MENSAJES PADRE/MADRE -->
<section id="mensajesPadre" class="section">
  <div class="section-title"><h2>💬 Mensajes</h2><p>Comunícate con el cuidador vinculado.</p></div>
  <div class="card caregiver-chat"><div class="chat-head"><span class="avatar">👨‍⚕️</span><div><strong>Cuidador vinculado</strong><small>🟢 Disponible</small></div></div><div class="chat-messages"><div class="message received">Hola. El usuario completó 3 actividades hoy. 😊</div><div class="message received">La rutina va avanzando bien.</div></div><div class="chat-compose"><input id="parentChatInput" placeholder="Escribe un mensaje..." onkeydown="if(event.key==='Enter')sendParentMessage()"><button class="primary-btn" onclick="sendParentMessage()">Enviar</button></div></div>
</section>

<!-- SEGUIMIENTO CUIDADOR -->
<section id="seguimiento" class="section">
  <div class="title-row"><div><h2>👥 Usuarios vinculados</h2><p class="subtitle">Consulta el progreso de las cuentas vinculadas.</p></div></div>
  <div class="panel">
    <div class="list-item"><span>👤 Usuario de demostración</span><span class="badge">Vinculado</span></div>
    <div class="list-item"><span>🎯 Actividades completadas</span><strong>8</strong></div>
    <div class="list-item"><span>⭐ Progreso semanal</span><strong>82%</strong></div>
    <div class="list-item"><span>🔔 Alertas</span><span class="badge">Sin alertas</span></div>
  </div>
</section>

<!-- ALERTAS -->
<section id="alertas" class="section">
  <div class="title-row"><div><h2>🔔 Alertas</h2><p class="subtitle">Notificaciones importantes del sistema.</p></div></div>
  <div class="panel"><div class="success">✓ Actualmente no hay alertas activas.</div><div class="alert">ℹ️ Cuando el prototipo detecte una situación configurada como alerta, aparecerá aquí.</div></div>
</section>

<!-- VINCULO -->
<section id="vinculo" class="section">
  <div class="title-row"><div><h2 id="linkTitle">🔗 Vincular cuentas</h2><p id="linkSubtitle" class="subtitle">Gestiona la vinculación entre cuentas.</p></div></div>
  <div class="link-box">
    <h3>Tu código de vinculación</h3>
    <p>Comparte este código con la persona que deseas vincular.</p>
    <div class="link-code">MOW-4821</div>
    <button class="secondary" onclick="copyCode()">Copiar código</button>
  </div>
  <div class="panel">
    <h3>Vincular una cuenta</h3>
    <p class="subtitle">El usuario o cuidador puede introducir el código de la otra cuenta.</p>
    <div class="link-row" style="margin-top:13px"><input id="linkCode" placeholder="Ej: MOW-4821"><button class="primary" style="width:auto;margin:0" onclick="linkAccount()">Vincular</button></div>
    <div id="linkResult"></div>
  </div>
  <div class="panel" style="margin-top:18px"><h3>👥 Cuentas vinculadas</h3><div id="linkedList"><div class="list-item"><span>No hay cuentas vinculadas todavía.</span></div></div></div>
</section>

<!-- CUIDADORES -->
<section id="cuidadores" class="section">
  <div class="title-row"><div><h2>🧑‍⚕️ Recomendaciones de cuidadores</h2><p class="subtitle">Consulta perfiles y puntuaciones antes de elegir.</p></div></div>
  <div class="caregiver-grid">
    <div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👩‍⚕️</div><div><h3>Laura Martínez</h3><span class="score">⭐ 4.9 / 5</span></div></div><div class="stars">★★★★★</div><p>Experiencia en acompañamiento, actividades educativas y apoyo familiar.</p><div class="tags"><span class="tag">5 años experiencia</span><span class="tag">Inclusión</span></div><button class="hire" onclick="hire('Laura Martínez')">Solicitar cuidador</button></div>
    <div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👨‍⚕️</div><div><h3>Andrés Gómez</h3><span class="score">⭐ 4.8 / 5</span></div></div><div class="stars">★★★★★</div><p>Enfoque en acompañamiento diario, actividades y seguimiento del progreso.</p><div class="tags"><span class="tag">4 años experiencia</span><span class="tag">Actividades</span></div><button class="hire" onclick="hire('Andrés Gómez')">Solicitar cuidador</button></div>
    <div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👩‍⚕️</div><div><h3>Sofía Rodríguez</h3><span class="score">⭐ 4.7 / 5</span></div></div><div class="stars">★★★★★</div><p>Perfil orientado al acompañamiento personalizado y comunicación con familias.</p><div class="tags"><span class="tag">3 años experiencia</span><span class="tag">Familias</span></div><button class="hire" onclick="hire('Sofía Rodríguez')">Solicitar cuidador</button></div>
  </div>
  <div class="panel" style="margin-top:20px"><h3>⭐ ¿Cómo funciona la puntuación?</h3><p class="subtitle">En la versión conectada, la puntuación se calculará a partir de las valoraciones de las familias, experiencia, cumplimiento y calidad del servicio.</p></div>
</section>

<!-- PADRE/MADRE -->
<section id="inicioPadre" class="section"><div class="title-row"><div><h2>👨‍👩‍👧 Panel familiar</h2><p class="subtitle">Consulta de forma sencilla cómo va tu hijo y qué necesita.</p></div></div><div class="stats-grid"><div class="stat-card"><b>82%</b><span>📈 Progreso semanal</span></div><div class="stat-card"><b>8</b><span>🎯 Actividades realizadas</span></div><div class="stat-card"><b>24</b><span>⭐ Estrellas</span></div></div><div class="info-grid"><div class="panel"><h3>👦 Mi hijo</h3><div class="list-item"><span>Estado</span><span class="badge">Activo</span></div><div class="list-item"><span>Última actividad</span><strong>Ejercicios de memoria</strong></div><div class="list-item"><span>Rutina de hoy</span><strong>4/5 completada</strong></div></div><div class="panel"><h3>💡 Recomendación</h3><div class="success">Continúa reforzando las actividades de memoria y comunicación.</div></div></div></section>
<section id="progresoPadre" class="section"><div class="title-row"><div><h2>📊 Progreso</h2><p class="subtitle">Resumen del avance de tu hijo.</p></div></div><div class="panel"><div class="progress-row"><strong>Actividades</strong><strong>82%</strong></div><div class="progress-wrap"><div class="progress-bar" style="width:82%"></div></div><div class="list-item"><span>🧠 Memoria</span><span class="badge">Excelente</span></div><div class="list-item"><span>🎨 Colores</span><span class="badge">En progreso</span></div><div class="list-item"><span>🗣️ Comunicación</span><span class="badge">En progreso</span></div></div></section>
<section id="actividadesPadre" class="section"><div class="title-row"><div><h2>🎯 Actividades</h2><p class="subtitle">Revisa y recomienda actividades para tu hijo.</p></div></div><div class="activity-grid"><div class="activity"><span class="emoji">🧠</span><h3>Memoria</h3><p>Ayuda a reforzar atención y memoria.</p><button onclick="parentActivity('Memoria')">Recomendar</button></div><div class="activity"><span class="emoji">🎨</span><h3>Colores</h3><p>Reconocimiento y asociación de colores.</p><button onclick="parentActivity('Colores')">Recomendar</button></div><div class="activity"><span class="emoji">🔢</span><h3>Números</h3><p>Conteo y reconocimiento de números.</p><button onclick="parentActivity('Números')">Recomendar</button></div><div class="activity"><span class="emoji">🗣️</span><h3>Comunicación</h3><p>Prácticas sencillas de comunicación.</p><button onclick="parentActivity('Comunicación')">Recomendar</button></div></div></section>
<section id="rutinasPadre" class="section"><div class="title-row"><div><h2>📅 Rutinas</h2><p class="subtitle">Consulta la rutina de tu hijo.</p></div></div><div class="panel"><div class="progress-row"><strong>Rutina de hoy</strong><strong>4/5</strong></div><div class="progress-wrap"><div class="progress-bar" style="width:80%"></div></div><div class="routine-list"><div class="routine-item done">✓ <span>Levantarse</span></div><div class="routine-item done">✓ <span>Cepillarse los dientes</span></div><div class="routine-item done">✓ <span>Desayunar</span></div><div class="routine-item done">✓ <span>Preparar mochila</span></div><div class="routine-item">○ <span>Actividad de aprendizaje</span></div></div></div></section>
<section id="alertasPadre" class="section"><div class="title-row"><div><h2>🚨 Alertas</h2><p class="subtitle">Información importante sobre tu hijo.</p></div></div><div class="panel"><div class="success">✓ No hay alertas importantes en este momento.</div><div class="alert">ℹ️ Las alertas del prototipo aparecerán aquí cuando estén conectadas.</div></div></section>
<section id="buscarCuidadoresPadre" class="section"><div class="title-row"><div><h2>🔎 Buscar cuidador</h2><p class="subtitle">Busca perfiles, experiencia y calificaciones.</p></div></div><div class="caregiver-grid" id="parentCaregiverCards"></div></section>
<section id="cuidadoresPadre" class="section"><div class="title-row"><div><h2>⭐ Cuidadores recomendados</h2><p class="subtitle">Perfiles destacados para facilitar tu elección.</p></div></div><div class="caregiver-grid"><div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👩‍⚕️</div><div><h3>Laura Martínez</h3><span class="score">⭐ 4.9 / 5</span></div></div><div class="stars">★★★★★</div><p>Experiencia en acompañamiento y apoyo educativo.</p><div class="tags"><span class="tag">6 años</span><span class="tag">Inclusión</span></div><button class="hire" onclick="requestCaregiver('Laura Martínez')">Solicitar</button></div><div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👨‍⚕️</div><div><h3>Andrés Gómez</h3><span class="score">⭐ 4.8 / 5</span></div></div><div class="stars">★★★★★</div><p>Experiencia en acompañamiento diario y actividades.</p><div class="tags"><span class="tag">5 años</span><span class="tag">Actividades</span></div><button class="hire" onclick="requestCaregiver('Andrés Gómez')">Solicitar</button></div><div class="caregiver"><div class="caregiver-top"><div class="caregiver-avatar">👩‍⚕️</div><div><h3>Sofía Rodríguez</h3><span class="score">⭐ 4.7 / 5</span></div></div><div class="stars">★★★★★</div><p>Acompañamiento personalizado y comunicación con familias.</p><div class="tags"><span class="tag">4 años</span><span class="tag">Familias</span></div><button class="hire" onclick="requestCaregiver('Sofía Rodríguez')">Solicitar</button></div></div></section>
<section id="mensajesPadre" class="section"><div class="title-row"><div><h2>💬 Mensajes</h2><p class="subtitle">Comunícate con el cuidador vinculado.</p></div></div><div class="card"><div class="chat-messages"><div class="message received">Hola, familia. Hoy avanzamos muy bien con la rutina. 😊</div><div class="message received">La actividad de memoria fue completada.</div></div><div class="chat-compose"><input id="parentChatInput" placeholder="Escribe un mensaje..." onkeydown="if(event.key==='Enter')sendParentMessage()"><button class="primary" style="width:auto;margin:0" onclick="sendParentMessage()">Enviar</button></div></div></section>

<!-- PERFIL -->
<section id="perfil" class="section">
  <div class="title-row"><div><h2>👤 Perfil</h2><p class="subtitle">Información de la cuenta.</p></div></div>
  <div class="panel"><h3 id="profileRole">Usuario</h3><div class="list-item"><span>Correo</span><strong id="profileEmail">--</strong></div><div class="list-item"><span>Estado de vinculación</span><span class="badge" id="profileLink">Sin vincular</span></div></div>
</section>

<!-- CONFIG -->
<section id="config" class="section">
  <div class="title-row"><div><h2>⚙️ Configuración</h2><p class="subtitle">Preferencias de Mowgly.</p></div></div>
  <div class="panel"><div class="list-item"><span>🔔 Notificaciones</span><span class="badge">Activadas</span></div><div class="list-item"><span>🚨 Alertas de seguridad</span><span class="badge">Activadas</span></div><div class="list-item"><span>☁️ Sincronización</span><span class="badge">Pendiente Supabase</span></div></div>
</section>


<section id="rutinas" class="section">
  <div class="section-title"><h2>📅 Mi rutina</h2><p>Organiza tu día paso a paso.</p></div>
  <div class="card"><div class="progress-row"><strong>Rutina de la mañana</strong><span id="routineCount">0/5</span></div><div class="progress"><div id="routineBar" class="progress-fill" style="width:0%"></div></div>
    <div class="routine-list" id="routineList"></div>
  </div>
</section>

<section id="logros" class="section">
  <div class="section-title"><h2>🏆 Mis logros</h2><p>Cada esfuerzo cuenta.</p></div>
  <div class="stats-grid"><div class="stat-card"><b id="userStarsBig">0</b><span>⭐ Estrellas</span></div><div class="stat-card"><b id="userLevel">1</b><span>🌟 Nivel</span></div><div class="stat-card"><b id="completedCount">0</b><span>🎯 Actividades</span></div></div>
  <div class="cards-grid" id="achievementsGrid"></div>
</section>

<section id="comunicacion" class="section">
  <div class="section-title"><h2>💬 Mi cuidador</h2><p>Comunícate de forma sencilla y segura.</p></div>
  <div class="card caregiver-chat"><div class="chat-head"><span class="avatar">🧑‍⚕️</span><div><strong>Mi cuidador</strong><small id="caregiverStatus">🟢 Disponible</small></div></div>
    <div id="chatMessages" class="chat-messages"><div class="message received">¡Hola! ¿Cómo estás hoy? 😊</div><div class="message received">Recuerda completar tu rutina.</div></div>
    <div class="chat-compose"><input id="chatInput" placeholder="Escribe un mensaje..." onkeydown="if(event.key==='Enter')sendMessage()"><button class="primary-btn" onclick="sendMessage()">Enviar</button></div>
  </div>
</section>

<section id="rutinasCuidador" class="section">
  <div class="section-title"><h2>📅 Rutinas</h2><p>Crea y asigna rutinas a las personas vinculadas.</p></div>
  <div class="card"><h3>➕ Nueva actividad</h3><div class="form-row"><input id="newRoutineText" placeholder="Ej: Cepillarse los dientes"><button class="primary-btn" onclick="addRoutineItem()">Agregar</button></div><div id="caregiverRoutineList" class="routine-list"></div></div>
  <div class="card"><h3>📈 Resumen</h3><p>Progreso de la rutina: <strong id="careRoutineProgress">0%</strong></p><div class="progress"><div id="careRoutineBar" class="progress-fill" style="width:0%"></div></div></div>
</section>

<section id="buscarCuidadores" class="section">
  <div class="section-title"><h2>⭐ Buscar cuidador</h2><p>Consulta perfiles, experiencia y calificaciones.</p></div>
  <div class="cards-grid" id="caregiverCards"></div>
</section>

</main>
</div>
</div>

<script>
let selectedRole='usuario';
let currentEmail='';

function login(){
  const email=document.getElementById('email').value.trim();
  currentEmail=email||'demo@mowgly.app';
  openApp();
}

function register(){
  const email=document.getElementById('email').value.trim();
  currentEmail=email||'demo@mowgly.app';
  openApp();
}

function selectRole(role){
  selectedRole=role;
  document.getElementById('userRole').classList.toggle('active',role==='usuario');
  document.getElementById('parentRole').classList.toggle('active',role==='padre');
  document.getElementById('careRole').classList.toggle('active',role==='cuidador');
}

function openApp(){
  document.getElementById('loginScreen').classList.add('hidden');
  document.getElementById('app').classList.remove('hidden');
  const labels={usuario:'Usuario',padre:'Padre/Madre',cuidador:'Cuidador'};
  const avatars={usuario:'👤',padre:'👨‍👩‍👧',cuidador:'🧑‍⚕️'};
  document.getElementById('roleLabel').textContent=labels[selectedRole];
  document.getElementById('topAvatar').textContent=avatars[selectedRole];
  document.getElementById('profileRole').textContent='Cuenta de '+labels[selectedRole];
  document.getElementById('profileEmail').textContent=currentEmail||'--';
  buildMenu();
  if(selectedRole==='usuario'){showSection('aprender',document.querySelector('.nav-btn'));openTopic('animales',document.querySelector('.learn-category'));}
  else if(selectedRole==='padre'){showSection('inicioPadre',document.querySelector('.nav-btn'));renderParentCaregivers();}
  else showSection('inicio',document.querySelector('.nav-btn'));
}

function buildMenu(){
  const side=document.getElementById('sidebar');
  if(selectedRole==='usuario') side.innerHTML=`
    <button class="nav-btn active" onclick="showSection('aprender',this)">🌟 Aprender</button>
    <button class="nav-btn" onclick="showSection('explorar',this)">🌎 Explorar y aprender</button>
    <button class="nav-btn" onclick="showSection('rutinas',this)">📅 Mi rutina</button>
    <button class="nav-btn" onclick="showSection('logros',this)">🏆 Mis logros</button>
    <button class="nav-btn" onclick="showSection('vinculo',this)">🔗 Vincular con cuidador</button>
    <button class="nav-btn" onclick="showSection('comunicacion',this)">💬 Mi cuidador</button>
    <button class="nav-btn" onclick="showSection('perfil',this)">👤 Mi perfil</button>
    <button class="nav-btn" onclick="showSection('config',this)">⚙️ Configuración</button>
    <button class="nav-btn" onclick="logout()" style="margin-top:15px;color:#d9534f">🚪 Cerrar sesión</button>`;
  else if(selectedRole==='padre') side.innerHTML=`
    <button class="nav-btn active" onclick="showSection('inicioPadre',this)">🏠 Inicio</button>
    <button class="nav-btn" onclick="showSection('progresoPadre',this)">📊 Progreso</button>
    <button class="nav-btn" onclick="showSection('logros',this)">🏆 Puntaje y logros</button>
    <button class="nav-btn" onclick="showSection('rutinasPadre',this)">📅 Rutinas</button>
    <button class="nav-btn" onclick="showSection('actividadesPadre',this)">🎯 Actividades</button>
    <button class="nav-btn" onclick="showSection('alertasPadre',this)">🚨 Alertas</button>
    <button class="nav-btn" onclick="showSection('buscarCuidadoresPadre',this)">🔎 Buscar cuidador</button>
    <button class="nav-btn" onclick="showSection('cuidadoresPadre',this)">⭐ Cuidadores recomendados</button>
    <button class="nav-btn" onclick="showSection('vinculo',this)">🔗 Vincular cuidador</button>
    <button class="nav-btn" onclick="showSection('mensajesPadre',this)">💬 Mensajes</button>
    <button class="nav-btn" onclick="showSection('perfil',this)">👤 Mi perfil</button>
    <button class="nav-btn" onclick="showSection('config',this)">⚙️ Configuración</button>
    <button class="nav-btn" onclick="logout()" style="margin-top:15px;color:#d9534f">🚪 Cerrar sesión</button>`;
  else side.innerHTML=`
    <button class="nav-btn active" onclick="showSection('inicio',this)">🏠 Inicio</button>
    <button class="nav-btn" onclick="showSection('seguimiento',this)">👥 Mis usuarios</button>
    <button class="nav-btn" onclick="showSection('actividadesCuidador',this)">🎯 Actividades</button>
    <button class="nav-btn" onclick="showSection('rutinasCuidador',this)">📅 Rutinas</button>
    <button class="nav-btn" onclick="showSection('sensores',this)">📊 Sensores</button>
    <button class="nav-btn" onclick="showSection('alertas',this)">🚨 Alertas</button>
    <button class="nav-btn" onclick="showSection('vinculo',this)">🔗 Vincular cuentas</button>
    <button class="nav-btn" onclick="showSection('comunicacion',this)">💬 Mensajes</button>
    <button class="nav-btn" onclick="showSection('perfil',this)">👤 Mi perfil</button>
    <button class="nav-btn" onclick="showSection('config',this)">⚙️ Configuración</button>
    <button class="nav-btn" onclick="logout()" style="margin-top:15px;color:#d9534f">🚪 Cerrar sesión</button>`;
}

function showSection(id,btn){
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  if(btn)btn.classList.add('active');
}

function completeActivity(btn){
  btn.textContent='✓ Completada';
  btn.style.background='#2c9a64';
  alert('Actividad registrada. En la versión con Supabase este avance se guardará y podrá ser consultado por el cuidador vinculado.');
}

function caregiverNote(){
  const note=prompt('Escribe la observación del cuidador:');
  if(note)alert('Observación registrada en modo demostración.');
}

function copyCode(){
  navigator.clipboard?.writeText('MOW-4821');
  alert('Código MOW-4821 copiado.');
}

function linkAccount(){
  const code=document.getElementById('linkCode').value.trim().toUpperCase();
  const result=document.getElementById('linkResult');
  if(!code){result.innerHTML='<div class="alert">Escribe un código de vinculación.</div>';return}
  if(code==='MOW-4821'){
    result.innerHTML='<div class="success">✓ Cuenta vinculada correctamente en la demostración.</div>';
    document.getElementById('linkedList').innerHTML='<div class="list-item"><span>Cuenta Mowgly vinculada</span><span class="badge">Vinculada</span></div>';
    document.getElementById('profileLink').textContent='Vinculada';
  }else{
    result.innerHTML='<div class="alert">No encontramos ese código. Verifica que esté correcto.</div>';
  }
}

function hire(name){
  alert('Solicitud enviada a '+name+' en modo demostración. En la versión conectada podremos agregar disponibilidad, mensajería, contratación y pagos.');
}


let stars=0, challenges=0;

function addStar(){
  stars++;
  challenges=Math.min(3,challenges+1);
  document.getElementById('starCounter').textContent='⭐ '+stars+' estrellas';
  document.getElementById('learningProgress').style.width=(challenges/3*100)+'%';
  document.getElementById('progressText').textContent=challenges+' de 3 retos completados';
  if(challenges===3) alert('🏆 ¡Insignia desbloqueada! Completaste la misión de hoy.');
}

function memoryChallenge(btn){
  const answer=prompt('¿Qué elemento viste entre los tres? Escribe: perro, manzana o estrella.');
  if(answer && answer.toLowerCase().includes('estrella')){
    addStar(); btn.textContent='✓ ¡Correcto!';
  }else if(answer){ alert('Casi. Inténtalo de nuevo: recuerda los tres elementos.'); }
}

function colorChallenge(btn,color){
  if(color===colorTarget){ addStar(); btn.textContent='✓'; document.getElementById('colorHint').textContent='¡Excelente! Has encontrado el color correcto.'; colorTarget=colorTarget==='rojo'?'azul':'verde';}
  else alert('¡Inténtalo otra vez! Mowgly te da una pista: busca el color '+colorTarget+'.');
}

function numberChallenge(btn,n){
  if(n===8){addStar();btn.textContent='✓ Correcto';} else alert('Casi. Mira la secuencia: aumenta de 2 en 2.');
}

function wordChallenge(btn){ addStar(); btn.textContent='✓ ¡Aprendido!'; alert('INCLUSIÓN: significa que todas las personas pueden participar y tener oportunidades.'); }

function quickAnswer(btn,correct){
  if(correct){addStar();btn.textContent='✓ ¡Muy bien!';}else alert('Cuando necesitas ayuda, es importante comunicarlo a una persona de confianza.');
}

function assignActivity(name){
  alert('Actividad "'+name+'" asignada en modo demostración. En Supabase se guardará para el usuario vinculado.');
}


function startMemoryGame(){
  document.getElementById('gameModal').classList.remove('hidden');
  renderMemoryLevelPicker();
}

function renderMemoryLevelPicker(){
  document.getElementById('gameContent').innerHTML=`
    <h2>🧠 Juego de Memoria</h2>
    <p class="subtitle">Elige con cuántas parejas quieres jugar.</p>
    <div class="quick-options" style="justify-content:center">
      <button onclick="renderMemoryBoard(3)">🟢 Fácil · 3 parejas</button>
      <button onclick="renderMemoryBoard(4)">🟡 Medio · 4 parejas</button>
      <button onclick="renderMemoryBoard(6)">🔵 Avanzado · 6 parejas</button>
    </div>`;
}

function renderMemoryBoard(numPairs){
  const allSymbols=['🐶','🍎','⭐','🌈','🚗','🎈','🐱','☀️','🌸','🐟','🎵','🍇'];
  const symbols=allSymbols.slice(0,numPairs);
  const shuffled=[...symbols,...symbols].sort(()=>Math.random()-0.5);
  let first=null, lock=false, matched=0;

  document.getElementById('gameContent').innerHTML=`
    <h2>🧠 Juego de Memoria</h2>
    <p class="subtitle">Encuentra las parejas. Tómate tu tiempo, no hay reloj.</p>
    <div class="memory-board" id="memoryBoard" style="grid-template-columns:repeat(${numPairs<=3?3:4},1fr)"></div>
    <div id="memoryMessage" class="game-message">Toca una carta para comenzar.</div>
    <button class="secondary" style="margin-top:12px" onclick="renderMemoryLevelPicker()">← Cambiar nivel</button>`;

  const board=document.getElementById('memoryBoard');
  shuffled.forEach((symbol)=>{
    const card=document.createElement('button');
    card.className='memory-card';
    card.textContent=symbol;
    card.dataset.symbol=symbol;
    card.setAttribute('aria-label','Carta boca abajo');
    card.onclick=()=>{
      if(lock || card.classList.contains('revealed') || card.classList.contains('matched')) return;
      card.classList.add('revealed');
      if(!first){first=card;return}
      if(first.dataset.symbol===card.dataset.symbol){
        first.classList.add('matched'); card.classList.add('matched');
        matched++; first=null;
        document.getElementById('memoryMessage').textContent='⭐ ¡Muy bien, es una pareja!';
        if(matched===numPairs){
          addStar();
          document.getElementById('memoryMessage').textContent='🏆 ¡Excelente! Encontraste todas las parejas.';
        }
      }else{
        lock=true;
        document.getElementById('memoryMessage').textContent='🤔 Casi. Míralas de nuevo con calma.';
        setTimeout(()=>{
          first.classList.remove('revealed');card.classList.remove('revealed');
          first=null;lock=false;
          document.getElementById('memoryMessage').textContent='Toca una carta.';
        },1500);
      }
    };
    board.appendChild(card);
  });
}

let colorTarget='';
function startColorGame(){
  const colors=['rojo','azul','verde'];
  colorTarget=colors[Math.floor(Math.random()*colors.length)];
  document.getElementById('colorTargetText').textContent='Mowgly dice: ¡encuentra el color '+colorTarget+'!';
}
function chooseColor(color){
  if(!colorTarget){alert('Primero pulsa "Comenzar".');return}
  if(color===colorTarget){
    addStar();
    document.getElementById('colorTargetText').textContent='🎉 ¡Correcto! Pulsa Comenzar para otro reto.';
    colorTarget='';
  }else{
    alert('Casi. Mira bien la indicación de Mowgly e inténtalo otra vez.');
  }
}

function newNumberGame(){
  const start=Math.floor(Math.random()*5)+1;
  const step=[1,2,3][Math.floor(Math.random()*3)];
  const answer=start+step*3;
  document.getElementById('numberQuestion').textContent=`${start} → ${start+step} → ${start+step*2} → ?`;
  const options=[answer,answer+1,Math.max(1,answer-1)].sort(()=>Math.random()-0.5);
  document.getElementById('numberOptions').innerHTML=options.map(n=>`<button onclick="chooseNumber(this,${n},${answer})">${n}</button>`).join('');
}
function chooseNumber(btn,n,answer=8){
  if(n===answer){
    addStar();btn.textContent='✓ '+n;
    btn.style.background='#eaf9f0';
  }else alert('Casi. Mira cuánto aumenta cada número.');
}

function closeGame(){
  document.getElementById('gameModal').classList.add('hidden');
  document.getElementById('gameContent').innerHTML='';
}


const topics={
  animales:{
    icon:'🐾',title:'Mundo de los animales',description:'Conoce animales y descubre datos curiosos.',
    cards:[
      ['🦁','León','Vive en grupos llamados manadas.','Es conocido como un gran felino.'],
      ['🐘','Elefante','Tiene una trompa que utiliza para muchas tareas.','Es uno de los animales terrestres más grandes.'],
      ['🐬','Delfín','Vive en el agua y se comunica mediante sonidos.','Es un mamífero marino.'],
      ['🦋','Mariposa','Pasa por una transformación durante su vida.','Sus alas tienen patrones y colores variados.'],
      ['🐧','Pingüino','Es un ave que no vuela y puede nadar.','Muchas especies viven en zonas frías.'],
      ['🐶','Perro','Puede aprender órdenes y convivir con las personas.','Es un animal doméstico muy común.']
    ]
  },
  ciudades:{
    icon:'🏙️',title:'Ciudades del mundo',description:'Descubre lugares, culturas y ciudades famosas.',
    cards:[
      ['🇨🇴','Cartagena','Ciudad colombiana junto al mar Caribe.','Es conocida por su ciudad amurallada.'],
      ['🗼','París','Una ciudad famosa de Francia.','Es conocida por la Torre Eiffel.'],
      ['🗽','Nueva York','Una gran ciudad de Estados Unidos.','Es conocida por Times Square y Central Park.'],
      ['🏯','Tokio','Una gran ciudad de Japón.','Combina tecnología, tradición y cultura.'],
      ['🌉','San Francisco','Ciudad estadounidense junto al océano Pacífico.','Es famosa por el Golden Gate.'],
      ['🏛️','Roma','Ciudad histórica de Italia.','Tiene monumentos de la antigua Roma.']
    ]
  },
  naturaleza:{
    icon:'🌿',title:'Naturaleza',description:'Aprende sobre plantas, paisajes y nuestro planeta.',
    cards:[
      ['🌳','Árbol','Produce oxígeno y ofrece refugio a muchos seres vivos.','Los bosques tienen gran diversidad.'],
      ['🌊','Océano','Cubre gran parte de la superficie del planeta.','Es hogar de miles de especies.'],
      ['🏔️','Montaña','Es una elevación natural del terreno.','Algunas montañas tienen nieve en sus cumbres.'],
      ['🌋','Volcán','Puede expulsar lava, gases y cenizas.','Los volcanes forman parte de la actividad de la Tierra.'],
      ['🌻','Planta','Necesita agua, luz y nutrientes para crecer.','Las plantas son importantes para los ecosistemas.'],
      ['🌈','Arcoíris','Aparece cuando la luz interactúa con gotas de agua.','Puede verse con diferentes colores.']
    ]
  },
  cuerpo:{
    icon:'🧍',title:'Conozco mi cuerpo',description:'Aprende de manera sencilla sobre las partes del cuerpo.',
    cards:[
      ['❤️','Corazón','Ayuda a mover la sangre por el cuerpo.','Trabaja continuamente.'],
      ['🧠','Cerebro','Participa en el pensamiento, movimiento y aprendizaje.','Nos ayuda a procesar información.'],
      ['👁️','Ojos','Nos permiten ver nuestro entorno.','La visión nos ayuda a orientarnos.'],
      ['👂','Oídos','Nos permiten escuchar sonidos.','También participan en el equilibrio.'],
      ['🫁','Pulmones','Participan en la respiración.','Ayudan a intercambiar oxígeno y dióxido de carbono.'],
      ['🦴','Huesos','Dan estructura y soporte al cuerpo.','Junto con los músculos permiten el movimiento.']
    ]
  },
  espacio:{
    icon:'🚀',title:'Viaje por el espacio',description:'Explora planetas, estrellas y el universo.',
    cards:[
      ['☀️','Sol','Es una estrella ubicada en el centro de nuestro sistema solar.','Nos proporciona luz y energía.'],
      ['🌍','Tierra','Es el planeta donde vivimos.','Tiene agua, aire y una gran variedad de vida.'],
      ['🌙','Luna','Es el satélite natural de la Tierra.','La vemos cambiar de fase durante el mes.'],
      ['🔴','Marte','Es conocido por su apariencia rojiza.','Es uno de los planetas del sistema solar.'],
      ['🪐','Saturno','Es famoso por sus anillos.','Es un planeta gigante gaseoso.'],
      ['⭐','Estrella','Es una enorme esfera de gas muy caliente.','El Sol también es una estrella.']
    ]
  },
  oficios:{
    icon:'👩‍🚒',title:'Conozcamos los oficios',description:'Descubre trabajos que ayudan a nuestra comunidad.',
    cards:[
      ['👨‍⚕️','Médico','Ayuda a cuidar la salud de las personas.','Trabaja en prevención, diagnóstico y tratamiento.'],
      ['👩‍🏫','Profesor','Ayuda a otras personas a aprender.','Puede enseñar diferentes materias.'],
      ['👨‍🚒','Bombero','Ayuda en emergencias y rescates.','También participa en prevención de incendios.'],
      ['👩‍🍳','Cocinero','Prepara alimentos y diferentes recetas.','Puede trabajar en hogares o restaurantes.'],
      ['👷','Constructor','Participa en la construcción y mantenimiento de espacios.','Puede trabajar con diferentes materiales.'],
      ['👮','Policía','Ayuda a mantener la seguridad y el orden.','Trabaja para proteger a la comunidad.']
    ]
  }
};

let currentTopic='animales';
let exploreQuizIndex=0;

function openTopic(topic,btn){
  currentTopic=topic;
  document.querySelectorAll('.learn-category').forEach(b=>b.classList.remove('active'));
  if(btn)btn.classList.add('active');
  const data=topics[topic];
  document.getElementById('topicHero').querySelector('.topic-icon').textContent=data.icon;
  document.getElementById('topicTitle').textContent=data.title;
  document.getElementById('topicDescription').textContent=data.description;
  document.getElementById('exploreCards').innerHTML=data.cards.map((c,i)=>`
    <div class="explore-card">
      <div class="big-icon">${c[0]}</div>
      <h3>${c[1]}</h3>
      <p>${c[2]}</p>
      <button class="learn-more" onclick="showFact(this,'${encodeURIComponent(c[3])}')">💡 Saber más</button>
      <div class="fact hidden"></div>
    </div>`).join('');
  newExploreQuiz();
}

function showFact(btn,fact){
  const box=btn.parentElement.querySelector('.fact');
  box.textContent=decodeURIComponent(fact);
  box.classList.toggle('hidden');
  btn.textContent=box.classList.contains('hidden')?'💡 Saber más':'📖 Ocultar';
}

const quizData={
  animales:[
    ['¿Cuál de estos animales es un mamífero marino?',['Delfín','Mariposa','León'],'Delfín'],
    ['¿Cuál animal tiene una trompa?',['Elefante','Pingüino','Perro'],'Elefante'],
    ['¿Cuál de estos animales puede volar?',['Mariposa','Elefante','Delfín'],'Mariposa']
  ],
  ciudades:[
    ['¿En qué país está Cartagena?',['Colombia','Italia','Japón'],'Colombia'],
    ['¿Qué ciudad es conocida por la Torre Eiffel?',['París','Tokio','Roma'],'París'],
    ['¿En qué país está Tokio?',['Japón','Francia','Colombia'],'Japón']
  ],
  naturaleza:[
    ['¿Qué necesitan las plantas para crecer?',['Agua y luz','Solo piedras','Solo arena'],'Agua y luz'],
    ['¿Dónde viven muchas especies marinas?',['Océano','Desierto','Montaña'],'Océano'],
    ['¿Qué puede expulsar un volcán?',['Lava','Hielo','Algodón'],'Lava']
  ],
  cuerpo:[
    ['¿Qué órgano participa en el pensamiento?',['Cerebro','Pie','Mano'],'Cerebro'],
    ['¿Qué usamos para escuchar?',['Oídos','Rodillas','Codos'],'Oídos'],
    ['¿Qué órgano ayuda a mover la sangre?',['Corazón','Ojos','Cabello'],'Corazón']
  ],
  espacio:[
    ['¿En qué planeta vivimos?',['Tierra','Marte','Saturno'],'Tierra'],
    ['¿Qué es el Sol?',['Una estrella','Un planeta','Un satélite'],'Una estrella'],
    ['¿Qué planeta es famoso por sus anillos?',['Saturno','Tierra','Marte'],'Saturno']
  ],
  oficios:[
    ['¿Quién ayuda a enseñar y aprender?',['Profesor','Cocinero','Constructor'],'Profesor'],
    ['¿Quién ayuda en incendios y rescates?',['Bombero','Médico','Profesor'],'Bombero'],
    ['¿Quién prepara alimentos?',['Cocinero','Policía','Bombero'],'Cocinero']
  ]
};

function newExploreQuiz(){
  const list=quizData[currentTopic];
  const q=list[Math.floor(Math.random()*list.length)];
  document.getElementById('exploreQuestion').textContent=q[0];
  document.getElementById('exploreFeedback').classList.add('hidden');
  document.getElementById('exploreAnswers').innerHTML=q[1].sort(()=>Math.random()-0.5).map(a=>
    `<button onclick="answerExplore(this,'${encodeURIComponent(a)}','${encodeURIComponent(q[2])}')">${a}</button>`).join('');
}

function answerExplore(btn,answer,correct){
  const feedback=document.getElementById('exploreFeedback');
  if(decodeURIComponent(answer)===decodeURIComponent(correct)){
    addStar();
    feedback.textContent='🎉 ¡Muy bien! Has aprendido algo nuevo.';
    feedback.classList.remove('hidden');
    btn.style.background='#eaf9f0';
  }else{
    feedback.textContent='💡 ¡Casi! Inténtalo de nuevo.';
    feedback.classList.remove('hidden');
  }
}

function logout(){
  closeGame();
  document.getElementById('app').classList.add('hidden');
  document.getElementById('loginScreen').classList.remove('hidden');
  document.getElementById('password').value='';
  stars=0; challenges=0;
}

let routineItems=[
 {text:'Levantarse',done:false},{text:'Cepillarse los dientes',done:false},{text:'Bañarse',done:false},{text:'Desayunar',done:false},{text:'Preparar mochila',done:false}
];
let totalCompleted=0;
function renderRoutine(){
 const list=document.getElementById('routineList'); if(!list)return;
 list.innerHTML=routineItems.map((x,i)=>`<label class="routine-item ${x.done?'done':''}"><input type="checkbox" ${x.done?'checked':''} onchange="toggleRoutine(${i},this.checked)"><span>${x.text}</span></label>`).join('');
 const done=routineItems.filter(x=>x.done).length, pct=Math.round(done/routineItems.length*100);
 const c=document.getElementById('routineCount'); if(c)c.textContent=`${done}/${routineItems.length}`;
 const b=document.getElementById('routineBar'); if(b)b.style.width=pct+'%';
 const cb=document.getElementById('careRoutineBar'); if(cb)cb.style.width=pct+'%';
 const cp=document.getElementById('careRoutineProgress'); if(cp)cp.textContent=pct+'%';
}
function toggleRoutine(i,v){routineItems[i].done=v;if(v){totalCompleted++;addStar();}renderRoutine();renderAchievements();}
function renderAchievements(){
 const grid=document.getElementById('achievementsGrid');if(!grid)return;
 const currentStars=stars, level=Math.max(1,Math.floor(currentStars/50)+1);
 const sb=document.getElementById('userStarsBig');if(sb)sb.textContent=currentStars;
 const lv=document.getElementById('userLevel');if(lv)lv.textContent=level;
 const cc=document.getElementById('completedCount');if(cc)cc.textContent=totalCompleted;
 const items=[['🌱','Primer paso','Completa tu primera actividad',totalCompleted>=1],['⭐','Coleccionista','Consigue 50 estrellas',currentStars>=50],['📅','Rutina completa','Completa toda tu rutina',routineItems.every(x=>x.done)],['🧠','Mente activa','Completa 5 actividades',totalCompleted>=5],['🏆','Gran explorador','Consigue 100 estrellas',currentStars>=100],['💬','Buen comunicador','Envía tu primer mensaje',localStorage.getItem('mowglyMessage')==='1']];
 grid.innerHTML=items.map(x=>`<div class="card"><div style="font-size:32px">${x[0]}</div><h3>${x[1]}</h3><p>${x[2]}</p><strong>${x[3]?'✅ Desbloqueado':'🔒 Bloqueado'}</strong></div>`).join('');
}
function sendMessage(){const input=document.getElementById('chatInput'),box=document.getElementById('chatMessages');if(!input||!box||!input.value.trim())return;const d=document.createElement('div');d.className='message sent';d.textContent=input.value.trim();box.appendChild(d);input.value='';localStorage.setItem('mowglyMessage','1');renderAchievements();setTimeout(()=>{const r=document.createElement('div');r.className='message received';r.textContent='¡Mensaje recibido! 😊';box.appendChild(r);box.scrollTop=box.scrollHeight;},500);}
function addRoutineItem(){const input=document.getElementById('newRoutineText');if(!input||!input.value.trim())return;routineItems.push({text:input.value.trim(),done:false});input.value='';renderRoutine();renderCaregiverRoutine();}
function renderCaregiverRoutine(){const el=document.getElementById('caregiverRoutineList');if(!el)return;el.innerHTML=routineItems.map((x,i)=>`<div class="routine-item ${x.done?'done':''}"><span style="flex:1">${x.text}</span><button onclick="removeRoutine(${i})">🗑️</button></div>`).join('');}
function removeRoutine(i){routineItems.splice(i,1);if(!routineItems.length)routineItems.push({text:'Nueva actividad',done:false});renderRoutine();renderCaregiverRoutine();}
function renderCaregivers(){const el=document.getElementById('caregiverCards');if(!el)return;const data=[['🧑‍⚕️','Laura Gómez','4.9','6 años',['Inclusión','Rutinas','Apoyo educativo']],['👩‍⚕️','Andrea Martínez','4.8','4 años',['Educación especial','Actividades','Acompañamiento']],['🧑‍⚕️','Carlos Rodríguez','4.7','7 años',['Autonomía','Seguridad','Recreación']]];el.innerHTML=data.map(c=>`<div class="card caregiver-card"><div style="font-size:42px">${c[0]}</div><h3>${c[1]}</h3><p class="rating">⭐ ${c[2]} / 5 · ${c[3]} de experiencia</p><div>${c[4].map(t=>`<span class="tag">${t}</span>`).join('')}</div><button class="primary-btn" style="margin-top:14px" onclick="requestCaregiver('${c[1]}')">Solicitar cuidador</button></div>`).join('');}
function requestCaregiver(name){alert('Solicitud enviada a '+name+'. Esta función quedará conectada a Supabase en la siguiente etapa.');}

function sendParentMessage(){
  const input=document.getElementById('parentChatInput');
  if(!input || !input.value.trim()) return;
  const box=document.querySelector('#mensajesPadre .chat-messages');
  const msg=document.createElement('div'); msg.className='message sent'; msg.textContent=input.value.trim(); box.appendChild(msg); input.value='';
}

function parentActivity(name){alert('La actividad "'+name+'" fue recomendada para tu hijo. En la versión conectada se guardará en Supabase.');}
function sendParentMessage(){const input=document.getElementById('parentChatInput');if(!input||!input.value.trim())return;alert('Mensaje enviado al cuidador en modo demostración.');input.value='';}
function renderParentCaregivers(){const el=document.getElementById('parentCaregiverCards');if(!el)return;const data=[['🧑‍⚕️','Laura Gómez','4.9','6 años',['Inclusión','Rutinas','Apoyo educativo']],['👩‍⚕️','Andrea Martínez','4.8','4 años',['Educación especial','Actividades','Acompañamiento']],['🧑‍⚕️','Carlos Rodríguez','4.7','7 años',['Autonomía','Seguridad','Recreación']],['👩‍⚕️','María Torres','4.6','5 años',['Comunicación','Familias','Rutinas']]];el.innerHTML=data.map(c=>`<div class="card caregiver-card"><div style="font-size:42px">${c[0]}</div><h3>${c[1]}</h3><p class="rating">⭐ ${c[2]} / 5 · ${c[3]} de experiencia</p><div>${c[4].map(t=>`<span class="tag">${t}</span>`).join('')}</div><button class="primary" style="margin-top:14px" onclick="requestCaregiver('${c[1]}')">Solicitar cuidador</button></div>`).join('');}
function initNewFeatures(){renderRoutine();renderCaregiverRoutine();renderAchievements();renderCaregivers();}

// Inicializar las funciones nuevas después de declarar todas sus variables.
initNewFeatures();
</script>

<div id="gameModal" class="game-modal hidden">
  <div class="game-window">
    <button class="close-game" onclick="closeGame()">✕</button>
    <div id="gameContent"></div>
  </div>
</div>
</body>
</html>
