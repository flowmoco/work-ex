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
