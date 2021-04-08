# Installing coq using opam (Ubuntu and FreeBSD)

 - Date created: Feb-2021
 - Last updated: 07-Apr-2021

As seen in Windows XP.

---

[opam][1] is a 'source-based package manager for OCaml'.

## Ubuntu

This is just what worked for me on an Ubuntu 18.04 computer.

I just followed some docs and installed coq (8.12.0) using opam.

### opam

An official release of opam is available in a [ppa][2]. We can use that.

    sudo add-apt-repository ppa:avsm/ppa
    sudo apt update
    sudo apt install opam

### Set up an opam environment

    opam init
    opam switch create coq 4.10.0+flambda  # (twice?)
    opam install num ocamlfind lablgtk3-sourceview3

### Coq

Download the version of coq that you would like to have.

Now let's compile coq. Might take a while.

    ./configure
    make
    sudo make install

### Versions of software involved
 - Coq: 8.12.0
 - opam: 2.0.4
 - Ubuntu 18.04

## FreeBSD

What worked for FreeBSD system (FreeBSD 12.2-RELEASE-p4).

### opam

Use the version from the FreeBSD Ports Collection.

    cd /usr/ports/devel/ocaml-opam
    sudo make install clean

### Build and install coq

Once opam has been installed initialize it with

    opam init

Now install `opam-depext` to figure out what more packages are needed to build coq.

    opam install opam-depext
    eval $(opam env)
    opam-depext coq

Install any more packages if needed.

Now, 'pin' the coq version to the version you need (to avoid auto upgradation of the package so that potential future trouble due to version mismatch may be avoided) and install it.

    opam pin add coq 8.13.1
    eval $(opam env)

### Versions of software involved
 - Coq: 8.13.1
 - opam: 2.0.8
 - FreeBSD 12.2-RELEASE-p4

## References
 - [https://opam.ocaml.org/](https://opam.ocaml.org/)
 - [https://coq.inria.fr/opam-using.html](https://coq.inria.fr/opam-using.html)
 - [https://opam.ocaml.org/doc/Install.html#Ubuntu](https://opam.ocaml.org/doc/Install.html#Ubuntu)
 - [https://github.com/ProofGeneral/PG#installing-proof-general](https://github.com/ProofGeneral/PG#installing-proof-general)
 - [https://coq.inria.fr/user-interfaces.html](https://coq.inria.fr/user-interfaces.html)
 - [https://github.com/cpitclaudel/company-coq](https://github.com/cpitclaudel/company-coq)


[1]: https://opam.ocaml.org/
[2]: https://opam.ocaml.org/doc/Install.html#Ubuntu
[3]: https://opam.ocaml.org/doc/Install.html#Binary-distribution
[5]: https://github.com/cpitclaudel/company-coq
[6]: https://coq.inria.fr/opam-using.html
