# 📡 Supervision WiFi – Home Assistant
Surveille automatiquement l’état de vos appareils WiFi/Tuya et recevez des notifications Telegram dès qu’un équipement devient hors ligne.

Ce projet inclut :
- Capteur global `binary_sensor.supervision_wifi`
- Détection hors-ligne via Ping
- Alertes Telegram avec image
- Boutons interactifs (pause 5 min, 1h, 2h, 6h, 24h)
- Vue Lovelace complète
- YAML propres, organisés, prêts à l’emploi

---

## ✨ Fonctionnalités

### 🟢 Supervision automatique
Le système vérifie périodiquement si vos appareils WiFi/Tuya sont accessibles via l’intégration **Ping**.  
- **ON** → Appareil en ligne  
- **OFF** → Appareil hors ligne

### 📩 Alerte Telegram en cas de panne
Si un ou plusieurs appareils ne répondent plus, Home Assistant envoie :
- Une image
- La liste des appareils hors ligne
- Un menu interactif pour désactiver temporairement la supervision

### ⏱ Pause simple
Vous pouvez désactiver la supervision WiFi :
- 5 minutes  
- 1 heure  
- 2 heures  
- 6 heures  
- 24 heures  

Alors elle se réactivera **automatiquement**.

---

# 🛠️ Installation

## 1️⃣ Prérequis
- Home Assistant (supervised, OS, container ou Core)
- Intégration **Ping (ICMP)** activée
- Telegram Bot configuré (`telegram_bot:` dans votre configuration)
- Une image dans `/config/www/wifi.jpg`  
  *(Vous pouvez utiliser n'importe quelle image)*

---

# 📡 2️⃣ Créer les capteurs WiFi "online" (méthode recommandée)

Les capteurs `binary_sensor.*_online` sont **obligatoires** pour que la supervision fonctionne.

Voici **la méthode simple**, demandée :

---

## 🛠️ Méthode 1 — Via l'interface Home Assistant (recommandé)

1. **Paramètres → Appareils & Services**
2. Cliquez sur **"Ajouter une intégration"**
3. Recherchez **Ping**
4. Saisissez l'**adresse IP** de l'appareil
5. Donnez un **nom clair** (ex : “Thermostat Chambre Parents”)
6. Home Assistant va créer automatiquement :

binary_sensor.thermostat_chambre_parents_online


➡️ Répétez pour chaque appareil WiFi/Tuya que vous souhaitez surveiller.

⭐ **Conseil :** Pensez à réserver les adresses IP dans votre routeur pour éviter les changements.

---

## 🧱 3️⃣ Ajouter les fichiers YAML (Supervision WiFi)

Placez les fichiers dans les dossiers suivants :

homeassistant/
├── template/supervision_wifi.yaml
├── input_boolean/supervision_wifi.yaml
├── automations/wifi_alert.yaml
└── automations/wifi_disable_buttons.yaml


Ne pas oublier :
- `binary_sensor.supervision_wifi`
- L’image `wifi.jpg` dans `/config/www/`

Un exemple de `SECRETS_EXAMPLE.yaml` est fourni.

---

# 🧩 Structure du dépôt

supervision-wifi-homeassistant/
├── README.md
├── LICENSE
├── SECRETS_EXAMPLE.yaml
├── images/
├── www/
│ └── wifi.jpg (optionnel)
└── homeassistant/
  ├── template/
  │ └── supervision_wifi.yaml
  ├── input_boolean/
  │ └── supervision_wifi.yaml
  ├── automations/
  │ ├── wifi_alert.yaml
  │ └── wifi_disable_buttons.yaml
  └── entities/
  └── binary_sensor_supervision_wifi.yaml


📄 Licence
Ce projet est distribué sous licence MIT.
Vous êtes libre de l'utiliser, le modifier et le partager.

❤️ Remerciements
Merci d’utiliser ce template !
N’hésitez pas à ouvrir une Issue ou à proposer une Pull Request.
