# Analysedossier — Final Assessment

<!-- Vul elke sectie aan. Hernoem de koppen niet: de automatische controle zoekt ze.
     Screenshots zet je in docs/images/ en voeg je toe met ![beschrijving](images/bestand.png).
     Toon nooit gevoelige waarden (wachtwoorden, tokens, kubeconfig) op een screenshot. -->

## Architectuur

Beschrijving van je applicatie en een architectuurschema: cluster, nodes, namespaces, ingress/tunnel, monitoring.

## Cluster

Cloudprovider, aantal en grootte van de nodes, en hoe je de cluster aanmaakte (manueel of Terraform/OpenTofu).
Screenshot van `kubectl get nodes -o wide`.

## Deployment

Stappenplan met commando's: hoe deploy je de applicatie, en hoe kan iemand anders dit reproduceren?
Screenshot van `kubectl get pods -o wide` (pods verspreid over de nodes).

## Secrets

Welke secrets, hoe aangemaakt, hoe gebruikt in de deployments en in CI/CD (zonder waarden te tonen).

## Helm en omgevingen

Structuur van je chart; wat verschilt tussen `values-test.yaml` en `values-prod.yaml`? Screenshot van de Helm-releases per omgeving.

## Schaalbaarheid

Replicas, `topologySpreadConstraints` en je HPA. Screenshot van de HPA die opschaalt onder belasting.

## HTTPS

Traefik of Cloudflare tunnel: hoe ingesteld, en waarom deze keuze? Screenshot van de site via HTTPS.

## CI/CD

Wat doet je pipeline, wanneer draait ze, en hoe beperk je het gebruik van Actions-minuten? Screenshot van een geslaagde run.

## Monitoring

Prometheus en Grafana: wat meet je? Screenshot van je dashboard.

## Keuzes

Motivatie van je belangrijkste keuzes en hun nadelen (provider, node-sizing, Traefik vs. Cloudflare, …).
