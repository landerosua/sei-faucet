# cosmos-discord-faucet
Discord faucet bot for any blockchain based Cosmos  


<details>
  <summary>List of available commands:</summary>

1. Request coins through the faucet  
`$request sei1rr2pf542snhvr7re933lu8xq58cuy8uavzaqzm`

Transaction status explanation:  
✅ - mean bot send transaction to your address

2. Displays the current status of the node where faucet is running  
`$faucet_status`

3. Show tap address  
`$faucet_address` or `$tap_address`

4. Show transaction information for a specific transaction ID  
`$tx_info B40F057439183F5A1226FB1B0B66A8781AF0174060205A3FF316C8CEB35EB4D9`

5. Show address balance  
`$balance sei1rr2pf542snhvr7re933lu8xq58cuy8uavzaqzm`  

</details>  


## Requirements
- python3.6+  
- Cosmos REST server 
- Cosmos RPC server  

## How to install  
1. Run command below  
```bash
apt update \ &&
apt install -y python3-pip python3-venv git tmux \ &&
git clone https://github.com/landeros/sei-faucet.git \ &&
cd sei-faucet \ &&
python3 -m venv venv \ &&
source venv/bin/activate \ &&
pip3 install -r requirements.txt
```
2. [Create Discord token](https://github.com/reactiflux/discord-irc/wiki/Creating-a-discord-bot-&-getting-a-token)  
3. Fill in config.ini  
4. Invite the bot to your channel  
5. Run REST server. Below is an example  
```bash
tmux new -s sei_rest -d seicli rest-server --laddr tcp://localhost:1317 --node tcp://localhost:26657 --chain-id atlantic-1
```  


## How to run  
Start faucet bot  
```
tmux new -s discord_faucet_bot -d cd ~/sei-faucet && source venv/bin/activate && python3 discord_faucet_bot.py
```  
  
### Alternatively, the bot can be run through systemd:  
- If necessary, change the username and the path to the script folder in `discord-faucet-bot.service`  

- Start the service  
```
ln -s $HOME/cosmos-discord-faucet/discord-faucet-bot.service /etc/systemd/system/ \
&& systemctl daemon-reload \
&& systemctl enable discord-faucet-bot.service \
&& systemctl start discord-faucet-bot.service \
&& systemctl status discord-faucet-bot.service
```  

