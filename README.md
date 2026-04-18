# CRICS Backend

A Node.js/Express backend that manages cricket events, players, matches, teams, and leaderboards using a MySQL database.

## Features

- CRUD operations for events
- Player creation, lookup by ID/email, and registration
- Match creation and retrieval (all/upcoming)
- Team lookup by player membership
- Leaderboard queries for top batsmen and top bowlers
- Uses MySQL for persistent storage

## Requirements

- Node.js 18+ recommended
- MySQL database

## Installation

1. Clone the repository.
2. Install dependencies:

```bash
npm install
```

3. Create a `.env` file in the project root with database credentials:

```env
PORT=3306
MYSQLHOST=localhost
MYSQLPORT=3306
MYSQLUSER=root
MYSQLPASSWORD=your_password
MYSQLDATABASE=your_database
```

4. Start the server:

```bash
node index.js
```

## Default Server Behavior

The server listens on `process.env.PORT` or `3306`.

## Available API Routes

Base path: `/api`

### Events

- `GET /api/events/` - List upcoming events
- `GET /api/events/:id` - Get event by ID
- `POST /api/events/` - Create a new event
- `DELETE /api/events/:id` - Delete an event

### Players

- `GET /api/players` - List all players
- `POST /api/players` - Add a new player
- `GET /api/players/:id` - Get player by ID
- `GET /api/players/email/:email` - Get player by email
- `GET /api/players/:id/recent-matches` - Get recent match stats for a player
- `GET /api/players/id-by-email/:email` - Get player ID by email
- `POST /api/register` - Register a player with name, email, password, and role

### Matches

- `GET /api/matches` - List all matches
- `GET /api/matches/upcoming` - List upcoming matches
- `POST /api/matches` - Add a new match

### Teams

- `GET /api/team/my-team/:player_id` - Get a player's team and its members

### Leaderboard

- `GET /api/top-batsmen` - Top 10 batsmen and wicket-keepers by runs
- `GET /api/top-bowlers` - Top 10 bowlers and all-rounders by wickets

## Database Notes

The application expects MySQL tables such as:

- `events`
- `players`
- `matches`
- `match_statistics`
- `teams`
- `player_team`

Adjust the schema to match the SQL queries used in the code.

## Security Notes

- Do not commit your `.env` file.
- Passwords are inserted directly into the database in the current implementation and should be hashed before production use.

## License

This repository uses the ISC license as declared in `package.json`.
