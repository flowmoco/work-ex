# Work Experience Guide for Raspberry PI

## Setup Raspberry PI

### Install raspian OS onto SD card

* Install [balena etcher](https://www.balena.io/etcher/)
* Download [Raspian](https://www.raspberrypi.org/downloads/raspbian/)
* Mount image on SD card using balena
* Insert SD card and power on PI

### Explore PI

* Follow introduction setup, set password.

#### Change os theme color

* Appearance setting -> system -> highlight color = #455E7E

### Install/update software

* run `sudo apt-get update` to update to latest software.
* reboot.

### Install Visual Studio code (VSCODE)

`sudo apt-get install code-oss=1.29.0-1539702286`

`sudo apt-mark hold code-oss` to stop updates to broken version.

## Setup a github account

* Go to <https://github.com/> and sign up.

* Create a sites folder `mkdir sites` (make directory sites).
* Go into folder `cd sites` (change directory sites).
* Clone this repository `git clone <-insert url->`.
* Go into repository folder `cd <-insert repo folder name->` (change directory repo-name).

## Modify and save back to github.

* Open content in code editor `open . -a code-oss` (open all in application code-oss).
* Explore static folder.
* Modify
* Add `git add .` or `git add <-insert filename->`.
* Commit `git commit -m "descriptive message of modification"`.
* Push `git push`.
* Repeat for practise.

## Install Apache and PHP to run php folder

This is to turn your machine into a server to run PHP code

* Install Apache `sudo apt-get install apache2 -y`.
* Test locally by opening the Pi’s web browser and visiting <http://localhost/>.
* Files will be stored in /var/www/html/ – to make life easy give all users write access to this folder. `sudo chmod -R 777 /var/www/html`
* Install PHP `sudo apt-get install php libapache2-mod-php -y`.

### point apache to php folder

Add the following to `/etc/apache2/sites-available/000-default.conf` after the existing VirtualHost tag you may need help to do this in nano text editor, note port number 88.


```apache
<VirtualHost *:88>
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For the default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com

        ServerAdmin webmaster@localhost
        DocumentRoot /home/pi/sites/work-ex/php

        <Directory "/home/pi/sites/work-ex/php">
                Order allow,deny
                Allow from all
                Require all granted
        </Directory>

        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>

```

* Update the `/etc/apache2/ports.conf` with `Listen 88`.
* Restart apache `sudo /etc/init.d/apache2 restart`.
* Now visit `http://localhost:88/` and you should see the site running!
* Make modifications and refresh!