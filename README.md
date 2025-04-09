# cookie_monster

Obtain cookies form a URL.


# To install

```sh
make clobber all
sudo make install clobber
```


# To use

```sh
/usr/local/bin/cookie_monster [-h] [-v level] [-V] [-p port] [-c cookie_name] [-n count]
	[-s] [-f fake_host] [-t] [-a] [-P post_string] host path

    -h                  print help and exit
    -v level            verbose / debug level
    -V                  print version and exit

    -p port             port to connect to (def: 80)
    -c cookie_name      only extract a cookie with the cookie_name (def: any)
    -n count            number of cookes (def: 1)
    -f fake_host        force HTTP Host: to be fake_host (def: host)
    -s                  strip extra HTTP text from cookie line (def: raw line)
    -t                  timestamp cookie fetches <<recommeded>> (def: do not)
    -a                  read all of the reply (def: HTTP headers only)
    -P post_string      issue a POST this this string instead of a GET

    host                host web server to connect
    path                URL path on the user to GET

HTTP Example:

    cookie_monster -t -n 100000 www.host.com /app/login.html > out 2>&1

HTTPS Example:

    nohup stunnel -D 0 -f -c -d 2000 -r www.host.com:443 &

    cookie_monster -t -p 2000 -n 100000 -f www.host.com 127.0.0.1 /app/login.html > out 2>&1

HTTPS Login Post Example:

    nohup stunnel -f -c -d 127.0.0.1:8088 -r www.host.com:443 &

    cookie_monster -t -p 8088 -n 100000 -f www.host.com -P 'login=username&pass=password&submit=Log+On' 127.0.0.1 /path/login.html

cookie_monster version: 1.6.1 2025-04-09
```


# Reporting Security Issues

To report a security issue, please visit "[Reporting Security Issues](https://github.com/lcn2/cookie_monster/security/policy)".
