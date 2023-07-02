# Installing Fish shell on macOS using homebrew

## Install Fish

`brew install fish`

## Find out the path of fish

`which fish`

## Make fish the default shell on macOS

1. Enter `sudo nano /etc/shells` in Terminal and add the output of `which fish` at the end

```
# List of acceptable shells for chpass(1).
# Ftpd will not allow users to connect who are not using
# one of these shells.

/bin/bash
/bin/csh
/bin/dash
/bin/ksh
/bin/sh
/bin/tcsh
/bin/zsh
/opt/homebrew/bin/fish
```

2. Then go to:

- System Settings
- Users & Groups
- right click on your username > Advanced Options...
- search the Login Shell menu and click on the fish shell in the dropdown menu

## Add the brew path to the fish shell

`fish_add_path /opt/homebrew/bin`

## Auto Completions

`fish_update_completions`

## Config fish

`fish_config`

## Add cdf functionality

1. to cd to the current Finder directory (very usefull)

2. go to `cd .config/fish/functions/`

3. `touch cdf.fish`

4. `nano cdf.fish` and enter:

```
function pfd -d "Return the path of the frontmost Finder window"
  osascript 2>/dev/null -e '
    tell application "Finder"
      return POSIX path of (target of window 1 as alias)
    end tell'
end

function cdf -d "cd to the current Finder directory"
  cd (pfd)
end
```

