# TODO list script

A script that processes your TODO.txt file and parses any time estimates
mentioned in it.

Takes into account weekends and holidays.

## Installation

Simply install the Node modules required by `package.json`:

```
npm install
```

## Usage

### Step 1: create a TODO.txt

The `TODO.txt` file can have any text inside it. The only thing that the script
cares about is that you add time estimates to your tasks with square brackets.
For example:

```
- presentation [2 h]
  - preparation
  - generate a PDF and a PPTX and send them to the clients
- do the thing that you promised yesterday!!! [1.5 h]
- foo bar
- big project: stage 1 asap [10 days]
- big project: stage 2 [22 days]
```

### Step 2: run the script

```
chmod +x todo
./todo /path/to/TODO.txt
```

That will print this:

```
######################## TODO list (4 tasks: 195.5 hours, 33 days) ########################

- presentation [0.3 days]
- do the thing that you promised yesterday!!! [0.3 days]
- big project: stage 1 ASAP [10 days]

### 2021-02-08
- big project: stage 1 ASAP [finish]
- big project: stage 2 [22 days]

### 2021-03-10
- big project: stage 2 [finish]
```

Run `./todo --color /path/to/TODO.txt` for color output.

### .bash_aliases

It is recommended that you add lines like this in your .bash_aliases file:

```
alias todo='node /home/you/todolist/todo --color /home/you/TODO.txt | less -r'
alias todoraw='node /home/you/todolist/todo /home/you/TODO.txt'
alias todohtml='todoraw --color | aha > /tmp/todo-work.html && google-chrome /tmp/todo-work.html'
```

After this you can run `todoless` in the terminal and print a colored,
scrollable TODO list easily whenever you need it. If you need the raw output
(e.g. for copy-pasting), you can run `todo`. If you have `aha` installed
(install it on Linux with `sudo apt install aha`, you can generate a colored
HTML output of your TODO list.

