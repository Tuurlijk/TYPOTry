# TYPOTry
A smallish (193 MB) Vagrant box to try out the most recent TYPO3 release.

Just run `vagrant up` and visit:

* [http://9.1.0.local.typo3.org/typo3/](http://9.1.0.local.typo3.org/typo3/)

[![Flattr this git repo](http://api.flattr.com/button/flattr-badge-large.png)](https://flattr.com/submit/auto?user_id=Tuurlijk&url=https://github.com/Tuurlijk/TYPOTry&title=TYPOTry&language=Ansible&tags=github&category=software)

## Requirements

* [Virtualbox](https://www.virtualbox.org/) or another virtualization product - Free!
* [Vagrant](http://www.vagrantup.com/) - Version 1.8.4 or later is needed - Free!
* [Vagrant alpine plugin](https://github.com/maier/vagrant-alpine) - `vagrant plugin install vagrant-alpine`

## Installation

**without git**
* Download the latest [TYPOTry zip file](https://github.com/Tuurlijk/TYPOTry/archive/master.zip)
* Extract the zip file
* Open a command shell
* Go into the new directory
* Run `vagrant up`

**with git**
* Open a command shell
* Clone the repository: `git clone https://github.com/Tuurlijk/TYPOTry.git`
* Go into the new directory: `cd TYPOTry`
* Start the machine: `vagrant up`

Now you can visit:

* [http://9.1.0.local.typo3.org/typo3/](http://9.1.0.local.typo3.org/typo3/)

You can login as user `admin` with the password `supersecret`.

## How do I get onto the box?
You can login by doing a `vagrant ssh`. That user has full sudo privileges. Or you can `ssh vagrant@local.typo3.org` using password `vagrant`.

To add your public ssh key to the authorized_keys file of the vagrant user, you can execute the following command:

```bash
 cat ~/.ssh/id_rsa.pub | ssh vagrant@local.typo3.org 'cat >> .ssh/authorized_keys'
```

Now you will be able to get into the box as user vagrant without supplying a password.

## MailHog
[MailHog](https://github.com/mailhog/MailHog) runs a super simple SMTP server which catches any message sent to it to display in a web interface. This makes it easy to test forms without actually sending mail to the 'real' mail address. Set your favourite app to deliver to smtp://127.0.0.1:1025 instead of your default SMTP server, then check out [http://mail.local.typo3.org](http://mail.local.typo3.org) to see the mail that's arrived so far.

## Can't connect after the vagrant up?

This box needs internet connectivity to resolve the local.typo3.org domain name to the IP of the box. If you are not connected to the Internet you will need to add the following entries to your hosts file:

* `192.168.144.120 9.1.0.local.typo3.org`

## Known Problems

* On Windows machines you may need to enable VT-X in the bios of your machine. vt-x is disabled in the BIOS, you can disable this in the image settings under system tab processor, PAE/NX disable or you can enable this setting in your BIOS. Check: [http://www.sysprobs.com/disable-enable-virtualization-technology-bios](http://www.sysprobs.com/disable-enable-virtualization-technology-bios) and check your windows version ( minimal a Pro-edition) or [Enable without BIOS](http://stackoverflow.com/questions/31581854/enabling-intel-virtualization-vt-x-without-option-in-bios).
* Vagrant may complain about a 'space' character in your path. Ruby can't handle this. You will need to move the Vagrant box to a path without spaces and try again.

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

If you wish to work on the code that built this box, then head over to [https://github.com/Tuurlijk/TYPO3.Packer](https://github.com/Tuurlijk/TYPO3.Packer).
