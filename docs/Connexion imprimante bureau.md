# 🖨️ Connexion à l'imprimante de bureau

## 📝 Objectif
Configurer une connexion à l'imprimante de bureau via IPP sur Windows 10 et Windows 11.

---

## 📌 Prérequis
- Être **connecté au réseau Backoffice** ou en **connexion câblée**.
- L’**adresse IP de l’imprimante** : `10.6.190.50`

---

## 🛠️ Étapes détaillées

### 1️⃣ **Ouvrir les paramètres d’imprimante**
1. **Accéder au panneau de configuration** :
   - **Windows 10** : Taper `Panneau de configuration` dans la barre de recherche et ouvrir l’application.
   - **Windows 11** : Aller dans `Paramètres` > `Bluetooth et appareils` > `Imprimantes et scanners`.

2. Cliquer sur **Ajouter une imprimante ou un scanner**.
3. Sélectionner **L'imprimante que je veux n'est pas répertoriée**.

---

### 2️⃣ **Connexion via IPP (Internet Printing Protocol)**
1. Sélectionner **Ajouter une imprimante à l'aide d'une adresse TCP/IP ou d'un nom d'hôte**.
2. Cliquer sur **Suivant**.
3. Dans le champ **Nom d'hôte ou adresse IP**, entrer :
   ```
   10.6.190.50
   ```
4. Laisser **Rechercher automatiquement le pilote** activé.
5. Cliquer sur **Suivant** et attendre la détection.
6. Sélectionner le pilote d'imprimante si demandé (*choisir le modèle exact de l'imprimante*).
7. Cliquer sur **Suivant**, puis **Terminer**.

---

## 🔄 Vérification et tests
1. Aller dans **Imprimantes et scanners**.
2. Sélectionner l’imprimante nouvellement ajoutée.
3. Cliquer sur **Imprimer une page de test**.
4. Vérifier que l’impression fonctionne.

---

## 💡 Remarques et Conseils
- **Si l’imprimante ne répond pas** : Vérifier la connexion réseau et que l’adresse IP `10.6.190.50` est correcte.
- **Si Windows ne trouve pas le pilote** : Installer manuellement le pilote correspondant depuis le site du fabricant.
- En cas de problème persistant, **contacter le service informatique** : si@canopycannes.com ou au **5021**.
