## Procédure:

On lance le docker-compose
```
sudo docker-compose up -d --build
```

On attach le debug dans VsCode avec F5 ou Run > Start debugging

## Liste des extensions interressantes:

![alt text](extensions.png)

## settings.json

```
{
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode",
        "editor.formatOnSave": true
    },
    "[python]": {
        "editor.formatOnSave": true
    },
    "python.linting.pylintEnabled": false,
    "python.linting.flake8Enabled": true,
    "python.linting.enabled": true,
    "python.formatting.provider": "black",
    "python.linting.banditEnabled": false,
    "window.zoomLevel": -1,
    "workbench.iconTheme": "material-icon-theme",
    "tabnine.experimentalAutoImports": true,
    "redhat.telemetry.enabled": false,
    "[xml]": {
        "editor.defaultFormatter": "redhat.vscode-xml",
        "editor.formatOnSave": true
    },
    "python.defaultInterpreterPath": "/usr/bin/python3"
}
```

## Aditionnal memo


Pour dump la db du container
```
docker exec -t your-db-container pg_dumpall -c -U your_user > dump_`date +%d-%m-%Y"_"%H_%M_%S`.sql
```

Pour push le dump dans le container de la db
```
cat your_dump.sql | docker exec -i your-db-container psql -U your_user
```

Pour changer le ownership des fichier dans un container depuis le host
```
docker exec -u 0:0 your-container chown -R your-user /backup
```