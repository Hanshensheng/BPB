<h1 align="center">Proxy IP Scanner Guide</h1>

> [!CAUTION]
> This script is written by Chinese developers, and upon downloading and extracting the zip file, it is detected as a virus. Therefore, it is not recommended to use it if you have sensitive information on your computer. You can run it in an isolated environment like VMware for safety.


## Step 1 - Download the Project
First, download the entire project from here: [Github](https://github.com/bia-pain-bache/BPB-Worker-Panel/archive/refs/heads/main.zip)
<br><br>
## Step 2 - Temporarily Disable Windows Security
Go to Windows Security, then Virus & threat protection, and click on Manage Settings. In this section, temporarily turn off all the toggles. Remember to turn them back on after the scan.
<br><br>
## Step 3 - Run the Scanner
Now, extract the project folder you downloaded. Inside, you will find another zip file named "CF优选反代IP(电脑版)" which contains the scanner folder. Extract this one as well.
Upon opening this folder, you'll see a file named "批处理启动iptest". Run it. From here on, it will ask a few questions in Chinese. I've provided the answers in order below. Make sure you are not connected to any VPN during the scan.

Here are the answers to the questions:

<ol>
  <li><strong>1 - Enter</strong></li>
  <li><strong>Enter</strong></li>
  <li><strong>Enter</strong></li>
  <li><strong>443 - Enter</strong></li>
  <li><strong>Enter</strong></li>
  <li><strong>Enter</strong></li>
  <li><strong>Enter</strong></li>
  <li><strong>0 - Enter</strong></li>
</ol>

Now you need to wait for the scan to complete and for it to run its tests. Afterward, press Enter, and the window will close. The results will be saved in a file named "ip" within the same folder. Open it to see a list of IPs, their Ping, and speed test results. Avoid selecting IPs with a speed test result of 0 KB/s. In the tutorials, I've explained how to set up Proxy IPs, both through the panel and the Cloudflare dashboard.

## Step 4 - Enable Windows Security

Make sure to turn Virus & threat protection back on. This will likely cause the folder to be detected as a virus and subsequently deleted.
