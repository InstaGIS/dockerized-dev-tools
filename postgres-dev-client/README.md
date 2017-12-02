PostgreSQL + Python development client
======================================

## What's included
- PostgreSQL client & psycopg2
- Python 3 & IPython
- Virtualenv & Virtualenvwrapper

## Usage

### Run image in container

- Shell without access to the running user's home directory:
`$ docker run --net=host -ti jtrhinstagis/postgres-dev-client`
- If both the uid and gid of the user running the container are **1000**:
`$ docker run -v $HOME:/home/instauser --net=host -ti jtrhinstagis/postgres-dev-client`
- Otherwise:
`$ docker run -v $HOME:/home/instauser -u root --net=host -ti jtrhinstagis/postgres-dev-client`

**Tip**: Create an alias, e.g. `$ alias instapy="docker run -v $HOME:/home/instauser --net=host -ti jtrhinstagis/postgres-dev-client"`

### Run Python interpreter

```
instauser@f7488b691b51:~$ ipython
In [1]: import psycopg2
In [2]: conn = psycopg2.connect("postgresql://myuser:mypass@myhost/mydb")
```
