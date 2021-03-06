direnv.vim - yup
================

This plugin aim is to integrate [Direnv][direnv] and [Vim][vim]. Because Vim can
shell out to other tools it's nice if the environment is in sync with the usual
shell.

It also `set filetype=bash` for `.envrc` files.

Features
--------

* Direnv environment loading
* `filetype=bash` for `.envrc` files
* Asynchronous running of Direnv command which won't delay your workflow.
  Supported in Vim 8 (with `job` and `channel`) or NeoVim.

Limitations
-----------

The Vimscript syntax seems to limit keys to alphanumeric characters. If any
environment variable key is something different the plugin might fail.

Mainline Vim doesn't (yet) have auto command event that is fired on directory
change, however in [NeoVim][neovim] there already is one named: `DirChange`.
Thanks to that Direnv will be fired only on `VimEnter` (as entering Vim isn't
directory change) and on `DirChange`.

For mainline Vim there is fallback that run on each `BufEnter` (not ideal
solution, but for now we have no other option).

Due to asynchronous calls to Direnv if you work too fast then it can happen that
variables from `.envrc` will not be yet loaded. However highly unlikely you are
so fast.

Install
-------

Then install the plugin.
With [Pathogen](https://github.com/tpope/vim-pathogen)

```
git clone https://github.com/direnv/direnv.vim.git ~/.vim/bundle/direnv.vim
```

and restart.

TODO
----

- Allow/deny authorization mechanism.
- Add proper Vim documentation.

My Vimscript skill is tangent to zero, feedback is welcome
<https://github.com/direnv/direnv.vim>

[direnv]: https://direnv.net
[vim]: http://vim.org
[neovim]: https://neovim.io
