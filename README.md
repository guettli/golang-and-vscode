# Golang and VSCode

## My background

I was born 1976 and I write software since I am 12 years old.

Seven years ago I switched from Emacs to PyCharm.

In 2022 I learned Go, which is now part of my daily work as Cloud Engineer at [Syself](https://syself.com/).

Here are my notes which I wrote down while switching from an IntellJ based IDE to vscode.

## Shortcuts

F2: refactor (rename Method)

ctrl-` --> show/hide terminal.

ctrl-space --> autocomplete (for example find the struct in a package and add the package name before the name) [docs](https://code.visualstudio.com/docs/editor/intellisense#_intellisense-features)

[Bookmark plugin](https://github.com/alefragnani/vscode-bookmarks): ctrl-alt-k (set bookmarks), ctrl-alt-j (jump to bookmarks, multiple times to jump to other bookmarks). You plan a short pair-programming session because you want to discuss some parts of the code? Be prepaired! Make bookmarks of the relevant parts of the code. 

You want to open a file from the terminal: `> code foo.go`

"Show all commands": ctrl+shift+p

ctrl-. --> "Quick fix" (for example fill struct)

ctrl-shift-p "open recent" --> Open recent Workspace. This is better than "File > Open Recent" because it provides autocomplete. By default this is mappend to ctrl-r, but I use ctrl-r for "Terminal: Run Recent Command".

Jump from a method on an interface to the implementation: ctrl-F12 (or context-menu "Go to Implementations")

# Search and Replace in one file

ctrl-h and then enter the old and the new term.

Then it is important which text input field has the focus.

If the old-string has the input, ENTER will skip to the next match.

If the new-string has the input, then ENTER will change the current part in the file.

If you want to undo your change, you need to press ESC first.

Not perfect. If someone has a better solution, please let me know.



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




go to beginning of a function: click on last element in breadcrumb-bar, then ENTER. Or use `ctrl-shift-. ENTER` to open breadcrumb bar. 


"Go to Symbol in Workspace": ctrl-t. Not very useful, since it shows the symbols of all imported libraries. I usually don't find my code this way. A work-around is to use ctrl-shift-f `⎵Foo(`, if you want to search for all methods called "Foo". Related: https://stackoverflow.com/questions/75085670/vscode-symbol-search-but-only-in-my-code and https://github.com/golang/go/issues/37236 and https://www.reddit.com/r/golang/comments/119r6ec/vscode_how_to_search_for_all_methods_called_foo/

After a search the searched term is still highlighted. I use ctrl-b to hide the panel on the left side, which removes the highlighting. Maybe there is an alternative solution?

# Plugins

[Go](https://marketplace.visualstudio.com/items?itemName=golang.go) Official Plugin, provided by the Go team at Google.

[GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) I don't use it for clone/switch/commit/push, but I use it for comparing the corrent code with the previous state. See [Revision Navigation](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens#revision-navigation). [Be sure to disable the distracting popUps](https://stackoverflow.com/a/58039473/633961). It is a bit like "Git History for Selection" in Intellij.

[YAML](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) YAML Language Support by Red Hat, with built-in Kubernetes syntax support (uses [prettier](https://prettier.io/) under the hood).

[Highlight Files](https://marketplace.visualstudio.com/items?itemName=ArturoDent.highlight-files) I want to see immediately if a file is outside my workspace. This plugin changes the color of the tab of a file. You add a badge to the tab, too. I use the camping unicode symbol: 🏕. Related [StackOverflow question](https://stackoverflow.com/questions/75244211/vscode-search-in-a-directory-which-is-outside-the-workspace).

[Peacock](https://marketplace.visualstudio.com/items?itemName=johnpapa.vscode-peacock) Subtly change the workspace color of your workspace. Ideal when you have multiple VS Code instances and you want to quickly identify which is which.

# settings.json

# Colors

I like to highlight the current line a bit more:

```
    "workbench.colorCustomizations": {
        "editor.lineHighlightBackground": "#213211",
    },
```

But highlighting is gone, if there is a selection: https://stackoverflow.com/questions/75582447/vscode-highlight-line-even-if-there-is-a-selection

# Gopls
Gopls is the Go language server which gets used by vscode, vim and most other editors.

```
    "gopls": {
        "importShortcut": "Definition"
    }
```
--> if you click on an import line (for example `myname "github.com/foo/bar")`) you get to the code of "foo/bar" in vscode. Don't open the browser.  Related: [Don't Open Imports in the Browser](https://dominikbraun.io/blog/vs-code-go-dont-open-imports-in-browser/)

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

## GitLens

Disable `gitlens.currentLine.enabled`. Especially the popup on hover makes too much noise.

Above setting did not remove all pop-ups. I disabled the GitLens plugin.


# Support for Yaml: autocomplete

I am editing a file called golangci.yaml.

The editor vscode provides autocomplete. It somehow seems to understand the format.

That's magic und very helpful.

# Missing

https://stackoverflow.com/questions/75085670/vscode-symbol-search-but-only-in-my-code

https://stackoverflow.com/questions/75071292/vscode-move-go-code-type-function-to-other-file

https://www.reddit.com/r/vscode/comments/10e7aoj/middle_button_paste_on_linux_only_works_after/


recently changed locations: https://stackoverflow.com/questions/72648730/recent-locations-in-vscode-like-in-intellij

Nice color theme. Overall vscode is a bit too colorful.

Developing Go code means working with generated files in most cases. It would be great if vscode could display files which were generated with a different background color. Rule of thubmb: If the file contains `DO NOT EDIT`, then the background color should be different. TODO: try to find a solution.

From method signature of an interface: Show all methods which implement this signature. At the moment clicking on the signature shows all places where this method gets used. But I am often looking for the list of implementations.

Floating windows (like detach terminal into a second window) is not possible. See [#10121](https://github.com/microsoft/vscode/issues/10121)
Now my favorite setup (one display for the code, one display for the output of the tests) is not possible: https://stackoverflow.com/questions/75592496/show-output-of-test-on-second-monitor

# Not solved yet

Copy+Paste does not work in the git-diff view of deleted lines: https://github.com/microsoft/vscode/issues/8226

I would like to have a better visual differentiation between my code and code from third party packages. https://stackoverflow.com/questions/75181580/higlight-files-which-are-not-from-my-repository

Navigation in packages outside the current workspace does not work. I can open the Go file, but symbols which are outside the current file are not known. This means vscode underlines them with red color and ctrl-click does not work :-(

# TODO

* ctrl-t to open new browser tab. I don't like to keep a state in my head. I am very used to open a new browser tab with ctrl-t. It should work in vscode, too.

* alt-shift-left/right for going to the previous locations is too far away. I need to move my pointer fingers away from F and J. Something I try to avoid.

My cursor is on the name of a method which implements an interface. I want to see the docstring of this method of the interface. How to get to navigate to the method signature of the interface?

Jump from method to corresponding interface which defines the methos signature: ctrl-shift-p "Find All Implementations", then F4 (jump to first match of the search result). In Goland you have icons near the line-numbers to jump up/down. This could be improved. Related: https://github.com/golang/vscode-go/issues/2628

# Related

* [Featurse of Go Plugin for vscode](https://github.com/golang/vscode-go/blob/master/docs/features.md) including short screencasts.
* [My vscode questions at Stackoverflow](https://stackoverflow.com/search?tab=newest&q=user%3a633961%20%5bvscode%5d)
* [ten flying fingers](https://github.com/guettli/ten-flying-fingers)
* [Thomas WOL: Working out Loud](https://github.com/guettli/wol)

# Feedback

I love feedback and I love to hear from you. Just create an issue and tell me what's on your mind.

