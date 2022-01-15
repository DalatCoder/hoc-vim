# Vim Master Class

Vim is an advanced text editor. Vim is powerful text editor!

Why 

- Vim is ubiquitous
- Vim is amazingly powerful
- Vim's knowledge is transferable
- Vim is cross-platform
- Vim is avaiable in a TUI and a GUI
- Vim has syntax highlighting
- Commands are easy to remember
- Vim is like a language
- Vim is thoroughly documented
- Vim is fun!

## 1. Quick Start

Vim modes:

- Normal mode (command mode)
- Insert mode
- Command-line mode (cmdline mode)

## 2. Vim Essentials 

### 2.1. Essential Navigation Commands 

- hjkl

- Ctrl-f: move forward (page down)
- Ctrl-b: move backward (page up)
- move forward by word, use "w". (using white space as word boundaries, use "W")
- move backward by word, use "b". (using white space as word boudaries, use "B")
- move sreen up: press "z" and "enter"
- go to the begining of the file: "gg"
- go to the beginning of the line: 0 or ^ (regex)
- go to the ending of the line: $ (regex)
- go to line command: 2gg or 2G (top of the file: gg, bottom of the file: G) (:1)
- go to line command in command mode: :1, :$
- display status: Ctrl G
- display more information on status: g Ctrl G
- `set ...`
- `set no...`
- to toggle an option, place a `!` at the end of the option `set ruler!`

### 2.2. Deleting Text and Thinking in Vim

- delete a character under the cursor: x
- delete a character at left of the cursor: X
- delete a word: dw

Pattern: `operatior{motion}`

`dw`

- `d`: The delete operation
- `w`: The word motion

Delete a line: `dd`
Delete to the end of the line: `d$` or `D`

`X` is the shortcut of `dl`
`D` is the shortcut of `d$`

Example some delete combination: `dj dk dw de d$ d^ d0`

There are some ways to accomplish the same task

Another pattern: `[count]operaton{motion}`

5dw

- `5`: the count / how many times to repeat
- `d`: the delete operation
- `w`: the word motion

The motion is also have the pattern: `[count]{motion}`

`3w`

- `3`: the count
- `w`: the word motion

We can even combine these motion to achieve this: `[count]operation[count]{motion}`

- `3w`: repeat word motion 3 times
- `d3w`: delete the 3w motion
- `2d3w`: delete the 3w motion 2 times

Dot command: repeat the previous command

