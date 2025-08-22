# bash-helpers
Misc aliases and scripts related to Bash vars and built-ins; part of [runsascoded/.rc](https://github.com/runsascoded/.rc)

## `bash-markdown-fence.py` (a.k.a. `bm`)
```bash
bash-markdown-fence.py
# Usage: bash-markdown-fence.py [OPTIONS] [COMMAND]...
#
#   Format a command and its output to markdown, either in a `bash`-fence or
#   <details> block, and copy it to the clipboard:
#
# Options:
#   -C, --no-copy  Disable copying output to clipboard (normally uses first
#                  available executable from ['pbcopy', 'xclip', 'clip']
#   -f, --fence    Pass 0-3x to configure output style: 0x: print output lines,
#                  prepended by "# ", in a `bash`-fence block; 1x: print a
#                  "```bash" fence block including the <command> and commented
#                  output lines; 2x: print a bash-fenced command followed by
#                  plain-fenced output lines; 3x: print a <details/> block, with
#                  command <summary/> and collapsed output lines in a plain
#                  fence.
#   --help         Show this message and exit.
```

Examples, using the command `seq 5`:

### `bm seq 5`
This prints the output from `seq 5`, prefixed with `#&nbsp;` to simulate Bash comments (for inclusion in a `bash`-"fence" block):
```bash
# 1
# 2
# 3
# 4
# 5
```

### `bmf seq 5`
Passing the `-f`/`--fence` flag once includes the command in the `bash`-fence:
```bash
seq 5
# 1
# 2
# 3
# 4
# 5
```

### `bmff seq 5`
Passing `-f`/`--fence` twice separates the `bash` command and its output into a `bash`-fence followed by a plain fence:
```bash
seq 5
```
```
1
2
3
4
5
```

### `bmfff seq 5`
Passing `-f`/`--fence` three times outputs a `<details>` block:
<details><summary><code>seq 5</code></summary>

```
1
2
3
4
5
```
</details>
