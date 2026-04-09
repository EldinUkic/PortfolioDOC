<h1 align="center">🌐 Netzwerk & Dienste</h1>

<p align="center">
  Detaillierte Beschreibung der Netzwerkarchitektur sowie der zentralen Netzwerkdienste DNS und DHCP innerhalb der simulierten Unternehmensumgebung.
</p>

<hr style="border: none; height: 5px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

<div style="background-color: #00334d; border-left: 6px solid #38C6FF; padding: 14px 18px; margin: 20px 0; border-radius: 8px; color: #d9f6ff;">
<strong>Hinweis:</strong><br>
Das Netzwerk ist bewusst einfach und übersichtlich aufgebaut, um typische Unternehmensdienste wie DNS, DHCP und die Kommunikation zwischen Client und Server realitätsnah abzubilden.
</div>

## 🧠 Zielsetzung & Architektur

Das Ziel dieses Netzwerks ist der Aufbau einer klar strukturierten und funktionalen Client-Server-Kommunikation innerhalb einer isolierten Laborumgebung. Dabei werden zentrale Netzwerkdienste über den Domain Controller bereitgestellt.

**Kern-Features:**

- **Zentrale Namensauflösung:** Interne und externe DNS-Anfragen werden über DC01 verarbeitet.
- **Automatische Adressvergabe:** Clients erhalten ihre Netzwerkkonfiguration dynamisch über DHCP.
- **Segmentierung:** Das interne Netzwerk ist logisch vom Internet getrennt.
- **Praxisnähe:** Das Setup bildet typische Grundlagen einer kleinen Unternehmensumgebung ab.

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔍 Netzwerk-Überblick

Die gesamte Kommunikation im Lab erfolgt über ein internes Netzwerk mit zentralem Server. Der Domain Controller stellt dabei die Dienste DNS und DHCP bereit und übernimmt zusätzlich die Verbindung zum Internet über einen separaten Adapter.

- **Netzwerkname:** `labnet`
- **Adressraum:** `192.168.10.0/24`
- **Zentrale Dienste:** DNS, DHCP
- **Topologie:** Client-Server-Modell mit DC01 als zentralem Knoten

### 💻 System-Matrix

| Hostname | Rolle                        | Betriebssystem      | IP-Adresse      | Besonderheit             |
| :------- | :--------------------------- | :------------------ | :-------------- | :----------------------- |
| **DC01** | DNS, DHCP, Domain Controller | Windows Server 2022 | `192.168.10.10` | Statische IP-Adresse     |
| **PC01** | Client                       | Windows 11 Pro      | DHCP            | Dynamische Konfiguration |
| **PC02** | Client                       | Windows 11 Pro      | DHCP            | Dynamische Konfiguration |


### 🗺️ Netzwerktopologie

```text
                    [Internet]
                        │
               ┌────────┴────────┐
               │  DC01 - NIC01   │
               │   NAT / Uplink  │
               └────────┬────────┘
                        │
          Internes Netzwerk: 192.168.10.0/24
                        │
        ┌───────────────┼──────────────┐
        │               │              │
┌───────┴──────┐ ┌──────┴──────┐ ┌─────┴───────┐
│     DC01     │ │    PC01     │ │    PC02     │
│192.168.10.10 │ │ DHCP Client │ │ DHCP Client │
│   statisch   │ │             │ │             │
└──────────────┘ └─────────────┘ └─────────────┘
```


</p> <hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 📡 Netzwerkkonfiguration

### 🔌 Adapter-Konzept

Der Server DC01 nutzt zwei Netzwerkadapter:

| Adapter | Typ               | Zweck                       |
| ------- | ----------------- | --------------------------- |
| NIC01   | NAT / Uplink      | Internetzugang              |
| NIC02   | Internes Netzwerk | Kommunikation im Firmennetz |

### ⚙️ IP-Konfiguration (DC01)

| Parameter        | Konfiguration |
| ---------------- | ------------- |
| IP-Adresse       | 192.168.10.10 |
| Subnetzmaske     | 255.255.255.0 |
| DNS              | 102.168.10.10 |
| Standard-Gateway | über NAT      |



<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">

## 🔎 DNS-Server

