Lets Twalk about it:

This is virtual machine for testing out Twalk. These configs will be used to make a production ready system. 

##Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

##Having problems?

1. Create a detailed issue.
2. Sit back, relax, apathy's back in style

############ marked for removal ###########

# Vagrant Ubuntu 14.04 Puppet Nginx

Simple example showing how to provision a Ubuntu 14.04 Nginx web server VM using Vagrant and Puppet.

Created and tested on Mac OSX 10.9.5, Vagrant 1.6.3, VirtualBox 4.3.6, otherwise using versions/boxes given in VagrantFile and Puppet config.

## Start

```
# Starts up VM and runs puppet to setup, downloading box if necessary
vagrant up
# On completion nginx should be running and accessible from host at http://192.168.33.10
```

## Details

Used [jfryman-nginx](https://forge.puppetlabs.com/jfryman/nginx) v0.1.1 module to puppetize nginx, added using:

```
puppet module install jfryman-nginx  --modulepath puppet/modules
```

This module does not include default index.html or config, so I added a vhost in site.pp (manifests/site.pp) and created a custom puppet module site_content (puppet/modules/site_content) which ensures /var/www exists and creates a simple index.html file.

## Notes

This is a bare bones example and does not include any security or configuration best practise, so do not use in production.

Any change to the puppet files requires you to run 'vagrant provision' to update.