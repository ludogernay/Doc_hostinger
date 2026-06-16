# Dépannage de la Caisse - Guide Complet

## 🔴 La caisse affiche un carré jaune ou rouge

Suivez les étapes suivantes dans l'ordre pour résoudre le problème :

---

## 1️⃣ Vérifier le câblage

- **Vérifiez que le câble réseau est correctement branché** sur le petit switch
- Assurez-vous que la connexion est bien établie (vérifiez les LED du switch)
- Vérifiez qu'il n'y a pas de câble endommagé ou mal inséré
- Reconnectez le câble si nécessaire
- Vérifiez que le petit switch est allumé et fonctionnel

---

## 2️⃣ Vérifier l'adresse IP et la configuration réseau complète

L'adresse IP de la caisse **doit être en 192.168.190.x** :

1. Ouvrez l'invite de commandes sur la caisse
2. Tapez la commande :
   ```
   ipconfig /all
   ```
3. Vérifiez les éléments suivants :
   - **Adresse IPv4** : doit être en **192.168.190.x** (exemple : `192.168.190.50`)
   - **Passerelle par défaut (Default Gateway)** : doit être **192.168.190.200**
   - **Serveur DHCP** : doit être activé et accessible (vérifiez la ligne "DHCP Enabled: Yes")
   - **Serveurs DNS** : doivent être présents et correctement configurés

**Si l'IP n'est pas correcte ou ne correspond pas à 192.168.190.x**, passez à l'étape 6 (Réinitialiser la configuration réseau).

---

## 3️⃣ Vérifier les DNS

Les DNS doivent être configurés avec les serveurs suivants :

- **DNS 1 : 1.1.1.1** (Cloudflare)
- **DNS 2 : 8.8.8.8** (Google)

### Comment vérifier/modifier les DNS :

1. Ouvrez les **Paramètres réseau** de Windows
2. Allez dans **Paramètres réseau avancés**
3. Sélectionnez votre adaptateur réseau et cliquez sur **Modifier**
4. Sélectionnez **Paramètres IPv4** et cliquez sur **Modifier**
5. Choisissez **Manuel** et entrez les DNS :
   - `1.1.1.1`
   - `8.8.8.8`
6. Cliquez sur **Enregistrer**

---

## 4️⃣ Tester la connectivité réseau

Vérifiez que la caisse peut communiquer avec les serveurs DNS :

1. Ouvrez l'invite de commandes
2. Exécutez les commandes suivantes :
   ```
   ping 1.1.1.1
   ```
   ```
   ping 8.8.8.8
   ```
3. Vous devriez recevoir des réponses ("Reply from..."). Si vous recevez des messages "Request timed out" ou "Host unreachable", il y a un problème de connectivité

**Si le ping échoue**, vérifiez :
- Que le câble réseau est bien connecté
- Que l'adresse IP et la passerelle sont correctes
- Que le serveur DHCP est actif et accessible

---

## 5️⃣ Désactiver le pare-feu (si le problème persiste)

Si les étapes précédentes n'ont pas résolu le problème :

1. Ouvrez le **Panneau de configuration** de Windows
2. Allez dans **Système et sécurité**
3. Cliquez sur **Pare-feu Windows Defender**
4. Cliquez sur **Activer ou désactiver le Pare-feu Windows Defender**
5. **Désactivez le pare-feu** pour les réseaux privés et publics
6. Cliquez sur **OK**

**Important :** Vérifiez également s'il existe d'autres logiciels de sécurité ou antivirus sur la caisse qui pourraient bloquer la connexion (Kaspersky, McAfee, Avast, etc.). Si c'est le cas, désactivez temporairement leur pare-feu respectif.

---

## 6️⃣ Redémarrer l'adaptateur réseau

Avant de réinitialiser complètement la configuration, essayez de redémarrer l'adaptateur réseau :

