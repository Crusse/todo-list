# TODO list script

A script that processes your TODO.txt file and parses any time estimates
mentioned in it.

The script takes weekends and holidays into account.

![Demo animation](https://github.com/Crusse/todo-list/blob/master/demo.gif?raw=true)

## Installation

Simply install the Node modules required by `package.json`:

```
npm install
```

## Usage

### Step 1: create a TODO.txt

The `TODO.txt` file can have any text inside it. The only thing that the script
cares about is that you add time estimates to your tasks inside square brackets.
For example:

```
- presentation asap [2 h]
  - preparation
  - generate a PDF and a PPTX and send them to the clients
- do the thing that you promised yesterday!!! [1.5 h]
- foo bar
- big project: stage 1 [50 days]
- big project: stage 2 (needs to done before july) [20 days]
```

### Step 2: run the script

```
chmod +x todo
./todo /path/to/TODO.txt
```

That will print this:

```
######################## TODO list (4 tasks: 423.5 hours, 71 days) ########################

- presentation ASAP [0.3 days]
- do the thing that you promised yesterday!!! [0.3 days]
- big project: stage 1 [50 days]

### 2021-04-02: [Holiday: Pitkäperjantai]

### 2021-04-04: [Holiday: Pääsiäispäivä]

### 2021-04-05: [Holiday: 2. pääsiäispäivä]

### 2021-04-07
- big project: stage 1 [finish]
- big project: stage 2 (needs to DONE BEFORE july) [20 days]

### 2021-05-01: [Holiday: Vappu]

### 2021-05-05
- big project: stage 2 (needs to DONE BEFORE july) [finish]

```

Run `./todo --color /path/to/TODO.txt` for color output.

Common important words (such as "asap", "soon", etc.) will be highlighted and
uppercase'd.

### .bash_aliases

It is recommended that you add lines like this in your .bash_aliases file:

```
alias todo='node /home/you/git/todo-list/todo --color /home/you/TODO.txt | less -r'
alias todoraw='node /home/you/git/todo-list/todo /home/you/TODO.txt'
alias todohtml='todoraw --color | aha > /tmp/todo-work.html && google-chrome /tmp/todo-work.html'
```

Now you can run `todoless` in the terminal and print a colored, scrollable TODO
list easily whenever you need it.

If you need the raw output (e.g. for copy-pasting), you can run `todo`. If you
have `aha` installed (install it on Linux with `sudo apt install aha`), you can
generate a colored HTML output of your TODO list.

