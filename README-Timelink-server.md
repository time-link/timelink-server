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
```

Be careful not include `.env` in commits. It is already include in
the `.gitignore` file of the project.

## Install `npm`

You need to have npm and node even if your are only developing the backend.

This is because in the development setup the frontend runs locally and requires node.
### Mac

Install npm with homebrew.

If you don't have `homebrew` follow instructions at https://brew.sh

```console
brew update
brew install node
% node -v
v16.9.1
% npm -v
7.21.1
```

Enter the `frontend` directory, install the NPM packages and start the live server using the `npm` scripts:

```bash
cd frontend
npm install
npm run serve
```

Then open your browser at http://localhost:8080


## Install poetry 

```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -
```

Add the PATH setting displayed at the end
of the `poetry` install to your `.bash_profile` or equivalent.

Reenter shell or open new terminal session.

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

Additionally setup your editor/to work with this env.



