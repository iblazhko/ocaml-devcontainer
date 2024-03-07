FROM ocaml/opam:ubuntu-lts-ocaml-5.3
LABEL maintainer="Ivan Blazhko <iblazhko@fastmail.in>"
RUN printf '\n\n' | bash -c "sh <(curl -fsSL https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh)" && \
    opam switch create 5.1.1 --jobs=8 && \
    eval $(opam env --switch=5.1.1) && \
    opam update && \
    opam install ocaml-lsp-server ocamlformat alcotest ounit2 qcheck base core -y
