# METaL Instructions
This repo contains a number of instructional materials related to the [METaL][] virtual reality system.

[METaL]:http://vrac.iastate.edu/METaL/

##Important Note about Line Endings

This repo standardizes on unix line endings upstream. However, LyX (used for the user manual) on Windows will save with Windows line endings. To solve this problem, please run this command to set a setting for this repo only:

```
git config core.autocrlf true
```

You will probably then need to do a `git reset --hard` to re-set all the trees (particularly working tree and index) to have the right line endings, so **be sure to do this immediately after cloning**.

For more information, you can see [this article on help.github](http://help.github.com/line-endings/) though note that we modified the commands so that they do not change the global configuration.