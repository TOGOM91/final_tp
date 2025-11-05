## Backend (`backend-API`)

Structure :
- `index.js` : point d'entrée
- `controllers/` : logique des routes (gameController.js, userController.js, ...)
- `models/` : schémas et modèles (Game.js, User.js, ...)
- `routes/` : définition des routes express
- `middlewares/` : middlewares d'authentification et d'autorisation

Variables d'environnement importantes :
- `PORT` : port du serveur (ex: 3000)
- `MONGO_URI` : URI MongoDB si utilisé
- `JWT_SECRET` : secret pour signer JWT

Démarrage en dev :
- `npm run dev` (si script présent) ou `node index.js`

Endpoints exposés (exemples) :
- `GET /api/game/all` : récupère tous les jeux
- `GET /api/genre/all` : récupère tous les genres
- `GET /api/review/all` : récupère toutes les reviews
- `GET /api/users/` : récupère les utilisateurs (peut exiger auth)

Sécurité :
- Vérifier `verifyToken.js` pour la validation du token JWT.
- Vérifier `authorizeRole.js` pour la restriction des routes par rôle (admin/user).

Connexion BD :
- Si `models` utilisent mongoose, vérifiez `index.js` pour la connexion à `MONGO_URI`.
- Si aucune BD externe n'est utilisée, vérifier si les modèles utilisent un stockage interne.

Logs et debugging :
- Monitorer les erreurs dans le terminal où tourne `node`.
- Pour l'erreur `ECONNREFUSED` côté frontend, s'assurer que le backend est lancé sur le port configuré et accessible.
