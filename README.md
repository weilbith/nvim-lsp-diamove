# !!!DEPRACTED!!!

**With the development of NeoVim all features of this plugin have become part of the core. Please read the commit message for  version [f75be5e](https://github.com/neovim/neovim/commit/f75be5e9d510d5369c572cf98e78d9480df3b0bb) to get further details.**

---

# NeoVim Language Server Diagnostic Movements

Add the missing navigation commands for the LSP diagnostics in a buffer.
This is an addition to the already existing `:cabove`, `:cbelow`, `:labove` and
`:lbelow` commands (which act on the quickfix and location list). In addition the
diagnostic movements are more secure and precise.

## Installation

Install the plugin with your favorite manager tool. Here is an example using
[dein.vim](https://github.com/Shougo/dein.vim):

```vim
call dein#add('weilbith/nvim-lsp-diamove', {
      \ 'on_cmd': ['Dabove', 'Dbelow'],
      \ })
```

It is recommended to use the [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig)
plugin to attach the language clients to your buffers.

## Usage

This plugin provides two the commands `:Dabove` and `:Dbelow`. They are
mapped to the convenient keys combos `[d` and `]d` (note that this can be
disabled). All commands and mappings can be prefixed with a count (e.g. `3[d`).

Please make sure that your buffer has an LSP client attached and the server is
supporting diagnostics. _NeoVim_ enables the pushing of diagnostics per default.

## Comparison & Design Decisions

This plugin attempts to be minimalistic. Therefore it does **not** customize the
callback function for the diagnostics. Rather it reuses the published
[`vim.lsp.util.diagnostics_by_buf`](https://neovim.io/doc/user/lsp.html) table.
The only advanced logic is the correct sort order of the diagnostic
list to guarantee precise jumps. This is for example not the case for `:cabove`
etc.
If you search for a plugin with more features to customize the diagnostic
behavior, checkout the
[diagnostic-nvim](https://github.com/haorenW1025/diagnostic-nvim) plugin. But be
aware that such plugin re-rewrites/overwrites the LSP callback completely (not extending it, at
the [current
state](https://github.com/haorenW1025/diagnostic-nvim/commit/4255eb7697e45550292076c4957028ee4d7232e1))
and thereby may not profit by future updates of _NeoVim_.
