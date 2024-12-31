# Virtual Machine Setup

> [!IMPORTANT]
> These instructions are specific to Ubuntu 24.04 LTS

## Initialize

```bash
sudo apt update && sudo apt upgrade
(optional) sudo apt install vim
(optional) sudo snap install code --classic
```

## Set up SSH key

```bash
ssh-keygen -t ed25519 -C "<email>"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/<private key>
```

## Set up Git

- Add public key to GitHub as authentication and (optional) signing key

```bash
sudo apt install git
git config --global user.name "<username>"
git config --global user.email "<email>"
(optional) git config --global commit.gpgsign true
(optional) git config --global gpg.format ssh
(optional) git config --global user.signingkey ~/.ssh/<public key>
```

## Download Odoo

```bash
(full repo) git clone git@github.com:odoo/odoo.git
(single branch) git clone git@github.com:odoo/odoo.git --depth 1 --branch <v> --single-branch ./odoo<v>/
```

## Set up Python

```bash
sudo apt install python3.xx-venv
cd ./odoo<v>/
python3.xx -m venv venv
source venv/bin/activate
(venv) pip install --upgrade pip
```

## Set up PostgreSQL

```bash
sudo apt install postgresql postgresql-client
sudo -u postgres createuser -d -R -S $USER
createdb $USER
```

### Initialize DB without demo data

```bash
(venv) python odoo-bin -i base -d $USER --without-demo all
```

## Install Dependencies

```bash
sudo apt install python3-pip libldap2-dev libpq-dev libsasl2-dev
(venv) pip install -r requirements.txt
sudo apt install wkhtmltopdf
```

## Set up VSCode to Recognize Odoo

Open workspace settings
```
CTRL + SHIFT + P
>> Preferences: Open Workspace Settings (JSON)
>>>> "python.analysis.extraPaths": ["/path/to/odoo/source"]
```
