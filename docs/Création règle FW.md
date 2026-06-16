# Créer une Règle sur Fortinet FortiGate - Guide Complet

## 📋 Introduction

Une règle de pare-feu sur Fortinet FortiGate contrôle le trafic réseau entre les interfaces (LAN, WAN, VLANs, etc.). Ce guide vous explique comment créer et configurer une règle de manière complète et détaillée.

---

## 🔐 Accéder à l'Interface de Gestion

### 1. Se connecter à FortiGate

1. Ouvrez un navigateur web en étant connecté au WIFI ADMIN
2. Allez à l'adresse IP du FortiGate (généralement `https://192.168.10.254`)
3. Entrez vos identifiants
4. Cliquez sur **Login**

> **Note :** Utilisez HTTPS pour une connexion sécurisée. Acceptez le certificat auto-signé si demandé.

### 2. Accéder à la section des Règles de Pare-feu

1. Dans le menu principal, cliquez sur **Policy & Objects**
2. Sélectionnez **Firewall Policy**
3. Vous verrez la liste des règles existantes

---

## ✨ Créer une Nouvelle Règle

### Étape 1 : Créer une Nouvelle Règle

1. Cliquez sur le bouton **Create New** (en haut à gauche)
2. Une nouvelle ligne s'ajoute au tableau des règles
3. Vous pouvez maintenant configurer les paramètres

### Étape 2 : Configurer les Paramètres Basiques

#### **Ordre de la Règle (Priority)**
- Les règles s'exécutent de haut en bas
- La première règle correspondante est appliquée
- Plus une règle est haute, plus elle a de priorité
- Vous pouvez réorganiser les règles en les glissant-déposant

#### **Nom de la Règle (Name)**
1. Cliquez sur le champ **Name**
2. Entrez un nom descriptif et clair
   - Exemple : `Allow_LAN_to_WAN`
   - Exemple : `Block_P2P_Traffic`
   - Exemple : `Allow_DNS_Query`

> **Bonne pratique :** Utilisez des noms explicites pour faciliter la maintenance future

---

## 🔄 Configurer les Interfaces

### Incoming Interface (Interface source)

1. Cliquez sur le champ **Incoming Interface**
2. Sélectionnez l'interface d'où provient le trafic
   - `port1` : Généralement WAN (Internet)
   - `port2`, `port3`, etc. : Généralement LAN
   - `VLAN100`, `VLAN200` : VLANs spécifiques
3. Cliquez sur **OK**

> **Exemple :** Si vous voulez autoriser le trafic du réseau local vers Internet, choisissez l'interface LAN

### Outgoing Interface (Interface destination)

1. Cliquez sur le champ **Outgoing Interface**
2. Sélectionnez l'interface vers laquelle va le trafic
3. Cliquez sur **OK**

> **Exemple :** Pour autoriser la sortie vers Internet, choisissez l'interface WAN

---

## 👥 Configurer les Adresses Source et Destination

### Source Address (Adresse source)

1. Cliquez sur le champ **Source Address**
2. Vous avez plusieurs options :
   - **All** : Tout le monde
   - **Sélectionner une adresse existante** : Cliquez et choisissez dans la liste
   - **Créer une nouvelle adresse** : Cliquez sur **Create Address**

#### Créer une Nouvelle Adresse Source

1. Cliquez sur **Create Address**
2. Remplissez les champs :
   - **Name** : Nom descriptif (ex : `Office_Subnet`)
   - **Type** : Choisissez le type
     - `IP/Netmask` : Pour une plage IP (ex : `192.168.1.0/24`)
     - `IP Range` : Pour une plage spécifique (ex : `192.168.1.10 - 192.168.1.20`)
     - `FQDN` : Pour un nom de domaine
   - **IP/Netmask** : Entrez l'adresse IP ou la plage
3. Cliquez sur **OK**

### Destination Address (Adresse destination)

1. Cliquez sur le champ **Destination Address**
2. Suivez le même processus que pour la source
3. Sélectionnez ou créez l'adresse de destination

> **Exemple :**
> - Source : `192.168.190.0/24` (Votre réseau interne)
> - Destination : `All` (Tout le monde sur Internet)

---

## 📡 Configurer les Services (Ports et Protocoles)

### Service / Protocol

