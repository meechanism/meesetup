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

1. Scroll Bars and Dark Theme
    - Go to: `System Settings > General > Appearance` and select `Dark`
   - Go to: `System Settings > General > Show Scroll Bars` and select `Always`
   - **_Why do I do this?_** I'm a front end developer, meaning I see and
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
    - Go to `Finder > Preferences`
   - Click on Advanced tab
   - Check `Show all filename extensions`
   - Check `Keep folders on top when sorting by name`

# Software clients to download and install

Note: All of these are free.

1. Browsers: Because I need to test in these
   - Brave (primary browser)
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
2. Install [Homebrew](https://brew.sh/), then:
   - `brew install git`
3. Install NVM (DO _NOT_ USE HOMEBREW) and node:
   - `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash`
   - `nvm install node`
4. Use the Homebrew version of git (as opposed to Apple's preinstalled flavor)
   - New apple chips do not need the path to be exported in your shell profile.
   - Install Git Gui/gitk: `brew install git-gui`
5. Setup git (creating ssh key, adding it to github, etc)
6. If your GIT has 2FA enabled, you will need to generate a [personal access token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line).
7. If using `GPG`, install the cli and [GPG suite](https://gpgtools.org/) to share it in keychain. This will sign your commits.
    ```sh
    $ brew install gpg
    ```
    Read more on [signing commits](https://help.github.com/en/github/authenticating-to-github/signing-commits)
7. Download mergetool `kdiff3` and set it as default:
    ```sh
    $ brew cask install https://raw.githubusercontent.com/Homebrew/homebrew-cask/6a96e5ea44803e52a43c0c89242390f75d1581ab/Casks/kdiff3.rb

    $ git config --global --add merge.tool kdiff3
    $ git config --global --add mergetool.kdiff3.path  "/Applications/kdiff3.app/Contents/MacOS/kdiff3"
    $ git config --global --add mergetool.kdiff3.trustExitCode false

    $ git config --global --add diff.guitool kdiff3
    $ git config --global --add difftool.kdiff3.path "/Applications/kdiff3.app/Contents/MacOS/kdiff3"
    $ git config --global --add difftool.kdiff3.trustExitCode false
    ```
8. Edit global `.gitconfig`
   ```sh
   [user]
      signingkey = rsa4096/CAB3D4DA702FFD01
      name = Mee Cha
      email = mee.cha.nism@gmail.com
   [merge]
      tool = kdiff3
   [mergetool "kdiff3"]
      path = /Applications/kdiff3.app/Contents/MacOS/kdiff3
      trustExitCode = false
   [diff]
      guitool = kdiff3
   [difftool "kdiff3"]
      path = /Applications/kdiff3.app/Contents/MacOS/kdiff3
      trustExitCode = false
   [alias]
      co = checkout
      ci = commit
      st = status -s
      br = branch
      hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
      type = cat-file -t
      cleanup = git clone https://github.com/EarnUp/olympic-lib.git branch --merged | grep  -v '\\*\\|master\\|develop' | xargs -n 1 git branch -d
      # cleanup=!git branch --merged | grep  -v '\*\|master\|develop' | xargs -n 1 git branch -d
   ```
8. Spice up zsh, add colors, context, and more: https://github.com/ohmyzsh/ohmyzsh

# Visual Studio Code setup

1. Install command line tools. Open VS Code and then press `Cmd + Shift + P` and type in `Install Command line tools`.
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
3. Install extensions:
   - Sass (syntax highlighting for sass/scss)
   - Document This (for generated JSDoc)
4. Setup usage from command line:
   - Open the Command Palette (⇧⌘P) and type `shell command` to find the Shell Command: Install 'code' command in PATH command.
   - Restart the terminal for the new `$PATH` value to take effect. You'll be able to type 'code .' in any folder to start editing files in that folder

# Mee miss anything?

Did I miss something vital or something that would make my life (or someone's
elses) totally amazing? Shoot me a message, or even better, open a pull request!

I hope this was helpful for you (and for future Mee)!
