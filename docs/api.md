## Spécification API

Voici une description des endpoints disponibles (basée sur les fichiers `routes/` et `controllers/`).

Routes générales :

- /api/game/
  - GET /api/game/all — Récupère tous les jeux
  - POST /api/game/ — Crée un jeu (auth required)
  - PUT /api/game/:id — Met à jour un jeu
  - DELETE /api/game/:id — Supprime un jeu (admin)

- /api/genre/
  - GET /api/genre/all — Récupère tous les genres
  - POST /api/genre/ — Crée un genre (auth admin)

- /api/review/
  - GET /api/review/all — Récupère toutes les reviews
  - POST /api/review/ — Crée une review (auth required)

- /api/users/
  - GET /api/users/ — Liste les utilisateurs (protection selon roles)
  - POST /api/users/register — Crée un utilisateur
  - POST /api/users/login — Authentifie un utilisateur et renvoie un token

Format des requêtes :
- Les corps attendus sont des JSON.
- Les réponses standard sont du JSON avec format `{ success: boolean, data: ..., message?: string }` (à confirmer selon implémentation réelle).

Exemples de cURL :

GET all games

```
curl -X GET "${API_BASE}api/game/all"
```

POST review (avec token)

```
curl -X POST "${API_BASE}api/review/" -H "Authorization: Bearer <TOKEN>" -H "Content-Type: application/json" -d '{"gameId":"...","rating":5,"comment":"Great"}'
```

(Remplacez `${API_BASE}` par l'URL de base réelle de l'API.)
