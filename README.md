# Node Auth Boilerplate

this is a boiler plate for an Express app with local user authentication. It exists so I have a customized boilerplate and don't have to start from scratch on all my projects.

## What It Includes

* Local Auth (email and password)
* Passport and passport-local
* Sessions for saving user info and displaying flash message
* Settings for PostresSQL and sequelize
* Hashed passwords
* EJS templating and ejs layouts
* Sequelize user model
* Materialize styling - nav and footer

## Included Models
**User Model**

| column | Type | Notes |
| ----------- | ---------- | --------------------|
| id | Integer | Serial primary key |
| firstname | String | Required lenght > 1 |
| lastname | String | - |
| email | String | Serial Unique Login |
| password | String | Hash |
| birtday | Date | - |
| admin | Boolean | Defaulted to False |
| pic | String | - |
| bio | text | - |
| createdAt | Date | Automatically added by Sequelize |
| updatedAt | Date | Automatically added by Sequelize |

## Included Routes

**Routes in Index (main)**

| Method | path | purpose |
| ----| ------------------------- | --------------- |
| GET | `/` | Home page |
| GET | `*` | Catch-all for 404s |

**Routes in controllers/auth.js**

| Method | path | purpose |
| ----| ------------------------- | --------------- |
| GET | `/auth/login` | Render login form |
| POST | `/auth/login` | Process login data |
| GET | `/auth/signup` | Render sign form |
| POST | `/auth/signup` | Process sign data |
| GET | `/auth/logout` | Remove user from session + redirect |

**Routes in controllers/profile.js**

| Method | Path | Purpose |
| ------ | ---------------------- | ---------------------------- |
| GET | `/profile/user` | Show user dashboard (authorized user only) |
| GET | `/profile/admin` | Show admin dashboard (authorized admin only) |
| GET | `/profile/guest/:id` | View user dashboard as guest (authorized user only) |

## Directions For Use

### 1. Clone the repository, but with a diffrent name

Run on the terminal

```sh
git clone <repo_link> <new_name>
```
**For example**

```sh
git clone git@github.com:davidvelichko52/node-auth-boiler-1.git shiny-new-project
```

### 2. Install the modules from package.json

```sh
npm i
```

### 3. Customize the new project

Remove defaulty stuff. For example:

* Tile in `layouts.ejs`
* Logo field in the nav bar
* Description and Repositry fields in package.json
* Remove this bpilerplate's readme content
* Swith Favicon to project-specific one (in `layouts.ejs` head section)

### 4. Create a new datebase for the new project

```sh
create <new_db_name>
```
**For example

```sh
createdb shiny_db
```

### 5. Alter Sequelize Config File

In `config/config.json`, update the database to the one created in step 4. Other settings likely okay, but check username, password, and dialect.

### 6. Check user model for relevance to new project's needs

For example, if the new project dosen't need a birthday field, then delete it from the user model and user migration files.

### 7. Run the Sequelize migrations

```sh
sequelize db:migrate
```
