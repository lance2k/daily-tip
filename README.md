# daily-tip

One vim/bash/zsh tip per day, in your first terminal of the morning.

```
💡 Daily tip 14/60 [vim]
   ciw = change inner word, with the cursor anywhere inside the word. The gateway to text objects.
```

Learning shell and vim commands from cheat sheets doesn't stick — you binge twenty
tips and remember none. `daily-tip` drips exactly one tip into the first terminal
you open each day. Use it three times that day and it's yours. That's the whole
method.

The 60 built-in tips are ordered as a curriculum: survival basics first (getting
out of vim, `Ctrl+R`), daily-driver moves next (`ciw`, the `.` command, pipes,
text objects), power tools last (macros, `:g/pattern/d`, `trap`, process
substitution). After tip 60 it wraps around — a second pass months later is free
spaced repetition.

## Install

```sh
git clone https://github.com/lance2k/daily-tip.git
ln -s "$PWD/daily-tip/daily-tip" ~/.local/bin/daily-tip
```

Then add this to the end of your `~/.zshrc` (or `~/.bashrc`):

```sh
(( $+commands[daily-tip] )) && daily-tip          # zsh
# command -v daily-tip >/dev/null && daily-tip    # bash
```

Requires bash 4+ (uses `mapfile`). The script itself runs in bash even when
called from zsh.

## Usage

| Command | What it does |
|---|---|
| `daily-tip` | Show the next tip — but only once per calendar day |
| `daily-tip again` | Reprint today's tip |
| `daily-tip next` | Impatient? Advance to one more tip right now |
| `daily-tip list` | Review all tips; `>` marks where you are |

Progress is stored in `~/.local/state/daily-tip/state` as a plain
`YYYY-MM-DD index` pair. Delete the file to start over.

## Adding your own tips

Tips live in a heredoc inside the script, one per line:

```
category|Tip text goes here.
```

The category (`vim`, `bash`, `zsh`, or anything else) is just a label shown in
brackets. Edit the list, keep each tip to one or two sentences, and the rotation
adjusts automatically.

## License

[MIT](LICENSE)
