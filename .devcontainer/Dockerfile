FROM ocaml/opam:ubuntu-24.04-ocaml-5.4
LABEL maintainer="Ivan Blazhko <iblazhko@fastmail.in>"

ARG OPAM_VERSION=2.5.0
ARG OCAML_VERSION=5.4.1

USER root
RUN printf '\n\n' | /usr/bin/bash -c "/usr/bin/bash <(curl -fsSL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh) --version $OPAM_VERSION"

USER opam
RUN opam switch create $OCAML_VERSION --jobs=8 && \
    echo "eval \$(opam env --switch=$OCAML_VERSION)" >> $HOME/.bashrc && \
    eval $(opam env --switch=$OCAML_VERSION) && \
    opam update && \
    opam install ocaml-lsp-server ocamlformat odoc utop alcotest ounit2 qcheck base core -y
