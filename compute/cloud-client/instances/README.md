Google Cloud Compute PHP Instances Samples
==========================================

[![Open in Cloud Shell][shell_img]][shell_link]

[shell_img]: http://gstatic.com/cloudssh/images/open-btn.svg
[shell_link]: https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googlecloudplatform/php-docs-samples&page=editor&working_dir=compute/cloud-client/instances

This directory contains samples for calling [Google Cloud Compute][compute]
from PHP. Specifically, they show how to manage your Compute Engine [instances][instances].

[compute]: https://cloud.google.com/compute/docs/apis
[instances]: https://cloud.google.com/compute/docs/instances/stop-start-instance

## Setup

### Authentication

Authentication is typically done through [Application Default Credentials][adc]
which means you do not have to change the code to authenticate as long as
your environment has credentials. You have a few options for setting up
authentication:

1. When running locally, use the [Google Cloud SDK][google-cloud-sdk]

        gcloud auth application-default login

1. When running on App Engine or Compute Engine, credentials are already
   set-up. However, you may need to configure your Compute Engine instance
   with [additional scopes][additional_scopes].

1. You can create a [Service Account key file][service_account_key_file]. This file can be used to
   authenticate to Google Cloud Platform services from any environment. To use
   the file, set the ``GOOGLE_APPLICATION_CREDENTIALS`` environment variable to
   the path to the key file, for example:

        export GOOGLE_APPLICATION_CREDENTIALS=/path/to/service_account.json

[adc]: https://cloud.google.com/docs/authentication#getting_credentials_for_server-centric_flow
[additional_scopes]: https://cloud.google.com/compute/docs/authentication#using
[service_account_key_file]: https://developers.google.com/identity/protocols/OAuth2ServiceAccount#creatinganaccount

## Install Dependencies

1. **Install dependencies** via [Composer](http://getcomposer.org/doc/00-intro.md).
    Run `php composer.phar install` (if composer is installed locally) or `composer install`
    (if composer is installed globally).

1. Create a service account at the
[Service account section in the Cloud Console](https://console.cloud.google.com/iam-admin/serviceaccounts/)

1. Download the json key file of the service account.

1. Set `GOOGLE_APPLICATION_CREDENTIALS` environment variable pointing to that file.

## Samples

To run the Compute Samples, run any of the files in `src/` on the CLI to print
the usage instructions:

```
$ php src/list_instances.php

Usage: list_instances.php $projectId $zone

  @param string $projectId Your Google Cloud project ID.
  @param string $zone The zone to create the instance in (e.g. "us-central1-a")
```

### Create an instance

```
$ php src/create_instance.php $YOUR_PROJECT_ID "us-central1-a" "my-new-instance-name"
Created instance my-new-instance-name
```

### List instances

```
$ php src/list_instances.php $YOUR_PROJECT_ID "us-central1-a"
Instances for YOUR_PROJECT_ID (us-central1-a)
 - my-new-instance-name
```

### Delete an instance

```
$ php src/delete_instance.php $YOUR_PROJECT_ID "us-central1-a" "my-new-instance-name"
Deleted instance my-new-instance-name
```

## Troubleshooting

If you get the following error, set the environment variable `GCLOUD_PROJECT` to your project ID:

```
[Google\Cloud\Core\Exception\GoogleException]
No project ID was provided, and we were unable to detect a default project ID.
```

## The client library

This sample uses the [Google Cloud Compute Client Library for PHP][google-cloud-php].
You can read the documentation for more details on API usage and use GitHub
to [browse the source][google-cloud-php-source] and [report issues][google-cloud-php-issues].

[google-cloud-php]: https://googleapis.github.io/google-cloud-php/#/docs/google-cloud/v0.152.0/compute/readme
[google-cloud-php-source]: https://github.com/GoogleCloudPlatform/google-cloud-php
[google-cloud-php-issues]: https://github.com/GoogleCloudPlatform/google-cloud-php/issues
[google-cloud-sdk]: https://cloud.google.com/sdk/
