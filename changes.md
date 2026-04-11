# Story spoilers ahead.

Where possible I will give specific line numbers for the line I have modified. When I say I have modified a line number, I mean the line with the YAML index \[number\]. The first line of Episode 1 is line 1 of umi1_0.yml, but its index is 109.

There's two major things:
The first one is that the "red truth" (and later "blue truth") throughout has inconsistent spacing, usually when the sentence before it ends with a period.
To fix this I have modified the following lines: 13136, 13137, 13180, 16872

The second one is that certain characters sometimes end their sentences with things like "☆" or "♪" instead of normal punctuation marks.
Throughout the patch, with a few exceptions this is just... gone? And it's not replaced with normal punctuation, so instead there's just awkward blank spaces and run-ons.
I'm inclined to believe this is an oversight rather than a purposeful choice, so I'm adding those back in. There are a few places where the punctuation *is* replaced for something reading as more "normal," but it's something you would see if you're reading any other version of Umineko (including the original Japanese), so I'm modifying that as well for consistency. If Ryukishi says Maria can say ☆ out loud who are we to deny that
Sentences with ☆: 8678, 14694, 22298, 23119, 23128, 23132, 23181, 23185, 23190, 23230, 24128, 32583, 32618
Sentences with ♪: 8653, 24135, 24138, 24145, 24267, 24309, 24393, 24496, 25602, 26079, 27118, 28728, 32614, 32623, 32636
Sentences that had their punctuation change reverted: 9785 ("really...?" from "really♪"), 23935 ("you knowwww?" from "you knowwww♪"), 24265 ("secret from Mama!" from "Mama♪")

Remaining minor misc changes:

* Extra spaces: 26220
* Missing period: 31560
* Lines that have the japanese end quote character in Episode 3 instead of the ending quotation mark: 18603, 19189
* "You knew that George slipped out of the mansion!!" This should be guesthouse (21228)
    * This was actually a mistake originating from Umineko Project that no one had changed before I found it, so I submitted a pull request to get it fixed there too. Love wins
* "it's a good view.Uu!" (23245)
* Reference to a "* shape" rather than an "× shape", in a reference to being "sewn" (21525)
* "instantly.]" (32174)
* "whatsover" -> "whatsoever" (2257)
* Typos in the Umineko Project script that this patch was based on, that were fixed in Umipro but not here (504, 826, 16303, 19616, 24625, 24906, 27212, 30167)
    * Sourced from the following commits:
    * https://github.com/umineko-project/umineko-scripting/commit/23784ec431385d81238dea23a5e86c7442ba6d75
    * https://github.com/umineko-project/umineko-scripting/commit/134a267165adce3e15dce672e9d07cc9a8f74077
    * https://github.com/umineko-project/umineko-scripting/commit/c347ddb894e804e2926a1b0c0090f606527d1416