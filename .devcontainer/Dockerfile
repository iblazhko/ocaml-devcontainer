FROM ocaml/opam:ubuntu-lts-ocaml-5.1
RUN opam switch create 5.1.0 --jobs=8 && \
    eval $(opam env --switch=5.1.0) && \
    opam install ocaml-lsp-server ocamlformat alcotest ounit2 qcheck base core -y
