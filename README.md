# craft-queue-worker
Adds a queue worker to an Ubuntu system for Craft CMS.

Variables in both files are enclosed in braces and need to be modified. You will need a unique name for each queue you want to run, site is a generic placeholder.

## Steps:
1. Login as root
2. Type `sudo nano /etc/systemd/system/site-queue@.service`
3. Add contents of site-queue@.service with variables replaced
4. Type `sudo systemctl start site-queue@{1..2}`
5. Type `sudo systemctl enable site-queue@{1..2}`
6. Type `sudo apt-get install mailutils`
7. Type `sudo nano ./usr/local/bin/srvc.sh`
8. Add contents of srvc.sh with variables replaced
9. Type `sudo crontab -e`
10. Add the contents of crontab to the bottom
11. To verify, type `journalctl -f -u site-queue@*.service`
