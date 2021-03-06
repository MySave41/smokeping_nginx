# Smokeping with Nginx

## Configuration examples

Because links to images generates with /smokeping/, all configs use this path for static files and images.

### simple.conf

Very simple, but main page not in /smokeping/, main page is http://smokeping.example.com/cgi-bin/smokeping.cgi

### big.conf

Partialy used content of `/etc/nginx/fastcgi_params`, except of `SCRIPT_FILENAME`.

### best.conf

Like `big.conf`, but with redirect from wrong URLs to main page.


## Installing

### Ubuntu / Debian

Replace here "smokeping.example.net" by your DNS name:

```shell
export MYSITENAME="smokeping.example.net"
sudo apt-get install smokeping fcgiwrap nginx
wget "https://github.com/vazhnov/smokeping_nginx/raw/master/best.conf"
sed -i -- s/smokeping\.example\.com/${MYSITENAME}/g best.conf
sudo chown root: best.conf
sudo mv best.conf /etc/nginx/sites-available/${MYSITENAME}.conf
sudo ln -s "../sites-available/${MYSITENAME}.conf" "/etc/nginx/sites-enabled/${MYSITENAME}.conf"
```

## Copyright

Distrubuted under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/) license.
