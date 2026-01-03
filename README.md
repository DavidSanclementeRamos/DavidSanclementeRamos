<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>David — Arquitecto de software | Java & Spring</title>
  <meta name="description" content="Portafolio de David: arquitectura modular, DDD, ADRs narrativos, y ecosistema de Spring." />
  <style>
    :root {
      --bg: #0f1221;
      --card: #171a2e;
      --text: #e6e9f2;
      --muted: #a7abc4;
      --accent: #63e6be;
      --accent2: #8be9fd;
      --danger: #ff6b6b;
      --shadow: 0 6px 20px rgba(0,0,0,0.25);
    }
    .light {
      --bg: #fafbff;
      --card: #ffffff;
      --text: #1c2237;
      --muted: #506080;
      --accent: #3bbf9b;
      --accent2: #2a9df4;
      --danger: #e64949;
      --shadow: 0 8px 24px rgba(27, 40, 75, 0.12);
    }
    html, body { height: 100%; }
    body {
      margin: 0;
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Noto Sans", "Liberation Sans", sans-serif;
      background: radial-gradient(1200px 800px at 80% -20%, rgba(99, 230, 190, 0.12), transparent 40%),
                  radial-gradient(1200px 800px at -20% 100%, rgba(139, 233, 253, 0.12), transparent 40%),
                  var(--bg);
      color: var(--text);
      line-height: 1.6;
    }
    .container {
      width: 100%;
      max-width: 1080px;
      margin: 0 auto;
      padding: 0 20px;
    }
    header {
      position: sticky;
      top: 0;
      background: linear-gradient(0deg, rgba(15,18,33,0.6), rgba(15,18,33,0.9));
      backdrop-filter: blur(8px);
      border-bottom: 1px solid rgba(255,255,255,0.06);
      z-index: 10;
    }
    nav {
      display: flex; align-items: center; justify-content: space-between;
      height: 64px;
    }
    .brand {
      display: flex; align-items: center; gap: 12px; font-weight: 700; letter-spacing: 0.2px;
    }
    .brand .logo {
      width: 28px; height: 28px; display: inline-flex; align-items: center; justify-content: center;
      border-radius: 8px; background: linear-gradient(135deg, var(--accent), var(--accent2));
      color: #0b0f1f; font-size: 16px; font-weight: 800;
      box-shadow: var(--shadow);
    }
    .nav-links a {
      color: var(--text); text-decoration: none; margin-left: 18px; font-weight: 600;
      padding: 8px 12px; border-radius: 8px;
    }
    .nav-links a:hover { background: rgba(255,255,255,0.06); }
    .toggle {
      display: inline-flex; gap: 8px; align-items: center; cursor: pointer; font-weight: 600;
      color: var(--muted); border: 1px solid rgba(255,255,255,0.1); padding: 6px 10px; border-radius: 10px;
    }
    .hero {
      padding: 64px 0 36px;
    }
    .hero-card {
      background: linear-gradient(180deg, rgba(255,255,255,0.04), rgba(255,255,255,0.02));
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 18px; box-shadow: var(--shadow);
      padding: 28px;
      display: grid; grid-template-columns: 1.2fr 0.8fr; gap: 20px;
    }
    .hero h1 { font-size: 34px; margin: 0 0 8px; letter-spacing: 0.2px; }
    .hero p { color: var(--muted); margin: 0 0 18px; }
    .badges { display: flex; flex-wrap: wrap; gap: 10px; margin: 18px 0; }
    .badge {
      display: inline-flex; align-items: center; gap: 8px;
      background: rgba(99, 230, 190, 0.12); color: var(--accent);
      border: 1px solid rgba(99, 230, 190, 0.35);
      padding: 8px 12px; border-radius: 999px; font-weight: 700; font-size: 13px;
    }
    .badge.spring { background: rgba(42, 157, 244, 0.12); color: var(--accent2); border-color: rgba(42,157,244,0.35); }
    .actions { display: flex; gap: 12px; flex-wrap: wrap; margin-top: 8px; }
    .btn {
      display: inline-flex; align-items: center; gap: 10px;
      text-decoration: none; font-weight: 700;
      padding: 10px 14px; border-radius: 12px; border: 1px solid rgba(255,255,255,0.1);
      color: var(--text);
    }
    .btn.primary { background: linear-gradient(135deg, var(--accent), var(--accent2)); color: #0b0f1f; border: none; }
    .btn:hover { filter: brightness(1.05); transform: translateY(-1px); transition: all 160ms ease; }
    .card {
      background: var(--card); border-radius: 16px; box-shadow: var(--shadow);
      border: 1px solid rgba(255,255,255,0.08); padding: 22px;
    }
    section { padding: 28px 0; }
    .grid {
      display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px;
    }
    h2 { margin: 0 0 12px; font-size: 24px; letter-spacing: 0.2px; }
    h3 { margin: 0 0 10px; font-size: 18px; }
    .meta { color: var(--muted); font-size: 13px; }
    .list { display: grid; gap: 12px; }
    .list-item {
      display: flex; align-items: flex-start; gap: 12px;
      background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.08);
      padding: 12px; border-radius: 12px;
    }
    .pill {
      display: inline-block; padding: 6px 10px; border-radius: 999px;
      background: rgba(255,255,255,0.06); border: 1px solid rgba(255,255,255,0.1);
      font-size: 12px; color: var(--muted); margin-right: 6px;
    }
    .footer {
      margin-top: 14px; padding: 18px 0; color: var(--muted); font-size: 13px;
      border-top: 1px solid rgba(255,255,255,0.08);
    }
    .socials { display: flex; gap: 10px; flex-wrap: wrap; }
    .socials a {
      display: inline-flex; align-items: center; gap: 8px;
      color: var(--text); text-decoration: none; padding: 8px 10px;
      border: 1px solid rgba(255,255,255,0.1); border-radius: 10px;
    }
    .avatar {
      width: 100%; min-height: 160px; border-radius: 14px;
      background: linear-gradient(135deg, rgba(99,230,190,0.18), rgba(139,233,253,0.18));
      border: 1px solid rgba(255,255,255,0.1);
      display: grid; place-items: center; color: #0b0f1f; font-weight: 800; font-size: 54px;
      box-shadow: var(--shadow);
    }
    @media (max-width: 900px) { .grid { grid-template-columns: repeat(2, 1fr); } }
    @media (max-width: 640px) {
      .hero-card { grid-template-columns: 1fr; }
      .grid { grid-template-columns: 1fr; }
      nav { flex-wrap: wrap; gap: 10px; height: auto; padding: 12px 0; }
      .nav-links { width: 100%; display: flex; flex-wrap: wrap; gap: 8px; }
    }
  </style>
