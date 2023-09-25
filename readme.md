# Rundeck - Ansible Podman project

This is a project directory to build and test Rundeck with the Ansible plugin in Podman or Docker.

## Configuration

- A `.env` file is **mandatory** to be able to build the project:

``` 
RUNDECK_DATABASE_DRIVER=org.mariadb.jdbc.Driver
RUNDECK_DATABASE_USERNAME=rundeck
RUNDECK_DATABASE_PASSWORD=pass
RUNDECK_DATABASE_URL=jdbc:mysql://mysql/rundeck?autoReconnect=true&useSSL=false
RUNDECK_GRAILS_URL=http://localhost:4440

MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=rundeck
MYSQL_USER=rundeck
MYSQL_PASSWORD=pass
```

**Don't forget to change the passwords!**

- Generate the SSH key in **PEM** format:

```
ssh-keygen -t rsa -m pem
```

## Usage

Start the Podman or Docker containers with their respective tools:

```
podman-compose up -d --file compose.yml
```

This will build the necessary containers and start the services.

The User Interface will be available on the http://localhost:4440 URL.

## The exported volumes

- `ansible-data:/etc/ansible/` - for the `hosts` file and the `ansible.cfg`
- `rundeck-home:/home/rundeck/` - for local keys in the `.ssh` directory
- `dbdata:/var/lib/mysql` - database files for data persistance

## License

MIT

## Author

Tamas Molnar - tmolnar0831@gmail.com - https://tomsitcafe.com