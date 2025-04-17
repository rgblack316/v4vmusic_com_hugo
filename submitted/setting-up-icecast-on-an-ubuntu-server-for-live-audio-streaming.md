---
title: Setting Up Icecast on an Ubuntu Server for Live Audio Streaming
author: Randy Black
date: 'Do not worry about this as it will be generated later'
categories:
  - Tutorials
tags:
  - Icecast
  - Live Stream
toc: true
---
This article was published orginially at [https://randallblack.com/icecast/](https://randallblack.com/icecast/) and is shared here by it's author.

# Setting Up Icecast on an Ubuntu Server for Live Audio Streaming

## Introduction

Icecast is an open-source streaming media server that allows you to broadcast live audio over the internet. Whether you’re hosting a podcast, an internet radio station, or live events, Icecast provides a flexible and powerful solution.

This guide will walk you through the process of installing and configuring Icecast on an Ubuntu server. By the end, you’ll have a working setup for streaming live audio.

---

## Step 1: Preparing Your Ubuntu Server

Before installing Icecast, update your system.

### System Requirements

- Ubuntu 18.04 or newer  
- At least 1GB of RAM and 1 CPU core (for low traffic)  
- A static IP address or domain name  
- Firewall configured to allow necessary traffic  

### Updating the System

Run the following command:

\```bash
sudo apt update && sudo apt upgrade -y
\```

---

## Step 2: Installing Icecast

To install Icecast, run:

\```bash
sudo apt install icecast2
\```

During installation, you’ll be asked if Icecast should start automatically. Select **Yes**.

### Enable Icecast to Start on Boot

Ensure Icecast starts on reboot:

\```bash
sudo systemctl enable icecast2
\```

### Verify Installation

Check if Icecast is installed:

\```bash
icecast2 -v
\```

---

## Step 3: Configuring Icecast

The main configuration file for Icecast is:

\```bash
/etc/icecast2/icecast.xml
\```

### Editing the Configuration File

Open it in a text editor:

\```bash
sudo nano /etc/icecast2/icecast.xml
\```

### Key Settings

- **Admin Credentials:** Update `<admin-user>` and `<admin-password>`.  
- **Hostname:** Replace `<hostname>` with your server’s IP or domain name.  
- **Mount Points:** Define the stream location.  

#### Example Configuration Snippet:

    <limits>
        <clients>100</clients>
        <sources>2</sources>
    </limits>

    <authentication>
        <admin-user>admin</admin-user>
        <admin-password>securepassword</admin-password>
    </authentication>

    <hostname>your-domain.com</hostname>

    <mount>
        <mount-name>/stream</mount-name>
        <public>1</public>
    </mount>

Save and exit the editor.

---

## Step 4: Starting and Testing Icecast

### Restart Icecast

\```bash
sudo systemctl restart icecast2
\```

### Check Status

\```bash
sudo systemctl status icecast2
\```

### Access the Icecast Web Interface

Visit: [http://your-server-ip:8000](http://your-server-ip:8000)

Log in with your admin credentials.

---

## Step 5: Setting Up a Source Client

Icecast requires a source client to send audio streams. Popular options:

- **BUTT (Broadcast Using This Tool)** – Simple and cross-platform.  
- **Liquidsoap** – Advanced scripting for automation.  
- **Mixxx** – DJ software with Icecast support.  

### Configuring BUTT

1. Download and install [BUTT](https://butt.sourceforge.io/).  
2. Open BUTT and go to **Settings → Main**.  
3. Click **Add** and enter:  
   - **Server:** Your Icecast server’s IP or domain  
   - **Port:** `8000`  
   - **Mount Point:** `/stream`  
   - **Username:** `source`  
   - **Password:** Your Icecast password  
4. Choose an audio input device and start streaming.

---

## Step 6: Streaming and Listening

### How to Stream

Once your source client is set up, start broadcasting. You should see the stream active in the web interface.

### How to Listen

Listeners can access your stream via:

- **VLC Player:** Open `http://your-server-ip:8000/stream`  
- **Web Browser:** Enter the same URL.  
- **Embedded Player:** Use an `<audio>` tag:

\```html
<audio controls>
    <source src="http://your-server-ip:8000/stream" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
\```

---

## Step 7: Securing Your Icecast Server

### Configure a Firewall

Allow Icecast’s port:

\```bash
sudo ufw allow 8000/tcp
\```

### Change Default Passwords

Modify passwords in `/etc/icecast2/icecast.xml` for security.

### Enable HTTPS (Optional)

For secure streaming, set up a reverse proxy with Nginx and Let’s Encrypt.

---

## Step 8: Monitoring and Troubleshooting

### Checking Logs

If issues arise, check logs:

\```bash
cat /var/log/icecast2/error.log
\```

### Common Issues and Fixes

| Issue | Solution |
|--------|---------|
| Icecast is not running | `sudo systemctl restart icecast2` |
| Cannot connect to Icecast | Ensure port `8000` is open in UFW |
| No audio streaming | Check source client settings and passwords |

---

## Conclusion

You now have a working Icecast server on Ubuntu! You’ve learned how to:

- Install Icecast  
- Configure its settings  
- Set up a source client  
- Secure and troubleshoot your server  

This setup lets you stream live audio to your audience anywhere.

---

## Additional Resources

- [Official Icecast Documentation](https://icecast.org/docs/)  
- [BUTT Streaming Guide](https://butt.sourceforge.io/)  

--------------------------------------------
Author info - Note this only needs to be submitted once as it gets saved on the site
You may submit again if you need to change your info
--------------------------------------------
"YOUR-NAME": "A brief description of yourself. May include [markdown formatted urls](https://your-website.com)"
