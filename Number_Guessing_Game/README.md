# Number Guessing Game

A command-line number guessing game written in Bash that uses a PostgreSQL database to track user statistics. This project was built as part of the FreeCodeCamp Relational Database certification.

## Features

* **Interactive Gameplay:** Generates a random secret number between 1 and 1000 and provides higher/lower feedback until the correct number is guessed.
* **Persistent User Data:** Connects to a PostgreSQL database to save usernames and track gameplay stats.
* **Returning User Recognition:** Welcomes back existing players and displays their total games played and their best (lowest) guess count.
* **Input Validation:** Ensures user input is a valid integer before processing the guess.

## Tech Stack

* **Language:** Bash Scripting
* **Database:** PostgreSQL
* **Environment:** Linux / Dev Container

## Prerequisites

To run this script locally, you will need:
* A Linux environment (or Git Bash / WSL on Windows)
* PostgreSQL installed and running

## Setup & Installation

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/number_guessing_game.git](https://github.com/yourusername/number_guessing_game.git)
   cd number_guessing_game

```

2. **Set up the PostgreSQL database:**
Log into your PostgreSQL terminal and run the following commands to create the database and table:
```sql
CREATE DATABASE number_guess;
\c number_guess

CREATE TABLE users (
  user_id SERIAL PRIMARY KEY,
  username VARCHAR(22) UNIQUE NOT NULL,
  games_played INT DEFAULT 0,
  best_game INT DEFAULT 0
);

```


3. **Make the script executable:**
```bash
chmod +x number_guess.sh

```



## Usage

Run the script from your terminal:

```bash
./number_guess.sh

```

You will be prompted to enter a username (up to 22 characters). If it is your first time, the game will welcome you as a new player. If you are returning, it will display your previous stats before the game begins.

## Database Schema

The database relies on a single `users` table to track player history.

| Column | Type | Constraints | Description |
| --- | --- | --- | --- |
| `user_id` | `SERIAL` | `PRIMARY KEY` | Auto-incrementing unique ID |
| `username` | `VARCHAR(22)` | `UNIQUE, NOT NULL` | The player's chosen username |
| `games_played` | `INT` | `DEFAULT 0` | Total number of games finished |
| `best_game` | `INT` | `DEFAULT 0` | The lowest number of guesses used to win |

```

```
