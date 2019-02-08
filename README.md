# iiif-sandbox-simple
A simple sandbox for experimenting with different IIIF viewers.

## Acknowledgements
The code and basic implementation for this site was shamelessly borrowed from
[this IIIF Workshop](https://github.com/jronallo/iiif-workshop-new).

## How to update the viewer code
This is easiest to do if you have [Yarn](https://yarnpkg.com/en/) installed.

```
yarn add universalviewer
yarn add mirador
cp -r node_modules/mirador/dist mirador
cp -r node_modules/universalviewer/uv uv
```
There may be a better way to refresh the viewer code, but for now, that will
have to do.

## How to manually deploy this code to our AWS S3 bucket
You must first [install](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
and [configure the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).

Here's a hint, you'll need to login to the [UCLA Library AWS User Portal](https://uclalibrary.awsapps.com/start).
Then find your credentials...
![AWS CLI Access Screenshot](docs/images/aws-access-screenshot.png)

When you have your credentials set up, you can run the following as a sanity check:
```
aws s3 ls
```
If that command returns at least one bucket named `iiif-viewers`, you're ready to deploy!

Assuming you're in the root of this project, run the following to deploy it to
the iiif-viewers bucket on S3:

Start with a dry run to verify everything is OK:

```
aws --dryrun s3 sync . s3://iiif-viewers/ --exclude "node_modules*" --exclude ".git*" --delete
```

As soon as you're sure that command will work correctly, omit the `--dryrun`.

```
aws s3 sync . s3://iiif-viewers/ --exclude "node_modules*" --exclude ".git*" --delete
```
