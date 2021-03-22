# Installing coqtail in nvim with vim-plug

coqtail is a [user interface][1] for the coq proof assistant that can be used with the vim/nvim editor. Coqtail is available as a vim plugin.

It is probably a good idea to use a plugin manager while installing installing vim plugins. Especially when you are using multiple plugins.

There are many plugin managers available for vim. I use [vim-plug][2], which as they say, is a 'minimalistic vim plugin manager'.

I prefer to use nvim when I need to work with coqtail. First check if the current version of coqtail is supported in the version of nvim that you have.

We can install vim-plug to work with nvim using:

    sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
           https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'

Now ask nvim to use vim-plug by editing the file at `/home/user/.config/nvim/init.vim` and adding the following.

    " Plugins will be downloaded under the specified directory.
    call plug#begin('~/.config/nvim/plugged')

    " Make sure you use single quotes
    Plug 'whonore/Coqtail'

    " Initialize plugin system
    call plug#end()

Afterwards, start nvim and [do][3]

    :PlugInstall

to install the plugins that we mention.

and run 

    :UpdateRemotePlugins

to make sure that the plugin is [loaded automatically][4] when required.

This command needs to be run every time a plugin is installed, updated or deleted.

And now you should be good to go. :-)


### References
 - [https://coq.inria.fr/user-interfaces.html](https://coq.inria.fr/user-interfaces.html)
 - [https://github.com/junegunn/vim-plug](https://github.com/junegunn/vim-plug)
 - [https://www.linode.com/docs/guides/how-to-install-neovim-and-plugins-with-vim-plug/](https://www.linode.com/docs/guides/how-to-install-neovim-and-plugins-with-vim-plug/)
 - [https://neovim.io/doc/user/remote_plugin.html](https://neovim.io/doc/user/remote_plugin.html)


[1]: https://coq.inria.fr/user-interfaces.html
[2]: https://github.com/junegunn/vim-plug
[3]: https://www.linode.com/docs/guides/how-to-install-neovim-and-plugins-with-vim-plug/
[4]: https://neovim.io/doc/user/remote_plugin.html
