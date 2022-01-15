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

