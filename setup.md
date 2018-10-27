# EC2 instance, Google Domains, Static Site

## Setup EC2 instance
* "Launch Instance"
* Pick AMI
  * `ami-0ac019f4fcb7cb7e6`
* Take all defaults until you get to "Configure Security Group"
  * At this point, we have SSH access configured by default, but we want to add HTTP. If we don't do this, we will wonder why we cant access our instance via HTTP once we setup and start Apache.
    * Add Rule -> HTTP
* Review and Launch the Instance, name your key pair and download it, and add it to known hosts:
  * `ssh -i "<your_key_pair>.pem" ubuntu@<DNS_for_instance>`

## Setup Apache
* `ssh ubuntu@<DNS_for_instance>`
* `apt update`
* `apt get apache2`
* `sudo service start apache2`
* `sudo service --status-all`
* Visit the DNS for your EC2 instance and ensure you get the Apache "It works" page
* Edit `var/www/html` to serve your static content
