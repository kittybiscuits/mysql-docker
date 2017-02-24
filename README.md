# Purpose

A quick and simple local MySQL server for development or testing.

MySQL version: 8.0

## Notes

MySQL data files are created in your home directory (in `$HOME/docker-data/mysql`) and will
persist across container destruction and recreation.

This location can be changed by editing `volumes` in [docker-compose.yml](docker-compose.yml).

# Database initialization

Upon container creation, the database will be empty. You will need to do one or a combination of
the following:

- Manually create your database schema.
- Have your application create the database schema and run migration scripts.

## Automation via Docker

You can also have your database initialized during container creation via sql and bash scripts.

To have `*.sql`, `*.sql.gz`, and `*.sh` scripts automatically run on container creation:

1. Place the script(s) in the [init](init) directory.
1. Edit [init/Dockerfile](init/Dockerfile) and specify each script appropriately.
	- One example is provided (commented out) for reference.

# Usage

Use the following information to connect to the database. These values may be changed in
[docker-compose.yml](docker-compose.yml).

- Hostname: 127.0.0.1
- Port: 3306
- Admin username: root
- Admin password: (none)

# Convenience scripts

The following convenience scripts are provided:

- [start.sh](start.sh) - Start the container. Download and build images if necessary.
- [stop.sh](stop.sh) - Stop the container. Does not destroy anything.
- [destroy.sh](destroy.sh) - Kill and destroy the container. Does not delete any data.

# Troubleshooting

Validate the contents of [docker-compose.yml](docker-compose.yml):

	$ docker-compose config

View the status of the container:

	$ docker-compose ps

# Reference

- [MySQL image docs](https://store.docker.com/images/3083290a-203f-4c04-b2de-cc057959d2c9?tab=description)

