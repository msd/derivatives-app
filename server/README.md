# Instructions To Run Server

Make sure python 3.7 and npm 6.13+ are both installed on your system.

## Windows

### Install requirements

OPTIONAL: activate a venv (to avoid installing these packages globally).

In terminal execute 
`pip install django jellyfish tensorflow keras django-webpack-loader`


### Run server
`cd` to this directory (`server`)

Django by default uses port 8000, you can omit it in the following command.
`python manage.py runserver 8000`.
If you have troubles with this port you can try a different one.

If successful the (second to) last line in console will be
`Starting development server at http://127.0.0.1:8000/`

Connect on `localhost:8000` (or whatever port you may have specified)

Stop server using `Ctrl+C`

## Mac/Linux

### Install python modules
In terminal execute 
`pip3 install django jellyfish tensorflow keras django-webpack-loader`

### Run server
`cd` to this directory (`server`)

Django by default uses port 8000, you can omit it in the following command:
`python3 manage.py runserver 8000`.
If you have troubles with this port you can try a different one.

If successful the (second to) last line in console will be
`Starting development server at http://127.0.0.1:8000/`

Connect on `localhost:8000` (or whatever port you may have specified)

Stop server using `Ctrl+C`

## Login to admin page

(Mac/Linux please replace `python` with `python3`)

Create a superuser (only needs to be done when the database is new/deleted)

`python manage.py createsuperuser`

`python manage.py makemigrations`

`python manage.py migrate`

Admin page URL: `localhost:8000/admin`

## Load CSV data

Assumes data directory is extracted alongside the server directory

```bash
python manage.py migrate
python manage.py shell  # This will create a python shell!
```

Then, in the created Python shell:

```python
>>>import loadcsv
>>>loadcsv.main()
```

Note: For example purposes it is sufficient to load a single year.
(Approx 10 minutes for `all` months YMMV)
Select more years at your own risk (and waste of time).

Note Note: Do not commit the resulting `db.sqlite3` file yet...

## Install React dependencies

`npm install`

A node environment has been set up via `npm init`, so you can just make your way to the `server/` directory and run the following commands:

We use django-webpack-loader because it automatically interfaces between Django and the bundles created by webpack. It's hugely helpful and does a bunch of busywork for us :)

## Bundle Webpack data and run server

To bundle any changes you have made to the React code, you should run, from the directory `server/`:

```bash
npm run build
```

To automatically re-bundle if any changes are made, you can tell Webpack to watch the files with:

```bash
npm run watch
```

After this, you can run the server as usual with `python3 manage.py runserver 8000`.
