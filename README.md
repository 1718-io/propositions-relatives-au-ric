# Quelques propositions quant au RIC

## Dev environment

### Debian and GNU / Linux


```bash
# ---- ----------- ---- #
# ----  GIT CONFIG ---- #
# ----  ---------- ---- #

git config --global commit.gpgsign true
git config --global user.name "Jean-Baptiste-Lasselle"
git config --global user.email jean.baptiste.lasselle.pegasus@gmail.com
git config --global user.signingkey 7B19A8E1574C2883
# Now, to sign Git commits, for example inside an SSH session (where TTY is a bit different ...)
export GPG_TTY=$(tty)

git config --global --list

# will re-define the default identity in use
# https://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch06_04.htm
ssh-add ~/.ssh.perso.backed/id_rsa

export GIT_SSH_COMMAND='ssh -i ~/.ssh.perso.backed/id_rsa'
ssh -Ti ~/.ssh.perso.backed/id_rsa git@github.com

# if [ -d ~/propositions-relatives-au-ric ]; then
  # rm -fr ~/propositions-relatives-au-ric
# fi;

git clone git@github.com:gravitee-lab/propositions-relatives-au-ric.git ~/propositions-relatives-au-ric
cd ~/propositions-relatives-au-ric

export FEATURE_ALIAS='ric-interne'
# git flow feature start ${FEATURE_ALIAS} && git push -u origin --all
# git checkout "feature/${FEATURE_ALIAS}"
export COMMIT_MESSAGE="feat.(${FEATURE_ALIAS}): adding build and run with https://github.com/gravitee-io/gravitee-docs/blob/master/Dockerfile "
# git add --all && git commit -m "${COMMIT_MESSAGE}" && git push -u origin HEAD
atom .

```


* run the hugo dev server, in the same folder, in antoher shell session, in parallel :

```bash
# go must be installed
export PATH=$PATH:/usr/local/go/bin
hugo serve --watch -b http://127.0.0.1:1313/
```

#### Installations on the dev machine


* Intall hugo extended version (some hugo themes require that, and the hugo compose theme requries it, to build sass css resources) :

```bash
export PATH=$PATH:/usr/local/go/bin
# check you hugo version with [hugo version] command
# My hugonon extended installed  version was [v0.78.2] so I set HUGO_VERSION to 0.78.2 (without the v, to be pure semver)
# Set the HUGO_VERSION to the version of your hugo installation
export HUGO_VERSION=0.78.2
echo "HUGO_VERSION=[${HUGO_VERSION}]"

mkdir -p ~/.hugo.extended/v${HUGO_VERSION}
git clone https://github.com/gohugoio/hugo.git ~/.hugo.extended/v${HUGO_VERSION}
cd ~/.hugo.extended/v${HUGO_VERSION}
git checkout "v${HUGO_VERSION}"
go install --tags extended
```

* Install the Golang platform

```bash
# Choose the version of golang you want at [https://github.com/golang/go/releases]
export GOVERSION=1.15.6
export GOOS=linux
export GO_CPU_ARCH=amd64

export DWLD_URI=https://golang.org/dl/go${GOVERSION}.${GOOS}-${GO_CPU_ARCH}.tar.gz

curl -LO https://golang.org/dl/go${GOVERSION}.${GOOS}-${GO_CPU_ARCH}.tar.gz

mkdir -p /usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}

# ---
# delete any previous installation

if [ -f /usr/local/go ]; then
 sudo rm -fr /usr/local/go
fi;

if [ -f /usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}/go ]; then
 sudo rm -fr /usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}/go
fi;

sudo tar -C /usr/local -xzf go${GOVERSION}.${GOOS}-${GO_CPU_ARCH}.tar.gz

# [/usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}/go] is a folder, executables are in [/usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}/go/bin]
sudo ln -s /usr/local/golang/${GOVERSION}/${GOOS}/${GO_CPU_ARCH}/go /usr/local/go

unset GOVERSION
unset GOOS
unset GO_CPU_ARCH

export PATH=$PATH:/usr/local/go/bin
go version
```


### CORS configuration of the http server

The Apache 2 HTTP Server "`httpd`" is used to deploy the website to Heroku. An `httpd.conf` configuration file was added to configure CORS to allow all origins :

```ini
#
# Apparemment, d'après [https://enable-cors.org/server_apache.html] :
#
Header set Access-Control-Allow-Origin "*"
```

### Docker images and the GIT COMMIT ID

* to retrievethe GIT COMMIT ID fromthe docker image : ccc
* and to find the same commit ona git repo :

```bash
# ---
#
git log --abbrev-commit --pretty=oneline
# ---
# And from the graph displayed here :
git log --graph --abbrev-commit --decorate --date=relative  --format=format:'%C(bold red)%h%C(reset)%C(bold green)%d%C(reset) %C(bold blue)%ai %C(reset) %C(yellow)%ar%C(reset)%n'' %C(white)%s%C(reset) %C(dim white)- %an%C(reset)' --all

# ---
# also
git log --graph --decorate --pretty=oneline --abbrev-commit --all
```
