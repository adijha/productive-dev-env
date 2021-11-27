# bash functions

```

function gitpush() {
    git add .
    if [ "$1" != "" ]
    then
        git commit -m "$1"
    else
        print $fg_bold[red] "Oh! you missed to write commit message"
        return 0
    fi # closing statement of if-else block
    git push origin HEAD
}

function gitnew() {
    git checkout master
    git pull
    if [ "$1" != "" ]
    then
        git checkout -b "$1"
    else
        print $fg_bold[red] "Oh! you missed to write branch name"
        return 0
    fi # closing statement of if-else block
}


```
