# Static Site Quickstart
All you need to get started with a static website. Search and replace `mystaticsite.com` to whatever `site.com` you want throughout. It should be replaced in the Cloudformation template, the github action to deploy the stack, and in the config.toml example.

## AWS Generated Resources
### Manual Steps BEFORE Running:
- Register your Domain in Route53. AWS will generate a Route53 Hosted Zone after registration.
- Request a public ACM Certificate with AWS Certificate Manager, using DNS validation.

### Running Cloudformation
Cloudformation template will generate all necessary resources to host a static website on S3 linked to a Cloudfront Distribution. All resources are listed under youre newly created stack, including:
- S3 Bucket to host the static content
- S3 Bucket Policy for public access THROUGH Cloudfront
- CloudFront Origin Access Identity to limit access to the Bucket content
- CloudFront Distribution to provide to access the Bucket content and to link up the Domain name.

## Content Generation
I like to generate static code [Hugo](https://gohugo.io/), but that isnt actually included in this repo itself. Hugo will generate everything you need; all you need to do to get started is to follow their [quickstart](https://gohugo.io/getting-started/quick-start/). Other useful commands:
- Run locally with `hugo server -D`
- Build for s3 with `hugo -D`
- Deploy build to s3 with `hugo -v deploy`

## Pipeline Automation: GitHub Action
- Validate Cloudformation with [cfn_nag](https://github.com/stelligent/cfn_nag)
