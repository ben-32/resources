Edit shell configuration:
```console
open ~/.zshrc
```

Make `clear` actually clear the console, not just scroll down (add to shell configuration):
```console
alias clear="clear && printf '\e[3J'"
```

Enforce automatic shut-down (5:25pm) to limit overtime:
```console
sudo pmset repeat shutdown MTWRFSU 17:25:00
sudo crontab -e
    30 17 * * * /sbin/shutdown -h now
```

Clear Poetry cache:
```console
rm -rf .cache/pypoetry
poetry cache clear . --all
```

Annihilate Docker resources:
```console
docker stop `docker ps -q`
docker rm `docker ps -a -q`
docker rmi `docker images -q`
docker volume rm `docker volume ls -qf dangling=true`
docker network remove `docker network ls -q`
docker-compose down
```

```console
running=$(docker ps -q)
if ! [ -z ${running} ]; then
    docker stop ${running}
fi
docker system prune -f --volumes --all
```
