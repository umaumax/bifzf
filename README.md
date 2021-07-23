# bash implemented fuzzy finder

## how to use
``` bash
ls | bifzf
```

e.g. for docker exec
``` bash
docker-exec () {
  local container_id=$(docker ps | bifzf | awk '{print $1}')
  [[ -z $container_id ]] && return
  docker exec -it $container_id /bin/bash
}
```
