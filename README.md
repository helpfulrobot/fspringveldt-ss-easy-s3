# Amazon S3 bucket integration
Seamlessly integrates assets,theme assets, css and js with S3 - with optional CloudFront CDN.
## Minimum requirements
```
silverstripe/framework: ^3.4.* 
silverstripe/cms: ^3.4.*
aws/aws-sdk-php: ^3.18
```
## Installation and Setup
To install, run below from root of SilverStripe installation
```bash 
> composer require fspringveldt/ss-easy-s3
``` 
http://**your-site-url**?flush=1 once composer is complete the flush the manifest.

Once installed and configured, head on over to Amazon, create an account and bucket. Below are some resources you can use to assist during this process.

* [Using CloudFront with Amazon S3](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/MigrateS3ToCloudFront.html)
* [Getting Started with CloudFront](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html)
* [Syncing data with Amazon S3](http://docs.aws.amazon.com/aws-sdk-php/v2/guide/service-s3.html#syncing-data-with-amazon-s3)


Once your Amazon info is sorted, you'll need the following info from the Amazon console:

* key
* secret
* region
* bucket
* url
* distribution-id

...which is then input into your mysite the config file as: 
```yaml
S3Facade:
  config:
    dev:
      key:
      secret:
      region:
      bucket:
      url:
      distribution-id:
    test:
      key:
      secret:
      region:
      bucket:
      url:
      distribution-id:
    live:
      key:
      secret:
      region:
      bucket:
      url:
      distribution-id:
```

_NB: You can setup multiple configs per environment_
. A simple flush should complete your setup.

This module will __automagically__ re-write all your URL's to point to the resources from either the S3 Bucket or CloudFront url you specified.

## Migrate to S3 build-task
There is also a handy tool which will upload entire directories to your S3 bucket blisteringly fast. You can specify which directories to upload via the [_ _config/config.yml_](_config/config.yml) file by adding more entries to the ```migrationFolders``` property. The assets folder is added by default.
