# Chemnitz City Explorer

An interactive web app for discovering points of interest around Chemnitz — museums, galleries, restaurants, hotels, theatres, and more — on a live map. Users can browse and filter places by category, search by name, save favorites, and leave star ratings and reviews.

> Full-stack project: Next.js + TypeScript frontend, Node/Express + MongoDB backend, with map data sourced from OpenStreetMap GeoJSON.

## Features

- **Interactive map** of Chemnitz built on Leaflet + React Leaflet, with markers, popups, and fly-to navigation to a selected place.
- **Category browsing** — places are grouped into tourism, amenity, and shop categories (museum, gallery, artwork, guest house, hotel, restaurant, theatre, deli, and more).
- **Fuzzy search** by place name using Fuse.js, so partial or slightly misspelled queries still return results.
- **Cards view** with pagination and filtering alongside the map.
- **Authentication** — email/password sign-up and login, plus Google OAuth. Sessions are handled with JWTs stored in an httpOnly cookie.
- **Favorites** — logged-in users can save and remove places from their profile.
- **Reviews & ratings** — 1–5 star reviews per place, with an automatically computed average rating.
- **User profile** page showing saved favorites and account info.

## Tech Stack

**Frontend**
- Next.js 15 (App Router) + React 19
- TypeScript
- Tailwind CSS v4
- Material UI (MUI) + Toolpad Core
- Leaflet / React Leaflet + marker clustering
- Jotai (state management)
- Axios, Framer Motion, React Icons

**Backend**
- Node.js + Express 5
- MongoDB + Mongoose
- JWT (jsonwebtoken) + bcryptjs for auth
- Google Auth Library (OAuth 2.0)
- Fuse.js for fuzzy search
- cookie-parser, cors, dotenv

**Data**
- `Chemnitz.geojson` — OpenStreetMap-derived points of interest, auto-seeded into MongoDB on first run.

## Project Structure

```
chemnitz/
├── chemnitz-backend/        # Express + MongoDB API
│   ├── Chemnitz.geojson     # POI seed data
│   └── src/
│       ├── config/          # DB connection + GeoJSON seeding
│       ├── controllers/     # auth, google auth, features, favorites, reviews, users
│       ├── middleware/      # JWT auth guard
│       ├── models/          # User, Attraction (Feature) schemas
│       ├── routes/          # /auth, /user, /feature
│       └── utils/           # JWT config, validators
└── chemnitz-frontend/       # Next.js app
    └── src/
        ├── app/             # routes: home, login, signup, dashboard, profile, about
        ├── api/             # axios calls to the backend
        ├── components/      # map, cards, forms, header, profile, general UI
        ├── config/          # axios instance
        ├── lib/             # auth + validation helpers
        └── types/           # shared TypeScript types
```

## Notes

- The map is centered on Chemnitz (`50.8323, 12.9253`) and uses OpenStreetMap tiles.
- CORS is configured for `http://localhost:3000`; update the origin in `src/index.js` and the OAuth redirect URIs when deploying.

