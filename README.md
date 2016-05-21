# Circle CI and Github Pages.
Playing with [CircleCi](https://circleci.com) to deploy automatically projects to [gh-pages](https://pages.github.com/).

You can see the results [here](http://andresvillanueva.com.ve/deployment-circleci-gh-pages/)¡Say hi to this cute kittie!. Files are available at [develop](https://github.com/Villanuevand/deployment-circleci-gh-pages/tree/develop) or [master](https://github.com/Villanuevand/deployment-circleci-gh-pages/tree/master) branches .
.

Special thanks to:
* [Eldarlabs](https://github.com/eldarlabs) github organization, for the repo [eldarlabs/ghpages-deploy-script](https://github.com/eldarlabs/ghpages-deploy-script).
* [@jcouyang](https://github.com/jcouyang) for  [circle.yml](https://gist.github.com/jcouyang/81ae59d10c15572c79d8) gist.
* [@motemen](https://github.com/motemen) for [push-gh-pages.sh
](https://gist.github.com/motemen/8595451) gist.

## ¿How can i do it?

### Configure user Machine at Circle CI.
Go to this [link](https://circleci.com/docs/github-security-ssh-keys/#machine-user-keys) and follow the instructions. ¡Are really simple!

### Create the circle.yml file
You can configurate the circle.yml file to you needs, in this [link](https://circleci.com/docs/configuration/). But, i used the followed [circle.yml file](https://github.com/eldarlabs/ghpages-deploy-script/blob/master/circle.yml).

### Create deploy.sh script
I use this [deploy.sh](https://github.com/eldarlabs/ghpages-deploy-script/blob/master/scripts/deploy-ghpages.sh) script courtesy of [@eldarlabs](https://github.com/eldarlabs).

### Configure Circle CI variable enviroment
The script also seems to require you to init the git user and email. To hide this information, the script will grab the information from circleci environment variable. You will need to configure environment variables GH_NAME (GitHub Name) and GH_EMAIL (GitHub Email).
#### But.. ¿How can i do that?
* Really simple just go to [CircleCi](https://circleci.com)
* Click on project settings => Build Settings => Enviroment Variables
* Add 2 new enviroment variables:
    * GH_NAME (GitHub Name) .
    * GH_EMAIL (GitHub Email).

_Reference Image - Enviroment Variables Configuration:_

![Enviroment Variable - Villanuevand](http://drive.google.com/uc?export=view&id=0ByoQ8u8IrvxGZ0hXRkxFeFlKRDQ)

### Mark `deploy.sh` as executable
Into `./scripts` folder run `chmod +x deploy.sh` to make the script executable and avoid build error:
```.sh
./scripts/deploy.sh build
bash: line 1: ./scripts/deploy.sh: Permission denied

./scripts/deploy.sh build returned exit code 126

Action failed: ./scripts/deploy.sh build
```

Push any change to `master` branch, check the build in Circle Ci, and enjoy how push automatycally to your `gh-page` branch.

**¡Feel free to contribute!**

#### License
[MIT License](https://raw.githubusercontent.com/Villanuevand/deployment-circleci-gh-pages/master/LICENSE).

Copyright (c) 2016 Andrés Villanueva.

