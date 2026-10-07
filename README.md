<!-- Header estètic blau coordinat amb la teva paleta -->
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=a8c4f0&height=180&section=header&text=keep-alive&fontColor=1b2e4b&fontSize=38&desc=Keeping%20my%20portfolio%20backend%20warm%20on%20Render&descSize=16&descColor=1b2e4b&descAlignY=65&fontAlignY=42" width="100%" alt="keep-alive" />

[![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-a8c4f0?style=for-the-badge&logo=githubactions&logoColor=1b2e4b)](https://github.com/features/actions)
&nbsp;
[![Render](https://img.shields.io/badge/Render-c5b9f0?style=for-the-badge&logo=render&logoColor=2d1b6e)](https://render.com/)
&nbsp;
[![Cron Status](https://img.shields.io/badge/Ping-Every_10_min_%C2%B7_08%3A30%E2%80%9319%3A00-b8e8d4?style=for-the-badge&logoColor=2d1b6e)](#)
&nbsp;
[![Cron-Job](https://img.shields.io/badge/Scheduler-cron--job.org-f4b8d4?style=for-the-badge&logoColor=2d1b6e)](https://cron-job.org/)

</div>

<br/>

<div align="center">
  🇬🇧 <b>English</b> &nbsp;|&nbsp; 🇪🇸 <a href="README.es.md">Castellano</a> &nbsp;|&nbsp; 🇨🇦 <a href="README.ca.md">Català</a>
</div>

<br/>

---

## 🇬🇧 English

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;Why does this repository exist?

Free tier services on **Render** go to sleep after a few minutes of inactivity, so the first request after a pause takes a while to respond (*cold start*). The free tier also has a monthly limit of instance hours shared by all services, so keeping every backend awake 24/7 isn't sustainable.

That's why this repository keeps only my **portfolio backend** warm, and only during the hours recruiters are most likely to visit: a ping to `/health` **every 10 minutes from 08:30 to 19:00 (Europe/Madrid)**. Outside that window, and for the rest of my projects, the first request may take 30–60 seconds while the server wakes up.

> 🕒 **Scheduler:** the ping runs on **[cron-job.org](https://cron-job.org/)**, configured with the `Europe/Madrid` timezone. GitHub Actions' `schedule` runs in UTC (it doesn't follow daylight saving time) and can be delayed or skipped, so the workflow in this repo only keeps a **manual trigger** (`workflow_dispatch`) for one-off pings.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Monitored Services

![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Portfolio Secretary](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Maintenance

* **Change the schedule or add a backend:** edit the job on cron-job.org (URL `https://your-backend.onrender.com/health`, every 10 min, timezone `Europe/Madrid`). Keep in mind that every backend kept awake consumes instance hours from Render's free tier.
* **One-off manual ping:** run the workflow [`.github/workflows/ping.yml`](.github/workflows/ping.yml) from the Actions tab (*Run workflow*).

<br/>

---

<div align="center">

Desenvolupat per **Carme Medina Canalda**  
*Full Stack Developer · Barcelona*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-a8c4f0?style=flat-square&logo=linkedin&logoColor=1b2e4b)](https://www.linkedin.com/in/carme-medina-canalda-250457132/)
[![Portfolio](https://img.shields.io/badge/Portfolio-c5b9f0?style=flat-square&logoColor=2d1b6e)](https://carme-portfoli.onrender.com/)

</div>
