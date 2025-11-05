## Variables d'environnement

Frontend (`admin-dashboard`) — Vite :
- Les variables publiques doivent commencer par `VITE_`.

Variables recommandées :

- `VITE_API_BASE_URL` — URL de base de l'API (ex: `https://final-tp-1.onrender.com/`)

Exemple `.env` pour le frontend (`admin-dashboard/.env` ou `.env.local`) :

```
VITE_API_BASE_URL=https://final-tp-1.onrender.com/
```

Backend (`backend-API`) :
- `PORT` — port d'écoute (ex: 3000)
- `MONGO_URI` — URI vers la base de données MongoDB
- `JWT_SECRET` — clé pour signer les JWT

Exemple `.env` pour le backend :

```
PORT=3000
MONGO_URI=mongodb+srv://<user>:<pass>@cluster0.mongodb.net/mydb
JWT_SECRET=changeme
```

Notes :
- Ne commitez pas vos `.env` contenant des secrets. Ajoutez-les à `.gitignore`.
- Fournissez un `.env.example` (sans secrets) pour documenter les variables attendues.
