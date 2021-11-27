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
<hr/>

# Auto Refresh on code change

### you need to install these tools

```
brew install chrome-cli
sudo npm i -g nodemon 
```

### permission

![image](https://user-images.githubusercontent.com/42930642/143677146-7421d6d1-3b6e-44c2-814a-aeb380a51760.png)


### script

save this file as refresher.js in root directory

```
const { exec } = require('child_process');

const merchantDashboard = 'Razorpay Dashboard';
const adminDashboard = 'Razorpay - Admin Panel';

function reloadTab(tabId) {
  exec('chrome-cli reload -t ' + tabId, (error, stdout, stderr) => {
    if (error) {
      console.log(`error: ${error.message}`);
      return;
    }
    if (stderr) {
      console.log(`stderr: ${stderr}`);
      return;
    }
    if (stdout) {
      console.log(`stdout: ${stdout}`);
      return;
    }
  });
}
function refreshChromeTab(matchString) {
  exec('chrome-cli list tabs', (error, stdout, stderr) => {
    let tabId = '';
    if (error) {
      console.log(`error: ${error.message}`);
      return;
    }
    if (stderr) {
      console.log(`stderr: ${stderr}`);
      return;
    }
    let arrTab = stdout.split('\n');
    arrTab.forEach(element => {
      if (element.includes(matchString)) {
        tabId = element
          .split(' ')[0]
          .replace('[', '')
          .replace(']', '');
      }
    });
    reloadTab(tabId);
  });
}

refreshChromeTab(adminDashboard);

```

### RUN COMMAND

```
nodemon  -e js,styl  refresher.js 
```