1. Cliquez sur le champ **Service**
2. Vous pouvez :
   - **All** : Tous les ports/protocoles
   - **Sélectionner un service prédéfini** : HTTP, HTTPS, DNS, SSH, RDP, etc.
   - **Créer un service personnalisé**

#### Services Prédéfinis Courants

| Service | Port | Protocole | Utilisation |
|---------|------|-----------|------------|
| HTTP | 80 | TCP | Web non sécurisé |
| HTTPS | 443 | TCP | Web sécurisé |
| DNS | 53 | UDP/TCP | Résolution de noms |
| SSH | 22 | TCP | Accès serveur sécurisé |
| RDP | 3389 | TCP | Bureau à distance Windows |
| SMTP | 25 | TCP | Envoi d'emails |
| POP3 | 110 | TCP | Réception d'emails |
| FTP | 21 | TCP | Transfert de fichiers |
| PING | ICMP | - | Diagnostic réseau |

#### Créer un Service Personnalisé

1. Cliquez sur **Create Service**
2. Remplissez les champs :
   - **Name** : Nom du service (ex : `Custom_App_Port`)
   - **Category** : Choisissez une catégorie
   - **Protocol** : TCP, UDP, ou ICMP
   - **Destination Port Range** : Entrez le port ou la plage (ex : `8080` ou `8000-8100`)
3. Cliquez sur **OK**

---

## ✅ Configurer l'Action (Action)

### Allow ou Deny

1. Cliquez sur le champ **Action**
2. Choisissez parmi les options :
   - **Accept** : Autorise le trafic
   - **Deny** : Refuse le trafic (envoie un refus)
   - **Reject** : Refuse le trafic (sans réponse)

> **Différence :**
> - **Deny** : L'appareil reçoit un message "Connexion refusée"
> - **Reject** : Pas de réponse, plus sécurisé

---

## 📊 Options Avancées

### Logging (Journalisation)

1. Cliquez sur la ligne de la règle pour l'éditer
2. Cochez **Log Allowed Traffic** pour enregistrer les connexions acceptées
3. Cochez **Log Denied Traffic** pour enregistrer les connexions refusées
4. Accédez aux logs via **Log & Report > Firewall Traffic**

### Schedule (Planification)

1. Cliquez sur le champ **Schedule**
2. Sélectionnez un horaire :
   - **Always** : La règle s'applique 24/7
   - **Business Hours** : Uniquement pendant les heures de bureau
   - **Créer un horaire personnalisé** pour des restrictions spécifiques

### NAT (Network Address Translation)

1. Cochez **Enable NAT** si nécessaire
2. Sélectionnez le type de NAT :
   - **Source NAT (SNAT)** : Masque l'adresse IP source
   - **Destination NAT (DNAT)** : Redirige vers une adresse destination

### QoS (Quality of Service)

1. Allez dans l'onglet **QoS**
2. Activez **Enable QoS** si vous voulez contrôler la bande passante
3. Configurez :
   - **Priorité** : Haute, Normale, Basse
   - **Limite de bande passante** : Pour limiter la vitesse

---

## 🔍 Exemples de Règles Pratiques

### Exemple 1 : Autoriser le trafic LAN vers Internet

| Paramètre | Valeur |
|-----------|--------|
| **Name** | Allow_LAN_to_Internet |
| **Incoming Interface** | LAN (port2) |
| **Outgoing Interface** | WAN (port1) |
| **Source Address** | 192.168.190.0/24 |
| **Destination Address** | All |
| **Service** | All |
| **Action** | Accept |
| **Logging** | Activé |

### Exemple 2 : Autoriser l'accès SSH à un serveur spécifique

| Paramètre | Valeur |
|-----------|--------|
| **Name** | Allow_SSH_to_Server |
| **Incoming Interface** | WAN (port1) |
| **Outgoing Interface** | LAN (port2) |
| **Source Address** | All |
| **Destination Address** | 192.168.190.50 |
| **Service** | SSH (port 22) |
| **Action** | Accept |
| **Logging** | Activé |

### Exemple 3 : Bloquer un service spécifique

| Paramètre | Valeur |
|-----------|--------|
| **Name** | Block_Torrent |
| **Incoming Interface** | LAN (port2) |
| **Outgoing Interface** | WAN (port1) |
| **Source Address** | All |
| **Destination Address** | All |
| **Service** | Torrent |
| **Action** | Deny |
| **Logging** | Activé |

