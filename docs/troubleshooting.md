## Dépannage (Troubleshooting)

Problème courant : `GET http://localhost:3000/api/... net::ERR_CONNECTION_REFUSED`

Cause probable :
- Le frontend tente de joindre `http://localhost:3000` alors que le backend n'est pas lancé localement ou est déployé sur une URL distante.

Solutions :
1. Démarrer le backend localement :
   - `cd backend-API` puis `npm install` puis `npm run dev` ou `node index.js`.
   - Vérifier que l'API répond : `curl http://localhost:3000/api/game/all`.

2. Si l'API est déployée (ex: Render) :
   - Mettre à jour la variable d'environnement côté frontend (Vite) `VITE_API_BASE_URL` pour pointer vers `https://final-tp-1.onrender.com/`.
   - Exemple : créer `admin-dashboard/.env` contenant `VITE_API_BASE_URL=https://final-tp-1.onrender.com/` puis relancer le frontend.

3. Vérifier CORS :
   - Si l'API répond mais le navigateur bloque la requête, vérifiez que le backend envoie les en-têtes CORS appropriés (`Access-Control-Allow-Origin`).

4. Vérifier que vous n'utilisez pas d'URL mal formée :
   - Vous avez mentionné `http://localhost:3000z` — c'est une faute de frappe. Vérifiez qu'il n'y a pas de `z` à la fin.

5. Rechercher les occurrences dans le code et remplacer :
   - Rechercher `http://localhost:3000` ou variantes et remplacer par `import.meta.env.VITE_API_BASE_URL` (frontend) ou par la variable d'env côté backend.

Debug rapide :
- Ouvrez la console DevTools -> Network pour voir l'URL exacte et la raison de l'échec.
- Testez l'URL directement via curl/Postman pour vérifier si le serveur répond.

Si vous voulez, je peux automatiquement rechercher toutes les occurrences de `localhost` et proposer un patch pour utiliser la variable d'environnement (optionnel, me le demander explicitement).