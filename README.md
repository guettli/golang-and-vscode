# Golang and VSCode

## My background

I was born 1976 and I write software since I am 12 years old.

Seven years ago I switched from Emacs to PyCharm.

In 2022 I learned Go, which is now part of my daily work as Cloud Engineer at [Syself](https://syself.com/).

Here are my notes which I wrote down while switching from an IntellJ based IDE to vscode.

## Shortcuts

F2: refactor (rename Method)

ctrl-` --> show/hide terminal.

ctrl-space --> autocomplete (for example find the struct in a package and add the package name before the name)

Bookmark plugin: ctrl-alt-k (set bookmarks), ctrl-alt-j (jump to bookmarks, multiple times to jump to other bookmarks)

You want to open a file from the terminal: `> code foo.go`

"Show all commands": ctrl+shift+p

ctrl-. --> "Quick fix" (for example fill struct)

ctrl-shift-p "open recent" --> Open recent Workspace. This is better than "File > Open Recent" because it provides autocomplete. By default this is mappend to ctrl-r, but I use ctrl-r for "Terminal: Run Recent Command".


# Formatting

ctrl-s --> format and clean file. For example you get `.../foo_test.go:24:2: imported and not used: "github.com/somerepo/somepkg"` since you removed the usage of "somepkg", then you don't need to move up to the import statements. Just hit ctrl-s.



# Tests

ctrl-shift-p "Go: Generate Unit Tests for File". But I don't use the table-driven test which vscode generates. I prefer boring straightforward tests, except I would have many rows in the table of the table-driven test. Related: [table-driven tests are overrated](https://www.reddit.com/r/golang/comments/10e9ebg/tabledriven_tests_are_overrated/)


# Navigation

"Go to file": ctrl+p


ctrl-e --> switch between recently used files. Good if you want to swith to the previous file quickly. Otherwise I prefer ctrl-p


ctrl-g --> goto line


alt-shift-CursorLeft/Right move to previous places

f4 --> goto next search result (for example after a search with ctrl-shift-f): Related https://stackoverflow.com/questions/75161780/go-to-first-match-of-ctrl-shift-f-search



Jump from method to corresponding interface which defines the methos signature: ctrl-shift-p "Find All Implementations", then F4 (jump to first match of the search result). In Goland you have icons near the line-numbers to jump up/down. This could be improved. Related: https://github.com/golang/vscode-go/discussions/1735

go to beginning of a function: click on last element in breadcrumb-bar, then ENTER. Or use `ctrl-shift-. ENTER` to open breadcrumb bar. 


"Go to Symbol in Workspac": ctrl-t. Not very useful, since it shows the symbols of all imported libraries. I usually don't find my code this way. Related: https://stackoverflow.com/questions/75085670/vscode-symbol-search-but-only-in-my-code

After a search the searched term is still highlighted. I use ctrl-b to hide the panel on the left side, which removes the highlighting. Maybe there is an alternative solution?

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

## Custom Keybindings

In general I try to use the keybindings of vscode. Here are some keybindings which I configured.

ctrl-ö --> "Go: Test function at Cursor or Test Previous"

ctrl-r --> "Terminal: Run Recent Command". This is the same keybinding like searching backwards in the shell history :-)
Example: run `make test`.

# Missing

https://stackoverflow.com/questions/75085670/vscode-symbol-search-but-only-in-my-code

https://stackoverflow.com/questions/75071292/vscode-move-go-code-type-function-to-other-file

https://www.reddit.com/r/vscode/comments/10e7aoj/middle_button_paste_on_linux_only_works_after/

history for selection

recently changed locations.

Nice color theme. Overall vscode is a bit too colorful.

# Not solved yet

Copy+Paste does not work in the git-diff view of deleted lines: https://github.com/microsoft/vscode/issues/8226



# Related

* [My vscode questions at Stackoverflow](https://stackoverflow.com/search?tab=newest&q=user%3a633961%20%5bvscode%5d)
* [ten flying fingers](https://github.com/guettli/ten-flying-fingers)
* [Thomas WOL: Working out Loud](https://github.com/guettli/wol)

# Feedback

I love feedback and I love to hear from you. Just create an issue and tell me what's on your mind.

