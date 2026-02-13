# Kukuk DevOps Abschlussprojekt

Dieses Projekt beinhaltet eine Beispielanwendung mit CI/CD und Kubernetes-Deployment.

---

## Projektübersicht

Das Projekt besteht aus einem **Spring Boot Backend** und einem **Angular Frontend**. Beide Komponenten werden über eine CI/CD-Pipeline automatisiert bereitgestellt und deployt.

Das Backend wurde zu einer vollständigen Spring-Boot-Anwendung erweitert, indem die Abhängigkeit `spring-boot-starter-web` sowie die notwendigen Annotationen hinzugefügt wurden.

Für die Pipeline wurde **GitHub Actions** anstelle von **Jenkins** verwendet, da es Probleme mit dem Jenkins-Server gab.

---

## CI/CD-Prozessbeschreibung

Die beiden Module des Projekts werden automatisiert über eine CI/CD-Pipeline bereitgestellt und deployt.

Nach jedem Push in den `main`-Branch startet der Build-Prozess automatisch.  
Für die Development-Umgebung werden Tests gebaut und ausgeführt.

---

## Beschreibung der `application.properties` und Maven-Profile

In dieser Datei befinden sich die Konfigurationen für die **Produktions-** und **Development-Umgebung**.

Über Maven-Profile werden die entsprechenden Umgebungsvariablen und Konfigurationen aktiviert.

---

## Deploymentschritte

Nach dem Build – wie in der Projektübersicht beschrieben – werden Docker-Images für beide Module erstellt.

Ein `Dockerfile` befindet sich jeweils im Root-Verzeichnis jedes Moduls.  
Die Docker-Images werden anschließend in eine Docker-Registry gepusht.

Für jedes Modul wird jeweils:

- ein Image für die **Production-Umgebung**
- ein Image für die **Development-Umgebung**

erstellt und veröffentlicht.

Diese Images werden anschließend verwendet, um die Artefakte in einem Kubernetes-Cluster zu deployen.
