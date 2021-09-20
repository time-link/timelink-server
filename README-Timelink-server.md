# To setup development environment

Fork and clone from https://github.com/time-link/timelink-server.git

```bash
git clone https://github.com/time-link/timelink-server.git
```

## Create .env file

Duplicate `.env-sampple` as `.env` and edit with local values
 (check comments in the file).

 ```bash
 cp .env-sample .env

Be careful not include `.env` in commits. It is already include in
the `.gitignore` file of the project.

## Install poetry with

```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -
```

Add the PATH setting displayed at the end
of the `poetry` install to your `.bash_profile` or equivalent.

Reenter shell or open new terminal session.

## Install dependencies

```bash
cd ./backend/app
poetry install
```

After install check env path with

```bash
poetry env info
```

You can now enter a shell with the new 
environment with

```bash
poetry shell
```

Aditionally setup your editor/to work with this env.



