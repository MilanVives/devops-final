# Devops & Cloud Computing — eindopdracht

Dit is jouw repository voor de **Final Assessment** van Devops & Cloud Computing (VIVES, 3SD).
De volledige opdracht staat op de cursussite.

> ⚠️ Werk in **deze** repository (`VivesMDima/2627-devops-ti-final-<jouw-username>`), die je via je eigen accept-link kreeg — niet in de template-repository waarop ze gebaseerd is.

## Snel starten

1. Kopieer `frontend/`, `backend/`, `compose.yaml` en `k8s/` uit je projectrepository (PE1/PE2) naar hier.
2. Vul `project.yaml` in, ook `live_url` (de HTTPS-URL van je productie-omgeving).
3. Bouw je Helm chart in `helm/app/`. **`templates/nodeinfo.yaml` niet verwijderen** en `/nodeinfo` via je ingress/tunnel routeren.
4. CI/CD in `.github/workflows/deploy.yml`, monitoring in `monitoring/`, eventueel Terraform in `infra/terraform/`.
5. Schrijf `docs/analysedossier.md`, screenshots in `docs/images/`.
6. Dien in: `./scripts/submit.sh` (Windows: in **Git Bash**). Je resultaat verschijnt onder **Releases**.

> **Push geweigerd met `refusing to allow an OAuth App to create or update workflow`?**
> Je token mag geen workflows wijzigen. Voeg die rechten toe met `gh auth refresh -s workflow`
> (als je met `gh` inlogt), of push via SSH.

## Links

- Productie: _vul aan_
- Test: _vul aan_
- Monitoring-dashboard: _vul aan_

## Automatische controles

De controles zijn een **vangnet**: een FAIL wijst op een probleem dat ook in de beoordeling meetelt.
Een volledige PASS garandeert geen maximumscore — de docent beoordeelt het geheel.

### F-R0: project.yaml ingevuld

`naam`, `studentennummer`, `github`, `dockerhub` en `live_url` zijn ingevuld.

### F-R1: Helm chart geldig

`helm lint` en `helm template` met `values-test.yaml` én `values-prod.yaml` slagen, de output is geldig volgens `kubeconform -strict`, en er zijn naast `nodeinfo` minstens 3 workloads.

### F-R2: Schaalbaarheid geconfigureerd

In productie: elke Deployment heeft minstens 2 replicas en `topologySpreadConstraints`, en er is een HorizontalPodAutoscaler.

### F-R3: Resources en probes

In productie heeft elke container een `readinessProbe`, `resources.requests` en `resources.limits`.

### F-R4: Geen gecommitte secrets

`gitleaks` vindt niets in de volledige Git-geschiedenis, en er staat geen `*.tfstate` in de repository.

### F-R5: CI/CD aanwezig

Een workflow in `.github/workflows/` die bij een push naar `main` (met `paths`-filter) bouwt en met Helm deployt; elke job heeft `timeout-minutes`.

### F-R6: Live via HTTPS

`live_url` antwoordt met HTTP 200 over HTTPS met een geldig certificaat.

### F-R7: Multi-node

`live_url/nodeinfo` toont minstens 3 verschillende nodes.

### F-R8: Analysedossier volledig

`docs/analysedossier.md` heeft alle verplichte koppen en minstens 8 screenshots die in de repository staan.
