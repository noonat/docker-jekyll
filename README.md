Jekyll Base Docker Image
========================

This image can be used as a base image for Dockerfiles for your Jekyll sites.
It includes Nginx (to serve the static content), Ruby (and jekyll-related gems),
and Pygments. It expects your static content to be in `/opt/site`.

A Dockerfile using it might look like so:

```dockerfile
FROM noonat/jekyll
COPY . /opt/src
WORKDIR /opt/src
RUN jekyll build && \
    rm -rf /opt/site && \
    mv _site /opt/site
```

You can override the nginx virtual host by replacing
`/etc/nginx/conf.d/jekyll.conf` with your own config.
