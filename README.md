<style>
  .hero-text {
    position: absolute;
    top: 10%;
    left: 52%;
    transform: translateX(-50%);
    width: clamp(160px, 45%, 600px);
    padding: clamp(6px, 1.2vw, 12px);
    background: rgba(0, 0, 0, 0.72);
    border-radius: clamp(8px, 1.5vw, 16px);
    text-align: center;
    z-index: 1;
  }
  .hero-title {
    color: #ffffff;
    font-size: clamp(13px, 2.2vw, 22px);
    font-weight: 700;
    margin: 0;
    letter-spacing: 0.5px;
  }
  .hero-subtitle {
    color: rgba(255, 255, 255, 0.75);
    font-size: clamp(8px, 1.2vw, 12px);
    margin: 6px 0 0;
    letter-spacing: 0.4px;
  }
  /* Solo en pantallas pequeñas */
  @media (max-width: 600px) {
  .hero-text {
    top: 50%;
    transform: translate(-50%, -50%);
    width: 60%;
  }
  }
</style>
<div style="
    position: relative;
    width: 100%;
    overflow: hidden;
">
  <img
    src="./ddio625-88c6c961-13c1-43ee-a08f-3c3ceeb7f053.gif"
    style="
      display: block;
      width: 100%;
      height: auto;
      filter: brightness(0.25);
    "
  >
  <div class="hero-text">
    <h1 class="hero-title">
      Hola, soy Gustavo Tuesta
    </h1>
    <p class="hero-subtitle">
      Software Engineering Student · Backend Developer
    </p>
  </div>
</div>
<!-- SOBRE MÍ -->
<div style="
    display: flex;
    align-items: center;
    justify-content: center;
    gap: clamp(15px, 4vw, 50px);
    padding: clamp(30px, 5vw, 60px) 5%;
    flex-wrap: nowrap;
">
  <div style="
      flex: 1 1 auto;
      min-width: 0;
      max-width: 330px;
  ">
    <h2 style="
        color: #ffffff;
        font-size: clamp(21px, 2.7vw, 30px);
        margin: 0 0 18px;
        text-align: center;
    ">
      Sobre mí
    </h2>
    <p style="
        color: #b8b8b8;
        font-size: clamp(13px, 1.3vw, 16px);
        line-height: 1.7;
        margin: 0;
        text-align: justify;
    ">
      Soy estudiante de Ingeniería de Software con Inteligencia Artificial y desarrollador enfocado principalmente en el backend. Me gusta construir APIs, trabajar con bases de datos y desarrollar sistemas utilizando tecnologías como Node.js, NestJS y TypeScript. También exploro el campo de la Inteligencia Artificial y el Machine Learning, buscando combinar el desarrollo de software con soluciones inteligentes. Actualmente dedico gran parte de mi tiempo a aprender, desarrollar proyectos propios y enfrentar nuevos retos que me permitan seguir creciendo como desarrollador.
    </p>
  </div>
  <div style="
      flex: 0 1 280px;
      min-width: 150px;
      max-width: 280px;
      text-align: center;
  ">
    <img
      src="./Pixel Hacking Sticker by keywee motion.gif"
      style="
          width: 100%;
          height: auto;
      "
    >
  </div>
</div>
<!-- TECNOLOGÍAS -->
<div style="
    padding: 0 clamp(30px, 5vw, 60px) 5%;
    text-align: center;
">
  <h2 style="
      color: #ffffff;
      font-size: clamp(25px, 3.2vw, 30px);
      margin: 0 0 35px;
  ">
    Tecnologías
  </h2>
  <div style="
      display: flex;
      justify-content: center;
      align-items: stretch;
      gap: clamp(15px, 3vw, 40px);
      flex-wrap: nowrap;
  ">
    <!-- TECNOLOGÍAS PRINCIPALES -->
    <div style="
        flex: 1 1 0;
        min-width: 0;
        max-width: 500px;
        padding: clamp(18px, 2.5vw, 25px);
        background: rgba(255, 255, 255, 0.04);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 16px;
    ">
      <h3 style="
          color: #ffffff;
          font-size: clamp(18px, 2.2vw, 20px);
          margin: 0 0 25px;
      ">
        Tecnologías principales
      </h3>
      <div style="
          display: flex;
          justify-content: center;
          align-items: center;
          flex-wrap: wrap;
          gap: clamp(12px, 2vw, 20px);
      ">
        <img src="https://skillicons.dev/icons?i=nodejs" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=nestjs" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=ts" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=postgres" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=docker" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=git" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=github" width="50" height="50">
      </div>
    </div>
    <!-- EXPERIENCIA ADICIONAL -->
    <div style="
        flex: 1 1 0;
        min-width: 0;
        max-width: 500px;
        padding: clamp(18px, 2.5vw, 25px);
        background: rgba(255, 255, 255, 0.025);
        border: 1px solid rgba(255, 255, 255, 0.08);
        border-radius: 16px;
    ">
      <h3 style="
          color: #ffffff;
          font-size: clamp(18px, 2.2vw, 20px);
          margin: 0 0 25px;
      ">
        Experiencia adicional
      </h3>
      <div style="
          display: flex;
          justify-content: center;
          align-items: center;
          flex-wrap: wrap;
          gap: clamp(12px, 2vw, 20px);
      ">
        <img src="https://skillicons.dev/icons?i=java" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=python" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=sqlite" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=angular" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=tensorflow" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=react" width="50" height="50">
        <img src="https://skillicons.dev/icons?i=nextjs" width="50" height="50">
      </div>
    </div>
  </div>
</div>
<!-- GITHUB STREAK -->
<div style="
    display: flex;
    justify-content: center;
    padding: 20px 5% 50px;
">
  <img
    src="https://streak-stats.demolab.com?user=GustavoTuesta&theme=github-dark-dimmed"
    alt="GitHub Streak"
    style="
        width: min(100%, 650px);
        height: auto;
    "
  >
</div>