</head>
<body>
  <header>
    <div class="container">
      <nav>
        <div class="brand">
          <div class="logo">D</div>
          <div>David — Arquitecto de software</div>
        </div>
        <div class="nav-links">
          <a href="#proyectos">Proyectos</a>
          <a href="#habilidades">Habilidades</a>
          <a href="#podcasts">Podcasts</a>
          <a href="#adrs">ADRs</a>
          <a href="#contacto">Contacto</a>
        </div>
        <button class="toggle" id="themeToggle" aria-label="Cambiar tema">🌙 Modo</button>
      </nav>
    </div>
  </header>

  <main class="container">
    <section class="hero">
      <div class="hero-card">
        <div>
          <h1>Arquitectura modular, DDD y ecosistema Spring</h1>
          <p>
            Soy arquitecto y desarrollador Java. Diseño sistemas clínico-administrativos con enfoque en agregados,
            separación hexagonal y documentación estratégica (ADRs narrativos, guías y rule discovery).
          </p>
          <div class="badges">
            <span class="badge">Java 17+</span>
            <span class="badge spring">Spring Boot</span>
            <span class="badge spring">Spring Security</span>
            <span class="badge">Hibernate/JPA</span>
            <span class="badge">REST + JSON</span>
            <span class="badge">DDD / ADRs</span>
          </div>
          <div class="actions">
            <a class="btn primary" href="#proyectos">Ver proyectos</a>
            <a class="btn" href="#habilidades">Stack y experiencia</a>
          </div>
        </div>
        <div>
          <div class="avatar" aria-label="Avatar de David">D</div>
          <div class="socials" style="margin-top:12px;">
            <a href="https://github.com/tu-usuario" target="_blank" rel="noopener">GitHub</a>
            <a href="https://www.linkedin.com/in/tu-perfil" target="_blank" rel="noopener">LinkedIn</a>
            <a href="https://twitter.com/tu-usuario" target="_blank" rel="noopener">Twitter</a>
            <a href="mailto:tu-email@dominio.com">Email</a>
          </div>
        </div>
      </div>
    </section>

    <section id="proyectos">
      <h2>Proyectos destacados</h2>
      <div class="grid">
        <article class="card">
          <h3>Clínica Modular — Agenda y Facturación</h3>
          <p class="meta">Java, Spring Boot, DDD, ADRs, Hexagonal</p>
          <p>
            Sistema experimental clínico-administrativo con agregados de Agenda, Facturación y Pagos. Exhibe decisiones
            arquitectónicas con ADRs enlazados y separación de dominios.
          </p>
          <div>
            <span class="pill">Aggregate: Appointment</span>
            <span class="pill">Billing/Invoice</span>
            <span class="pill">Payments</span>
          </div>
          <div class="actions" style="margin-top:10px;">
            <a class="btn primary" href="https://github.com/tu-usuario/tu-repo">Repositorio</a>
            <a class="btn" href="#adrs">ADRs</a>
          </div>
        </article>

        <article class="card">
          <h3>Spring Security — Roles y Ética de errores</h3>
          <p class="meta">Spring Security, I18n, Hierarchies</p>
          <p>
            Implementación de jerarquías de excepciones con mensajes internacionalizados y códigos semánticos.
            Demuestra diseño ético de errores y trazabilidad.
          </p>
          <div>
            <span class="pill">I18n</span>
            <span class="pill">ErrorCatalog</span>
            <span class="pill">DTO Separation</span>
          </div>
          <div class="actions" style="margin-top:10px;">
            <a class="btn primary" href="https://github.com/tu-usuario/otro-repo">Repositorio</a>
            <a class="btn" href="#habilidades">Stack</a>
          </div>
        </article>

        <article class="card">
          <h3>Proyecciones contables — Plan de Cuentas</h3>
          <p class="meta">Java, JPA, Reporting</p>
          <p>
            Modelado de reportes contables con proyecciones y agregados financieros, acompañados de ADRs y documentación de reglas.
          </p>
          <div>
            <span class="pill">Ledger/Journal</span>
            <span class="pill">Read Models</span>
            <span class="pill">ADR Links</span>
          </div>
          <div class="actions" style="margin-top:10px;">
            <a class="btn primary" href="https://github.com/tu-usuario/repo-contable">Repositorio</a>
            <a class="btn" href="#adrs">ADRs</a>
          </div>
        </article>
      </div>
    </section>

    <section id="habilidades">
      <h2>Habilidades técnicas</h2>
      <div class="grid">
        <div class="card">
          <h3>Back-end y arquitectura</h3>
          <div class="list">
            <div class="list-item">
              <strong>Java & JVM:</strong> Java 17+, Streams, Records, testing (JUnit/AssertJ).
            </div>
            <div class="list-item">
              <strong>Spring:</strong> Boot, Web, Security, Data JPA, Validation, Actuator.
            </div>
            <div class="list-item">
              <strong>Arquitectura:</strong> DDD, agregados, separación hexagonal, DTOs y módulos.
            </div>
            <div class="list-item">
              <strong>Persistencia:</strong> JPA/Hibernate, perfiles, migraciones (Flyway/Liquibase).
            </div>
          </div>
        </div>
        <div class="card">
          <h3>Diseño y documentación</h3>
          <div class="list">
            <div class="list-item">
              <strong>ADRs:</strong> decisiones narrativas con contexto, consecuencias y estado.
            </div>
            <div class="list-item">
              <strong>Guías:</strong> README orientado a reclutadores, rule discovery, glosarios.
            </div>
            <div class="list-item">
              <strong>Calidad:</strong> convenciones, ética de errores, internacionalización.
            </div>
          </div>
        </div>
        <div class="card">
          <h3>DevOps y exposición</h3>
          <div class="list">
            <div class="list-item">
              <strong>CI/CD:</strong> GitHub Actions (build/test), SonarLint local.
            </div>
            <div class="list-item">
              <strong>Exhibición:</strong> GitHub Pages, portafolio curado, releases etiquetadas.
            </div>
            <div class="list-item">
              <strong>Demo:</strong> perfiles de aplicación, seeds y endpoints de muestra.
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="podcasts">
      <h2>Podcasts y charlas</h2>
      <div class="grid">
        <article class="card">
          <h3>DDD sin ceremonia</h3>
          <p class="meta">Podcast • Diseño de agregados y valor narrativo de ADRs</p>
          <p>
            Conversación sobre cómo eliminar redundancia en modelos de dominio y hacer que la documentación cuente la evolución real.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://enlace-al-podcast">Escuchar</a>
            <a class="btn" href="#adrs">Ver ADRs</a>
          </div>
        </article>
        <article class="card">
          <h3>Ética de errores y i18n</h3>
          <p class="meta">Podcast • Jerarquías de excepciones y semántica</p>
          <p>
            Cómo diseñar errores que enseñen y guíen, con catálogos internacionalizados y códigos consistentes.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://enlace-al-podcast">Escuchar</a>
            <a class="btn" href="#habilidades">Stack</a>
          </div>
        </article>
        <article class="card">
          <h3>Proyecciones contables</h3>
          <p class="meta">Charla • Reporting con agregados</p>
          <p>
            Modelos contables como piezas expositivas: planes de cuentas, balances y trazabilidad.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://enlace-a-la-charla">Ver</a>
            <a class="btn" href="#proyectos">Proyecto</a>
          </div>
        </article>
      </div>
    </section>

    <section id="adrs">
      <h2>ADRs y documentación</h2>
      <div class="grid">
        <article class="card">
          <h3>Índice de decisiones</h3>
          <p class="meta">Evolución arquitectónica</p>
          <p>
            Un único documento narrativo que unifica ADRs clave: separación de DTOs, eliminación de agregados innecesarios,
            convenciones de error y módulos.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://github.com/tu-usuario/tu-repo/blob/main/docs/ADRs.md">Ver índice</a>
            <a class="btn" href="#proyectos">Proyectos</a>
          </div>
        </article>
        <article class="card">
          <h3>Guías para reclutadores</h3>
          <p class="meta">README narrativo</p>
          <p>
            Guía breve y clara para entender el sistema, cómo correrlo y qué decisiones lo hacen interesante.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://github.com/tu-usuario/tu-repo">Repositorio</a>
            <a class="btn" href="#contacto">Contacto</a>
          </div>
        </article>
        <article class="card">
          <h3>Rule discovery</h3>
          <p class="meta">Dominios: Agenda, Facturación, Pagos</p>
          <p>
            Documentos estandarizados con reglas, invariantes y ejemplos para facilitar comprensión y contribución.
          </p>
          <div class="actions">
            <a class="btn primary" href="https://github.com/tu-usuario/tu-repo/tree/main/docs/rules">Ver reglas</a>
          </div>
        </article>
      </div>
    </section>

    <section id="contacto">
      <h2>Contacto</h2>
      <div class="card">
        <p>
          ¿Te interesa conversar sobre arquitectura, DDD y Spring? Estoy abierto a colaboraciones, mentorías y oportunidades.
        </p>
        <div class="socials">
          <a href="mailto:tu-email@dominio.com">Email</a>
          <a href="https://www.linkedin.com/in/tu-perfil" target="_blank" rel="noopener">LinkedIn</a>
          <a href="https://github.com/tu-usuario" target="_blank" rel="noopener">GitHub</a>
        </div>
      </div>
    </section>

    <div class="footer">
      © 2026 David — Portafolio experimental • Java & Spring • Hecho con cariño y rigor
    </div>
  </main>

  <script>
    // Toggle de tema (oscuro/claro)
    const root = document.documentElement;
    const toggle = document.getElementById('themeToggle');
    const stored = localStorage.getItem('theme');
    if (stored === 'light') root.classList.add('light');
    toggle.addEventListener('click', () => {
      root.classList.toggle('light');
      localStorage.setItem('theme', root.classList.contains('light') ? 'light' : 'dark');
    });

    // Scroll suave para anclas
    document.querySelectorAll('a[href^="#"]').forEach(a => {
      a.addEventListener('click', e => {
        const id = a.getAttribute('href').slice(1);
        const el = document.getElementById(id);
        if (el) {
          e.preventDefault();
          el.scrollIntoView({ behavior: 'smooth', block: 'start' });
        }
      });
    });
  </script>
</body>
</html>
