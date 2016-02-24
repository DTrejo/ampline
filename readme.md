# ampline
amp up your command line.

assign variables to output from common commands

a great complement to tab completion

No longer will you find yourself copy-pasting long paths into `git add`, or tab-completing deep directory structures.

### `npm -g install ampline`

### show not tell

A simple example:

```sh
$ ls
1 amp
2 node_modules
3 package.json
4 readme.md
5 screenshots

$ cat 4
# executes cat readme.md
TODO write a readme. Lorem ipsum dolor sit amet, consectetur adipisicing elit,
sed do eiusmod.

$ amp echo "hi" >> 4
# executes echo "hi" >> readme.md

$ gs # this is an alias that uses `amp`
1  M readme.md

$ ga readme.md
1 M  readme.md

$ git commit -m 'added hi to my readme.'
```

A more complicated example:

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
    # give me variable saving!
    alias gs='amp -p "...(.*)$" git status -s'
    alias gbr='amp -p " ? (?:remotes\\/)?(?:origin\\/)?(.*)$" git branch' # supports -a, -r flags

    alias l='CLICOLOR_FORCE=1 amp -p "(.*)" ls -1'
    alias find='amp -p "(.*)" find'

    # give me variable expansion!
    alias subl='amp subl'
    alias ga='amp git add'
    alias grm='amp git rm'
    alias gco='amp git checkout'
    alias gd='amp git diff'
    alias gdh='amp git diff HEAD'
    alias gunstage='amp git unstage'
    alias cat='amp cat'
    alias less='amp less'
    alias mocha='amp mocha'
```


## Enjoy! I hope you like it :) - @DTrejo

@peterlyon suggested I add this photo!

![Amplifier History - Vai](http://carvinimages.com/images/amplifierhistory/Vai420x320.bmp)
