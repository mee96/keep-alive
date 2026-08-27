<!-- Header estètic blau coordinat amb la teva paleta -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=a8c4f0&height=180&section=header&text=keep-alive&fontColor=1b2e4b&fontSize=38&desc=GitHub%20Action%20to%20prevent%20Render's%20cold%20starts&descSize=16&descColor=1b2e4b&descAlignY=65&fontAlignY=42" width="100%" alt="keep-alive" />

[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-a8c4f0?style=for-the-badge&logo=githubactions&logoColor=1b2e4b)](https://github.com/features/actions)
&nbsp;
[![Render](https://img.shields.io/badge/Render-c5b9f0?style=for-the-badge&logo=render&logoColor=2d1b6e)](https://render.com/)
&nbsp;
[![Cron Status](https://img.shields.io/badge/Ping_Interval-Every_10_min-b8e8d4?style=for-the-badge&logoColor=2d1b6e)](#)
&nbsp;
[![Cron-Job](https://img.shields.io/badge/Backup-cron--job.org-f4b8d4?style=for-the-badge&logoColor=2d1b6e)](https://cron-job.org/)

</div>

<br/>

<div align="center">
  <b>🇪🇸 Castellano</b> &nbsp;•&nbsp; <b>🇬🇧 English</b>
</div>

<br/>

---

## 🇪🇸 Castellano

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;¿Por qué existe este repositorio?

Los servicios en el plan gratuito de **Render** entran en modo suspensión (*sleep*) tras unos minutos de inactividad, lo que provoca que la primera petición después del parón tarde bastante en responder (*cold start*). 

Este repositorio resuelve ese problema de forma sencilla: contiene un **GitHub Action** que ejecuta un `curl` cada 10 minutos contra los endpoints `/health` de mis backends. De esta forma se mantienen activos continuamente **sin necesidad de infraestructura compleja ni costes adicionales**.

> ⚠️ **Nota sobre la fiabilidad:** Los eventos programados (`schedule/cron`) de GitHub Actions no son 100% precisos y sufren retrasos o desestimaciones periódicas según la carga de sus servidores. Como medida preventiva, se utiliza en paralelo la plataforma externa **[cron-job.org](https://cron-job.org/)** para realizar pings de respaldo y asegurar una disponibilidad continua.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Servicios monitorizados

Actualmente mantiene despiertos los siguientes backends:

![Plántealo](https://img.shields.io/badge/Plántealo-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)
![Chat Y2K](https://img.shields.io/badge/Chat_Y2K-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Conecta4](https://img.shields.io/badge/Conecta_4-a8c4f0?style=flat-square&logoColor=1b2e4b)
![SkinCareApp](https://img.shields.io/badge/SkinCare_App-b8e8d4?style=flat-square&logoColor=2d1b6e)
![BBT API](https://img.shields.io/badge/BBT_API-f0e4a0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/plant-fill.svg?color=%232FB5AE&height=18" height="16"> **[Plántealo](https://github.com/AlmaQm/Plantealo)** (`plantealo`) — [`https://plantealo.onrender.com/`](https://plantealo.onrender.com/)
* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Portfolio Secretary](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)
* <img src="https://api.iconify.design/ph/chats-teardrop-fill.svg?color=%23FF6FA8&height=18" height="16"> **[Chat Y2K](https://github.com/mee96/Chat)** (`chat-backend-6g1r`) — [`https://chat-frontend-o57q.onrender.com/`](https://chat-frontend-o57q.onrender.com/)
* <img src="https://api.iconify.design/ph/game-controller-fill.svg?color=%235B9BD5&height=18" height="16"> **[Conecta 4](https://github.com/mee96/juego-conecta-4)** (`conecta4-backend`) — [`https://conecta4-backend.onrender.com/`](https://conecta4-backend.onrender.com/)
* <img src="https://api.iconify.design/ph/drop-fill.svg?color=%232FB5AE&height=18" height="16"> **[SkinCareApp](https://github.com/mee96/SkinCareApp)** (`skincareapp-api`) — [`https://skincareapp-api.onrender.com/health`](https://skincareapp-api.onrender.com/health)
* <img src="https://api.iconify.design/ph/coffee-fill.svg?color=%23E0A63B&height=18" height="16"> **[BBT — BubbleTea API](https://github.com/mee96/BBT)** (`bbt-760x`) — [`https://bbt-760x.onrender.com/`](https://bbt-760x.onrender.com/)

También hace ping al clúster de **Qdrant Cloud** que usan Bunsen y Chat, mis dos RAGs (`/collections`, autenticado con el secreto `QDRANT_API_KEY`).

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Mantenimiento

* **Añadir un nuevo backend:** Simplemente añade una nueva línea al workflow [`.github/workflows/ping.yml`](.github/workflows/ping.yml):
<pre><code>curl -sf https://tu-backend.onrender.com/health || true</code></pre>

* **Eliminar un backend:** Retira la línea `curl` correspondiente del archivo `ping.yml`.

<br/>

---

## 🇬🇧 English

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;Why does this repository exist?

Free tier services on **Render** go to sleep after a few minutes of inactivity, resulting in high latency on the first request (*cold start*). 

This repository solves that issue effortlessly: it hosts a **GitHub Action** that performs a `curl` ping every 10 minutes to the `/health` endpoints of my deployed backends. This keeps them warm and ready **without requiring third-party infrastructure or extra costs**.

> ⚠️ **Reliability Note:** Scheduled GitHub Actions (`schedule/cron`) do not execute with 100% precision and can be delayed or skipped depending on server load. As a preventive fallback, **[cron-job.org](https://cron-job.org/)** is configured in parallel to handle backup pings and ensure seamless uptime.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Monitored Services

Currently keeping the following backends active:

![Plántealo](https://img.shields.io/badge/Plántealo-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)
![Chat Y2K](https://img.shields.io/badge/Chat_Y2K-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Conecta4](https://img.shields.io/badge/Conecta_4-a8c4f0?style=flat-square&logoColor=1b2e4b)
![SkinCareApp](https://img.shields.io/badge/SkinCare_App-b8e8d4?style=flat-square&logoColor=2d1b6e)
![BBT API](https://img.shields.io/badge/BBT_API-f0e4a0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/plant-fill.svg?color=%232FB5AE&height=18" height="16"> **[Plántealo](https://github.com/AlmaQm/Plantealo)** (`plantealo`) — [`https://plantealo.onrender.com/`](https://plantealo.onrender.com/)
* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Portfolio Secretary](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)
* <img src="https://api.iconify.design/ph/chats-teardrop-fill.svg?color=%23FF6FA8&height=18" height="16"> **[Chat Y2K](https://github.com/mee96/Chat)** (`chat-backend-6g1r`) — [`https://chat-frontend-o57q.onrender.com/`](https://chat-frontend-o57q.onrender.com/)
* <img src="https://api.iconify.design/ph/game-controller-fill.svg?color=%235B9BD5&height=18" height="16"> **[Conecta 4](https://github.com/mee96/juego-conecta-4)** (`conecta4-backend`) — [`https://conecta4-backend.onrender.com/`](https://conecta4-backend.onrender.com/)
* <img src="https://api.iconify.design/ph/drop-fill.svg?color=%232FB5AE&height=18" height="16"> **[SkinCareApp](https://github.com/mee96/SkinCareApp)** (`skincareapp-api`) — [`https://skincareapp-api.onrender.com/health`](https://skincareapp-api.onrender.com/health)
* <img src="https://api.iconify.design/ph/coffee-fill.svg?color=%23E0A63B&height=18" height="16"> **[BBT — BubbleTea API](https://github.com/mee96/BBT)** (`bbt-760x`) — [`https://bbt-760x.onrender.com/`](https://bbt-760x.onrender.com/)

It also pings the **Qdrant Cloud** cluster used by Bunsen and Chat, my two RAGs (`/collections`, authenticated via the `QDRANT_API_KEY` secret).

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Maintenance

* **Add a new backend:** Add a new line to the [`.github/workflows/ping.yml`](.github/workflows/ping.yml) workflow file:
<pre><code>curl -sf https://your-backend.onrender.com/health || true</code></pre>

* **Remove a backend:** Delete the corresponding `curl` line from `ping.yml`.

<br/>

---

<div align="center">

Desenvolupat per **Carme Medina Canalda**  
*Full Stack Developer · Barcelona*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-a8c4f0?style=flat-square&logo=linkedin&logoColor=1b2e4b)](https://www.linkedin.com/in/carme-medina-canalda-250457132/)
[![Portfolio](https://img.shields.io/badge/Portfolio-c5b9f0?style=flat-square&logoColor=2d1b6e)](https://carme-portfoli.onrender.com/)

</div>
