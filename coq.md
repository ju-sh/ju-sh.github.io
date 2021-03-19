# Setting up coq with emacs as interface

This is just what worked for me on an Ubuntu 18.04 computer.

I followed some docs and compiled coq (8.12.0) from source using an environment set up with opam.

## opam

[opam][1] is a 'source-based package manager for OCaml'

An official release of opam is available in a [ppa][2]. We can use that.

```
sudo add-apt-repository ppa:avsm/ppa
sudo apt update
sudo apt install opam
```

## Set up an opam environment

```
opam init
opam switch create coq 4.10.0+flambda  # (twice?)
opam install num ocamlfind lablgtk3-sourceview3
```

## Coq

Download the version of coq that you would like to have.

Now let's compile coq. Might take a while.

```
./configure
make
sudo make install
```

## Proof general and company-coq

Proof general mode of emacs, together with the company-coq package can be used as an interface for coq as mentioned [here][4].

### .emacs file

Add the following to your .emacs file.
```
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
(package-initialize)
```

(Source: [3])

### Edit gpg.conf

Go to ~/.emacs.d/elpa/gnupg/ directory (make it if it doesn't exist) and open the gpg.conf file.

Add the following to it.

```
keyserver hkp://keys.gnupg.net:80
```

### Receive gpg keys

Run

```
gpg --homedir ~/.emacs.d/elpa/gnupg --receive-keys 066DAFCB81E42C40
```

### Install the packages inside emacs

Finally, open up emacs and run (to update the list of packages, I guess)

```
M-x package-refresh-contents
```

Then, install the packages with

```
M-x package-install RET proof-general 
M-x package-install RET company-coq
```

[company-coq][5] extends the proof general's coq mode.

## Versions of software involved
Coq: 8.12.0
opam: 2.0.4
proof-general: 20210131.2042
company-coq: 20200729.401

[1]: https://opam.ocaml.org/
[2]: https://opam.ocaml.org/doc/Install.html#Ubuntu
[3]: https://github.com/ProofGeneral/PG#installing-proof-general
[4]: https://coq.inria.fr/user-interfaces.html
[5]: https://github.com/cpitclaudel/company-coq
