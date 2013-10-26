# ampline
amp up your command line.

assign variables to output from common commands

a great complement to tab completion

### show not tell

![screenshot][screenshot]
[screenshot]:https://rawgithub.com/dtrejo/ampline/master/screenshots/screenshot.png


## basic actions

- list the variables you have saved

```sh
	$ amp
```

- expand the variables you have saved
```sh
	$ amp vim 1 2 3-5
```

- run a command (step 1: expand variables, step 2: run command, step 3: each line
  that matches the `-p` regex will be saved to a variable)

```sh

	$ amp -p "(.*)" ls -1
	1 amp
	2 node_modules
	3 package.json
	4 readme.md
	5 screenshots

	# let's view what the current variables are set to
	$ amp
	1 = amp
	2 = node_modules
	3 = package.json
	4 = readme.md
	5 = screenshots
```

## suggested aliases
Because you don't want to type `amp` all over the place.

These are the aliases I use. Since I only just wrote this, there aren't that
many. Based on these it shouldn't be too hard write/customize your own set of
aliases.

```sh
	# give me variable expansion!
	alias subl='amp subl'
	alias ga='amp git add'
	alias gco='amp git checkout'
	alias gd='amp git diff'
	alias cat='amp cat'
	alias less='amp less'

	# give me variable saving!
	alias gs='amp -p "...(.*)$" git status -s'
	alias gbr='amp -p " ? (.*)$" git branch' # haha wow thats funny regex
	alias l='CLICOLOR_FORCE=1 amp -p "(.*)" ls -1'
```
