FROM ocaml/opam:ubuntu-22.04-ocaml-5.3
LABEL maintainer="Ivan Blazhko <iblazhko@fastmail.in>"

ARG OPAM_VERSION=2.3.0
ARG OCAML_VERSION=5.3.0

RUN printf '\n\n' | bash -c "sh <(curl -fsSL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh) --version $OPAM_VERSION" && \
    opam switch create $OCAML_VERSION --jobs=8 && \
    eval $(opam env --switch=$OCAML_VERSION) && \
    opam update && \
    opam install ocaml-lsp-server ocamlformat odoc utop alcotest ounit2 qcheck base core -y
