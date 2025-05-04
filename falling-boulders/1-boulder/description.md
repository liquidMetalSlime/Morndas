# Messy image name numbering
Each of the images in '../../daImages/' is numbered; only, they're numbered phonetically(?);
and changing them one at a time is inefficient. A solution can easily be found in solutions to
past *mistakes*: an easy mix of the 'find', 'mv' and RegEx.

Simply need to match an unknown length of characters up to a '-', deleting the excess text after
it, along with the '-'.

First, my primitive brain requires grep as a matching assistance:
***ls pics-windows10/ | grep -Eo '.*'**

1-windowsinstall.png
2-installnow.png
3-setupisstarting.png
activatewindows-four.png
hwylts-fourteen.png
...


Of course, matching whatever we can firstly, then thinning it out:
At first, I used **'\w{1,}'**; but this would catch digits as well:

1
windowsinstall
png
2
installnow
png
3
...


As such, it's better to use brackets; such as with **'\[A-Za-z\]*'**:
windowsinstall
png
installnow
png
setupisstarting
png
...


Now, no numbers; but oh no, now file extensions are being caught!
Initially, I used **\[A-Za-z\]{1,}** alone; but this results in the
exact same result.
Then, I tried **'\[A-Za-z\]*-'**


This can be solved with **'\[A-Za-z\]{1,}-'**, grabbing WHATEVER text
is behind a hyphen, then grabbing that hyphen with it
# **Stopped 2025-04-30 : 02:10:04 AM**





# **Started 2025-05-02 : 11:56:15 AM**
I realized, upon playing around with how I was going to replace and add parts,
that I'd need to use **sed**; which is fine, just have to warm back up to it again.


Which then naturally lead to the obvious necessity to target the part to be removed;
leading to a transition from **\[A-Za-z\]{1,}(-.)** to **\-\[A-Za-z\]{1,}**, which is
really just a reversal of the former, leading to:
-windowsinstall
-installnow
-setupisstarting
-four
-fourteen
-twelve
-eight
...


But now it's catching the files that I had manually changed to a proper format, so we need
to cut those out somehow. This lead to me going with a big guess: **\-^(win)^(ins)^(set)\[A-Za-z\]{1,}**,
which ends up with a mass purge:
-four
-fourteen
-five
=-=-=-=-=-=


Then, a second try with: **\-\[^(win)\]\[A-Za-z\]{1,}**;
which, at a 1st, 2nd, and third glance, it worked:
-setupisstarting
-four
-fourteen
-twelve
-eight
-eleven
-ten
-thirteen
-five
-six
-seven
=-=-=-=-=


But it didn't, *-windowsinstall* may be gone, but so is *-nine*, though is would seem to be the path.
Then, 2 minutes later, it hit me, it doesn't matter right now, removing all instances after '-' won't
harm anything, and can be remedied if anything, if wanted.
Then...

user@host ~/path/path/ (main)> **sed -r s/'\-\[A-Za-z\]{1,}'//d**
sed: -e expression #1, char 19: unknown option to `s'


:(


So, had to reread 'info sed' real quick:

### 3.3 The ‘s’ Command
### =======================
#### The ‘s’ command (as in substitute) is probably the most important in ‘sed’ and has a lot of different options.  The syntax of the ‘s’ command is ‘s/REGEXP/REPLACEMENT/FLAGS’

Then confirming the 'd' flag use:

### 3.4 Often-Used Commands
### =======================

#### If you use ‘sed’ at all, you will quite likely want to know these commands.
#### ‘d’

```sh
     Delete the pattern space; immediately start next cycle.

     Example: delete the second input line:
          $ seq 3 | sed 2d
          1
          3
```
but then I figured, why am I using 'd'? It's being replaced? according to the documentation? so, after
completely forgettnig what tool I could use as a replacement despite using it 2 months ago for 200 music files;
I dug around:

https://stackoverflow.com/a/2372739
https://unix.stackexchange.com/a/306258
https://stackoverflow.com/a/2372739

All of them reminding me of **rename**, the Perl tool specifically; also solidifying the necessity of it over **sed**
in mass file renaming operations, for now.


After going back over *rename --help* I tried:
**rename -nv '\-\[A-Za-z\]{1,}' 'test' directory **

Then, upon looking around, I discovered that, *gasp*, my **rename** wasn't the *proper* **rename** based off shown behaviour from:
[this post](https://stackoverflow.com/a/1086509),
[this post](https://unix.stackexchange.com/a/72728),
and, following the previous:
[this post!](https://unix.stackexchange.com/a/730895)

With the last post being a HIGHLY extensive explanation of not only rename, but the annoying factor of different binaries existing under the same name!
The most important bit, really, is:

```
Check your own version
note There's another binary tool with the same name used on some distro. Depending on your distro, the Perl version can be called perl-rename, file-rename, prename, pname or rename.
There's also a Python rename command out there !
```

This, then, lead to me installing the appropriate package for the AUR: 'perl-rename'


## Solution
Then, to my greatest of joys: ___"perl-rename -n 's/-\[A-Za-z\]{1,}/-TEST/' *"___

1-windowsinstall.png -> 1-TEST.png
2-installnow.png -> 2-TEST.png
3-setupisstarting.png -> 3-TEST.png
activatewindows-four.png -> activatewindows-TEST.png
hwylts-fourteen.png -> hwylts-TEST.png

text was now being CHANGED, at last; just had to get the proper **rename** binary that supported RegEx!





side things learned in the journey, add this into a separate thing, eventually:
Switching between buffer and nvimtree - [01](https://www.reddit.com/r/neovim/comments/13j9onv/switching_between_nvimtree_and_bufferline/)



I am unashamed to admit that, for every usage of RegEx, I ALWAYS open [Regex Crossword](https://regexcrossword.com) and use it's 'Help' section. It's
not going to always work, but for this it generally does.



Started 2025-04-30 : 01:42:25 AM
Stopped 2025-04-30 : 02:10:04 AM

Started 2025-05-02 : 11:56:15 AM
Stopped 2025-05-02 : 12:01:05 AM

Started 2025-05-04 : 12:51:35 AM
Stopped 2025-05-04 : 03:10:42 AM

Started 2025-05-04 : 01:24:00 PM
Stopped


## Time to Solve

# Sources for internal issues:
[Brackets & Markdown I](https://www.markdownguide.org/basic-syntax/#characters-you-can-escape)
[Brackets & Markdown II](https://stackoverflow.com/questions/16027723/how-to-escape-backslash-bracket-in-markdown)


