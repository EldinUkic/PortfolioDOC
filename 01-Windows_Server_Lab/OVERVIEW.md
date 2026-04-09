<h1 align="center">🖥️ Windows Enterprise Lab</h1>

<p align="center">
  Simulation einer vollständigen Windows-Unternehmensinfrastruktur · Lernprojekt & Portfolio
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Status-In%20Entwicklung-blue?style=flat-square" />
  <img src="https://img.shields.io/badge/Windows%20Server-2022-0078D4?style=flat-square&logo=windows" />
  <img src="https://img.shields.io/badge/VirtualBox-Umgebung-183A61?style=flat-square" />
  <img src="https://img.shields.io/badge/Domain-lab.local-27ae60?style=flat-square" />
</p>

<hr style="border: none; height: 5px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

<div style="background-color: #5c4700; border-left: 6px solid #d4a017; padding: 14px 18px; margin: 20px 0; border-radius: 8px; color: #f8e7a1;">
<strong>⚠️ Hinweis:</strong><br>
Dieses Projekt befindet sich derzeit in der Entwicklungsphase. Aus diesem Grund kann die Dokumentation stellenweise unvollständig sein oder noch ergänzt werden.
</div>

## Projektübersicht

In diesem Projekt wird eine realitätsnahe Windows-Unternehmensumgebung aufgebaut und simuliert. Ziel ist es, ein funktionierendes Firmennetzwerk mit zentraler Verwaltung zu erstellen und die grundlegenden Abläufe moderner IT-Infrastrukturen praktisch zu verstehen.

Der Fokus liegt auf der Einrichtung eines Servers auf Basis von Windows Server 2022, der zentrale Dienste wie Active Directory, DNS und DHCP bereitstellt. Ergänzend dazu werden Client-Systeme mit Windows 11 Pro eingebunden, die in die Domäne integriert und zentral verwaltet werden.

Zusätzlich werden typische Aufgaben aus der Praxis umgesetzt, wie Benutzerverwaltung, Rechtevergabe sowie die Analyse und Behebung von Netzwerk- und Systemproblemen. Das Lab wird kontinuierlich erweitert, um weitere Technologien und realistische Szenarien zu integrieren und so praxisnahe IT-Kenntnisse aufzubauen.

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🗺️ Architektur-Übersicht

![Network Diagram](./assets/architektur.png)

<table>
  <tr>
    <td width="60%" valign="top">
      <h2>📘 Systembeschreibung</h2>
      <p>
        Die Architektur zeigt eine zentral verwaltete Unternehmensumgebung mit einem Domain Controller (DC01), 
        der zentrale Dienste wie Active Directory, DNS und DHCP bereitstellt.
      </p>
      <p>
        Die Clients (PC01, PC02) sind über ein internes Netzwerk verbunden und Teil der Domäne. 
        Sie beziehen ihre Netzwerkkonfiguration automatisch vom DHCP-Server und nutzen den DNS-Server 
        zur Namensauflösung.
      </p>
      <p>
        Zusätzlich verfügt der Server über eine zweite Netzwerkschnittstelle, die den Zugriff auf das Internet ermöglicht.
      </p>
    </td>
    <td width="40%" valign="top">
      <h2>⚙️ Systemdaten</h2>
      <p>
        <strong>Domain Controller:</strong> DC01<br>
        <strong>Clients:</strong> PC01, PC02<br>
        <strong>Domain:</strong> lab.local<br>
        <strong>Netzwerk:</strong> 192.168.10.0/24
      </p>
    </td>
  </tr>
</table>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

### 🛠️ Tech-Stack

| Technologie         | Verwendung                       |
| ------------------- | -------------------------------- |
| Windows Server 2022 | Domain Controller, Server-Rollen |
| Windows 11 Pro      | Client-Systeme (PC01, PC02)      |
| VirtualBox          | Virtualisierungsplattform        |
| Active Directory DS | Zentrale Benutzerverwaltung      |
| DNS / DHCP          | Netzwerkdienste                  |

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🗂️ Dokumentation

| Dokument                 | Inhalt                                                        |
| ------------------------ | ------------------------------------------------------------- |
| `01-infrastruktur.md`    | Systemübersicht, Hardware, Netzwerkkonfiguration, Domain Join |
| `02-network.md`          | Netzwerkarchitektur, DNS, DHCP, IP-Schema                     |
| `03-active-directory.md` | OU-Struktur, Benutzer, Gruppen, Verifikation                  |
| `04-GPO.md`              | Gruppenrichtlinien, Passwort-Policy, Client Restrictions      |
