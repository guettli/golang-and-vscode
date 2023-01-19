# Golang and VSCode

F2: refactor (rename Method)

alt-shift-CursorLeft/Right move to previous places

ctrl-` --> show/hide terminal.

ctrl-e --> switch between recently used files.

ctrl-space --> autocomplete (for example find the struct in a package and add the package name before the name)

Bookmark plugin: ctrl-alt-k (set bookmarks), ctrl-alt-j (jump to bookmarks, multiple times to jump to other bookmarks)

You want to open a file from the terminal: `> code foo.go`

"Go to Symbol in Workspac": ctrl-t

"Go to file": ctrl+p

"Show all commands": ctrl+shift+p

ctrl-. --> "Quick fix" (for example fill struct)

ctrl-r --> Open recent Workspace. This is better than "File > Open Recent" because it provides autocomplete.

ctrl-s --> format and clean file. For example you get `.../foo_test.go:24:2: imported and not used: "github.com/somerepo/somepkg"` since you removed the usage of "somepkg", then you don't need to move up to the import statements. Just hit ctrl-s.

ctrl-g --> goto line

ctrl-shift-p "Go: Generate Unit Tests for File". But I don't use the table-driven test which vscode generates. I prefer boring straightforward tests, except I would have many rows in the table of the table-driven test. Related: [table-driven tests are overrated](https://www.reddit.com/r/golang/comments/10e9ebg/tabledriven_tests_are_overrated/)

f4 --> goto next search result (for example after a search with ctrl-shift-f): Related https://stackoverflow.com/questions/75161780/go-to-first-match-of-ctrl-shift-f-search

go to beginning of a function: click on last element in breadcrumb-bar, then ENTER.

# Plugins

Go

# ripgrep in vscode

in .bashrc:
```
if [[ "$TERM_PROGRAM" == 'vscode' ]]; then
  alias 'rg'='rg --no-heading --column'
fi
```

Then you get output like this:
```
foo/bar.go:33:43: ... your term
```

And `foo/bar.go:33` is a hyperlink you can click.

# Config

## Keybinding

In general I try to use the keybindings of vscode. Here are some keybindings which I configured.

ctrl-ö --> "Go: Test function at Cursor or Test Previous"

# Missing

https://stackoverflow.com/questions/75085670/vscode-symbol-search-but-only-in-my-code

https://stackoverflow.com/questions/75071292/vscode-move-go-code-type-function-to-other-file

https://www.reddit.com/r/vscode/comments/10e7aoj/middle_button_paste_on_linux_only_works_after/

history for selection

recently changed locations.

Nice color theme. Overall vscode is a bit too colorful.

# Not solved yet

Copy+Paste does not work in the git-diff view of deleted lines: https://github.com/microsoft/vscode/issues/8226



