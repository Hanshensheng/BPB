# Installation via Cloudflare Pages

## Introduction
You probably know that there are two methods to use Cloudflare for creating a proxy: Worker and Pages. It's worth noting that the Worker method, which is more common, has a limitation of not allowing more than 100,000 requests per day. This limit is generally sufficient for 2-3 users. To bypass this limit in the Worker method, you could link a domain to the Worker, making it effectively unlimited (which seems to be a bug in Cloudflare). However, Pages does not have this limitation. Although, since we use a feature called Pages functions in this method, you will still receive an email notifying you of the 100k usage capacity, even if you use a personal domain. **But ultimately, experience has shown that your service will not be interrupted.**

Another significant advantage is the ease of updating. When the project code is updated, you can easily and quickly update your panel without needing to go through the setup steps again. More details are provided in the [Updating](#updating) section.

Additionally, the steps for using Pages are much simpler, and you can perform these tasks easily on your mobile phone.<br><br>

## Step 1 - Github
Create an account on [Github](https://github.com/signup) (you only need an email to sign up). Log in to Github with your credentials.

Now go to the Github address [BPB-Worker-Panel](https://github.com/bia-pain-bache/BPB-Worker-Panel) and click the Fork button at the top.
<br><br>
<p align="center">
  <img src="docs/assets/images/Fork_repo.jpg">
</p>

On the next page, don't change anything and click Create Fork. That's it for Github.
<br><br>

## Step 2 - Cloudflare Pages
If you don’t have a Cloudflare account, create one [here](https://dash.cloudflare.com/sign-up) (again, you only need an email to sign up).

Now, in your Cloudflare account, go to the `Workers and Pages` section from the left menu (where you previously created Workers) and click `Create Application`. This time, choose `Pages`:

<p align="center">
  <img src="docs/assets/images/Pages_application.jpg">
</p>

Here, click `Connect to Git` and proceed to the next step:

<p align="center">
  <img src="docs/assets/images/Connect_to_git.jpg">
</p>

Click on `BPB-Worker-Panel` to activate it and then click `Begin Setup`. In the next step, there is a `Project Name` field that will be the domain of your panel, so make sure to change it to a name of your choice. Now, there's a difference from Workers: if you want to change the UUID or Proxy IP, you cannot modify it in the code anymore. If you wish to use the default settings of the panel, that's fine, otherwise, read the [Advanced Settings](#advanced-settings-optional) section before proceeding.

Now you can click `Save and Deploy`. It will take a few seconds for the project to be installed. Wait until the `Continue to Project` button appears, click it, and go to the project page.
<br><br>

## Step 3 - Creating Cloudflare KV
From the left menu, go to the KV section:

<p align="center">
  <img src="docs/assets/images/Nav_dash_kv.jpg">
</p>

Click on `Create a namespace`, give it a name of your choice, and click Add.

Go back to the `Workers and Pages` section and enter the Pages project you created. Go to the `Settings` and then `Functions`:

<p align="center">
  <img src="docs/assets/images/Settings_functions.jpg">
</p>

Here, like in Workers, find the `KV namespace bindings` section on the page, click `Add binding`, and set the `Variable name` to `bpb` (exactly as written) and select the KV namespace you created in the second step. Click `save`.

<p align="center">
  <img src="docs/assets/images/Pages_bind_kv.jpg">
</p>

That’s it for KV. Now, you just need to deploy again to apply the KV changes.

From the top bar, return to `Deployment` and go to `view details` under the `Production` section:

<p align="center">
  <img src="docs/assets/images/Pages_production_details.jpg">
</p>

Now in the `Deployment detail` section, click the `Manage Deployment` button and then `Retry deployment`:

<p align="center">
  <img src="docs/assets/images/Pages_retry_deployment.jpg">
</p>

Wait a few seconds for the process to complete, and you’re done!

Go back and from the `Production` section, click `visit site`, then add `panel/` at the end to access your panel. Configuration guides and tips are available in the [main guide](configuration.md). Installation is complete, and the following explanations may not be necessary for everyone!
<br><br>

## Advanced Settings (Optional)
By now, you might have noticed that we haven’t discussed changing UUID and Proxy IP because you can use the default settings of the panel without this step.
<br><br>

**Changing UUID:**

As you know, UUID acts like a secret name used in subscription links and configurations. You can change it if needed. If you change this parameter, user connections will be interrupted, and you will need to provide the subscription link or configurations again. If you don’t define the UUID at this stage, the code will use a default UUID.
<br><br>

**Fixing Proxy IP:**

We have a problem where the code uses a large number of Proxy IPs by default, randomly selecting a new IP each time it connects to sites behind Cloudflare (covering a large portion of the web), resulting in intermittent changes to your IP. This IP change might be problematic for some (especially traders). To change the Proxy IP, starting from version 2.3.5, you can do it through the panel itself by applying it and updating the subscription. However, I recommend using the method described below because:

> [!CAUTION]
> If you apply the Proxy IP through the panel and that IP becomes unusable, you will need to provide a replacement IP and update the subscription. This means if you’ve given away the configuration and change the Proxy IP, it will be useless as the user doesn’t have a subscription to update the configuration. Therefore, it's recommended to use this method only for personal use. The advantage of the second method, which I’ll explain, is that it’s done through the Cloudflare dashboard and doesn’t require updating configurations.

<br>

To change UUID and Proxy IP on this page (Step 3, where you select BPB-Worker-Panel), scroll down and open the `Environment variables (advanced)` section:

<p align="center">
  <img src="docs/assets/images/Pages_env_vars.jpg">
</p>

Here, you need to specify the values. Click `Add variable` once and enter `UUID` in the first field with uppercase letters. Then, get a UUID from [here](https://www.uuidgenerator.net/) and enter it in the second field.

Now, click `Add variable` again, enter `PROXYIP` in the first field with uppercase letters, and you can get the IP from the link below. Open it to view a list of IPs, check their countries, and choose one:

>[Proxy IP](https://www.nslookup.io/domains/bpb.yousef.isegaro.com/dns-records/)

<p align="center">
  <img src="docs/assets/images/Proxy_ips.jpg">
</p>
<br>

## Updating:
One advantage of Pages over Worker is that when an update is released for the code, you no longer need to download a new version of worker.js and start from scratch! You don't need to interact with Cloudflare for updates. Simply go to your Github repository `BPB-Worker-Panel` and click `Sync fork`:

<p align="center">
  <img src="docs/assets/images/Sync_fork.jpg">
</p>

Then click `Update branch` and that’s it. The good part is that Cloudflare Pages will automatically detect this and update itself within about 1 minute.
