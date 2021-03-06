# craft-queue-worker
Adds a queue worker to an Ubuntu system for Craft CMS. This will run the Craft queue for a site every sixty seconds, and email you if the queue worker stops.

Variables in both files are enclosed in braces and need to be modified. You will need a unique name for each queue you want to run, site is a generic placeholder.

## Steps:
1. Disable Craft's queue runner by adding `'runQueueAutomatically' => false,` to the general.php file in the craft/config folder
2. SSH into server as root
4. Type `sudo nano /etc/systemd/system/site-queue@.service`
5. Add contents of site-queue@.service with variables replaced
6. Type `sudo systemctl start site-queue@{1..2}`
7. Type `sudo systemctl enable site-queue@{1..2}`
8. Type `sudo systemctl daemon-reload`
9. Type `sudo apt-get install mailutils`
10. Type `sudo nano /usr/local/bin/srvc.sh`
11. Add contents of srvc.sh with variables replaced
12. Type `sudo crontab -e`
13. Add the contents of crontab to the bottom
14. Type `sudo service cron restart`
15. To verify, type `journalctl -f -u site-queue@*.service`
