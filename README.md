
**Introduction**

These steps are designed to help a user setup a masternode without using any scripts. These beneficial because a user can use these steps to setup his or her masternode in any Operating system environment.



**Step 1**

Download the latest Slate core wallet and make sure the wallet is synced. This will be your "Control Wallet"

**Step 2**

Click on "Tools" and open the "Debug console"

**Step 3**

In the console. Type and press enter:

    createmasternodekey

Save this key in a txt file of your choice
    
**Step 4**

Still in the debug console. Type and press enter:

    getaccountaddress <AnyNameForYourMasternode>

EX. getaccountaddress masternode1

Save this address in a txt file also, this is the address where you would have to send yoour 350,000 SLX as collateral for your masternode.

**Step 5**

Close the debug console. Go to "Send" option in the core wallet, paste the address you created in step 4 into the "Pay To:" section. In the "Amount" area type 350,000 SLX and click "Send".

**Step 6**

Go back to Tools > Debug console. Type and press Enter:

    getmasternodeoutputs

Save the information in your txt file that was displayed. You should see a transaction hash and the output index number (it is always 0 or 1)

**Step 7**

Close the debug console. Go Tools and click on "Open Masternode Configuration File". In the file that just opened for you, all in one line write the name of the masternode you created in "Step 4". Followed by the IP address of where your masternode will be located and port (37415 for main net) you will be connecting to. Followed by masternode private key you created in "Step 3". Followed by the transaction hash you saved in "Step 6". Followed by the output index number you saved in "Step 6". Here is an example:

      <Name of Masternode(Use the name AnyNameForYourMasternode you entered earlier for simplicity)> <Unique IP address>:37415 <The   result of Step 1> <Result of Step 4> <The number after the long line in Step 4>

Another Example:

    Masternode1 31.14.135.27:37415 892WPpkqbr7sr6Si4fdsfssjjapuFzAXwETCrpPJubnrmU6aKzh c8f4965ea57a68d0e6dd384324dfd28cfbe0c801015b973e7331db8ce018716999 1

Once thats done click File > Save and close the file. Restart your "control wallet".

**Step 8**

Go to your VPS, if you are using Linux use this command and press enter:

     wget https://github.com/SlateEntertainmentGroup/SLX-blockbook/releases/download/testNetVersion/slate-0.1.04-x86_64-linux-gnu.tar.gz

**Step 9**

Unzip this file by running:

     tar -zxvf slate-0.1.04-x86_64-linux-gnu.tar.gz

**Step 10**

Go to your slate bin directory by running:

    cd ~/slate/bin

**Step 11**

start "slated" by running:

    ./slated

**Step 12**

Use "ctrl+c" to turn it off right away. We only did this create the hidden directory that you will need to access.

**Step 13**

Run this command:

    cd ~/.slate

**Step 14**

Run this command:

    nano slate.conf

and copy paste this information:

    rpcuser=<long random username>
    rpcpassword=<longer random password>
    rpcallowip=127.0.0.1
    server=1
    daemon=1
    logtimestamps=1
    maxconnections=256
    masternode=1
    externalip=<your unique public ip address of your VPS with the port number>
    masternodeprivkey=<Result of Step 3>
    
Press Ctrl+X, type "Y" and press enter to save

**Step 15**

Run these commands:

    cd ~/slate/bin
 
and 
 
    ./slated

**Step 16**

At this point your masternode started to sync and you watch its syncing progress by running this command:

    tail -f ~/.slate/debug.log
    
Wait till your masternode has synced by accepting all the blocks on the network, this will take a while.

**Step 17**

Once you see that the masternode synced by accepting all the blocks on the network, go to your "control wallet". Select Masternodes and click on "Start All"


    
 



