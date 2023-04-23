# CELESTIA-TOOL
A tool to help you monitor Celestia nodes. And automatically send notifications to your telegram bot. 


## Some function of the tool

- Check if the CPU usage is too high.
- Check if the RAM usage is too high.
- Check if the disk usage is too high.
- Check if the chain is stuck.
- Check samples height.
- Check node is synching.
- Report P2P checking.
- Report State checking.

## Setup Telegram Bot
First, you need to create a new bot using the Telegram BotFather. Open a chat with the BotFather on Telegram by searching for **`@BotFather`** in the search bar and click on it. Then type the command **`/newbot`** to start the process.<br>
The BotFather will ask you to choose a name and a username for your new bot. The name can be anything you want, but the username must be unique and end in bot (e.g. MyBot123_bot). Once you've chosen a name and username, the BotFather will give you an API token. This token is what you will use to access your bot's API, so make sure to keep it safe.<br>
Now, create a new telegram group adding the bot you have just created to the group, then you need to get the **id** of the chat.<br>
To get the id you have several options, the easiest way is to add **`@getidsbot`** to your group and the bot will automatically send the group id to the chat group.<br>
You will use the **`API token`** and **`id`** during the installation. I will name them <tg_token> and <tg_chat_id>.  

## Pre-condition
Clone repository
```bash
git clone https://gitlab.com/celestia_job/tool.git ~/tool
```

Make sure you have python3 on your server.<br>
To check python3 version, use the following command
```bash
python3 -V
which python3
```
If you don't have python, please follow these step
1. Install **`pyenv`**
```bash
sudo apt update -y
sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git 
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc
exec "$SHELL"
```
2. Install **`python3.8.10`**
```bash
pyenv install 3.8.10 
```
3. Create virtual environment and active
```bash
cd ~/tool
~/.pyenv/versions/3.8.10/bin/python -m venv venv
```

## Install & Update
1. Install requirements

Change python3 path with your path
```bash
cd ~/tool
venv/bin/python3 install -r requirements.txt
```
2. Create environment variables 
```bash
cp .env.example .env
```
Fill in the necessary parameters for the environment file: **`.env`**
3. Start tool with nohup
```bash
cd ~/tool
nohup python3 main.py 1>/dev/null 2>/dev/null &
```
4. To stop service, run the bellow command
```bash
kill -9 $(ps -aux | grep "python3 main.py" | awk '{print $2}')
```

## Done =))
Demo: https://t.me/CelestiaLightNodeTool