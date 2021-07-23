# telescope-repo.nvim: jump around the repositories in your filesystem

`telescope-repo` is an extension for [telescope.nvim][] that searches the filesystem for git (or other scm) repositories. One can then select a repository and open files in it.

[telescope.nvim]: https://github.com/nvim-telescope/telescope.nvim

**`telescope-repo.nvim` is based on [telescope-repo.nvim](https://github.com/nvim-telescope/telescope-ghq.nvim)**

## Installation

```lua
use{
  'nvim-telescope/telescope.nvim',
  requires = {
    'nvim-telescope/telescope-ghq.nvim',
  },
  config = function()
    require'telescope'.load_extension'ghq'
  end,
}
```

## External dependancies

### Required

- [`fd`][]

[`fd`]: https://github.com/sharkdp/fd

### Optional

- [`glow`][] to preview markdown files, will fallback to [`bat`][] if not present (and uses `cat` if neither are present)

[`glow`]: https://github.com/charmbracelet/glow
[`bat`]: https://github.com/sharkdp/bat

## Usage

Now supports `repo list` only.

### list

`:Telescope repo list`

Running `repo list` and list repositories' paths. In default, it does actions below when you input keys.

| key              | action               |
|------------------|----------------------|
| `<CR>` (edit)    | `builtin.git_files`  |
| `<C-x>` (split)  | `:chdir` to the dir  |
| `<C-v>` (vsplit) | `:lchdir` to the dir |
| `<C-t>` (tabnew) | `:tchdir` to the dir |

#### options

#### `bin`

Filepath for the binary `fd`.

```vim
" path can be expanded
:Telescope repo list bin=~/fd
```

#### `cwd`

Transform the result paths into relative ones with this value as the base dir.

Default value: `vim.fn.getcwd()`

#### `tail_path`

Show only basename of the path.

Default value: `false`

#### `shorten_path`

Call `pathshorten()` for each path.

Default value: `false`

## FAQ

### Getting the repository list is slow

You can use your `.fdignore` to exclude some folders from your filesystem. If there is enough interest, [#1](https://github.com/cljoly/telescope-repo.nvim/issues/1) could further enhance this

### How to use this plugin with Mercurial (hg), Fossil, Pijul…

See [#2](https://github.com/cljoly/telescope-repo.nvim/issues/2)
