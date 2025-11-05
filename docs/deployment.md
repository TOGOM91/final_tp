## Déploiement

Ce projet peut être déployé en séparant le frontend et le backend, ou en servant le build frontend depuis le backend.

Déploiement Backend (Render / Heroku / autre) :
- Assurez-vous que `PORT` et `MONGO_URI` sont configurés dans les variables d'environnement de la plateforme.
- Deploy : poussez le repo ou liez au dépôt, configurez le build (par ex `npm install` puis `npm start`).

Déploiement Frontend (Vite) :
- Construisez la version de production : `npm run build` dans `admin-dashboard`.
- Déployez le contenu de `dist/` sur un hôte statique (Netlify, Vercel) ou servez depuis le backend en production.
- Configurez `VITE_API_BASE_URL` sur la plateforme pour pointer vers l'URL backend (ex: `https://final-tp-1.onrender.com/`).

Conseils pour Render (où l'API est hébergée) :
- Vérifiez que l'URL fournie par Render est bien `https://final-tp-1.onrender.com/`.
- Dans le frontend, définissez la variable d'environnement `VITE_API_BASE_URL` sur cette URL.
- Si vous hébergez le frontend sur Render aussi, configurez la même variable via le dashboard de votre service.

Caveats :
- Toujours utiliser `https` en production.
- Gérer correctement les en-têtes CORS dans l'API pour autoriser les origines du frontend.
