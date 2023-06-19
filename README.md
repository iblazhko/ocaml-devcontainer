# OCaml Dev Container

This repository contains template for an OCaml project using
[Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers).

[`devcontainer.json`](./.devcontainer/devcontainer.json) uses a pre-built
Docker image based on Ubuntu 22.04 with the following components available

* `opam`
* `ocaml` 5.0.0
* `ocaml-lsp-server`
* `ocamlformat`
* `alcotest`
* `base`
* `core`

Image is `iblazhko/ocaml-dev:5.0.0` and it is available from Docker Hub:
<https://hub.docker.com/r/iblazhko/ocaml-dev>.

If you need to make any modifications to the development environment,
use included [`Dockerfile`](./.devcontainer/devcontainer.json) as a
starting point, modify the `Dockefile` to your liking, then build the image

```bash
docker build -t '<tag>:<version>' .
```

and update `"image"` value in the `devcontainer.json` to use the new image.

Alternatively, use `"dockerFile"` option instead of the `"image"`
in `devcontainer.json`.
