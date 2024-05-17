<!-- SignServer Community logo -->
<a href="https://signserver.org">
    <img src=".github/images/community-signserver.png?raw=true)" alt="SignServer logo" title="SignServer" height="70" />
</a>
<!-- SignServer Enterprise logo -->
<a href="https://www.keyfactor.com/products/signserver-enterprise/">
    <img src=".github/images/keyfactor-signserver-enterprise.png?raw=true)" alt="SignServer logo" title="SignServer" height="70" />
</a>

# SignServer Signing action

The SignServer Signing action can return a signed input produced by the provided SignServer endpoint and upload it as an artifact for access or further use.

# Community Support

In our Community we welcome contributions. SignServer Signing action is open source and community supported, there is no support SLA, but a helpful best-effort Community.

* To report a problem or suggest a new feature, use the [Issues](https://github.com/Keyfactor/signserver-signing-action/issues) tab.
* If you want to contribute actual bug fixes or proposed enhancements, use the [Pull requests](https://github.com/Keyfactor/signserver-signing-action/pulls) tab.
* Ask the community for ideas: [SignServer Discussions](https://github.com/Keyfactor/signserver-ce/discussions).
* Read more in our documentation: [SignServer Documentation](https://doc.primekey.com/signserver).
* See release information: [SignServer Release information](https://doc.primekey.com/signserver/signserver-release-information).
* Read more on the open source project website: [SignServer website](https://www.signserver.org/).

# Commercial Support

Commercial support is available for [SignServer Enterprise](https://www.keyfactor.com/platform/keyfactor-signserver-enterprise/).

# License

For License information, see [LICENSE](https://github.com/Keyfactor/signserver-signing-action/blob/main/LICENSE)

# Prerequisities

A running SignServer instance with the needed worker configured.

The supported workers as well as authentication types are listed below.

# Supported workers

The current version of this action supports 3 types of workers:
* `JArchiveSigner`: takes jar as input and uploads signed jar as artifact
* `PDFSigner`: takes pdf as input and uploads signed pdf as artifact
* `PlainSigner`: takes any input and uploads signed input as artifact

# Supported authentication types

The following authentication types are supported:
* `NOAUTH` - will be used as default if no clientcert is provided
* `CLIENTCERT` - need to provide clientcert and password for authentication

# Input parameters

`endpoint`: (Required) The SignServer signing endpoint.

`file-path`: (Required) The path to the file to be signed.

`worker-name`: (Required) The name of the Signer to use for the signing.

`worker-type`: (Required) The type of worker.

`client-cert`: (Optional) The client cert needed for authorization.

`password`: (Optional) Password for clientcert.


# Example usage

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
