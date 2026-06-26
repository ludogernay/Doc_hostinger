# 📡 Diagnostic – Panne Wifi & Services Réseau

## 📝 Objectif
Décrire les étapes pour identifier l'origine d'une panne wifi à l'hôtel et les services impactés, selon les deux infrastructures en place.

---

## 🏗️ Infrastructures en place

| Infrastructure | Périmètre |
|---|---|
| **MonacoDigital** | VMs, serveurs de données, internet via RJ45, musique d'ambiance |
| **Guest Tek** | Wifi hôtel (clients & chambres), connexion internet des TV (via bornes wifi) |

> 📍 Tous les équipements sont regroupés dans **une salle technique centralisée**.

---

## ⚠️ Signes d'alerte – Détection de la panne

- Signalement par la **réception ou les clients** (wifi inaccessible, TV sans internet)
- **LEDs éteintes ou rouges** constatées sur les équipements en salle technique

---

## 🔍 Étape 1 – Identifier les services impactés

Avant d'intervenir, déterminer ce qui ne fonctionne plus :

| Symptôme constaté | Infrastructure suspectée |
|---|---|
| Wifi clients indisponible (chambres) | **Guest Tek** |
| TV sans connexion internet | **Guest Tek** (TV connectées via bornes wifi) |
| Internet RJ45 coupé (salles de réunion, bureaux) | **MonacoDigital** |
| Musique d'ambiance coupée | **MonacoDigital** |
| Wifi **ET** TV hors ligne simultanément | **Guest Tek** en priorité |
| Tout le réseau hôtel hors ligne | Les **deux infrastructures** à vérifier |

---

## 🛠️ Étape 2 – Diagnostic en salle technique

### 🔦 Vérification visuelle des équipements

#### Côté **Guest Tek**
- [ ] Vérifier les **LEDs des bornes wifi** : vert = OK / rouge ou éteint = anomalie
- [ ] Vérifier les **LEDs du switch réseau** Guest Tek : ports actifs allumés ?
- [ ] Contrôler les **câbles RJ45** branchés sur le switch (aucun déconnecté ?)

#### Côté **MonacoDigital**
- [ ] Vérifier les **LEDs des serveurs / équipements** MonacoDigital
- [ ] Contrôler les voyants d'alimentation et de connectivité réseau

---

## 📱 Étape 3 – Test de connexion client

- Se connecter au **réseau wifi Guest Tek** depuis un smartphone ou ordinateur
- Tester l'accès à internet (ouvrir un navigateur)
- Tester depuis une **TV en chambre** si le wifi semble fonctionner

> ✅ Si la connexion fonctionne → panne résolue ou intermittente, surveiller.
> ❌ Si la connexion échoue → passer à l'étape 4.

---

## 🔄 Étape 4 – Actions correctives de premier niveau

### Côté **Guest Tek**
1. **Redémarrer les bornes wifi** concernées (débrancher / rebrancher l'alimentation)
2. **Redémarrer le switch** Guest Tek si plusieurs bornes sont en défaut
3. Attendre 2 à 3 minutes, puis retester la connexion

### Côté **MonacoDigital**
1. Vérifier l'alimentation des équipements (serveurs, routeur/gateway)
2. Redémarrer l'équipement en défaut si identifié clairement
3. Retester l'accès internet via RJ45 et la musique d'ambiance

---

## 📞 Étape 5 – Escalade support

Si la panne persiste après les actions de premier niveau, contacter le support :

| Infrastructure | Contact |
|---|---|
| **Guest Tek** | *(à compléter : numéro / email support Guest Tek)* |
| **MonacoDigital** | *(à compléter : numéro / email support MonacoDigital)* |
| **IT interne** | si@canopycannes.com – poste **5021** |

> ⚠️ Préciser lors de l'appel : les équipements concernés, les LEDs observées, et les actions déjà effectuées.

---

## ❗ Remarques
- Toujours **tester depuis un appareil client** après chaque intervention avant de clôturer.
- En cas de panne affectant à la fois le **wifi et les TV**, diagnostiquer **Guest Tek en priorité**.
- Prévenir la **réception** dès qu'une panne est confirmée et dès qu'elle est résolue.
