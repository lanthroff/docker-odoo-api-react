## Version

If on mac with apple silicon chip, use branch arm64, use branch amd64 otherwise

## Installation:
0. Clone with submodules
```
git@github.com:lanthroff/docker-odoo-api-react.git --recurse-submodules
```
1. Add odoo.localhost into your host configuration
```
127.0.0.1       odoo.localhost
```

2. Build the containers
```
sudo docker-compose up --build
```

1. Then Run > Start debugging
2. Connect to http://odoo.localhost
3. Create a database with master password being "educacode", then log in
and activate the module "example"
6. Go to users list and check Api Documentation group for your user
7. You can visit the OpenApi documentation at http://odoo.localhost/documentation
   
## Aditionnal memo

Dump the database from the container
```
docker exec -t your-db-container pg_dumpall -c -U your_user > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

Load the database dump into the container
```
cat your_dump.sql | docker exec -i your-db-container psql -U your_user
```

Change the ownership of a file into the container
```
docker exec -u 0:0 your-container chown -R your-user /backup
```