## Architecture du projet

Ce projet est composé de deux applications principales :

1. Frontend — `admin-dashboard` (React + Vite + TypeScript)
   - UI pour gérer les jeux, genres, utilisateurs et reviews.
   - Appelle l'API backend via une URL de base configurée par variable d'environnement.

2. Backend — `backend-API` (Node.js + Express + MongoDB ou stockage local selon configuration)
   - Expose des endpoints REST sous `/api/*` (games, genre, users, review, gamelist).
   - Organisé en `controllers/`, `models/`, `routes/`, `middlewares/`.

Flux de données :
- Le frontend envoie des requêtes HTTP (GET/POST/PUT/DELETE) vers le backend.
- Le backend traite la logique métier et accède aux modèles (BD) pour persister/retourner des données.

Diagramme (simplifié) :

Frontend (Vite/React) --> API (Express) --> Base de données (MongoDB / JSON)

Notes d'interopérabilité :
- Le frontend doit utiliser une variable d'environnement pour la base URL de l'API (`VITE_API_BASE_URL`).
- Le backend doit exposer la variable `PORT` et `MONGO_URI` si MongoDB est utilisée.

Sécurité :
- Middleware `verifyToken.js` pour vérifier JWT.
- Middleware `authorizeRole.js` pour vérifier les rôles d'accès.

Tests :
- Ajouter des tests unitaires pour les contrôleurs et routes côté backend (ex : Jest, supertest).
- Pour le frontend, ajouter quelques tests composants (ex : React Testing Library).
