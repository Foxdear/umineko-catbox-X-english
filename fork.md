The long and short: I am fixing identifiable, but usually small, issues that are present in the original patch, as I read them. I think they're worth fixing, and I hope that this can improve someone else's experience.

The English patch by &Olga is the way I read (as of writing, actively am reading) Umineko for the first time, after being directed to it by 07th-Mod as the best way to read Umineko. I've been skimming the Steam version on the side since I had purchased it, and while 07th-Mod does what they can, the referral was for a reason: the Switch engine is clearly superior on so many levels, and the patch and everything that went into it is incredible to look at. (I love decompiling and reverse engineering as a technical pursuit, but mostly from a distance.) I have so much respect for everyone responsible for bringing the patch to the way it is today.

So... what's with the fork? Well, I want this to be the best it can be, and it's the only option I have.

As &Olga says in the final release, "there may still be small issues left here and there. Incredibly minor stuff, like typos or missing punctuation." Well, as someone who is using this patch to read Umineko totally fresh, with (at least something of) an eye for detail and coding knowledge, I'm someone in the position to notice and fix these little issues. But the repo is closed. Understandably, &Olga has stepped away from the project.

This means the only way to put my changes out there is with a fork. I want to specify, I don't want to claim I've created the "new definitive version" or anything. 99.9% percent of the work has been done long ago by people with skills I don't have, and I don't have any interest in coming in and ripping up all floorboards. I am just some girl. 

But &Olga's goal was to create the "perfect version." The BEST way to read Umineko. I won't claim I'm capable of such a thing, but in this, I think we are aligned. If I can provide a better experience for someone else, I think that is meaningful.

This fork has two primary objectives:

## Fix things that are obviously missing or wrong
Currently this is basically missing punctuation, missing spaces, leftover Japanese symbols (there are a few lines that have 」 as the ending quotation mark, for example), and at least one minor factual error.

As a reader, I do have *some* questions about word choice and phrasing, but I am not a translator and I do not presume to be one. I see my role here as similar to an editor: not to alter the writing, but to try to present it in the best way possible.

## Make the repository easier to work with

In the original repository, in order to edit the translation, you used to have open script.rb, a single 25 MB file with over **four hundred sixty-four thousand** lines, and dig through that file to find the data you need to edit. This is so big that GitHub won't let you look at it in-browser. It's a pain to work with.

The translation on its own is about ~73k lines. This means that **less than 16%** of all of those lines of code are relevant to a translator, or anyone who just wants to try to improve the translation (like myself). The other ~84% lines are necessary data that needs to exist to make the game work, but the average person doesn't need to look at it. 

The solution is to take the translation out and make it viewable separately. I've modeled the repository after [Umineko Project's](https://github.com/umineko-project/umineko-scripting) - convenient, since most of this patch uses their translation - and am organizing the translation by chapter. Of course, *I haven't finished reading the story before starting this project*, so the organizing part will be done in pieces. The data is set up so that it doesn't matter what file the line is in exactly, as long as the line exists in a .yml file in one of the story subfolders. The organization is purely for human benefit.

Currently there are still some things you need to look at in script.rb, like character profiles and chapter titles. These will eventually be moved out as well.

A small quirk of this is that I used the `ushort([number])` accompanying each line as the line ID while moving it into a YAML file, but towards the end of the file this count starts over from 0 and continues to 7431. To avoid conflicts, I've appended "A" to the IDs of those lines, so they instead starts from `0A` and end at `7431A`.

For a detailed (but possibly incomplete) list of changes I've made, see [here](changes.md). Be aware this list contains spoilers.