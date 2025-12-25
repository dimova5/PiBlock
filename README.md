<div align="center">

# PiBlock 

![Java](https://img.shields.io/badge/Java-21-blue?style=for-the-badge&logo=openjdk&logoColor=white)
![Platform](https://img.shields.io/badge/Raspberry_Pi-5-c51a4a?style=for-the-badge&logo=raspberrypi&logoColor=white)
![License](https://img.shields.io/badge/Llicència-MIT-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Estat-Actiu-green?style=for-the-badge)

![Velocity](https://img.shields.io/badge/Velocity-Proxy-09add3?style=flat-square&logo=velocity&logoColor=white)
![Geyser](https://img.shields.io/badge/Geyser-Bedrock-2ecc71?style=flat-square&logo=geyser&logoColor=white)
![Paper](https://img.shields.io/badge/Paper-Server-F44336?style=flat-square&logo=papermc&logoColor=white)

**Servidors Minecraft per a Instituts: Fàcil, Ràpid i complert**

</div>

---

## 📌 Què és això?

**PiBlock** és un sistema que converteix una petita **Raspberry Pi 5** en un servidor professional de Minecraft.

La seva màgia és que permet jugar a tothom, sense importar si tenen un ordinador potent (Java) o juguen des del mòbil o la consola (Bedrock). Tot està integrat i funciona automàticament.

---

## 🏗️ Com funciona tècnicament?

A sota pots veure exactament com viatgen les paquets des de els clients fins al servidor.

```mermaid
flowchart TB
 subgraph subGraph0["Clients (Internet)"]
        J["Java Client (PC)<br>(TCP)"]
        B["Bedrock Client (Consola/Mobil)<br>(UDP)"]
        T["Tunnel Playit.gg<br>(IP diferent depenent del client)"]
  end
 subgraph subGraph1["Servidor (RP5)"]
    direction TB
        V["VELOCITY PROXY<br>Port: 25565 (TCP)<br>[Autenticacio i Gestio]"]
        G["GEYSER BRIDGE<br>Port: 19132 (UDP)<br>[Traduccio de Protocol]"]
        P["PAPER SERVER<br>Port: 30066 (TCP)<br>[Joc Principal]"]
        L["LIMBO SERVER<br>Port: 30000 (TCP)<br>[Fallback]"]
  end
    J == Connexio Estandard ==> T
    B -. Connexio Consola/Mobil .-> T
    T == Trafic Java ==> V
    T -. Trafic Bedrock .-> G
    G == |Traduccio de Paquets| ==> V
    V == Jugador Autenticat ==> P
    V -. Si Paper cau o reinicia .-> L

    L@{ shape: rect}
     J:::client
     B:::client
     T:::internet
     V:::velocity
     G:::geyser
     P:::paper
     L:::limbo
    classDef client fill:#2c3e50,stroke:white,color:white,stroke-width:2px
    classDef internet fill:#5b3fd6,stroke:white,color:white,stroke-width:2px
    classDef velocity fill:#09add3,stroke:white,color:white,stroke-width:4px
    classDef geyser fill:#2ecc71,stroke:white,color:white,stroke-width:2px
    classDef paper fill:#F44336,stroke:white,color:white,stroke-width:2px
    classDef limbo fill:#AFB42B,stroke:white,color:white,stroke-width:2px
    style subGraph1 stroke:#2962FF
```

### 💡 Explicació

Encara que el gràfic sembli complex, el procés segueix 3 passos simples:

1.  **Tunnel (Playit.gg):**
    *   Tothom entra per la mateixa porta (`Playit.gg`), sigui des de PC o Mòbil. Això evita haver de tocar la configuració del router.
    *   JAVA i BEDROCK tenen ports diferents per a connectar-se al servidor!!!

2.  **Filtre (Velocity i Geyser):**
    *   Si vens de **PC (Java)**, passes directament desde el tunnel a (`Velocity`, port 25565).
    *   Si vens de **Mòbil/Consola (Bedrock)**, parles un "idioma" diferent (UDP). Primer passes pel traductor (`Geyser`, port 19132), que converteix les teves dades perquè el porter t'entengui.

3.  **Joc (Paper o Limbo):**
    *   Un cop a dins, Velocity t'envia al servidor de joc (`Paper`, port 30066) per jugar.
    *   Si el joc s'està reiniciant o hi ha un error, en lloc d'expulsar-te, t'envia automàticament a la sala d'espera (`Limbo`, port 30000) fins que tot torni a funcionar.

---
## Instalació

- --L'instalació automatica encara esta sent desenvolupada--
  
## 🚀 Com engegar-ho

Per a engegar has d'obrir l'arxiu start_all.bat en windows, i tenim planejada una per a Linux.

```bat
start_all.bat
```
*Això obrirà automàticament tots els 4 processos necessaris en l'ordre correcte.*

---

## 👥 Equip de PiBlock

**Creat amb passió.**

[![Contribs](https://contrib.rocks/image?repo=dimova5/PiBlock)](https://github.com/dimova5/PiBlock/graphs/contributors)

<div align="center">
    <sub>Distribuït sota <b>MIT License</b></sub>
</div>
