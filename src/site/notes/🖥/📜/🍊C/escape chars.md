---
{"dg-publish":true,"permalink":"/🖥/📜/🍊C/escape chars/","tags":["cheat","unix"]}
---

in order to create a file called `"\?$*'KwaMe'*$?\"`

run 
```bash
touch \"\\\?\$\*\'KwaMe\'\*\$\?\\\"
```
1. **Double your `\`**, like this: `\\`, so that your shell does not interpret the backslashes from your filename as escape characters.
2. **Escape `"` and `'`**, like this: `\"`, `\'`, so that your shell interprets the double quotes as part of the filename.
3. **Escape `$`**, like this: `\$`, otherwise your shell will think you're using [**a variable**](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-5.html).
4. **Escape `?` and `*`**, like this: `\?`, `\*`, to prevent [**filename expansion**](https://www.gnu.org/software/bash/manual/html_node/Filename-Expansion.html).