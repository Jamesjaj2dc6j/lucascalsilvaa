[![GoDoc](https://godoc.org/github.com/containers/image?status.svg)](https://godoc.org/github.com/containers/image) [![Build Status](https://travis-ci.org/containers/image.svg?branch=master)](https://travis-ci.org/containers/image)
=

`image` is a set of Go libraries aimed at working in various way with
containers' images and container image registries.

The containers/image library allows application to pull and push images from
container image registries, like the upstream docker registry. It also
implements "simple image signing".

The containers/image library also allows you to inspect a repository on a
container registry without pulling down the image. This means it fetches the
repository's manifest and it is able to show you a `docker inspect`-like json
output about a whole repository or a tag. This library, in contrast to `docker
inspect`, helps you gather useful information about a repository or a tag
without requiring you to run `docker pull`.

The containers/image library also allows you to translate from one image format
to another, for example docker container images to OCI images. It also allows
you to copy container images between various registries, possibly converting
them as necessary, and to sign and verify images.

## Command-line usage

The containers/image project is only a library with no user interface;
you can either incorporate it into your Go programs, or use the `skopeo` tool:

The [skopeo](https://github.com/projectatomic/skopeo) tool uses the
containers/image library and takes advantage of many of its features,
e.g. `skopeo copy` exposes the `containers/image/copy.Image` functionality.

## Dependencies

This library does not ship a committed version of its dependencies in a `vendor`
subdirectory.  This is so you can make well-informed decisions about which
libraries you should use with this package in your own projects, and because
types defined in the `vendor` directory would be impossible to use from your projects.

What this project tests against dependencies-wise is located
[in vendor.conf](https://github.com/containers/image/blob/master/vendor.conf).

## Building

For ordinary use, `go build ./...` is sufficient.


Optionally, you can use the `containers_image_openpgp` build tag (using `go build -tags …`, or `make … BUILDTAGS=…`).
This will use a Golang-only OpenPGP implementation for signature verification instead of the default cgo/gpgme-based implementation;
the primary downside is that creating new signatures with the Golang-only implementation is not supported.

## Contributing

When developing this library, please use `make` to take advantage of the tests and validation.

## License

ASL 2.0

## Contact

- Mailing list: [containers-dev](https://groups.google.com/forum/?hl=en#!forum/containers-dev)
- IRC: #[container-projects](irc://irc.freenode.net:6667/#container-projects) on freenode.net
