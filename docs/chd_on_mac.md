# CHD Files on Mac

Guide for working with CHD (Compressed Hunks of Data) files on macOS systems.

## Prerequisites

- The ability to run commands in the `terminal` (it's usually in your Applications folder, in the Utilities subfolder).  You can copy from these text boxes and paste into the terminal.
- [Install Homebrew](https://brew.sh/) - Package manager for macOS
- At the time of writing, this command will install homebrew:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
````

- **Note**: You may also need to install Xcode Command Line Tools with 
```bash
xcode-select --install
``` 
if so prompted.

# Install `chdman`
`chdman` is a command line tool that lets you make `chd` files.  
```bash
brew install rom-tools
```

# Verify that the install worked
```bash
chdman
```
should output a usage guide for the tool

# Compressing bin / cue files
Let's say you have a bin-cue pair for game X.  From your working directory it's in `X/X.cue` and `X/X.bin` 
(note that there may be many track bin files.  Don't worry about that.)
you'll run 
```bash
chdman createcd -i X/X.cue -o X.chd
```
and that'll create X.chd in the directory you're in.

Note that typing long filenames with spaces and parentheses on can be challenging.  Your life may be made easier by adding `bash-completion` to your shell, which allows you to start typing a filename and hit tab to complete it.  To do so run
```bash
brew install bash-completion
```

If you have a bunch of sub-directories in the current directory, and you'd like to compress them all, you can use this bash script (which you're welcome to add to your `.bash_profile`):
```bash
chdall() { for dir in */; do [ -f "${dir%/}/${dir%/}.cue" ] && chdman createcd -i "${dir%/}/${dir%/}.cue" -o "${dir%/}.chd"; done; }
```

You can then run this script in a given directory by simply running `chdall` on the command prompt.


# Compressing iso files
This works exactly the same as with bin-cue files.  Just replace `cue` with `iso` and pretend the `bin` files don't exist (which should be easy because with `iso` files they don't).

```bash
chdman createcd -i X.iso -o X.chd
```

For a batch of `.iso`s in the current directory, you could use this script:
```bash
chdalliso() { for iso in *.iso; do chdman createcd -i "${iso}" -o "${iso%.iso}.chd"; done; }
```
(which you can again add to your `.bash_profile` if you wish to use it regularly, and which can be triggered by running `chdalliso` on the command prompt)
