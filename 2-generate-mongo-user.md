# Creating a User for Your MongoDB Database

- `secure DB` => create a dedicated user w/ access to DB

- ie.,.. configure a dedicated DB + user account for app

- need `root username + password` set in docker-compose.yml

        - ie., `MONGO_INITDB_ROOT_USERNAME` + `MONGO_INITDB_ROOT_PASSWORD`

- `avoid using root user`:

  - create new DB user for app + new DB that allows app access to that particular DB

  `docker exec -it 9eb90bfb bash`//or current container ID

  - Once inside container, `log in to the MongoDB root administrative account`:

  `mongo -u mongodbuser -p`//enter password from yml
                          .ie., ` your_mongodb_root_password ` => NOTE:/reminder: obviously, change this later...+ add to .gitignore in real world app
      `show dbs`

      `use tech`

      `db.createUser({user: 'techuser', pwd: 'your_mongodb_password', roles: [{role: 'readWrite', db: 'tech'}]})`//user and pwd => values defined in docker-compose.yml under `env variables section`=> change password later...

     `exit`

  - Log in to the authenticated DB:

  - first, exit out of current Mongo shell..

      `mongo -u techuser -p your_mongodb_password --authenticationDatabase tech`

  - exit Mongo

      `exit`

  - exit container

      `exit`
