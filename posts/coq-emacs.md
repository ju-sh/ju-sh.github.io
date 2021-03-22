# Setting up emacs as interface for coq

Proof general mode of emacs, together with the company-coq package can be used as an interface for coq as mentioned [here][4].

## .emacs file

Add the following to your `.emacs` file.

    (require 'package)
    (add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
    (package-initialize)

(Source: [Proof General github page][3])

## Edit gpg.conf

Go to `~/.emacs.d/elpa/gnupg/` directory (make it if it doesn't exist) and open the gpg.conf file.

Add the following to it.

    keyserver hkp://keys.gnupg.net:80

## Receive gpg keys

Run

    gpg --homedir ~/.emacs.d/elpa/gnupg --receive-keys 066DAFCB81E42C40

## Install the packages inside emacs

Finally, open up emacs and run (to update the list of packages, I guess)

    M-x package-refresh-contents

Then, install the packages with

    M-x package-install RET proof-general 
    M-x package-install RET company-coq

[company-coq][5] extends the proof general's coq mode.

## Versions of software involved
 - Coq: 8.12.0
 - proof-general: 20210131.2042
 - company-coq: 20200729.401

## References
 - [https://github.com/ProofGeneral/PG#installing-proof-general](https://github.com/ProofGeneral/PG#installing-proof-general)
 - [https://coq.inria.fr/user-interfaces.html](https://coq.inria.fr/user-interfaces.html)
 - [https://github.com/cpitclaudel/company-coq](https://github.com/cpitclaudel/company-coq)


[3]: https://github.com/ProofGeneral/PG#installing-proof-general
[4]: https://coq.inria.fr/user-interfaces.html
[5]: https://github.com/cpitclaudel/company-coq
