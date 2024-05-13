# Introduction

This action can return a signed input produced by the provided SignServer endpoint and uploads it as an artifact for access or further use.

# Prerequisities

A running SignServer instance with the needed worker configured.

The supported workers as well as authentication types are listed below.

# Current support

The current version of this action supports 3 types of workers:
* `JArchiveSigner`: takes jar as input and uploads signed jar as artifact
* `PDFSigner`: takes pdf as input and uploads signed pdf as artifact
* `PlainSigner`: takes any input and uploads signed input as artifact

And for authentication currently supported:
* `NOAUTH` - will be used as default if no clientcert is provided
* `CLIENTCERT` - need to provide clientcert and password for authentication

# Inputs

`endpoint`: (Required) The SignServer signing endpoint.

`file-path`: (Required) The path to the file to be signed.

`worker-name`: (Required) The name of the Signer to use for the signing.

`worker-type`: (Required) The type of worker.

`client-cert`: (Optional) The client cert needed for authorization.

`password`: (Optional) Password for clientcert.


# Usage

```
jobs:
  testing:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v4

    - name: Sign Jar
          uses: ./  ** change to correct action name **
          with:
            endpoint: http://localhost:80/signserver
            file-path: $GITHUB_WORKSPACE/input-file
            worker-name: PlainSigner
            worker-type: PlainSigner
```
