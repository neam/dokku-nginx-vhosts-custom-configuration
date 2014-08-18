# dokku-nginx-vhosts-custom-configuration

[Dokku](https://github.com/progrium/dokku) plugin to add custom configuration directives to the nginx vhost configuration on the dokku host.

## Background

Relevant use cases for when the nginx vhost configuration needs to be customized can be to set proxy timeouts in order to allow long running requests, setting specific SSL directives, enabled uploading of large files and the like.

## Installation

```bash
git clone https://github.com/neam/dokku-nginx-vhosts-custom-configuration.git /var/lib/dokku/plugins/nginx-vhosts-custom-configuration
```

## Simple usage

1. Add a file containing your custom configuration to your app repo. For instance, you can call it `nginx.inc.conf` and commit it in the root of your app's repository.

2. Set the environment variable NGINX_VHOSTS_CUSTOM_CONFIGURATION to the in-container path to the file above:

```bash
$ dokku config:set <app> NGINX_VHOSTS_CUSTOM_CONFIGURATION=nginx.inc.conf             # Server side
$ ssh dokku@server config:set <app> NGINX_VHOSTS_CUSTOM_CONFIGURATION=nginx.inc.conf  # Client side
```

You're done! This plugin will read app environment variable with in-container path to custom configuration file and import the custom configuration to the app-specific configuration on the  dokku host.

## License
MIT
