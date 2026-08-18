# aap-alerts
Felles alerts og config for aap-namespacet

## ⚠️ Alerts er midlertidig deaktivert

Alle alert-reglene i `alerts-gcp.yaml` er kommentert ut, og `spec.groups` er satt til `[]`.
Dette gjelder både `dev-gcp` og `prod-gcp`. 
Alle alertene for AAP er nå samlet under samme område på Grafana:
https://grafana.nav.cloud.nais.io/alerting/list?search=namespace:%22AAP%20%28Arbeidsavklaringspenger%29%22.

Merk: `nais/deploy` gjør *apply*, ikke *prune*. Ressursen må derfor fortsatt deployes med tom
regelliste for at reglene faktisk skal fjernes fra clusteret.

### Slik skrur du alertene på igjen
1. Fjern linja `groups: []` i `alerts-gcp.yaml`.
2. Avkommenter `groups`-blokken under.
3. Fjern denne seksjonen i README.
4. Merge til `main` – deploy kjører automatisk til dev-gcp og prod-gcp.

Ruting til Slack (`alert_config_dev.yaml` / `alert_config_prod.yaml`) er uendret, så alerts fra
andre kilder (f.eks. sårbarhetsvarsler) sendes fortsatt som før.
