# Zotcite

> [!Note]
> This fork contains local modifications for my workflow. The modifications
> were implemented with Codex/Claude.



_Zotcite_ is a Neovim plugin that provides integration with Zotero for
Markdown, Quarto, Rmd, vimwiki, Typst, LaTeX, and Rnoweb file types. With
_zotcite_ you can:

  - Do auto-completion of citation keys from Zotero database in
    Markdown, RMarkdown, Quarto, LaTeX, Rnoweb, and Typst documents.

  - Quickly see a notification with information on the reference under the
    cursor.

  - Open the PDF attachment of the reference associated with the citation key
    under the cursor.

  - Extract notes and highlighted text from PDF attachments of
    references.

  - Extract Zotero notes and annotations from Zotero database.

## Local changes in this version

- Better BibTeX citation keys are the default. If no Zotero entries have
  Better BibTeX keys, Zotcite falls back to template-generated keys.

- Better BibTeX keys are also read from `Citation Key: ...` lines in Zotero's
  Extra field when they are not exposed directly in the database.

- `:Zseek` now inserts the selected reference as a citation at the cursor. Use
  `:Zseek!` to only echo the selected reference. The default `<Leader>zs`
  mapping opens the same insertion picker.

- In TeX and Rnoweb buffers, Zseek inserts `\cite{key}` when the cursor is not
  already inside a citation command, and appends the selected key to the
  existing `\...cite...{}` block when it is.

- The Telescope picker shows `+` in the first column for entries with Zotero
  attachments.


## Installation

**Dependencies**

- Required:

  - Zotero >= 5 if not using Better-BibTeX. For Better-BibTeX users, Zotero >=
    8 is required.

  - The `sqlite3` command line application.

  - [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) as
    well as the tree-sitter parser for `yaml`.

- Optional:

  - [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) for an
    alternative way of inserting citation keys.

  - Python 3 is required if you are going to convert OpenDocument texts (`odt`)
    to markdown or extract annotations inserted in a PDF document by a PDF
    viewer other than Zotero. Please, see the Zotcite documentation for details.

Zotcite can be installed as any Neovim plugin. Below is an example of how to
install `zotcite` with [lazy.nvim](https://github.com/folke/lazy.nvim):

```lua
    {
        "jalvesaq/zotcite",
        dependencies = {
            "nvim-treesitter/nvim-treesitter",
            "nvim-telescope/telescope.nvim",
        },
        config = function ()
            require("zotcite").setup({
                -- your options here (see doc/zotcite.txt)
            })
        end
    },
```

> [!Note]
> You don't need to lazy load zotcite because it is a filetype plugin. This
> means that it already lazy loads its modules, which will be enabled only for
> the supported file types.

## Usage

Please, read the plugin's
[documentation](https://raw.githubusercontent.com/jalvesaq/zotcite/master/doc/zotcite.txt)
for further instructions.

## Screenshots

[See the Wiki](https://github.com/jalvesaq/zotcite/wiki/Screenshots)

## See also:

Zotcite's original Python code was based on the
[citation.vim](https://github.com/rafaqz/citation.vim) project.

Similar project: [telescope-zotero.nvim](https://github.com/jmbuhr/telescope-zotero.nvim)
