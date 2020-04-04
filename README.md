<img src="https://github.com/zhubanRuban/cpng/raw/images/cpng.png" alt="cpng logo" />

# cpng : Nginx for cPanel
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/zhubanRuban/cpng?style=flat-square)
![HitCount](http://hits.dwyl.io/zhubanRuban/cpng.svg)

Make your site use Nginx by switching a domain to PHP-FPM in WHM or cPanel MultiPHP Manager.

As simple as that:
- PHP-FPM is `on` - domain is served by `Nginx`
- PHP-FPM is `off` - domain is served by `Apache`

## Requirements

Up-to-date cPanel on CentOS 7/6.

## Installation

Log into your server as root and execute the following command:
```
bash <(curl -skL https://raw.githubusercontent.com/zhubanRuban/cpng/master/cpng) install
```
It will download the tool and integrate into the system.

## Important notes

When you enable PHP-FPM for a site, it is served by Nginx, therefore .htaccess rules designed for Apache will not work.
Make sure that you prepared corresponding Nginx rules.
For your convenience, you can place them into the following files in domain's document root:

- `.ngaccess.http.*.conf` rules for http connection
- `.ngaccess.http.*.conf` rules for https connection
- `.ngaccess.common.*.conf` rules common for both http and https

Then reload nginx with `cpng reload`

## Options

```
    -h|--help|help  show this help message

    rebuild         rebild Nginx configuration
                    it is also symlinked to /scripts/rebuildnginxconf for convenience to do it cPanel-way
    reload          check configuration, reload Nginx if check succeeds, restart Nginx if reload fails
                    it is also symlinked to /scripts/restartsrv_nginx for convenience to do it cPanel-way

    dryrun          display configuration to be aplied, but do not apply
    show            show applied configuration

    install         install cpng
    update          update cpng
    remove          remove cpng

```

## Uninstallation
```
cpng remove
```

## Contributing

I appreciate any feedback and bug reports to make the tool even better.

Please share your thoughts [here](https://github.com/zhubanRuban/cpng/issues).

Enjoy the hosting!
