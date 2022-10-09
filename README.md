![2022-10-10_01-26-48](https://user-images.githubusercontent.com/98663407/194782365-e4b251d4-ab99-4da3-b42a-2f36e127ef12.png)

# Telegram bot notifying you of events in your ISLM account

This system will send you a summary status of your host every hour, notify you via telegram of missed jailbreaks, inactive status and several other features.

  # Instructions for HAQQ Network

1 Create a telegram bot via @BotFather, set it up and get the bot's API token https://www.siteguarding.com/en/how-to-get-telegram-bot-api-token.

2 Create 2 groups: alarms and logs. Configure them, add the bot to the chats and get the chat IDs https://stackoverflow.com/questions/32423837/telegram-bot-how-to-get-a-group-chat-id.

3 Connect to your server and make necessary server updates apt update && apt upgrade -y

4 Create a statsfolder folder in $HOME dinestorefile mkdir $HOME/status/.

5 In this folder $HOME/status/ you must create a file cosmos.sh with the extension nano $HOME/status/cosmos.sh. You do not need to make any changes to the cosmos.sh file, it is ready to use.

You will be able to find cosmos.sh in this repository.

6 In this folder $HOME/status/ you must create a file haqq.conf with the extension nano $HOME/status/haqq.conf. Configure it.

You can find haqq.conf in this repository.
![2022-10-10_01-21-49](https://user-images.githubusercontent.com/98663407/194782385-f949e577-7641-4681-8175-2b2f15694706.png)

7 Install some packages with sudo apt-get install jq sysstat bc smartmontools fdisk -y.

8 Run bash cosmos.sh to check the settings. Normal output:
  ```
root@12345:~/status# bash cosmos.sh
 
exp/me >>>>>> 430832/430832.
gap >>>>>>>>> 0 blocks.
chain >>>>>>> haqq_54211-2.
consensus >>> 0.00.
block_time >> 5.97 sec.
priv_key >>>> right.
_active >>>>> false.
gov >>>>>>>>> no non-voting proposals.

_upgrade >>>> v1.0.3.
_time_left >> 18h 28m.
_appr_time >> Oct 10, 05:13.
  ```
  
9 Add some rules with chmod u+x $HOME/status/cosmos.sh.

10 Edit the crontab with crontab -e.
  ```
# status
1,11,21,31,41,51 * * * * bash $HOME/status/cosmos.sh >> $HOME/status/cosmos.log 2>&1
  ```
11 Check the logs with cat $HOME/status/cosmos.log or tail $HOME/status/cosmos.log -f.

![2022-10-10_01-21-19](https://user-images.githubusercontent.com/98663407/194782420-cc4de9c8-51ac-4cff-98b9-0651fd3933f9.png)