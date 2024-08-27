<h1 align="center">Frequently Asked Questions ⁉️</h1>

1. **Why can't I connect with the Fragment configuration?**
   - If you have enabled `Routing` and the VPN is not connecting, the only reason is that the Geo assets are not updated. Go to `Geo asset files` in the v2rayNG app menu and click on the cloud or download icon to update them. If the update fails, you will not be able to connect. If the update fails after several attempts, download the two files from the following links and instead of updating, click the add button and import these two files:
     > 
     >[geoip.dat](https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat)
     > 
     >[geosite.dat](https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat)
   <br>

2. **Why can't I connect with the Normal configuration?**
   - To use these configurations, turn off `Mux` in the settings of any application you are using.
   <br>

3. **Why don't Nekobox or Hiddify Next apps open any websites?**
   - You need to set the `remote DNS` in the application settings like this:
     > `https://8.8.8.8/dns-query`
   <br>

4. **Why doesn't v2rayNG open some things?**
   - `Enable local DNS` should be turned off in the `VPN Settings` section of the application settings.
   <br>

5. **Why is the Fragment config slow on my operator?**
   - Each operator has its own Fragment settings. Most of them work fine with the default settings of the panel, but these values may be better for your operator, you need to test:
     > `Length: 10-100`
     > 
     > `Length: 10-20`
   <br>

6. **Why is my Ping so high?**
   - Do not use `https://1.1.1.1/dns-query` for remote DNS as it increases ping.
   <br>

7. **I followed the instructions and added the Proxy IP from the two links but the sites won't open!**
   - The number of these IPs is large and many of them may be down. You have to test them to find a good one.
   <br>

8. **The proxy IP worked when I set it up, but now it's not working!**
   - If you use a single IP, it will probably stop working after a while and many sites will not open. You have to go through the steps from the beginning. It is best to leave the panel default if you are not doing anything specific that requires a static IP, do not set a single Proxy IP.
   <br>

9. **Why am I getting an error when I go to the `panel/` address?**
   - Follow the setup instructions, KV is not configured correctly.
   <br>

10. **I deployed but I'm getting Cloudflare error 1101!**
    - If it was a Worker, build it using the Pages method, and if that also gives an error, your Cloudflare account has been previously detected, create it with a new account and preferably using the Pages method.
    <br>

11. **Can I use this for trading?**
    - If your Cloudflare IP is Germany (which it usually is) use a single German Proxy IP and you should be fine, but it is best to use the Chain Proxy method to fix the IP.
    <br>

12. **I used TCP or Reality for Chain Proxy but it won't connect!**
    - In the v2rayNG settings, whatever is set for `VPN DNS`, set the same for `Local DNS` in the panel. For example, both should be 1.1.1.1.
    <br>

13. **I deployed using the Pages method but when I Sync fork for the new version in GitHub, the panel version doesn't change!**
    - Cloudflare creates a new test link for each version you update, so when you open the project you will see several different links in the Deployment section. None of these are the main link to your panel, you need to click on Visit Site in the Production section at the top of the page and enter the panel from there.
    <br>

14. **I enabled the non-TLS ports but they won't connect!**
    - Note that to use non-TLS configs, you must have deployed only through Workers without a custom domain.
    <br>

15. **Why is the Best Fragment config not connecting or pinging but not working?**
    - Turn off `Prefer IPv6` in the settings.
