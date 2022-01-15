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

### 2.3. The Vim help system

- `:help <COMMAND>`: `:help dd`
- `:help {subject}`: `:help count`
- `:help :help`

- `Ctrl o`: navigate to previous docs
- `Ctrl i`: navigate to current docs
- `Ctrl ]`: jump to definition of the word under the cursor

### 2.4. Deleting, Yanking and Putting

#### 2.4.1 Cut, Copy and Paste

Why?

- Move text around a file
- Duplicate text
- Make an in-file backup
- Reuse the same text

You've already been cutting

- `d` and `x` cut text, not just delete it
- `cut` = `delete` and `save` into a `register`
- `register` is a clipboard-like storage location

`dd` cut a line into an `unnamed register` (`default register`)

- `p`: put command (paste command)

- swapline `ddp` or `ddP`

Even after you paste the text, it stays in the `unnamed register` until it's overwritten by another operation.

Standard vs Vim

- cut = delete
- copy = yank
- paste = put

Yank is a `operator`, so we can use the pattern: `[count]operator[count]{motion}`

### 2.5. Undo & Redo

- `u`: undo 
- `Ctrl r`: redo 

### 2.6. Register Types

- Unnamed
- Numbered
- Named

Registers

- Unnamed register = `""`
- Numbered reigsters = `"0`, `"1`, ..., `"9`

- `""` holds text from `d, c, s, x` and `y` operations.
- `"0` holds last text yanked `y`
- `"1` holds last text deleted `d` or changed `c`
- numbered registers shift with each `d` or `c`

To look at the register, we can use: `:reg`

Put text at a specific register: `"7p`

Using `blackhole` register: `"_`

- `^J` is a newline character

Named register: `"a`, ... `"b`

`"A` append text to the existing `"a`

Repeating with Registers

- `[count][register]operator`
- `[register][count]opeartor`
