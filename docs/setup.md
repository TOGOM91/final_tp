## Installation et configuration locale

Prérequis :
- Node.js (14+ recommandé)
- npm ou yarn
- Git
- (Optionnel) MongoDB si vous souhaitez exécuter le backend avec une base de données réelle

1) Cloner le dépôt

   git clone <repo-url>
   cd API_Jeu-main

2) Installer et lancer le backend

   cd backend-API
   npm install
   # Créez un .env local (voir docs/env_variables.md)
   npm run dev

3) Installer et lancer le frontend (admin-dashboard)

   cd admin-dashboard
   npm install
   # Créez un .env.local (ou utilisez .env) basé sur admin-dashboard/.env.example
   npm run dev

4) Accéder à l'application

- Frontend (par défaut Vite) : http://localhost:5173 (ou port affiché par Vite)
- Backend : http://localhost:3000 (si `PORT=3000` configuré pour l'API)

Remarques :
- Si vous hébergez l'API sur Render ou un autre fournisseur, mettez à jour `VITE_API_BASE_URL` pour pointer vers l'URL distante.
- Pour les builds de production : `npm run build` dans `admin-dashboard` puis déployer les fichiers statiques.
