# Dynamic DNS updater for Cloudflare using the REST API

The won't update Cloudflare unless your IP address changes and it works with a free Cloudflare account

Current IP address is retrieved from [ifconfig.co](https://ifconfig.co)

The files should be placed in ```/etc/dnsupdater/``` and made executable

```bash
sudo git clone https://github.com/withanhdammit/dnsupdater.git /etc/dnsupdater
```

The credential files should be moved to ```/root/.creds/``` and set with read-only permissions for the root user

```bash
sudo chmod 0400 /root/.creds/twilio
```
```bash
sudo chmod 0400 /root/.creds/cloudflare
```

Schedule the script to run every 15 minutes with a root cron job

```bash
(sudo crontab -l; echo "*/15    *        *       *       *      /etc/dnsupdater/dnsupdater.sh fqdn.domain.com") | sudo crontab -
```

