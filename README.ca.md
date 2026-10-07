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
  🇬🇧 <a href="README.md">English</a> &nbsp;|&nbsp; 🇪🇸 <a href="README.es.md">Castellano</a> &nbsp;|&nbsp; 🇨🇦 <b>Català</b>
</div>

<br/>

---

## 🇨🇦 Català

### <img src="https://api.iconify.design/ph/question-fill.svg?color=%235B9BD5&height=24" height="22"> &nbsp;Per què existeix aquest repositori?

Els serveis en el pla gratuït de **Render** entren en mode suspensió (*sleep*) després d'uns minuts d'inactivitat, cosa que provoca que la primera petició després de l'aturada trigui força a respondre (*cold start*). A més, el pla gratuït té un límit mensual d'hores d'instància compartit entre tots els serveis, així que mantenir tots els backends desperts 24/7 no és sostenible.

Per això aquest repositori manté actiu només el **backend del meu portfolio**, i només en les hores en què és més probable que el visitin reclutadors: un ping a `/health` **cada 10 minuts de 08:00 a 19:00 (Europe/Madrid)**. Fora d'aquesta franja, i a la resta dels meus projectes, la primera petició pot trigar 30–60 segons mentre el servidor arrenca.

> 🕒 **Com funciona:** dues peces treballen juntes. **[cron-job.org](https://cron-job.org/)** (zona horària `Europe/Madrid`) fa ping a `/health` cada 10 minuts per mantenir el backend en calent, però no pot despertar un servei que ja està adormit (Render respon `503` sense arrencar-lo). Per això la GitHub Action d'aquest repo s'executa **un cop per hora en horari laboral**, amb reintents, per despertar-lo quan cal — al matí o després d'un ping fallit. El seu `schedule` va en UTC (`0 6-16 * * *`), així que a l'hivern la franja es desplaça una hora.

---

### <img src="https://api.iconify.design/ph/cpu-fill.svg?color=%23B372CF&height=24" height="22"> &nbsp;Serveis monitoritzats

![Bunsen](https://img.shields.io/badge/Bunsen-c5b9f0?style=flat-square&logoColor=2d1b6e)

* <img src="https://api.iconify.design/ph/robot-fill.svg?color=%23B372CF&height=18" height="16"> **[Bunsen — Secretari de Portfolio](https://github.com/mee96/portfoli.v2)** (`bunsen-backend`) — [`https://bunsen-backend.onrender.com/health`](https://bunsen-backend.onrender.com/health)

---

### <img src="https://api.iconify.design/ph/gear-six-fill.svg?color=%232FB5AE&height=24" height="22"> &nbsp;Manteniment

* **Canviar l'horari o afegir un backend:** edita el job a cron-job.org (URL `https://el-teu-backend.onrender.com/health`, cada 10 min, zona horària `Europe/Madrid`). Tingues en compte que cada backend que es manté despert consumeix hores d'instància del pla gratuït de Render.
* **Ping manual puntual:** executa el workflow [`.github/workflows/ping.yml`](.github/workflows/ping.yml) des de la pestanya Actions (*Run workflow*).

<br/>

---

<div align="center">

Desenvolupat per **Carme Medina Canalda**  
*Full Stack Developer · Barcelona*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-a8c4f0?style=flat-square&logo=linkedin&logoColor=1b2e4b)](https://www.linkedin.com/in/carme-medina-canalda-250457132/)
[![Portfolio](https://img.shields.io/badge/Portfolio-c5b9f0?style=flat-square&logoColor=2d1b6e)](https://carme-portfoli.onrender.com/)

</div>
