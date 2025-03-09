# traefik-as-a-reverse-proxy
Using Traefik as a reverse proxy to run multiple applications on one Docker Host.

## Setting up
### What needs to be established:
Docker and Docker-compose

### Cloning repo
To customize, make a repository clone in the desired folder
```
https://github.com/Kaboom-Corporation/traefik-as-a-reverse-proxy
```
### Edit data
1. Then open the file `traefik-configurations/traefik-data/traefik.yml` and change `example.com` to the email address where the certificate information will be sent.

2. And then run the command `htpasswd -nb admin Your_security_password` (needed install `apt-get install apache2-utils`). 
Where `Your_security_password` is your super secret password.
Then we change the `PASSWORD` in the file `traefik-configurations/traefik-data/configurations/dynamic.yml` to the obtained value.

3. Open `traefik-configurations/docker-compose.yml` and change `example.com` to your domain name.
4. Give the file `traefik-configurations/traefik-data/acme.json` 600 access with the command: 
`
chmod 600 acme.json
`

### Finally
Go back to the directory where `docker-compose.yml` is (the default is `traefik-configurations`) and write the command: `docker-compose up`. If there are no errors, then disconnect and write the command `docker-compose up -d`, which does not block the console
