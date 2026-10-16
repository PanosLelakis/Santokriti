# Santokriti

**Santokriti** is a full-stack tourist-guide website for a fictional Greek island, developed as a university team project in 2024. Visitors can explore places on an interactive map, while registered users can save their favourite locations.

**[Open the live demo](https://santokriti.fly.dev/)**

## Features

- Interactive map with Leaflet markers, marker clustering and OpenStreetMap tiles.
- Place pages with descriptions, keywords and image galleries.
- User registration, login and session-based authentication.
- Personal bookmarks and a shopkeeper view showing associated places and bookmark counts.
- Interface resources for English, Greek and Spanish.

## Technology Stack

**Backend:** JavaScript, Node.js, Express, PostgreSQL (`pg`), bcrypt and express-session.

**Frontend:** Handlebars, HTML, CSS, Bootstrap, jQuery, Leaflet and Slick Carousel.

## Team and Contribution

Developed jointly by **Lefteris Gkliatis** and **Panos Lelakis**. Panos contributed across the application, with his main focus on backend development.

## Project Status

The code is preserved in its original coursework form. It contains known bugs and unfinished features:

- Category-filter controls and the contact form do not have complete supporting behaviour.
- Adding an already-bookmarked place can produce an error.
- Automatic database initialization and sample-data loading are incomplete; local execution requires manual database preparation.

## Local Execution

Run commands from the repository root. The following is a brief outline for a **new local database**:

1. Install Node.js, npm and PostgreSQL, and create an empty database.
2. Run `npm ci` and create a local `.env` containing `DATABASE_URL=postgresql://username:password@localhost:5432/databasename`, using your own database details.
3. Execute `model/postgres/create_tables.sql` through a PostgreSQL client to create the tables.
4. Run `npm start`, open `http://localhost:3000/register` and create two accounts. Make the second account a **shopkeeper**; the bundled ownership data assumes `userId = 2`.
5. Through the PostgreSQL client, execute the SQL statements defined by `insertPlaceSql` and `insertOwnsSql` inside `populatePlaceAndOwnsTables()` in `model/postgres/tg-model-postgres.mjs`. Copy the SQL statements themselves, without the surrounding JavaScript declarations. For a fresh database, this loads the sample places and associates them with user `2`.
6. Open `http://localhost:3000` to use the application. The default port is `3000`, configurable through `PORT`.

The existing setup helpers are not a complete first-run installer. This outline describes the manual preparation required by the current implementation.

## License

Original project code is available under the [ISC License](LICENSE). Third-party libraries, map data, fonts and images retain their respective licenses and attribution requirements.
