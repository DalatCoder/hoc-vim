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

### 2.7. Transforming and Substituting text

#### 2.7.1. Insert mode

Way to enter inserting mode:

- `i`
- `I` or (`^i`): go to the beginning of the line and enter insert mode
- `a` append text
- `A` or (`$a`)
- `o` add line below and enter insert mode
- `O` add line above and enter insert mode

Create a line contains 80 `*` character

`[counter]operation{i,o}[typeST]<Esc>`

- `80i*<Esc>`

Create comment section lines
- `5o#<Esc>`

Create a list of IP address
- `4o10.11.12.<Esc>`

#### 2.7.2. Replace mode

It's just really another form of insert mode

Press `R`, now whatever you type will overwrite the existing text
Press `r{character}` to replace 1 character

#### 2.7.3. Changing mode

Using `[count]c{motion}`, behave like the `d` command.

- `cc` to change the entire line
- `~` to change text style
- `g~w` to change text style of the `word`
- `g~~` to change text style of the entire line
- `gU{motion}` to force change to `UPPERCASE`
- `gUU` to force the entire line to `UPPERCASE`
- `gu{motion}` to force change to `lowecase`
- `guu` to force the entire line to `lowercase`

#### 2.7.4. Joinging line

- `J` join line and add some space
- `gJ` join line but don't add space

#### 2.7.5. Search

Linewise searching

- `f{character}`: search forward
- `F{character}`: search backward
- Press `;` to repeat the search (forward)
- Press `,` to repeat the search (backward)
- `t{character}`: place the cursor before the seach result
- `T{character}`: place the cursor after the seach result

`f` & `t` are motions

Search the entire file

- `/{keyword}`
- Press `n` to move to the next result
- Press `N` to move to the previous result

Search options

- `is (incsearch`: search realtime
- `hls (highlightsearch)`: highlight search results
- `:nohls` to remove highlighting (not disable)

Common pattern

- performing a search `/and`
- using `cw` to change word
- press `Esc`
- press `n` to move to the next match
- press `.` to repeat the previous command (`cw`)

Search backward using `?` instead of `/`

Place the cursor under a word and press `*` (or `#`) to go to the next instance of this word. (press `n` or `N` to move)

`/` also the `motion`, so we can combine this with an `operator` like `d`

#### 2.7.6. Substitude (find and replace)

- `:s/old/new/` perform search and replace in the current line (the first occurence)

- `:s/old/new/[flags]`, using `g` for change all occurences on the current line

- `[range]s/old/new/[flags]`, for finding and replacing on multiple line

- `:1s`, change in the line with number of `1`
- `:1,5s`, change in the first line to line 5
- `$`: last line
- `.`: current line
- `:.,$`: current line to the lastline
- `%` or (1,$): all lines (entire file)

Specify `range` by the `pattern`: `/pattern-1/,/pattern-2/`

Define a custom `pattern` sign: `:s#pattern-1#,#pattern-2#/old/new/g`

## 3. Text objects and Macros

### 3.1. Text objects 

Text construct, such as:
- words
- sentences
- paragraphs
- tags
- delimited 

Those are `vim text object`.

Text object are used after an `operator` (similar to motions)

When you combine a command with a text object, a command operates
on the entire object regradless of the cursor position.

- `daw`: delete a word (include whitespace)
- `diw`: delete inner word

Pattern

- `{operator}{a}{object}`
- `{operator}{i}{object}`

Examples

- `daw`: Delete a word
- `ciw`: change inner word

The text object for an `entire` sentence is `as` and for an inner sentence `is`

- `das`: Delete an `entire` sentences

A sentence boundary is a `period`.

A paragrap boundary is a `blank line`.

- `ap`: entire paragraph
- `ip`: inner paragraph

Examples

- `dap`: delete an entire paragraph

Patterns:

- `ci[` (or `ci]`): for changing text between `[]`
- `ci(` (or `ci)`): for changing text between `()`
- `ci<` (or `ci>`): for changing text between `<>`
- `ci{` (or `ci}`): for changing text between `{}`
- `ci"`: for changing text between `""`
- `ci'`: for changing text between `''`
- `ci``: for changing text between `\`\``

Tag object 

- `at`: a tag
- `it`: inner tag

Block object

- `aB`
- `iB`

Text object is used in 2 forms
- `a` form (a, all)
- `i` form (inner)

### 3.2. Macros

Repeat a series of commands.

`macros` also called `complex repeat`

One of the most common uses of `vim macros` is to change the format
of data or text.

Macros are nothing more than a recorded sequence of `keystrokes`.
These keystrokes are actually saved in registers. When you playback
a macro, all the keystrokes recorded in the register are played back
and it's exactly the same as if you were to type those keystrokes
again.

- To create a `macros`: `q{register}`
- When you are done: type `q`
- To play a macros: `@{register}`

Macro Best Practices

- Normalize the cursor position: (`0`)
- Perform edits and operations.
- Position your cursor to enable easy replays: (`j`)

Repeat a macros with `[count]@{register}`

Macros are stored in registers and register can be append.

- `qa` and `qA` (to append)

Look at the content of the macro with: `:reg {register-name}`

Reminder to substitute command:

- `:s/"/'/g`: replace all `"` to `'`
- `:s/(//g`: remove all `(` character
- `:s/)//g`: remove all `)` character
- `:s/ => /,/g`: change all ` => ` to `,`

Ways to repeat a macro

- using `count`
- using `normal` command: `27,35normal @a`: @a is executed from line 27 to 35.

To modify a macro, just `put` it from register, modify and `yank` into
the register.

- `"ap`
- modify
- `"ay$"

Saving macros using `.viminfo` file

- `.viminfo` file
- stores history and non-empty registers
- read when vim starts
- can easily overwrite registers

Saving macros using `.vimrc` file

- `let @a = '0iNOTE:€ü €ýaj€ýa'`
- `let @t = 'ITODO: ^[j`

Review

- Macros are a recorded series of keystrokes
- Macros use registers
- Start recording: `q{REGISTER}`
- Append to a macro: `q{CAPITAL_REGISTER}`
- Playback: `@{REGISTER}`
- Repeat last played macro: `@@`
- Range: `:[range]normal @{REGISTER}`

## 4. Visual mode

Versions

- Use `v` to start characterwise visual mode
- Use `V` to start linewise visual mode
- Use `Ctrl-v` to start blockwise visual mode (vertical visual mode)

- Use motions to expand the visual area
- Use text objects to expand the visual area

Some of commands you can use in visual mode include:
- `~`: switch case
- `c`: change
- `d`: delete
- `y`: yank
- `r`: replace
- `x`: delete
- `I`: insert
- `A`: append
- `J`: join
- `u`: make lowercase
- `U`: make uppercase
- `>`: shift right
- `<`: shilf left

Using `o` to reverse (or `O`)

Append to all lines: `Ctrl-v`, select lines and press `A` or (`I`)

