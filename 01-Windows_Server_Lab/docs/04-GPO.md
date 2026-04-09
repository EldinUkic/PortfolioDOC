<h1 align="center">⚙️ Gruppenrichtlinien (GPO)</h1>

<p align="center">
Konfiguration und Verifikation von Gruppenrichtlinien (GPOs) zur zentralen Verwaltung der Active Directory Umgebung.
</p>

<hr style="border: none; height: 5px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🧠 Projektziel

In diesem Projekt habe ich in einer Active-Directory-Umgebung Gruppenrichtlinien (GPOs) eingerichtet, um Benutzer und Computersysteme zentral zu verwalten und abzusichern.

**Ziele:**

- zentrale Verwaltung aller Clients
- einheitliche Sicherheitsrichtlinien
- Reduzierung manueller Konfiguration
- klare Struktur und Nachvollziehbarkeit

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🧱 Funktionsweise (einfach erklärt)

GPOs funktionieren wie automatische Regeln:

1. GPO wird erstellt
2. GPO wird mit einer OU verknüpft
3. Benutzer oder Computer bekommen die Regeln automatisch
4. Anwendung erfolgt beim Login oder Neustart

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔗 Verknüpfung mit OUs

<div style="display:flex; gap:20px; align-items:center; flex-wrap:wrap;">

<div style="flex:1; min-width:250px;">

| OU        | GPO                 | Zweck                  |
| --------- | ------------------- | ---------------------- |
| Users     | Password Policy     | Passwort-Sicherheit    |
| Computers | Security Baseline   | Systemabsicherung      |
| Clients   | Client Restrictions | Benutzer-Einschränkung |

📌 GPOs wurden getrennt nach Benutzer- und Computerobjekten angewendet.

⚠️ **Wichtiger Hinweis:**
Passwort-Richtlinien funktionieren korrekt nur über die **Default Domain Policy** oder Fine-Grained Password Policies – nicht über eine normale OU-GPO.

</div>

<div style="flex:1; min-width:250px;">

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

</div>

</div>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔐 GPO 1: Passwort-Richtlinie

<div style="display:flex; gap:20px; flex-wrap:wrap;">

<div style="flex:1; min-width:250px;">

### Einstellungen

- Passwort-Komplexität: **Aktiviert**
- Minimale Passwortlänge: **12 Zeichen**
- Passwort-Verlauf: **10 Passwörter**
- Maximales Passwortalter: **90 Tage**
- Minimales Passwortalter: **1 Tag**

📌 Ziel: Sichere Passwörter erzwingen und Angriffe erschweren

⚠️ **Fachlicher Hinweis:**
Diese Richtlinie wurde als **Domain Password Policy** umgesetzt (Default Domain Policy).

</div>

<div style="flex:1; min-width:250px;">

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

</div>

</div>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 💻 GPO 2: Security Baseline

<div style="display:flex; gap:20px; flex-wrap:wrap;">

<div style="flex:1; min-width:250px;">

### Einstellungen

- Zugriff auf Systemsteuerung eingeschränkt
- CMD deaktiviert
- Task-Manager eingeschränkt

📌 Ziel: Benutzer können keine kritischen Systemeinstellungen verändern

</div>

<div style="flex:1; min-width:250px;">

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

</div>

</div>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🚫 GPO 3: Client Restrictions

<div style="display:flex; gap:20px; flex-wrap:wrap;">

<div style="flex:1; min-width:250px;">

### Einstellungen

- Desktop-Einstellungen eingeschränkt
- USB-Nutzung deaktiviert (optional)
- Softwareinstallation eingeschränkt

📌 Ziel: Einheitliche und kontrollierte Client-Umgebung

</div>

<div style="flex:1; min-width:250px;">

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

</div>

</div>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔄 Anwendung der Richtlinien

```cmd
gpupdate /force
```

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔍 Verifikation (entscheidend)

```cmd
gpresult /r
```

👉 Zeigt alle angewendeten Gruppenrichtlinien

<div style="display:flex; gap:20px; flex-wrap:wrap;">

<div style="flex:1; min-width:250px;">

✔️ GPO funktioniert, wenn:

- deine GPO im Ergebnis erscheint
- Einstellungen am Client sichtbar sind

</div>

<div style="flex:1; min-width:250px;">

<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

</div>

</div>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## ✅ Praktischer Nachweis (sehr wichtig)

Zusätzlich habe ich überprüft, dass die Richtlinien im Alltag wirklich greifen.

**Beispiele:**

- Systemsteuerung blockiert
- CMD gesperrt
- Task-Manager deaktiviert
- USB-Geräte eingeschränkt

📸 **Empfohlene Screenshots:**

- Fehlermeldung beim Öffnen der Systemsteuerung
- Blockierte CMD
- Deaktivierter Task-Manager

👉 Das zeigt klar: **Die GPOs funktionieren wirklich, nicht nur in der Theorie**

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">


<div style="background-color: #234; padding: 15px; border-left: 5px solid #38C6FF; border-radius: 5px;">
  <strong>📊 FAZIT:</strong><br><br>
Ich habe:

- Gruppenrichtlinien erstellt
- mit OUs verknüpft
- Sicherheitsrichtlinien umgesetzt
- Client-Einschränkungen konfiguriert
- Anwendung getestet (`gpupdate`)
- Funktion verifiziert (`gpresult`)

👉 Ergebnis:
Zentrale, sichere und einheitliche Verwaltung der gesamten Active-Directory-Umgebung

</div>
