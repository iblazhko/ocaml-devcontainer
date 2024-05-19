# OCaml Dev Container

This repository contains template for an OCaml project using
[Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers).

[`devcontainer.json`](./.devcontainer/devcontainer.json) uses a pre-built
Docker image based on `ocaml/opam:ubuntu-22.04-ocaml-5.2` with the following
components available:

-   `opam` 2.1.5
-   `ocaml` 5.2.0
-   `ocaml-lsp-server`
-   `ocamlformat`
-   `odoc`
-   `alcotest`
-   `ounit2`
-   `qcheck`
-   `base`
-   `core`

Image is `iblazhko/ocaml-dev:5.2.0` and it is available from Docker Hub:
<https://hub.docker.com/r/iblazhko/ocaml-dev>.

```bash
 docker pull iblazhko/ocaml-dev:5.2.0
```

If you need to make any modifications to the development environment,
use included [`Dockerfile`](./.devcontainer/Dockerfile) as a
starting point, modify the `Dockefile` to your liking, then build the image:

```bash
docker build -t '<tag>:<version>' .
```

and update `"image"` value in the `devcontainer.json` to use the new image.

Alternatively, use `"dockerFile"` option instead of the `"image"`
in `devcontainer.json`, note however that image building may take a long time and this will affect startup time of devcontainer, so it is recommended to use a pre-built image.

To build multi-platform image, use following commands in `.devcontainer`:

Create multi-platform buildx container if you do not have one already:

```bash
docker buildx create --name multiplatform --bootstrap --use
```

Invoke multi-platform build and load resulting images into local Docker:

```bash
docker buildx build --platform linux/amd64,linux/arm64 --load --tag iblazhko/ocaml-dev:5.2.0 --tag iblazhko/ocaml-dev:5.2 --tag iblazhko/ocaml-dev:latest .
```

Invoke multi-platform build and push resulting images to Docker Hub:

```bash
docker buildx build --platform linux/amd64,linux/arm64 --push --tag iblazhko/ocaml-dev:5.2.0 --tag iblazhko/ocaml-dev:5.2 --tag iblazhko/ocaml-dev:latest .
```
