# Disclaimer
I am not a owner of this bot. I just forked the repo and added heroku support.

# Note For Heroku
Anyone who want's to deploy this bot on your heroku account please do not leech any 18+ adult content because i won't be responsible if your app or account get banned. Use your bot on heroku wisely.

# What is this repo about?
This is a telegram bot writen in python for mirroring files on the internet to our beloved Google Drive.

# Inspiration 
This project is heavily inspired from @out386 's telegram bot which is written in JS.

# Features Supported:
- Mirroring direct download links to google drive
- Download progress
- Upload progress
- Download/upload speeds and ETAs
- Docker support
- Uploading To Team Drives.
- Index Link support
- Service account support
- Mirror all youtube-dl supported links
- Mirror telegram files

# Upcoming features (TODOs):

## First visit this link for all the details about bot:
```
https://github.com/lzzy12/python-aria-mirror-bot
```

# Requirement
- Ubuntu or Windows 10 with WSL
- Python3

# How to deploy?
Deploying is pretty much straight forward and is divided into several steps as follows:

- Install Python3
```
sudo apt install python3
```
## Installing requirements for bot
- Download requirements file and install
```
wget https://raw.githubusercontent.com/usmanmughalji/forbot/master/requirements.txt

sudo -H pip3 install -r requirements.txt
```

## Clone this repo and go to folder
```
git clone https://github.com/usmanmughalji/python-aria-mirror-bot-heroku.git

cd python-aria-mirror-bot-heroku
```

## Setup config file
```
mv config_sample.env config.env
```
- Remove the first line saying:
```
_____REMOVE_THIS_LINE_____=True
```
Fill up rest of the fields. Meaning of each fields are discussed below:
- **BOT_TOKEN** : The telegram bot token that you get from @BotFather
- **GDRIVE_FOLDER_ID** : This is the folder ID of the Google Drive Folder to which you want to upload all the mirrors.
- **DOWNLOAD_DIR** : The path to the local folder where the downloads should be downloaded to
- **DOWNLOAD_STATUS_UPDATE_INTERVAL** : A short interval of time in seconds after which the Mirror progress message is updated. (I recommend to keep it 5 seconds at least)  
- **OWNER_ID** : The Telegram user ID (not username) of the owner of the bot
- **AUTO_DELETE_MESSAGE_DURATION** : Interval of time (in seconds), after which the bot deletes it's message (and command message) which is expected to be viewed instantly. Note: Set to -1 to never automatically delete messages
- **IS_TEAM_DRIVE** : (Optional field) Set to "True" if GDRIVE_FOLDER_ID is from a Team Drive else False or Leave it empty.
- **USE_SERVICE_ACCOUNTS**: (Optional field) (Leave empty if unsure) Whether to use service accounts or not. For this to work see  "Using service accounts" section below.
- **INDEX_URL** : (Optional field) Refer to https://github.com/CHEF-KOCH/goindex-drive The URL should not have any trailing '/'
- **TELEGRAM_API** : This is to authenticate to your telegram account for downloading Telegram files. You can get this from https://my.telegram.org DO NOT put this in quotes.
- **TELEGRAM_HASH** : This is to authenticate to your telegram account for downloading Telegram files. You can get this from https://my.telegram.org
- **USER_SESSION_STRING** : Session string
- **Note** : You can limit maximum concurrent downloads by changing the value of MAX_CONCURRENT_DOWNLOADS in aria.sh. By default, it's set to 3

## Generate token.pickle for G-Drive or Team-Drive by running:
```
python3 generate_drive_token.py
```
## Generate Session string by running:
```
python3 generate_string_session.py
```

# Deploying on Heroku
- Login into your heroku account with command and follow on screen instructions:
```
curl https://cli-assets.heroku.com/install-ubuntu.sh | sh

heroku login
```
- Create a new Heroku app:
```
heroku create appname

Example: heroku create myfirstbot
```
- Select this app in your Heroku-cli:
```
heroku git:remote -a appname

Example: heroku git:remote -a myfirstbot
```

- Change Dyno Stack to a Docker Container:
```
heroku stack:set container
```
- Add Private Credentials and Config etc:
```
git add -f config.env token.pickle start.sh
```
- Commit new changes:
```
git commit -m "Add Private Stuff"

git commit -am "Add-Stuffs"
```
- Push Code to Heroku:
```
git push heroku HEAD:master --force
```
- Restart Worker by these commands:
```
heroku ps:scale worker=0
```
```
heroku ps:scale worker=1
```
## Credits, and Thanks to
* [lzzy12 (Owner of the bot)](https://github.com/lzzy12/python-aria-mirror-bot)
* [Bhadoo Cloud (Thanks for approved api)](https://github.com/ParveenBhadooOfficial)