1. Ouvrez l'invite de commandes **en tant qu'administrateur**
2. Exécutez les commandes suivantes :
   ```
   ipconfig /release
   ```
   ```
   ipconfig /renew
   ```
3. **Attendez 2 minutes** que les modifications prennent effet
4. Testez de nouveau la connexion avec `ping 8.8.8.8`

---

## 7️⃣ Réinitialiser complètement la configuration réseau

Si le problème persiste toujours, réinitialisez complètement la configuration réseau :

1. Ouvrez l'invite de commandes **en tant qu'administrateur**
   - Appuyez sur `Win + R`
   - Tapez `cmd` et appuyez sur `Ctrl + Shift + Entrée`

2. Exécutez les commandes suivantes dans l'ordre :
   ```
   ipconfig /release
   ```
   ```
   ipconfig /renew
   ```
   ```
   ipconfig /flushdns
   ```

3. **Attendez 3 à 5 minutes** que les modifications prennent effet complètement

4. Redémarrez la caisse (optionnel mais recommandé) :
   ```
   shutdown /r /t 60
   ```
   (Cela redémarrera la machine dans 60 secondes)

---

## 8️⃣ Redémarrer la machine (si nécessaire)

Si vous n'avez pas déjà redémarré :

1. Cliquez sur **Démarrer** dans le coin inférieur gauche
2. Cliquez sur **Arrêter** ou **Redémarrer**
3. Choisissez **Redémarrer**
4. **Attendez que la machine redémarre complètement** (2-3 minutes)

---

## 9️⃣ Revérifier l'adresse IP et la connectivité

Après toutes les modifications, vérifiez de nouveau :

1. Ouvrez l'invite de commandes
2. Tapez :
   ```
   ipconfig /all
   ```
3. Confirmez que :
   - L'adresse IPv4 est bien en **192.168.190.x**
   - La passerelle par défaut est **192.168.190.1**
   - Les DNS sont correctement configurés

4. Testez la connectivité :
   ```
   ping 8.8.8.8
   ```
   Vous devriez recevoir des réponses positives

---

## 🔟 Diagnostics avancés (si le problème persiste)

Si toutes les étapes précédentes n'ont pas résolu le problème, collectez les informations suivantes pour le support :

1. **Dump complet de la configuration réseau** :
   ```
   ipconfig /all > C:\network_config.txt
   ```

2. **Résultats du test de connectivité** :
   ```
   ping 8.8.8.8 -n 10 > C:\ping_test.txt
   ```

3. **État des services réseau** :
   ```
   netstat -an > C:\netstat.txt
   ```

4. **Logs du système** :
   - Ouvrez l'**Observateur d'événements** (Event Viewer)
   - Allez dans **Journaux Windows > Système**
   - Cherchez les erreurs réseau des dernières heures
   - Prenez des captures d'écran des erreurs pertinentes

5. **Vérifiez les paramètres de la caisse** :
   - Consultez les paramètres logiciels de la caisse pour vérifier si elle n'a pas d'IP statique mal configurée
   - Vérifiez que le serveur PMS (Property Management System) est accessible et fonctionnel

---

## ✅ Résumé des étapes

| Étape | Action |
|-------|--------|
| 1 | Vérifier le câblage sur le petit switch |
| 2 | Vérifier l'IP, la Gateway et les DNS avec `ipconfig /all` |
| 3 | Vérifier les DNS (1.1.1.1 et 8.8.8.8) |
| 4 | Tester la connectivité avec `ping 8.8.8.8` |
| 5 | Désactiver le pare-feu Windows et autres logiciels de sécurité |
| 6 | Redémarrer l'adaptateur réseau avec `ipconfig /release` et `ipconfig /renew` |
| 7 | Réinitialiser complètement la configuration réseau |
| 8 | Redémarrer la machine si nécessaire |
| 9 | Revérifier l'IP et la connectivité |
| 10 | Collecter les diagnostics avancés pour le support |

---