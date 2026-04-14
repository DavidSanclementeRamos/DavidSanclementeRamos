# 👋 Hola, soy David Stiven Sanclemente

Desarrollador Java backend enfocado en arquitectura hexagonal y DDD.  
Construí un sistema de gestión clínica como proyecto de portafolio — de cero, con errores documentados, dos refactorizaciones y más de 90 decisiones arquitectónicas registradas.  
Busco mi primera oportunidad profesional en equipos que trabajen con sistemas complejos.

📍 Colombia · 📫 [davidrsmos434@gmail.com](mailto:davidrsmos434@gmail.com) · 💼 [LinkedIn](https://linkedin.com/in/David Rsmos) · 🐙 [GitHub](https://github.com/DavidSanclementeRamos)

---

## Stack

![Java](https://img.shields.io/badge/Java-17-orange?logo=java&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.x-6DB33F?logo=spring&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?logo=springsecurity&logoColor=white)
![Hibernate](https://img.shields.io/badge/Hibernate_JPA-59666C?logo=hibernate&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker_(Testcontainers)-2496ED?logo=docker&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white)

---

## 🏥 Proyecto principal: ClinicaDefinitiva2

> Sistema de gestión clínica odontológica construido con arquitectura hexagonal y DDD.  
> Un año de desarrollo, dos refactorizaciones completas, y cada decisión importante documentada.

🔗 **[Ver repositorio](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2)** · 📖 **[Historia del proyecto](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/blob/master/STORY.md)**

### Lo que lo diferencia de un CRUD con Spring Boot

- **Arquitectura hexagonal real** — dominio puro sin importaciones de Spring, puertos y adaptadores, capas claras.
- **Dominio rico** — agregados con invariantes, Value Objects con validaciones propias, servicios de dominio para lógica cross-aggregate.
- **Autorización RBAC + ABAC** — no solo roles: también ownership, sector y especialidad determinan el acceso.
- **Manejo híbrido de errores** — `Outcome` para flujos técnicos (autenticación), excepciones para reglas de negocio (ADR-40).
- **Más de 90 ADRs** — cada decisión importante tiene contexto, alternativas evaluadas y consecuencias documentadas.
- **Evolución transparente** — incluye ADRs superados, lecciones aprendidas y material histórico como evidencia del proceso.

### Módulos

| Módulo | Descripción | Estado |
|--------|-------------|--------|
| **Actores** | Pacientes, odontólogos, guardianes, recepcionistas | ✅ Probado |
| **Agenda (Schedule)** | Turnos (Shift), disponibilidad, citas | ✅ Probado |
| **Autorización** | RBAC/ABAC híbrido, roles múltiples, permisos contextuales | ✅ Probado |
| **Autenticación** | JWT stateless, bloqueo por intentos | ⚠️ Parcial |
| **Servicios odontológicos** | Catálogo con variantes por especialidad | ⚠️ Sin pruebas de integración |
| **Facturación** | Tarifas vigentes, snapshot inmutable, DIAN simulado | ⚠️ Sin pruebas de integración |
| **Contabilidad** | Plan de cuentas (PUC), asientos, saldos iniciales | ⚠️ Sin pruebas de integración |

### Documentación destacada

- [Índice de ADRs](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/blob/master/docs/architecture/decisions/README.md) — catálogo de decisiones arquitectónicas activas, organizadas por categoría.
- [Visión general de la arquitectura](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/blob/master/docs/architecture/overview.md) — bounded contexts, capas y principios.
- [Lecciones aprendidas](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/tree/master/docs/evolution/lessons-learned) — errores cometidos, refactorizaciones y por qué se tomaron.
- [Guía de autorización](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/blob/master/docs/guides/authorization/guia-estrategia-autorizacion-security-context.md) — cómo funciona el sistema RBAC/ABAC en el proyecto.

> El proyecto es open source. Si te interesa contribuir, revisa [`CONTRIBUTING.md`](https://github.com/DavidSanclementeRamos/ClinicaDefinitiva2/blob/master/CONTRIBUTING.md) — hay tareas en todos los niveles de dificultad.

---

## ¿Qué tipo de trabajo busco?

Rol de desarrollador Java backend en un equipo donde la arquitectura sea una conversación real, no un checklist.  
Me interesa especialmente el sector salud o fintech — contextos con reglas de negocio complejas donde el modelado del dominio importa.  
Estoy en etapa de primer empleo y busco un equipo donde pueda aportar desde el primer día y seguir creciendo.

---

⭐ Si el proyecto o el enfoque te resulta útil, una estrella ayuda a que otros lo encuentren.
