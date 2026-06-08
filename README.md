# Flights CRUD Operation (Express + Sequelize)

This project is a Node.js REST API for flight-related CRUD building blocks.  
Current implemented module: **Airplane creation** using **Express** + **Sequelize** + **MySQL**.

## Tech Stack

- Node.js
- Express
- Sequelize + sequelize-cli
- MySQL (`mysql2`)
- dotenv
- winston (logging)

## Project Structure

```text
src/
  config/         # app/server/logger configuration
  controllers/    # request/response handling
  migrations/     # sequelize DB migrations
  middlewares/    # request middlewares (placeholder)
  models/         # sequelize models
  repositories/   # DB access layer
  routes/         # API route registration
  services/       # business logic layer
  index.js        # app entry point
```

## API Endpoints

Base path: `/api`

- `GET /api/v1/info`  
  Health/info endpoint.

- `POST /api/v1/airplanes`  
  Create an airplane.

  Request body:
  ```json
  {
    "modelNumber": "A320",
    "capacity": 180
  }
  ```

## Setup Instructions

1. Install dependencies:
   ```bash
   npm install
   ```

2. Create `.env` in project root:
   ```env
   PORT=3000
   ```

3. Initialize Sequelize config (if `src/config/config.json` is missing):
   ```bash
   npx sequelize init
   ```
   This creates `src/config/config.json` and seeders/migrations folders (depending on setup).  
   Add your DB credentials for `development`, `test`, and `production`.

4. Run migrations:
   ```bash
   npx sequelize db:migrate
   ```

5. Start server:
   ```bash
   npm run dev
   ```

## Architecture Flow

`Route -> Controller -> Service -> Repository -> Sequelize Model -> MySQL`

- **Controller**: validates/reads request and sends response.
- **Service**: holds business logic.
- **Repository**: performs DB operations.

## Notes

- `src/config/config.json` is gitignored by design.
- Logs are written to console and `combined.log`.