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
























I am unashamed to admit that, for every usage of RegEx, I ALWAYS open [Regex Crossword](https://regexcrossword.com) and use it's 'Help' section. It's not going to always work, but for this it generally does.



Began 2025-04-30 : 01:42:25 AM


## Time to Solve

# Sources for internal issues:
[Brackets & Markdown I](https://www.markdownguide.org/basic-syntax/#characters-you-can-escape)
[Brackets & Markdown II](https://stackoverflow.com/questions/16027723/how-to-escape-backslash-bracket-in-markdown)