### Exemple 4 : Redirection de port (Port Forwarding)

| Paramètre | Valeur |
|-----------|--------|
| **Name** | Forward_HTTP_to_Server |
| **Incoming Interface** | WAN (port1) |
| **Outgoing Interface** | LAN (port2) |
| **Source Address** | All |
| **Destination Address** | 192.168.190.100 |
| **Service** | HTTP (port 80) |
| **Action** | Accept |
| **Enable NAT** | Oui (DNAT) |
| **NAT IP Address** | 192.168.190.100 |

---

## 💾 Sauvegarder et Appliquer

### Sauvegarder la Règle

1. Une fois les paramètres configurés, cliquez sur **OK** ou **Apply**
2. Un message de confirmation s'affiche
3. La règle est maintenant active

### Vérifier l'Application

1. Allez sur **Status > Dashboard**
2. Vérifiez les statistiques de trafic
3. Vérifiez les logs : **Log & Report > Firewall Traffic**

### Sauvegarder la Configuration Globale

1. Allez sur **System > Configuration > Backup**
2. Cliquez sur **Save**
3. La configuration du FortiGate est sauvegardée

---

## 🧪 Tester la Règle

### Tester une Règle Allow

1. Depuis un client du réseau, essayez d'accéder au service autorisé
   ```
   ping destination_ip
   ```
   ou
   ```
   telnet destination_ip port
   ```

2. Vérifiez les logs du FortiGate pour confirmer

### Tester une Règle Deny

1. Essayez d'accéder au service bloqué
2. Vous devriez recevoir une erreur de connexion
3. Vérifiez les logs pour voir la tentative bloquée

---

## ⚠️ Bonnes Pratiques

### Organisation des Règles

- **Placez les règles spécifiques en haut** (exemple : bloquer un IP spécifique)
- **Placez les règles générales en bas** (exemple : Allow All)
- **Utilisez des commentaires** pour documenter chaque règle
- **Groupez les règles par fonction** (ex : toutes les règles DNS ensemble)

### Sécurité

- **Appliquez la politique du moindre privilège** : Autorisez uniquement ce qui est nécessaire
- **Bloquez par défaut** : Nier tout, puis autoriser sélectivement
- **Activez le logging** pour toutes les règles importantes
- **Revoyez régulièrement** les règles obsolètes
- **Testez les changements** en environnement non-critique avant

### Performance

- **Les règles spécifiques** s'exécutent plus vite que les règles générales
- **Placez les règles fréquentes** en haut pour éviter les scans inutiles
- **Utilisez les services prédéfinis** plutôt que des plages de ports générales

### Maintenance

- **Documentez chaque règle** : Pourquoi elle existe, qui l'a créée, quand
- **Maintenez une liste** des adresses et services utilisés
- **Mettez à jour régulièrement** les listes de blocage

---

## 🔧 Dépannage Commun

### La Règle n'a Aucun Effet

1. Vérifiez que la règle est **Active** (case cochée)
2. Vérifiez que les interfaces sont **correctes**
3. Vérifiez que les adresses source/destination correspondent
4. Vérifiez l'ordre : une règle Deny avant Allow bloquera tout
5. Consultez les logs pour confirmer la correspondance

### Les Ports sont Fermés Malgré la Règle

1. Vérifiez que **Enable NAT** n'est pas activé accidentellement
2. Vérifiez les règles **précédentes** qui pourraient être plus prioritaires
3. Vérifiez que le **service/port** est correctement configuré
4. Testez avec un port différent pour vérifier

### Trop de Trafic Autorisé

1. Revoyez les règles **Allow** trop générales
2. Utilisez des adresses source/destination plus **spécifiques**
3. **Limitez les services** autorisés au strict minimum
4. Ajoutez des règles **Deny** avant les règles **Allow**

---

## 📝 Checklist de Création de Règle

- [ ] Définir le **nom** de la règle clairement
- [ ] Choisir les **interfaces** source et destination
- [ ] Configurer les **adresses** source et destination
- [ ] Définir le **service/port**
- [ ] Définir l'**action** (Accept/Deny)
- [ ] Configurer le **logging**
- [ ] Vérifier l'**ordre** par rapport aux autres règles
- [ ] **Sauvegarder** la configuration
- [ ] **Tester** la règle
- [ ] **Documenter** la règle dans un registre
- [ ] **Vérifier** les logs pour validation

---