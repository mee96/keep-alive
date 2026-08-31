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
  🇬🇧 <a href="README.md">English</a> &nbsp;|&nbsp; 🇪🇸 <a href="README.es.md">Castellano</a> &nbsp;|&nbsp; 🇨🇦 <b>Català</b>
</div>

<br/>

---

## 🇨🇦 Català

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;Per què existeix aquest repositori?

Els serveis en el pla gratuït de **Render** entren en mode suspensió (*sleep*) després d'uns minuts d'inactivitat, cosa que provoca que la primera petició després de l'aturada trigui força a respondre (*cold start*).

Aquest repositori resol aquest problema de forma senzilla: conté una **GitHub Action** que executa un `curl` cada 10 minuts contra els endpoints `/health` dels meus backends. D'aquesta manera es mantenen actius contínuament **sense necessitat d'infraestructura complexa ni costos addicionals**.

> ⚠️ **Nota sobre la fiabilitat:** Els esdeveniments programats (`schedule/cron`) de GitHub Actions no són 100% precisos i pateixen retards o desestimacions periòdiques segons la càrrega dels seus servidors. Com a mesura preventiva, s'utilitza en paral·lel la plataforma externa **[cron-job.org](https://cron-job.org/)** per fer pings de suport i assegurar una disponibilitat contínua.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Serveis monitoritzats

Actualment manté desperts els següents backends:

![Plántealo](https://img.shields.io/badge/Plántealo-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)
![Chat Y2K](https://img.shields.io/badge/Chat_Y2K-f4b8d4?style=flat-square&logoColor=2d1b6e)
![Conecta4](https://img.shields.io/badge/Conecta_4-a8c4f0?style=flat-square&logoColor=1b2e4b)
![SkinCareApp](https://img.shields.io/badge/SkinCare_App-b8e8d4?style=flat-square&logoColor=2d1b6e)
![BBT API](https://img.shields.io/badge/BBT_API-f0e4a0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/plant-fill.svg?color=%232FB5AE&height=18" height="16"> **[Plántealo](https://github.com/AlmaQm/Plantealo)** (`plantealo`) — [`https://plantealo.onrender.com/`](https://plantealo.onrender.com/)
* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Secretari de Portfolio](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)
* <img src="https://api.iconify.design/ph/chats-teardrop-fill.svg?color=%23FF6FA8&height=18" height="16"> **[Chat Y2K](https://github.com/mee96/Chat)** (`chat-backend-6g1r`) — [`https://chat-frontend-o57q.onrender.com/`](https://chat-frontend-o57q.onrender.com/)
* <img src="https://api.iconify.design/ph/game-controller-fill.svg?color=%235B9BD5&height=18" height="16"> **[Conecta 4](https://github.com/mee96/juego-conecta-4)** (`conecta4-backend`) — [`https://conecta4-backend.onrender.com/`](https://conecta4-backend.onrender.com/)
* <img src="https://api.iconify.design/ph/drop-fill.svg?color=%232FB5AE&height=18" height="16"> **[SkinCareApp](https://github.com/mee96/SkinCareApp)** (`skincareapp-api`) → `/health` + `/db-check` (manté actiu el MySQL compartit d'Aiven — usat per SkinCareApp, BBT i altres)
* <img src="https://api.iconify.design/ph/coffee-fill.svg?color=%23E0A63B&height=18" height="16"> **[BBT — BubbleTea API](https://github.com/mee96/BBT)** (`bbt-760x`) — [`https://bbt-760x.onrender.com/`](https://bbt-760x.onrender.com/)

També fa ping al clúster de **Qdrant Cloud** que fan servir Bunsen i Chat, els meus dos RAGs (`/collections`, autenticat amb el secret `QDRANT_API_KEY`).

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Manteniment

* **Afegir un nou backend:** Simplement afegeix una nova línia al workflow [`.github/workflows/ping.yml`](.github/workflows/ping.yml):
<pre><code>curl -sf https://el-teu-backend.onrender.com/health || true</code></pre>

* **Eliminar un backend:** Retira la línia `curl` corresponent del fitxer `ping.yml`.

<br/>

---

<div align="center">

Desenvolupat per **Carme Medina Canalda**  
*Full Stack Developer · Barcelona*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-a8c4f0?style=flat-square&logo=linkedin&logoColor=1b2e4b)](https://www.linkedin.com/in/carme-medina-canalda-250457132/)
[![Portfolio](https://img.shields.io/badge/Portfolio-c5b9f0?style=flat-square&logoColor=2d1b6e)](https://carme-portfoli.onrender.com/)

</div>
