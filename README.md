<!-- archived-provider -->
This Terraform provider is archived, per our [provider archiving process](https://terraform.io/docs/internals/archiving.html). What does this mean?

1. The code repository and all commit history will still be available.
1. Existing released binaries will remain available on the releases site.
1. Documentation will remain on the Terraform website.
1. Issues and pull requests are not being monitored.
1. New releases will not be published.

If anyone from the community or an interested third party is willing to maintain it, they can either be granted access here or fork the repository for their own uses. If you are interested in maintaining this provider, please reach out to the [Terraform Provider Development Program](https://www.terraform.io/guides/terraform-provider-development-program.html) at *terraform-provider-dev@hashicorp.com*.

---

<!-- /archived-provider -->

Terraform Provider
==================

- Website: https://www.terraform.io
- [![Gitter chat](https://badges.gitter.im/hashicorp-terraform/Lobby.png)](https://gitter.im/hashicorp-terraform/Lobby)
- Mailing list: [Google Groups](http://groups.google.com/group/terraform-tool)

<img src="https://cdn.rawgit.com/hashicorp/terraform-website/master/content/source/assets/images/logo-hashicorp.svg" width="600px">

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.12.x
-	[Go](https://golang.org/doc/install) 1.11 (to build the provider plugin)

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/terraform-providers/terraform-provider-ultradns` and built it   

```sh
$ mkdir -p $GOPATH/src/github.com/terraform-providers; cd $GOPATH/src/github.com/terraform-providers
$ git clone https://github.com/smehboub/terraform-provider-ultradns.git
$ cd $GOPATH/src/github.com/terraform-providers/terraform-provider-ultradns
$ GO111MODULE=on go get github.com/hashicorp/terraform@v0.12.0
$ GO111MODULE=on go mod tidy
$ GO111MODULE=on go mod vendor
$ make build
```

Copy the provider to terraform plugins location   
-	[Terraform plugins locations](https://www.terraform.io/docs/extend/how-terraform-works.html#plugin-locations)

Using the built provider
------------------------

Open a terminal (GIT BASH for Windows or a another for Linux and macOS)   

```sh
$ git clone https://github.com/smehboub/terraform-provider-ultradns.git
$ cd terraform-provider-ultradns/scripts
$ chmod 700 install-provider.sh
$ ./install-provider.sh
```

Developing the Provider
---------------------------

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.11+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

```sh
$ make bin
...
$ $GOPATH/bin/terraform-provider-ultradns
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```
