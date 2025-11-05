## Frontend (`admin-dashboard`)

Technos : React + TypeScript + Vite

Points importants :
- Les variables d'environnement côté client (Vite) doivent commencer par `VITE_`.
- Base URL de l'API : `import.meta.env.VITE_API_BASE_URL`.

Fichier d'entrée : `src/main.tsx`

Exemples d'utilisation pour appeler l'API :

```ts
const API_BASE = import.meta.env.VITE_API_BASE_URL || 'http://localhost:3000/';
fetch(`${API_BASE}api/users/`)
  .then(r => r.json())
```

Astuce : ne pas hardcoder `http://localhost:3000` dans le code — utiliser la variable d'environnement.

Fichier `.env.example` (situé dans `admin-dashboard/.env.example`) :

```
VITE_API_BASE_URL=https://final-tp-1.onrender.com/
```

Build & production :
- `npm run build` pour produire la version optimisée.
- Déployer les fichiers de `dist/` sur un hébergeur statique (Netlify, Vercel, Render static, etc.).

Remplacement automatique des URLs codées en dur (optionnel) :
- Rechercher `http://localhost:3000` et remplacer par `import.meta.env.VITE_API_BASE_URL` dans les fichiers TypeScript/JSX.
- Exemple concret d'adaptation d'un appel axios :

```ts
// avant
axios.get('http://localhost:3000/api/game/all')

// après
axios.get(`${import.meta.env.VITE_API_BASE_URL}api/game/all`)
```

Note sur CORS :
- Si le backend n'autorise pas les requêtes depuis l'origine du frontend, configurez CORS côté backend (`cors` package) pour autoriser votre domaine frontend.
