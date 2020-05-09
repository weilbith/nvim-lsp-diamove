# NVim LSP DiaMove

Add the missing navigation commands for the LSP diagnostics in a buffer.
This is an addition to the already existing `:cabove`, `:cbelow`, `:labove` and
`:lbelow` commands for the quickfix and location list. In addition the
diagnostic movements are more secure and precise.

## Installation

Install the plugin with your favorite manager tool. Here is an example using
[dein.vim](https://github.com/Shougo/dein.vim):

```vim
call dein#add('weilbith/nvim-lsp-diamove')
```

It is recommended to use install the
[nvim-lsp](https://github.com/neovim/nvim-lsp) plugin attach language clients to
your buffers.

## Usage

This plugin provides with two the commands `:Dabove` and `:Dbelow`. They are
mapped to the convenient keys combos `[d` and `[d` (note that this can be
disabled). All commands and mappings can be prefixed with a count (e.g. `3[d`).

Please make sure that your buffer has a LSP client attached and the server is
supporting diagnostics. _NeoVim_ enables the pushing of diagnostics per default.
