# Les Matheson's Notes

## Experiments:

[Prototype video slides][]

## Operational stuff

- The node.js server (`npm start`) treats the reveal.js/ tree as web root.  The relative paths of its subdirs are mapped accordingly.

- Windows only: there's a .lnk shortcut in [npm-reveal.lnk][] which launches the Windows version of node's `npm` to start the web server (use cygstart from Cygwin to launch it, or Explorer)

- Using this tree structure works:
```
~/reveal.js/
    plugin/markdown/
            ./proto.html  << Our presentation wrapper, includes link to proto.md
            ./markdown.js
            ./marked.js
            ./proto.md --> symlink to ../../riddle/video/proto.md

~/reveal.js/riddle/video/
        ./proto.md  << Our slides

```

- Slide ordering: we should use vertical slides for any continuous sequences, because the remote clicker only drives up/down, it can't do left-right.  So that suggests "long vertical sequences of cue cards work best for a single video segment."

## Log
9/23/18 - Windows is a problem hosting node.js.  The node install for unix doesn't work on cygwin, and the Windows build of Node doesn't like mintty.  So you have to start a Command.exe window, then run "npm start" in the c:\Cygwin64\home\lesma\reveal.js dir to get a functioning http server, and then the problem is that the windows version of node has no symlink support, so having markdown located over in the riddle/ tree doesn't work as we expect!

Possible solution:  move riddle/ under the reveal.js tree and symlink it to ~/

9/22/18 - the Markdown smoke-test passed.  I installed node.js on the Mac and was able to do the [full setup](../reveal.js#full-setup) instructions to get presentations working with the browser.  

Then, if you navigate to [the markdown hello-world page](./plugin/markdown/example.html), you find that it calls out to an [example.md](./plugin/markdown/example.md) with stuff that works in the browser as long as `npm start` is running in the `~/reveal.js/` directory.


[Prototype video slides]: ./plugin/markdown/proto.html
[npm-reveal.lnk]: ./npm-reveal.lnk
