
# CoBuild

## Equipe

- BAKAROU Hajar
- EL MESSOUSSI MOHAMED SINANE
- MOTASSIM Ahmed Taha

## 📦 Structure du Projet

Ce dépôt utilise les **submodules Git** pour gérer le frontend et le backend dans des dépôts séparés.

---

## 🔧 Étapes de configuration

### 1. Cloner le projet avec les submodules

```bash
git clone --recurse-submodules https://github.com/bakarouhajar/CoBuild.git
```

> 💡 Si vous avez déjà cloné sans les submodules :
```bash
git submodule update --init --recursive
```

---

### 2. Mettre à jour les submodules

Pour récupérer les dernières modifications dans le frontend/backend :
```bash
git submodule update --remote --merge
```

---

### 3. Ajouter des changements dans un submodule

Si vous modifiez un submodule et souhaitez mettre à jour la référence :
```bash
cd cobuild_front  # ou cobuild_back
git checkout main # pour cobuild_front et cobuild back
git pull origin main # pour cobuild_front et cobuild back

cd ..
git add cobuild_front  # ou git add cobuild_back
git commit -m "Mise à jour du submodule"
git push origin main
```

---

## ⚙️ Backend : Configuration Spring Boot

### 1. Prérequis
- Java 17+
- Maven
- MySQL

### 2. Base de données

Créer une base de données nommée `cobuild` :
```sql
CREATE DATABASE cobuild;
```

### 3. Fichier `.env.local` ou `application.properties`

Configurer les identifiants MySQL :
```
DB_URL=jdbc:mysql://localhost:3306/cobuild?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
DB_USERNAME=NOM_UTILISATEUR
DB_PASSWORD=MOT_DE_PASSE
```

Lancer l'application Spring Boot :
```bash
./mvnw spring-boot:run
```

L'API sera accessible sur : `http://localhost:8080`

---

## 💻 Frontend : React + Vite

### 1. Prérequis
- Node.js (v18+)
- npm

### 2. Installation

```bash
cd cobuild_front
npm install
```

### 3. Configuration environnement

Créer un fichier `.env` dans le dossier `cobuild_front` :
```
VITE_API_URL=http://localhost:8080
```

### 4. Démarrer l'application React

```bash
npm run dev
```

L'interface sera accessible sur : `http://localhost:5173`

---

## 🔗 Liaison Frontend / Backend

- Assurez-vous que le backend accepte les requêtes CORS depuis `http://localhost:5173`.
- Vérifiez que les tokens JWT sont correctement envoyés dans les headers `Authorization`.

---

## 🧪 Tests

- Tester la création de compte (travailleur / porteur)
- Créer un projet, un poste, une tâche
- Appliquer à un poste et accepter une candidature
- Messagerie entre travailleur et porteur