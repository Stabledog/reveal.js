# Les Matheson's Notes

## Experiments:

[Prototype video slides][]

## Operational stuff

- The node.js server (`npm start`) treats the reveal.js/ tree as web root.  The relative paths of its subdirs are mapped accordingly.

- Using this tree structure works:
```
~/reveal.js/
    plugin/markdown/
            ./example.html  << Our presentation wrapper, includes link to example.md
            ./markdown.js
            ./marked.js
            ./example.md --> symlink to ~/riddle/video/example.md

~/riddle/video/
        ./example.md  << Our slides

```

- Slide ordering: we should use vertical slides for any continuous sequences, because the remote clicker only drives up/down, it can't do left-right.  So that suggests "long vertical sequences of cue cards work best for a single video segment."

## Log
9/22/18 - the Markdown smoke-test passed.  I installed node.js on the Mac and was able to do the [full setup](../reveal.js#full-setup) instructions to get presentations working with the browser.  

Then, if you navigate to [the markdown hello-world page](./plugin/markdown/example.html), you find that it calls out to an [example.md](./plugin/markdown/example.md) with stuff that works in the browser as long as `npm start` is running in the `~/reveal.js/` directory.


[Prototype video slides]: ./plugin/markdown/proto.html

