# 🖨️ Configuration d'une imprimante de caisse Epson

## 📝 Objectif
Configurer une nouvelle imprimante de caisse Epson en lui assignant manuellement l’adresse IP de l’ancienne imprimante.

---

## 📌 Prérequis
- **Câble Ethernet** pour relier le PC à l’imprimante.
- **Accès administrateur** sur le PC.
- **Numéro de série** de l’imprimante (au dos).
- **Adresse IP de l’ancienne imprimante à réutiliser**.

---

## 🛠️ Étapes détaillées

### 1️⃣ **Connexion physique**
1. Connecter un **câble Ethernet** entre votre PC et l’imprimante.

---

### 2️⃣ **Configurer une IP locale manuelle sur le PC**
1. Aller dans le **Panneau de configuration**.
2. Cliquer sur **Réseau et Internet**.
3. Aller dans **Centre Réseau et Partage**.
4. Cliquer sur la connexion **Ethernet** utilisée.
5. Cliquer sur **Propriétés**.
6. Sélectionner **Protocole Internet version 4 (TCP/IPv4)**.
7. Attribuer une **IP manuelle** compatible avec celle de l’imprimante (ex. : `192.168.192.100`).
8. Valider avec **OK** > **OK** > **Fermer**.

---

### 3️⃣ **Connexion à l’interface web de l’imprimante**
1. Ouvrir un navigateur web.
2. Entrer l’adresse : `http://192.168.192.168`

#### 🔐 Connexion administrateur :
- **ID** : `epson`
- **Mot de passe** : `epson` ou **numéro de série** (inscrit au dos de l’imprimante).

---

### 4️⃣ **Configuration réseau de l’imprimante**
1. Chercher la section **TCP/IP**.
2. Trouver l’option **Get IP Address** ou **Obtenir adresse IP**.
3. Sélectionner **Manual** (manuel).
4. Entrer :
   - **IP de l’ancienne imprimante**
   - **Masque de sous-réseau**
   - **Passerelle**
   - **DNS primaire/secondaire** *(identiques à l’ancienne config)*
5. Cliquer sur **Soumettre**.

---

### 5️⃣ **Redémarrage et test**
1. Sur la page suivante, cliquer sur **Reset**.
2. L’imprimante redémarre, la page web sera coupée.
3. Reconfigurer le PC avec son adresse IP d’origine.
4. **Tester l’impression**.

---

## ❗ Remarques
- S’assurer que l’imprimante est bien sur le VLAN adéquat après redémarrage.
- En cas d’échec, vérifier les câbles, les IP ou contacter le service informatique : si@canopycannes.com ou **5021**.
