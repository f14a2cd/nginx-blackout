# nginx-blackout

A little guide how to turn the blackout on automatically in the needed time interval.

1) Add the HTML-file from this repo (english or russian version) somewhere to the server (e.g. `/var/www/nginx-blackout/index.html`)
2) Edit your root location in the nginx config to be like this:

```nginx
location /nginx-blackout {
    root /var/www;
    break;
}

location / {
    if ($time_iso8601 ~ ^2019-12-15T09:[0-2][0-9]:[0-9][0-9] ) {
    	return 302 /nginx-blackout;
    }
    # ... usual location config
}
```

3) Check that it works with the current date :)
