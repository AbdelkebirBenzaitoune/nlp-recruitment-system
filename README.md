# 🧠 NLP Recruitment System – Assistant Carrière Intelligent

[![Live Demo](https://img.shields.io/badge/demo-live-brightgreen)](https://abdelkebirbenzaitoune.github.io/nlp-recruitment-system)
[![Python](https://img.shields.io/badge/python-3.8%2B-blue)](https://python.org)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## 📘 Description du projet

Application web d’aide à la candidature qui analyse un **CV** et une **offre d’emploi**, calcule un **score de compatibilité**, génère des **quiz personnalisés** pour mesurer les compétences et propose des **recommandations ciblées** (formations, projets, certifications).  
Un **assistant IA** accompagne le candidat pour comprendre ses résultats et progresser efficacement.

---

## 🧩 Architecture du projet

```
nlp-recruitment-system/
│
├── backend-ms/                  # Backend Flask (API REST)
│   ├── apps.py                  # Entrée principale du serveur Flask
│   ├── cv_parsing/              # Extraction et parsing du texte (NLP + LLM)
│   │   ├── extractors.py
│   │   ├── gemini_parser.py
│   │   ├── job_parsing.py
│   │   └── pipeline.py
│   ├── cv_job_matching.py       # Calcul de similarité CV–offre
│   ├── quiz_module.py           # Génération et évaluation de quiz IA
│   ├── models/                  # Schémas et accès MongoDB
│   │   ├── user.py
│   │   └── result.py
│   ├── notebooks/               # Prototypes et tests Jupyter
│   ├── requirements.txt
│   └── .env                     # Variables d’environnement locales
│
├── client/                      # Frontend React (Vite + TailwindCSS)
│   ├── src/
│   │   ├── api/axios.js         # Gestion des requêtes API
│   │   ├── contexts/AuthContext.jsx
│   │   ├── components/…         # Interface utilisateur (auth, quiz, etc.)
│   │   ├── pages/
│   │   │   ├── AuthPage.jsx
│   │   │   ├── DemoPage.jsx
│   │   │   └── AssistantWorkspace.jsx
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── images/interface.png
│   ├── videos/VedioDemo.mp4
│   ├── package.json
│   ├── vite.config.js
│   └── tailwind.config.js
│
└── README.md
```

---

## ⚙️ Technologies utilisées

**Backend :**
- Flask, Flask-CORS, Flask-JWT-Extended, Flask-Bcrypt  
- PyMongo, Sentence-Transformers  
- Google Gemini API (LLM)

**Frontend :**
- React (Vite), TailwindCSS, Axios  
- Lucide-react (icônes)  

**Base de données :**
- MongoDB (local ou MongoDB Atlas)
- Schéma de données (MongoDB) :
  
  users : { email, password_hash, firstName, lastName, createdAt }
  
  results : { user, type (cv|job|matching|quiz), data, meta, refs, createdAt }
---

## 🚀 Installation et exécution

### 1️⃣ Cloner le projet
```bash
git clone https://github.com/<username>/nlp-recruitment-system.git
cd nlp-recruitment-system
```

---

### 2️⃣ Lancer le backend Flask
```bash
cd backend-ms
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/macOS
# source venv/bin/activate

pip install -r requirements.txt
```

Créer un fichier `.env` :
```bash
MONGO_URI=mongodb://127.0.0.1:27017/?directConnection=true
JWT_SECRET=change_me_secret
GEMINI_API_KEY=ta_cle_api_gemini
```

Démarrer le serveur :
```bash
python apps.py
# => http://localhost:5000
```

> ⚠️ Si tu obtiens `ECONNREFUSED 127.0.0.1:27017`, vérifie que MongoDB est lancé :
> ```bash
> net start MongoDB
> ```
> ou lance un conteneur Docker :
> ```bash
> docker run -d --name mongo -p 27017:27017 -v mongo_data:/data/db mongo:7
> ```

---

### 3️⃣ Lancer le frontend React
```bash
cd client
npm install
npm run dev
# => http://localhost:5173
```

---

## 🧠 Fonctionnalités principales

- 📄 **Analyse CV ↔ Offre d’emploi** (similarité sémantique)
- 🧩 **Score global de compatibilité** (et sous-scores par compétence)
- 🧠 **Quiz IA personnalisés** basés sur les compétences détectées
- 🪄 **Assistant conversationnel** (LLM) pour conseils et recommandations
- 📈 **Recommandations concrètes** : cours, certifications, mini-projets

---

## 🔗 Endpoints principaux

| Méthode | Endpoint                           | Description |
|---------:|-----------------------------------|-------------|
| POST     | `/api/auth/register`              | Créer un compte utilisateur |
| POST     | `/api/auth/login`                 | Authentification JWT |
| POST     | `/api/upload`                     | Téléversement de fichier (CV / offre) |
| POST     | `/api/parse-cv`                   | Extraction et parsing du CV |
| POST     | `/api/parse-job`                  | Extraction et parsing de l’offre |
| POST     | `/api/match`                      | Calcul du score de compatibilité |
| POST     | `/api/quiz/generate`              | Génération d’un quiz IA |
| GET      | `/api/assistant/recommendations`  | Recommandations personnalisées |

---

## 🧰 Dépannage

| Erreur | Cause probable | Solution |
|--------|----------------|-----------|
| `ECONNREFUSED 127.0.0.1:27017` | MongoDB non démarré | Lance le service local ou un conteneur Docker |
| `CORS policy` | Mauvaise configuration Flask ou Axios | Vérifie la config `Flask-CORS` et `axios.js` |
| `Gemini API Error` | Clé API invalide ou quota atteint | Vérifie `GEMINI_API_KEY` |
| Vidéo non visible | Mauvais chemin vers `/videos/VedioDemo.mp4` | Place la vidéo dans `client/public/videos` |

---

## 👥 Auteurs

- **Benzaitoune Abdel Kebir**  
  Master 2 Science et Ingénierie des Données – Université Mohammed V, Rabat  
  📧 beabdo14@gmail.com  

- **Aabid Mohamed Amine**  
- **Najib Ilham**  
- **Nidal Igrou**

---

## 📄 Licence
Projet académique — libre d’utilisation à des fins pédagogiques et démonstratives.
