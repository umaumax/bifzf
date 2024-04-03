# bash implementation of fuzzy finder

This is for a poor target machine or temporary .bashrc setting login environment.

## how to use
``` bash
ls | bifzf

seq 1 30 | BIFZF_MAX_LINE=20 bifzf
```

e.g.
``` bash
function docker-exec () {
  local container_id=$(docker ps | bifzf | awk '{print $1}')
  [[ -z $container_id ]] && return
  docker exec -it $container_id /bin/bash
}

BLACK=$'\e[30m' RED=$'\e[31m' GREEN=$'\e[32m' YELLOW=$'\e[33m' BLUE=$'\e[34m' PURPLE=$'\e[35m' LIGHT_BLUE=$'\e[36m' WHITE=$'\e[37m' GRAY=$'\e[90m' DEFAULT=$'\e[0m'

# kubectl log fzf
function klf() {
  clear
  local kpod_line=$(kubectl get pods -A | BIFZF_MAX_LINE=30 fzf)
  [[ -z $kpod_line ]] && return
  local namespace=$(echo $kpod_line | awk '{print $1}')
  local name=$(echo $kpod_line | awk '{print $2}')
  echo kubectl logs pods/$name -n $namespace
  echo "${GREEN}kubectl logs pods/$name -n $namespace ${DEFAULT}"
}

# kubectl describe fzf
function kdf() {
  clear
  local kpod_line=$(kubectl get pods -A | BIFZF_MAX_LINE=30 fzf)
  [[ -z $kpod_line ]] && return
  local namespace=$(echo $kpod_line | awk '{print $1}')
  local name=$(echo $kpod_line | awk '{print $2}')
  kubectl describe pods/$name -n $namespace
  echo "${GREEN}kubectl describe pods/$name -n $namespace ${DEFAULT}"
}
```

