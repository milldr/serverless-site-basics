# Hugo Content
Generate hugo content here.

## Automated deployment
Add the following to `config.toml` for S3 build and deployment. Change region and bucket name as necessary
```
[deployment]
order = [".png$", ".jpg$", ".gif$", ".svg$"]

[[deployment.targets]]
URL = "s3://mystaticsite?region=us-west-2"

[[deployment.matchers]]
# Cache static assets for 20 years. should be good
pattern = "^.+\\.(js|css|png|jpg|gif|svg|ttf|woff|eot|xml)$"
cacheControl = "max-age=630720000, no-transform, public"
gzip = true

[[deployment.matchers]]
pattern = "^.+\\.(html|xml|json)$"
gzip = true
```
