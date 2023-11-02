# swinn
Implementation of [Blezzing - blezz](https://github.com/Blezzing/blezz) in pure Bash (4+ should be fine).
![image](https://github.com/magpie514/swinn/assets/323651/cabf49b5-a1d5-4a4d-b4a5-5e7f31a8493d)

Given a blezz-formatted file, it'll allow you to launch programs or start tasks by pressing a button or sequence of buttons. Should be compatible with Blezz files, and [rofi-blezz](https://github.com/davatorium/rofi-blezz) as well.

## Reasoning
I started using Blezz files to define launchers and I find it very convenient, specially as a Rofi plugin. I wanted something compatible with the same files for the console, and I thought that if I'm in a situation where I can't use Rofi, I'd probably be in some limited environment through SSH. So I made it as minimal as possible using only a modern-ish version of Bash (considered AWK, but bash is common enough!)

## Syntax
`directoryName:`
Defines the contents of a directory. It's similar to a "goto" label. Anything before a label will be top level.
`dir(key, dirName)`
When pressing `key` it'll open the defined directory.
`act(key, label, action)`
When pressing `key` it'll start the defined action. Use sh-compatible syntax.
`# Comment`
Lines starting with a # will be commented out.
### Keys
Any key you can type on your keyboard should work for the value of `key`, I've tested it with non-US characters, capitals and such without issue.
```
# This is a sample blezz file, and a comment.
dir(1, test)
act(2, Firefox, firefox)

test:
act(1, libreoffice)
```
Will let you press "2" to launch firefox, and "1, 1" to open libreoffice.


## Keys
`.` to go back to a previous folder, or close the application if at top level. You may also quit with Ctrl+C. Any assigned key will perform its given action, and non-assigned keys should show an alert.