<table style="width:100%; border-collapse: collapse;">
  <tr>
    <td width="40%" valign="top">
      <table style="width:100%; border-collapse: collapse;">
      <h3 align="center">⚙️ Konfiguration</h3>
        <tr>
          <th>Einstellung</th>
          <th>Wert</th>
        </tr>
        <tr>
          <td>DNS-IP</td>
          <td>192.168.10.10</td>
        </tr>
        <tr>
          <td>Zone</td>
          <td>lab.local</td>
        </tr>
        <tr>
          <td>Forwarder</td>
          <td>externer DNS</td>
        </tr>
      </table>
    </td>
    <td width="60%" valign="top">
      <table style="width:100%; border-collapse: collapse;">
      <h3 align="center">✅ Verifikation (DNS)</h3>
        <tr>
          <th>Test</th>
          <th>Befehl</th>
          <th>Erwartetes Ergebnis</th>
        </tr>
        <tr>
          <td>Domain testen</td>
          <td><code>nslookup lab.local</code></td>
          <td>Antwort vom DNS</td>
        </tr>
        <tr>
          <td>Server testen</td>
          <td><code>nslookup dc01.lab.local</code></td>
          <td>Richtige IP-Adresse</td>
        </tr>
      </table>
    </td>
  </tr>
</table>


<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">


## 📦 DHCP-Server

<table style="width:100%; border-collapse: collapse;">
  <tr>
    <td width="40%" valign="top">
      <table style="width:100%; border-collapse: collapse;">
         <h3 align="center">⚙️ Konfiguration</h3>
        <tr>
          <th>Einstellung</th>
          <th>Wert</th>
        </tr>
        <tr>
          <td>Netzwerk</td>
          <td>192.168.10.0/24</td>
        </tr>
        <tr>
          <td>Bereich</td>
          <td>192.168.10.100 – 192.168.10.200</td>
        </tr>
        <tr>
          <td>DNS</td>
          <td>192.168.10.10</td>
        </tr>
        <tr>
          <td>Lease</td>
          <td>8 Tage</td>
        </tr>
      </table>
    </td>
    <td width="60%" valign="top">
      <table style="width:100%; border-collapse: collapse;">
        <h3 align="center">✅ Verifikation (DHCP)</h3>
        <tr>
          <th>Test</th>
          <th>Prüfung</th>
          <th>Erwartetes Ergebnis</th>
        </tr>
        <tr>
          <td>Scope aktiv</td>
          <td>DHCP-Konsole</td>
          <td>Aktiv</td>
        </tr>
        <tr>
          <td>Leases</td>
          <td>Address Leases</td>
          <td>Clients sichtbar</td>
        </tr>
        <tr>
          <td>Client-IP</td>
          <td><code>ipconfig /all</code></td>
          <td>DHCP korrekt</td>
        </tr>
      </table>
    </td>
  </tr>
</table>


<p align="center">
  <img src="../assets/" width="500" alt=" Nachweis folgt">
</p>

<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">


## ✅ Validierung der Umgebung

| Test            | Durchführung                     | Erwartetes Ergebnis       |
| --------------- | -------------------------------- | ------------------------- |
| Konnektivität   | `ping DC01`, `ping PC02`         | Beide erreichbar          |
| Namensauflösung | `nslookup dc01.lab.local` (PC01) | IP wird korrekt aufgelöst |
| DHCP            | `ipconfig /all` (PC01)           | IP + DNS vorhanden        |
| Domänenkontakt  | `echo %logonserver%` (PC01)      | \\DC01                    |


<hr style="border: none; height: 2px; background: linear-gradient(to right, transparent, #ffff, transparent); margin: 30px 0;">


<div style="background-color: #234; padding: 15px; border-left: 5px solid #38C6FF; border-radius: 5px;">
  <strong>📊 FAZIT:</strong>

  Die Netzwerkumgebung funktioniert vollständig und stabil.
  Alle Clients erhalten automatisch ihre Konfiguration, die Namensauflösung funktioniert korrekt und die Kommunikation zwischen den Systemen ist sichergestellt.

  Damit bildet das Netzwerk die Grundlage für den Betrieb der Active Directory Umgebung.
  
</div>
