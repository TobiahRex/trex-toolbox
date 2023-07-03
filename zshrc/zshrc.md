# [Home](../README.md) > ZSH
Custom tools for improving the ZSH experience.


1. Navigation shortcuts
  ```bash
  alias pro="code ~/.zshrc"
  alias lsa="ls -aGFh"
  alias l='ls'
  alias lsal='ls -al'
  ```
  others for super lazy people
  ```bash
  function mkcd {
    mkdir "$1"
    cd "$1"
  }

  function copy {
    cp -r "$1" "$2"
  }

  function del {
    rm -rf "$1"
  }

  function lk {
    cd "$1"
    ls -atGFh
  }

  function bk {
    cd ..
    ls -atGFh
  }

  function bk2 {
    cd ..
    cd ..
  }

  function bk3 {
    cd ..
    cd ..
    cd ..
  }

  function bk4 {
    cd ..
    cd ..
    cd ..
    cd ..
  }
  ```

2. Find and Kill ports that are in use
  ```bash
  function findport {
    echo "Searching..."
    if [[ "$2" ]]; then
      lsof -i tcp:"$1" | grep "$2"
    else
      lsof -i tcp:"$1"
    fi
  }

  function killport {
    if [[ "$2" ]]; then
      lsof -t -i tcp:"$1" | xargs kill -9
    else
      lsof -t -i tcp:"$1" | xargs kill
    fi
    echo "PORT: $1 killed"

    if [[ "$2" ]]; then
      findport $1 $2
    else
      findport $1
    fi
  }
  ```

3. Refresh your current ZSH profile
  ```bash
  function proref {
    if [[ $# -eq 0 ]]; then
      echo "refreshed"
      builtin . ~/.zshrc
    else
      echo "refreshed"
      builtin . "$@"
    fi
  }
  ```