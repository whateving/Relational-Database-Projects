# Celestial Bodies Database

This project is a relational database built with **PostgreSQL** that models a small fraction of the universe. It was created as part of the freeCodeCamp Relational Database Certification to demonstrate proficiency in database design, schema creation, and SQL constraints.

## Technologies & Skills
* **Database:** PostgreSQL
* **Tools:** psql (CLI), pg_dump
* **Skills Demonstrated:** * Relational database design (Primary and Foreign Keys)
  * Data typing (`VARCHAR`, `INT`, `NUMERIC`, `BOOLEAN`, `TEXT`)
  * Data integrity constraints (`UNIQUE`, `NOT NULL`)
  * Table sequencing (`SERIAL` auto-incrementing IDs)
  * Writing `CREATE TABLE` and `INSERT INTO` queries

## Database Schema
The `universe` database consists of five interconnected tables modeling celestial hierarchy:

1. **`galaxy`**: The top-level table containing different types of galaxies.
2. **`star`**: Stars belonging to specific galaxies.
3. **`planet`**: Planets orbiting specific stars.
4. **`moon`**: Moons orbiting specific planets.
5. **`constellation`**: A standalone table detailing star groupings.

### Relationships
* A **Star** belongs to a **Galaxy** (`galaxy_id` foreign key).
* A **Planet** orbits a **Star** (`star_id` foreign key).
* A **Moon** orbits a **Planet** (`planet_id` foreign key).

## How to Run Locally

If you want to view or query the database on your local machine, follow these steps:

**1. Clone the repository and navigate to the .sql file folder.**

**2. Ensure PostgreSQL is installed and running.**

**3. Log into your PostgreSQL terminal:**

```bash
psql -U postgres

```

**4. Rebuild the database from the dump file:**
Once inside the directory containing the `universe.sql` file, run the following command in your regular bash terminal to rebuild the database:

```bash
psql -U postgres < universe.sql

```

**5. Connect to the database:**

```sql
\c universe

```

*You can now run custom queries, like `SELECT * FROM planet;`, to explore the data!*

## Acknowledgements

* Built as a requirement for the [freeCodeCamp Relational Database Certification](https://www.freecodecamp.org/learn/relational-database/).

```

**A quick tip for GitHub:** Don't forget to replace `YOUR-USERNAME` and `YOUR-REPO-NAME` in the clone command with your actual GitHub username and repository name before committing the file!
