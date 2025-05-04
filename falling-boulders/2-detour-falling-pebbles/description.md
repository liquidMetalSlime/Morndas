


a small detour
halfway through finishing the issue of './../1-boulder/', I thought, *"dang I really need Discord Rich Presence for my nvim client!"*.
I don't, like at all, but the brain wants it; and fighting it has always proved futile; so, have 3 prominent options upon searching:

[discord.nvim](https://github.com/mistweaverco/discord.nvim)
[cord.nvim](https://github.com/vyfor/cord.nvim)
[presence.nvim](https://github.com/andweeb/presence.nvim)

The differences in immediate application aren't too noticeable, I think; could be bad eyes.
But, [cord.nvim](https://github.com/vyfor/cord.nvim) is shinier in github appearance, so I choose it.


I, in all of my foolishness and pride, thought; let's just stuff the plugin into init.lua as such:
{ "andweeb/presence.nvim" }
That'll totally work! Despite the back of my mind saying otherwise. It did not work; only lead to an error,
deleted from init.lua.

Then, despite my knowledge that it wouldn't work, I just stuffed the configuration file AND the nvim name link into
*init.lua*; surprise surprise, that didn't work wow who would've thought.



