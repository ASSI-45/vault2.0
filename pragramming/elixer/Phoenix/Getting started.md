-- -
https://www.youtube.com/watch?v=9xaN44PNxps
# Installing Phoenix
-- -
```bash
mix local.hex
mix archive.install hex phx_new
```

## Creating a Phoenix project
-- -
```bash
mix phx.new forum --database sqlite3
```

**_Note!:_** You can change the database to witch ever database your using.

## Project Structure
-- -
The hidden directories don't need tinkering, That's why there hidden in the first place. Such are these.
### Hidden files
1. `.elixir_ls` -> Elixir Language server
2. `_build` -> build files and artefacts
3. `gitignore` -> git ignore
4. `.formater` -> config for `mix format`(command)
### Main files and directories
1. `mix.exs` -> contains **dependencies**
2. `mix.lock` -> the **dependencies** retrieved with `mix deps.get` will be noted down here
3. `assets/` -> front-end stuff
4. `config/` -> holds config files
5. `deps/` -> holds dependencies
6. `prev/` -> accessories files that are not running the main app
7. `test/` -> test files for testing the app
8. `lib/` -> app code
## MVC (Model, View and Controller)
-- -
1. [[#Model]]
2. [[#Router]]
3. [[#View]]
4. [[#Controller]]

The controller will get an **GET** request, after witch the **_Controller_** is going to send an request for some _data_ to and from the **_Model_**. After the **_Controller_** has received some data its going to communicate with the **_View_** for some rendering of the page. As lastly after the **_Controller_** has received the _data_ its gowing to send it over to the **Front end**.

# Model
-- -

## Router
-- -
The **Router** file is located under `/lib/<app>/<app>_web/router.ex`. This is most defiantly the **Router** file. This file tells the app with **routes** exist.
# View
-- -

# Controller
-- -