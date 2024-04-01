# bash implementation of fuzzy finder

This is for a poor target machine or temporary .bashrc setting login environment.

## how to use
``` bash
ls | bifzf

seq 1 30 | BIFZF_MAX_LINE=20 bifzf
```

e.g. for docker exec
``` bash
docker-exec () {
  local container_id=$(docker ps | bifzf | awk '{print $1}')
  [[ -z $container_id ]] && return
  docker exec -it $container_id /bin/bash
}
```

