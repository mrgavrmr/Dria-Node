# Dria-Node
## Dria: Node Installation Guide
**In this Dria guide, we’ll show you how to easily set up a Dria node and start using this innovative platform for synthetic data generation. Our step-by-step guide will help you get your Dria node up and running—even if you’re just getting started with such technologies.**
[![](https://img1.teletype.in/files/45/5d/455d8a14-1d9d-4257-9366-66eef99f99e8.png)](https://img1.teletype.in/files/45/5d/455d8a14-1d9d-4257-9366-66eef99f99e8.png)
## About Dria
> Dria is a cutting-edge synthetic data generation platform that combines high quality, diversity, and complexity in a single interface. The Dria node enables you to create, manage, and scale data synthesis processes without requiring powerful hardware. With Dria, you can rapidly generate high-quality datasets for your AI projects using built-in tools and distributed processing capabilities.
## Dria Node Installation: Step-by-Step Guide
`Minimum server requirements: 8 CPU cores, 16 GB RAM, 200 GB SSD, Ubuntu 20.04+ OS`
## Installation Preparation
###  Obtaining an API Key
**Depending on your chosen AI models, you'll need to acquire an API key. This guide uses Google's Gemini model, but alternatives are available:**

**Gemini (FREE): [Get API key](https://aistudio.google.com/app/apikey "Get API key")**

**OpenRouter (paid): [Get API key](https://openrouter.ai "Get API key")**

**Ollama (free): No API required but consumes your system resources (requires powerful VPS)**

**OpenAI (paid): [Get API key](https://platform.openai.com/api-keys "Get API key")**

**Simply follow the link and click "Get API key" for your selected service.**
[![](https://img3.teletype.in/files/68/bf/68bfb898-4934-4786-a807-4a6c703bfa76.png)](https://img3.teletype.in/files/68/bf/68bfb898-4934-4786-a807-4a6c703bfa76.png)
**Accept the license agreement and click 'Create API key' on the next screen**
[![](https://img1.teletype.in/files/c0/ab/c0ab0082-ea49-4504-9f7b-cc31c7cb702b.png)](https://img1.teletype.in/files/c0/ab/c0ab0082-ea49-4504-9f7b-cc31c7cb702b.png)
**Then copy and save the key - you'll need it during the installation process.**
[![](https://img4.teletype.in/files/78/1c/781cede6-e50e-405e-84f3-2647d081d188.png)](https://img4.teletype.in/files/78/1c/781cede6-e50e-405e-84f3-2647d081d188.png)
## Obtaining Your Private Key
**Go to your wallet and follow the steps shown in the screenshot to get the private key.**
[![](https://img4.teletype.in/files/fa/36/fa3669e1-6ab8-4cff-bd7d-c5bcb41a7d99.png)](https://img4.teletype.in/files/fa/36/fa3669e1-6ab8-4cff-bd7d-c5bcb41a7d99.png)
## Connecting to the Server
**To connect to your server via SSH, run the following command in your terminal:**

`ssh username@hostname`
**username** – The username provided after purchasing the server (usually root).

**hostname** – Your server’s IP address.

**Password Input**
> When prompted, enter your password (characters won’t display for security).
You can paste the password (right-click or Ctrl+Shift+V).
Press Enter to confirm.
Upon successful login, you’ll see a welcome message.
[![](https://img4.teletype.in/files/b2/10/b2102035-e164-4969-95c8-c4f2771adb90.png)](https://img4.teletype.in/files/b2/10/b2102035-e164-4969-95c8-c4f2771adb90.png)

## Node Installation
**System Update**
`sudo apt update && sudo apt upgrade -y`
**Install the necessary packages**
`sudo apt install unzip -y`
**Download the archive with the node**
`wget https://github.com/firstbatchxyz/dkn-compute-launcher/releases/latest/download/dkn-compute-launcher-linux-amd64.zip`
[![](https://img2.teletype.in/files/59/76/5976ec8d-f19b-4223-ab2a-9f996fba887b.png)](https://img2.teletype.in/files/59/76/5976ec8d-f19b-4223-ab2a-9f996fba887b.png)
**Unpack the archive**
`unzip dkn-compute-launcher-linux-amd64.zip`
[![](https://img2.teletype.in/files/14/17/1417ccf8-da89-4ea9-9685-0147991df0cb.png)](https://img2.teletype.in/files/14/17/1417ccf8-da89-4ea9-9685-0147991df0cb.png)
**Launch the node and enter the data**
`./dkn-compute-node/dkn-compute-launcher`
**First, insert the wallet key and press Enter**
[![](https://img4.teletype.in/files/7b/1d/7b1d1cc7-dc47-4a41-92ea-0a001785f189.png)](https://img4.teletype.in/files/7b/1d/7b1d1cc7-dc47-4a41-92ea-0a001785f189.png)
**Next, select one of the gemini models, enter its number and press Enter**
[![](https://img2.teletype.in/files/5f/bd/5fbd370d-8e0c-4e5d-9d00-4a0dc2873497.png)](https://img2.teletype.in/files/5f/bd/5fbd370d-8e0c-4e5d-9d00-4a0dc2873497.png)
**Next, you need to enter the API key we received earlier, and skip the rest of the questions by pressing Enter**
[![](https://img3.teletype.in/files/ac/fd/acfd9a20-95b4-45ad-9760-9aad2e1ef4d1.png)](https://img3.teletype.in/files/ac/fd/acfd9a20-95b4-45ad-9760-9aad2e1ef4d1.png)
**If the logs are as in the screenshot, then everything went well.**
[![](https://img4.teletype.in/files/33/f8/33f864ff-61a7-4f3b-b83e-cbb1cc37b237.png)](https://img4.teletype.in/files/33/f8/33f864ff-61a7-4f3b-b83e-cbb1cc37b237.png)

> Now we need to make the node work in the background. To do this, close the application by pressing Ctrl+C and execute the commands written below.

**Create a service file**
```c
sudo bash -c "cat <<EOT > /etc/systemd/system/dria.service
[Unit]
Description=Dria Node
After=network.target

[Service]
User=root
EnvironmentFile=/root/dkn-compute-node/.env
ExecStart=/root/dkn-compute-node/dkn-compute-launcher
WorkingDirectory=/root/dkn-compute-node/
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOT"
```

**Run the node as a service (in the background)**
```c
sudo systemctl daemon-reload
sudo systemctl restart systemd-journald
sudo systemctl enable dria
sudo systemctl start dria
```

**View logs**
`sudo journalctl -u dria -f --no-hostname -o cat`

**If the logs are like in the screenshot, then the node is working fine.**
[![](https://img1.teletype.in/files/0e/d2/0ed20731-0db9-422d-be2e-f71620ee59da.png)](https://img1.teletype.in/files/0e/d2/0ed20731-0db9-422d-be2e-f71620ee59da.png)
**After installation**

Fill out [this form](https://form.typeform.com/to/Eav42hR3?typeform=&typeform-source=teletype.in "this form") to get a role in Discord

Check your result in a few days here: https://steps.leaderboard.dria.co/
## Useful commands
**View logs**
`sudo journalctl -u dria -f --no-hostname -o cat`

**Deleting a node**
```c
sudo systemctl stop dria
sudo systemctl disable dria
sudo rm /etc/systemd/system/dria.service
sudo systemctl daemon-reload
rm -rf /root/dkn-compute-node
```
## Project links:
**Website:** https://dria.co/

**Documentation:** https://docs.dria.co/

**Twitter:** https://x.com/driaforall

**Discord:** https://discord.com/invite/dria

**My Profile Twitter** https://x.com/MrGavrMr
