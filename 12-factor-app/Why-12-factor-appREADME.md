# 📦 12-Factor App – Warum?

## Hintergrund

Früher waren Anwendungen stark an einzelne Server gebunden.  
Sie liefen auf einer bestimmten Maschine und waren eng mit der zugrunde liegenden Infrastruktur gekoppelt.

Typische Probleme:

- Abhängigkeit von einem bestimmten Server
- Lokale Speicherung von Session-Daten
- Konfiguration direkt im Code
- Vertikale Skalierung (mehr CPU/RAM statt mehr Instanzen)
- Downtime bei Updates oder Skalierung
- Geringe Portabilität

Wenn der Server ausfiel, war die Anwendung nicht mehr verfügbar.

---

## Moderne Anforderungen

Heute laufen Anwendungen in:

- Cloud-Umgebungen (AWS, Azure, GCP)
- Containern (Docker)
- Kubernetes-Clustern
- Serverless-Plattformen
- Multi-Cloud-Architekturen

Moderne Systeme müssen:

- hochverfügbar sein (99.99%+)
- horizontal skalierbar sein
- portabel sein
- kontinuierlich deploybar sein
- unabhängig von der Infrastruktur funktionieren

---

## Das zentrale Problem

Wenn eine Anwendung:

- lokale Dateien nutzt
- Sessions lokal speichert
- Konfiguration hart codiert
- spezielle Server-Annahmen macht

→ ist sie **nicht cloud-native**.

Solche Anwendungen lassen sich schwer skalieren, automatisieren oder in modernen Plattformen betreiben.

---

## Ziel der 12-Factor Methodik

Die 12-Factor App definiert Prinzipien, damit Anwendungen:

- **portabel** sind (laufen in jeder Umgebung)
- **stateless** sind (kein lokaler Zustand)
- **horizontal skalierbar** sind
- **Cloud-ready** sind
- sauber in CI/CD integrierbar sind

---

## Vertikale vs. Horizontale Skalierung

**Früher:**
- Mehr RAM
- Mehr CPU
- Größerer Server  
→ Vertikale Skalierung

**Heute:**
- Mehr Instanzen starten  
→ Horizontale Skalierung

Container- und Kubernetes-Umgebungen basieren auf horizontaler Skalierung.

---

## Bedeutung für DevOps

Als DevOps Engineer muss man:

- beurteilen können, ob eine Anwendung cloudfähig ist
- Infrastruktur entkoppelt betreiben
- Skalierbarkeit ermöglichen
- Continuous Deployment unterstützen

Die 12-Factor-Prinzipien sind die Grundlage für:

- Docker
- Kubernetes
- CI/CD
- Infrastructure as Code
- GitOps

---

## Fazit

Moderne Anwendungen dürfen nicht an eine einzelne Maschine gebunden sein.  
Sie müssen portabel, skalierbar und unabhängig von der Infrastruktur funktionieren.

Genau dafür existiert die 12-Factor App Methodik.
