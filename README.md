# DockerMocker
Serves any number of static filetypes for early development testing, but is deployable to cloud for more accurate
results for testing interaction with your mifedom or just a generic serverless scheme.

## Quickstart
To encourage rapid iteration/deployment, this project is configured for use with [bingo](https://github.com/wejafoo/bin-go),
a mife-optimized build and deployment utility.

##### Local

$  `bingo --local`

##### GCP Remote

$  `REMOTE_ALIAS=stage  bingo --remote --alias=${REMOTE_ALIAS}`


## Notes on Configuration
### Extending Defaults

**Local deploy**s mount up `./dist` to `/usr/share/nginx/html`.  So, you can just add new test routes(directories) and
endpoints(files(with appropriate extensions)) to './dist' on the fly.

**Remote deploy**s, by default, copy the `./dist` to `/usr/share/nginx/html` on the image for subsequent remote deployment.
However, if you prepend your remote request route with `assets/`, requests can be proxied to the static files in your
GCP storage bucket or, by default, to your firebase hosting tied to the domain in bingo's domain-specific config file.

All other configurations are dependent on your own Nginx magic, which can be safely applied to
`./nginx/nginx.template.conf`.
