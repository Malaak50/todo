# 📱 Application TODO - Firebase & React Native

Une application de gestion de tâches moderne et professionnelle construite avec React Native, Expo et Firebase.

## ✨ Fonctionnalités

### 🔐 Authentification
- Connexion par email/mot de passe
- Inscription avec validation complète
- Authentification Google (OAuth)
- Gestion sécurisée des sessions

### ✅ Gestion des tâches
- Créer des tâches
- Marquer comme terminé/non terminé
- Supprimer des tâches
- Synchronisation en temps réel avec Firestore
- Statistiques (total, terminées, en cours)

### 🎨 Interface utilisateur
- Design moderne et professionnel
- Mode clair et mode sombre
- Animations fluides
- États vides informatifs
- Interface responsive

### 🔥 Firebase/Firestore
- Stockage cloud des données
- Synchronisation en temps réel
- Sécurité par utilisateur
- Pas de base de données locale (SQLite supprimé)

## 🚀 Installation

### Prérequis
- Node.js (v16 ou supérieur)
- npm ou yarn
- Expo CLI
- Compte Firebase

### Étapes

1. **Cloner le projet**
   ```bash
   cd c:\Users\malak\todo
   ```

2. **Installer les dépendances**
   ```bash
   npm install
   ```

3. **Configurer Firebase**
   - Créez un projet sur [Firebase Console](https://console.firebase.google.com)
   - Activez Authentication (Email/Password et Google)
   - Créez une base de données Firestore
   - Copiez `.env.example` vers `.env`
   - Remplissez les variables d'environnement :
     ```
     EXPO_PUBLIC_FIREBASE_API_KEY=votre_api_key
     EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=votre_auth_domain
     EXPO_PUBLIC_FIREBASE_PROJECT_ID=votre_project_id
     EXPO_PUBLIC_FIREBASE_APP_ID=votre_app_id
     EXPO_PUBLIC_GOOGLE_WEB_CLIENT_ID=votre_google_client_id
     ```

4. **Configurer les règles Firestore**
   ```javascript
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /todos/{todoId} {
         allow read, write: if request.auth != null && 
                             request.auth.uid == resource.data.userId;
         allow create: if request.auth != null;
       }
     }
   }
   ```

5. **Démarrer l'application**
   ```bash
   npm start
   ```

## 📁 Structure du projet

```
todo/
├── screens/
│   ├── LoginScreen.js          # Écran de connexion
│   ├── RegisterScreen.js       # Écran d'inscription
│   ├── HomeScreen.js           # Écran principal avec les tâches
│   ├── ProfileScreen.js        # Profil utilisateur
│   └── ...autres écrans
├── services/
│   └── firebase.js             # Configuration Firebase
├── store/
│   └── useTodoStore.js         # Store Zustand pour les tâches
├── context/
│   ├── AuthContext.js          # Contexte d'authentification
│   └── ThemeContext.js         # Contexte de thème
├── navigation/
│   ├── AppStack.js             # Navigation principale
│   ├── AppDrawer.js            # Menu drawer
│   └── NativeStack.js          # Stack natif
├── components/
│   └── AppBar.js               # Barre d'application
├── .env                        # Variables d'environnement
└── App.js                      # Point d'entrée

```

## 🎯 Utilisation

### Première utilisation

1. **Créer un compte**
   - Lancez l'application
   - Cliquez sur "Créer un compte"
   - Remplissez le formulaire
   - Ou utilisez "Continuer avec Google"

2. **Se connecter**
   - Entrez votre email et mot de passe
   - Ou utilisez Google Sign-In

### Gérer vos tâches

1. **Ajouter une tâche**
   - Cliquez sur le bouton "+ Ajouter"
   - Entrez le titre de la tâche
   - Cliquez sur "Ajouter"

2. **Marquer comme terminée**
   - Cliquez sur la tâche
   - La case à cocher se remplit
   - Le texte est barré

3. **Supprimer une tâche**
   - Cliquez sur l'icône 🗑️
   - La tâche est supprimée immédiatement

4. **Voir les statistiques**
   - En haut de l'écran
   - Total, Terminées, En cours

### Changer de thème

- Cliquez sur l'icône 🌙 (mode sombre) ou ☀️ (mode clair)
- Le thème change instantanément

## 🔧 Technologies utilisées

- **React Native** - Framework mobile
- **Expo** - Plateforme de développement
- **Firebase Authentication** - Authentification
- **Firestore** - Base de données NoSQL
- **Zustand** - Gestion d'état
- **React Navigation** - Navigation
- **Expo Auth Session** - OAuth Google

## 📊 Architecture

### Flux de données

```
User Action → Component → Store (Zustand) → Firestore
                                ↓
                            Update UI
```

### Authentification

```
LoginScreen/RegisterScreen → Firebase Auth → AuthContext → App
```

### Gestion des tâches

```
HomeScreen → useTodoStore → Firestore → Sync → UI Update
```

## 🐛 Dépannage

### Les tâches ne s'affichent pas
- Vérifiez votre connexion internet
- Vérifiez les règles Firestore
- Vérifiez que l'utilisateur est connecté
- Consultez la console pour les erreurs

### Erreur d'authentification
- Vérifiez les clés Firebase dans `.env`
- Vérifiez que l'authentification est activée dans Firebase Console
- Vérifiez que Google Sign-In est configuré

### Erreur de build
- Supprimez `node_modules` et réinstallez : `npm install`
- Nettoyez le cache Expo : `expo start -c`

## 📝 Notes importantes

- **SQLite supprimé** : Nous utilisons uniquement Firestore maintenant
- **Données cloud** : Toutes les données sont dans le cloud
- **Sécurité** : Chaque utilisateur ne voit que ses tâches
- **Temps réel** : Les modifications sont synchronisées instantanément

## 🎨 Personnalisation

### Modifier les couleurs du thème

Éditez `context/ThemeContext.js` :

```javascript
const lightTheme = {
  primary: "#votre_couleur",
  background: "#ffffff",
  // ...
};
```

### Ajouter des champs aux tâches

1. Modifiez `store/useTodoStore.js`
2. Ajoutez les champs dans Firestore
3. Mettez à jour l'interface dans `HomeScreen.js`

## 📄 Licence

Ce projet est à usage personnel et éducatif.

## 👨‍💻 Support

Pour toute question ou problème, consultez :
- [Documentation Firebase](https://firebase.google.com/docs)
- [Documentation Expo](https://docs.expo.dev)
- [Documentation React Native](https://reactnative.dev)

---

**Développé avec ❤️ en utilisant React Native et Firebase**
"# todo" 
