<!-- Header estètic blau coordinat amb la teva paleta -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=a8c4f0&height=180&section=header&text=keep-alive&fontColor=1b2e4b&fontSize=38&desc=Keeping%20my%20portfolio%20backend%20warm%20on%20Render&descSize=16&descColor=1b2e4b&descAlignY=65&fontAlignY=42" width="100%" alt="keep-alive" />

[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-a8c4f0?style=for-the-badge&logo=githubactions&logoColor=1b2e4b)](https://github.com/features/actions)
&nbsp;
[![Render](https://img.shields.io/badge/Render-c5b9f0?style=for-the-badge&logo=render&logoColor=2d1b6e)](https://render.com/)
&nbsp;
[![Cron Status](https://img.shields.io/badge/Ping-Every_10_min_%C2%B7_08%3A00%E2%80%9319%3A00-b8e8d4?style=for-the-badge&logoColor=2d1b6e)](#)
&nbsp;
[![Cron-Job](https://img.shields.io/badge/Scheduler-cron--job.org-f4b8d4?style=for-the-badge&logoColor=2d1b6e)](https://cron-job.org/)

</div>

<br/>

<div align="center">
  🇬🇧 <a href="README.md">English</a> &nbsp;|&nbsp; 🇪🇸 <b>Castellano</b> &nbsp;|&nbsp; 🇨🇦 <a href="README.ca.md">Català</a>
</div>

<br/>

---

## 🇪🇸 Castellano

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;¿Por qué existe este repositorio?

Los servicios en el plan gratuito de **Render** entran en modo suspensión (*sleep*) tras unos minutos de inactividad, lo que provoca que la primera petición después del parón tarde bastante en responder (*cold start*). Además, el plan gratuito tiene un límite mensual de horas de instancia compartido entre todos los servicios, así que mantener todos los backends despiertos 24/7 no es sostenible.

Por eso este repositorio mantiene activo solo el **backend de mi portfolio**, y solo en las horas en que es más probable que lo visiten reclutadores: un ping a `/health` **cada 10 minutos de 08:00 a 19:00 (Europe/Madrid)**. Fuera de esa franja, y en el resto de mis proyectos, la primera petición puede tardar 30–60 segundos mientras el servidor arranca.

> 🕒 **Cómo funciona:** dos piezas trabajan juntas. **[cron-job.org](https://cron-job.org/)** (zona horaria `Europe/Madrid`) hace ping a `/health` cada 10 minutos para mantener el backend en caliente, pero no puede despertar un servicio que ya está dormido (Render responde `503` sin arrancarlo). Por eso la GitHub Action de este repo se ejecuta **una vez por hora en horario laboral**, con reintentos, para despertarlo cuando hace falta — por la mañana o tras un ping fallido. Su `schedule` va en UTC (`0 6-16 * * *`), así que en invierno la franja se desplaza una hora.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Servicios monitorizados

![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Portfolio Secretary](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Mantenimiento

* **Cambiar el horario o añadir un backend:** edita el job en cron-job.org (URL `https://tu-backend.onrender.com/health`, cada 10 min, zona horaria `Europe/Madrid`). Ten en cuenta que cada backend que se mantiene despierto consume horas de instancia del plan gratuito de Render.
* **Ping manual puntual:** ejecuta el workflow [`.github/workflows/ping.yml`](.github/workflows/ping.yml) desde la pestaña Actions (*Run workflow*).

<br/>

---

<div align="center">

Desenvolupat per **Carme Medina Canalda**  
*Full Stack Developer · Barcelona*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-a8c4f0?style=flat-square&logo=linkedin&logoColor=1b2e4b)](https://www.linkedin.com/in/carme-medina-canalda-250457132/)
[![Portfolio](https://img.shields.io/badge/Portfolio-c5b9f0?style=flat-square&logoColor=2d1b6e)](https://carme-portfoli.onrender.com/)

</div>
