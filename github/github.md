# Github
Shortcuts for Github

1. Make a quick commit
  ```bash
  function gtup {
    git add .
    git commit -m "$1"
    git push
  }
  ```

2. Show the current origin address
  ```bash
  function gtr {
    git remote -v
  }
  ```
3. Change the current origin address
  ```bash
  function gtrchange {
    git remote remove origin
    git remote add origin "$1"
    git remote -v
  }
  ```
4. Clone a repo and cd into it
  ```bash
  function gtclone {
    if [ "$2" ]
    then
      git clone "$1" "$2"
      cd "$2"
      lsa
      ahere
    else
      git clone "$1"
      lsa
    fi
  }
  ```