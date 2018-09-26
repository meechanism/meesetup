# Mee's Setup :chicken: :sparkles:

Hay there.

I have noticed time and time again that I run a routine set of tasks when I
setup a new dev environment. This doesn't happen too often, but it does happen a
lot more than I want. Most of the time it is because I change jobs and get new
hard ware.

One time it was because my office was broken into by some thieves and my laptop
was stolen. That really sucked.

So to rid myself of these inconveniences and wasting time figuring out what are
all the steps I normally take, I thought it'd be smart for me to jot it down.

## Caveats

I'm usually developing on an Apple MacBook pro, so OSX is the operating system.

# OSX: System Settings

1. Turn on scroll bars
    - Go to: `System Settings > General > Show Scroll Bars` and select `Always`
    - ***Why do I do this?*** I'm a front end developer, meaning I see and
        evaluate user interfaces on the daily. Having that extra width
        take up normal view port space is very important to my dev and
        debugging routine.
2. Update touchpad settings (because I'm not a savage):
    - Go to: `System Settings > Trackpad > Scroll & Zoom (tab)` and uncheck
        the option for `Scroll Direction: Natural`
    - This is actually very unnatural for _me_ because I don't see myself
        dragging things around like I do on a phone.
3. Update Key repeat delay to very short (because I like to hold down my keys)
    - Go to: `System Settings > Keyboard > Delay Until Repeat` set to `short`
4. Dock:
    - Remove all the crap from the dock except: Finder, Calendar, Browser (later
        we can add VS Code and iTerm)
    - Go to: `System Settings > Dock` and change size to smallish.
    - Right click the `Download` folder in dock and chage `View Content as` to
        `List`
5. Show all filenames and extensions:
    - Go to Finder > Preferences
    - Click on Advanced tab
    - Check `Show all filename extensions`
    - Check `Keep folders on top when sorting by name`

# Software clients to download and install

Note: All of these are free.

1. Browsers: Because I need to test in these
    - Chrome
    - Firefox
    - Opera
    - Some extensions: [AdBlock Plus](https://adblockplus.org/),
        [Ebates](https://www.ebates.com/r/XOULON?eeid=28187),
        Wikibuy (Shameless plug, buy2save :kiss:)
2. [iTerm](https://www.iterm2.com/) - A better terminal
3. [Visual Studio Code](https://code.visualstudio.com/) - Code editor
4. [ImageOptim](https://imageoptim.com/mac) - Image optimizer

# Command line stuff

After installing iTerm, the following needs to be done:

1. Update default location of screen captures.
    - Open terminal: `defaults write com.apple.screencapture location ~/Documents/Screenshots`
2. Install [Homebrew](https://brew.sh/)
3. Using Homebrew, install the below:
    - `brew install node`
    - `brew install git`
4. Use the Homebrew version of git (as opposed to Apple's preinstalled flavor)
    - Add `export PATH="/usr/local/bin:${PATH}"` to `~/.bash_profile`
    - Refresh session: `source ~/.bash_profile`
    - The brew install comes with some nice tools installed that I like using,
        such as `gitk` and `git gui`
5. Setup git (creating ssh key, adding it to github, etc)
6. Add git aliases
    ```sh
    alias.aa=add --all
    alias.bv=branch -vv
    alias.ba=branch -ra
    alias.bd=branch -d
    alias.ca=commit --amend
    alias.cb=checkout -b
    alias.cm=commit -a --amend -C HEAD
    alias.ci=commit -a -v
    alias.co=checkout
    alias.di=diff
    alias.ll=log --pretty=format:%C(yellow)%h%Cred%d\ %Creset%s%Cblue\ [%cn] --decorate --numstat
    alias.ld=log --pretty=format:%C(yellow)%h\ %C(green)%ad%Cred%d\ %Creset%s%Cblue\ [%cn] --decorate --date=short --graph
    alias.ls=log --pretty=format:%C(green)%h\ %C(yellow)[%ad]%Cred%d\ %Creset%s%Cblue\ [%cn] --decorate --date=relative
    alias.mm=merge --no-ff
    alias.st=status --short --branch
    alias.tg=tag -a
    alias.pu=push --tags
    alias.un=reset --hard HEAD
    alias.uh=reset --hard HEAD^
    alias.cleanup=!git branch --merged | grep  -v '\*\|master\|develop' | xargs -n 1 git branch -d
    ```

# Visual Studio Code setup

1. If theme is not already dark, make it dark. Dark is the way.
    :new_moon_with_face:
2. Update user settings with:
    ```sh
    {
        "editor.renderWhitespace": "all",
        "files.trimTrailingWhitespace": true,
        "editor.rulers": [80,120],
        "files.exclude": {
            "**/.git": true,
            "**/.DS_Store": true,
            "**/node_modules": true,
            "**/log": true,
            "**/build": true,
            "**/tmp": true
        }
    }
    ```
2. Install extensions:
    - Sass (syntax highlighting for sass/scss)
    - Document This (for generated JSDoc)
3. Setup usage from command line: 
    - Open the Command Palette (⇧⌘P) and type `shell command` to find the Shell Command: Install 'code' command in PATH command.
    - Restart the terminal for the new `$PATH` value to take effect. You'll be able to type 'code .' in any folder to start editing files in that folder


# Mee miss anything?

Did I miss something vital or something that would make my life (or someone's
elses) totally amazing? Shoot me a message, or even better, open a pull request!

I hope this was helpful for you (and for future Mee)!
