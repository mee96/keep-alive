# keep-alive

Aquest repositori no fa res per si mateix: només conté un GitHub Action
([`.github/workflows/ping.yml`](.github/workflows/ping.yml)) que fa un `curl` cada 10 minuts
contra els endpoints `/health` de diversos backends desplegats a Render (pla gratuït):

- Bunsen (`bunsen-backend`)
- Chat (`chat-backend-6g1r`)
- Connect4 (`conecta4-backend`)
- SkinCareApp (`skincareapp-api`)
- BBT (`bbt-760x`)

A més, fa una petició a l'endpoint `/collections` del clúster de **Qdrant Cloud**
que fa servir el backend de Bunsen, per evitar que el clúster (pla gratuït) es
pausi per inactivitat. Aquesta petició necessita una API key, que es passa com
a secret del repositori (`QDRANT_API_KEY`) i mai apareix en text pla al YAML.

## Per què existeix

Render "adorm" els serveis gratuïts després d'uns minuts d'inactivitat, i el primer
request després de dormir triga molt (cold start). Aquest workflow simplement manté
els serveis desperts fent-los una petició periòdica, sense necessitat de cap
infraestructura ni cost addicional (s'executa a GitHub Actions).

Si en algun moment un backend deixa de necessitar-se, cal treure el seu `curl`
corresponent de `ping.yml`. Si es desplega un backend nou a Render, cal afegir-hi
una línia nova amb la mateixa fórmula: `curl -sf <url>/health || true`.
