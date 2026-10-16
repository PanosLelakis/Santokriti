# Santokriti

**Santokriti** is a full-stack tourist-guide website for a fictional Greek island, developed as a university team project. Visitors can explore places on an interactive map, while registered users can save their favourite locations.

**[Open the live demo](https://santokriti.fly.dev/)**

## Features

- **Interactive map:** Leaflet markers and marker clustering, with OpenStreetMap tiles.
- **Place pages:** descriptions, keywords and image galleries for individual locations.
- **User accounts:** registration, login and logout with session-based authentication.
- **Personal bookmarks:** save places, view saved entries and remove bookmarks.
- **Shopkeeper view:** list places associated with an account and their bookmark counts.
- **Localization:** interface resources for English, Greek and Spanish.

## Technology Stack

- **Backend:** JavaScript, Node.js, Express.
- **Frontend:** Handlebars, HTML, CSS, Bootstrap, jQuery.
- **Database:** PostgreSQL, accessed through `pg`.
- **Accounts:** bcrypt and express-session.
- **Maps and galleries:** Leaflet, Leaflet.markercluster, OpenStreetMap and Slick Carousel.

## Team and Contribution

Developed jointly by **Lefteris Gkliatis** and **Panos Lelakis** in 2024.

Panos contributed across the application, with his main focus on backend development. The project's design and implementation reflect the work of both team members.

## Local Setup

The following steps use a **new local PostgreSQL database**. Run commands from the repository root.

1. Install Node.js, npm and PostgreSQL. Create an empty database named `santokriti`.

2. Install dependencies and copy the configuration template:

   ```bash
   npm ci
   ```

   Copy `.env.example` to `.env`. Set `DATABASE_URL` to your local database connection string and replace `SESSION_SECRET` with a new random value. Keep `.env` private.

3. Create the application tables:

   ```bash
   node --input-type=module -e "import { initializeDatabase } from './model/postgres/tg-model-postgres.mjs'; process.exit((await initializeDatabase()) === true ? 0 : 1)"
   ```

4. Start the application:

   ```bash
   npm start
   ```

   Open `http://localhost:3000/register` and create an account with **Shopkeeper** selected. Stop the server with `Ctrl+C`.

5. Load the sample places and assign them to the first shopkeeper account:

   ```bash
   node --input-type=module -e "import { populatePlaceAndOwnsTables } from './model/postgres/tg-model-postgres.mjs'; process.exit((await populatePlaceAndOwnsTables()) === true ? 0 : 1)"
   ```

   This step skips population when the `Place` table already contains data. It does not reset an existing database.

6. Run `npm start` again and open `http://localhost:3000`. Register additional visitor accounts if needed. The default port is `3000`, configurable through `PORT`.

## Project Structure

`start.mjs` starts the server. Requests flow through `routes/` and `controller/`, with PostgreSQL access in `model/postgres/`, templates in `views/`, static assets in `public/` and translation resources in `locales/`.

## Prototype Status

This is an academic prototype. The category-filter controls and contact form are interface prototypes without complete supporting behaviour in this version.

## License

Original project code is available under the [ISC License](LICENSE). Third-party libraries, map data, fonts and images retain their respective licenses and attribution requirements.
