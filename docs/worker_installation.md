# Installation via Cloudflare Workers

First, download the Worker code from [here](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.js) and upload the file to your Cloudflare Workers dashboard (since the code has become very extensive, copying and pasting on a mobile phone has become very difficult, upload it as shown in the image below). On mobile, open the side menu, long press, and upload the file.

<p align="center">
  <img src="docs/assets/images/Worker_mobile_upload.jpg">
</p>

The panel works with its default UUID and Proxy IP, and you can continue with these settings. However, if you want to make changes, go to the [Advanced Settings](#advanced-settings-optional) section and return here.

Finally, `Save and Deploy` the Worker.
Now, return to the Workers dashboard and follow these steps:

<p align="center">
  <img src="docs/assets/images/Navigate_worker_dash.jpg">
</p>

Navigate to the `KV` section:

<p align="center">
  <img src="docs/assets/images/Nav_dash_kv.jpg">
</p>

In the KV section, click `Create a namespace` and enter a name of your choice, such as Test, then click `Add`.

Go back to the `Workers & Pages` section from the left menu, open the Worker you created, go to `Settings`, and select `Variables`. Scroll down to find `KV Namespace Bindings`, click `Add binding`, and select the KV you created from the dropdown on the right (in this example, it was Test). What's important is the dropdown on the left; make sure to set its value to `bpb` and then `Save and Deploy`.

<p align="center">
  <img src="docs/assets/images/Bind_kv.jpg">
</p>

For example, if your Worker domain is worker-polished-leaf-d022.workers.dev, add `panel/` at the end to access the panel. Example:

>`https://worker-polished-leaf-d022.workers.dev/panel`

You will be prompted to set a new password and log in, and that's it. Installation is complete, and the following explanations may not be necessary for everyone. Configuration guides and tips are available in the [main guide](configuration_fa.md).
<br><br>

## Advanced Settings (Optional)
You may have noticed that we haven’t discussed changing the UUID and Proxy IP because you can use the default settings of the panel. However, if you want to change them, you can follow these steps. It is recommended to at least change the UUID.

### 1. Changing UUID
As you know, UUID acts like a secret name used in subscription links and configurations, and you can change it if needed. Changing this parameter will interrupt user connections, and you will need to provide the subscription link or configurations again. If you don’t define the UUID at this stage, the code will use a default UUID.

In line 9, there is a UUID, and you can leave it unchanged, but preferably change it like this: get a UUID from [here](https://www.uuidgenerator.net/) (it’s also in line 9 of the code), and copy it to the previous location in line 10. Then `Save and Deploy` the Worker.

### 2. Fixing Proxy IP

We have a problem where this code uses a large number of Proxy IPs by default, randomly selecting a new IP each time it connects to sites behind Cloudflare (which covers a wide portion of the web), resulting in intermittent changes to your IP. This IP change might be problematic for some (especially traders). To change the Proxy IP, starting from version 2.3.5, you can do it through the panel itself by applying it and updating the subscription. However, I recommend using the method described below because:

> [!CAUTION]
> If you apply the Proxy IP through the panel and that IP becomes unusable, you will need to provide a replacement IP and update the subscription. This means if you’ve given away the configuration and change the Proxy IP, it will be useless as the user doesn’t have a subscription to update the configuration. Therefore, it's recommended to use this method only for personal use. The advantage of the second method, which I’ll explain, is that it’s done through the Cloudflare dashboard and doesn’t require updating configurations.

<br>

Open this link (also included in line 12 of the Worker code), which shows a list of IPs. You can check their countries and choose one.

>[Proxy IP](https://www.nslookup.io/domains/bpb.yousef.isegaro.com/dns-records/)

<p align="center">
  <img src="docs/assets/images/Proxy_ips.jpg">
</p>

The initial text in line 14 looks like this:

```javascript
const proxyIPs = ['bpb.yousef.isegaro.com'];
```

When you want to set the IP, it will look like this:
```javascript
const proxyIPs = ['8.218.149.193'];
```

`Save and Deploy` the Worker.
> [!WARNING]
> Be careful as there are many IPs, and many of them may become unusable. You should test them to find a good one.

> [!CAUTION]
> If you use a single IP, it might become unusable again after a while, and many sites may not load. You will need to repeat these steps from the beginning.
