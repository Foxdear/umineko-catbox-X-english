# Story spoilers ahead.

Where possible[^1] I will list all changes and give specific line numbers for the line I have modified. When I say I have modified a line number, I mean the line with the YAML index \[number\]. The first line of Episode 1 is line 1 of umi1_0.yml, but its index is 109.
[^1]:This is professional-speak for "unless I forgot."

There's two major things:
The first one is that the "red truth" (and later "blue truth") throughout has inconsistent spacing, usually when the sentence before it ends with a period.

<details>
   <summary>Truth fixes</summary>
   For my own reference, since the "truths" are usually pretty densely consolidated, here's all the chapters containing "truths" (from what I've read thus far) and whether or not I've checked them<br>
   Episode 2:<br>
   Chapter 11 - Done, no issues<br>
   Chapter 12 - Done, no issues<br>
   Chapter 13 - Done, no issues<br>
   Chapter 14 - Done with fixes on 13136, 13137, 13180<br>
   Chapter 15 - Done, no issues<br>
   Chapter 16 - Done, no issues<br>
   Episode 3:<br>
   Prologue - Done, no issues<br>
   Chapter 4 - Done, no issues<br>
   Chapter 5 - Done, no issues<br>
   Chapter 9<br>
   Chapter 10<br>
   Chapter 11<br>
   Chapter 13<br>
   Chapter 17<br>
   Episode 4:<br>
   Chapter 17<br>
   Chapter 19<br>
   Chapter 20<br>
   Chapter 21<br>
   16872<br>
</details>

<details>
   <summary>Example</summary>
    This isn't the most egeregious example, but this is probably the first one you'd see in the story.

   <img width="1999" height="512" alt="red text" src="https://github.com/user-attachments/assets/814b506e-6b28-40a4-bee0-d1b4febd63fb" />
   
   This looks pretty clearly off in-game, but this line in the code looks like this.
   
   ```'BEATRICE@r@v27/20701286."And I\'ll say more.@k@v27/20701287.@|@y@c900.@[No method exists by which the doors can be locked from the outside without using a key.@]@c.@k @v27/20701288.@|@y@c900.@[Regarding the windows, no method exists by which they could somehow be locked from the outside.@]@c."'```

   The line becomes *really* hard to read. As long as there is one space after the `@k` in-between all those instructions, you fix this issue, but it's hard to tell at a glance exactly what you're looking at. This sometimes leads to redundant spaces as well, which are even harder to perceive but are still a formatting issue.
</details>

The second one is that certain characters sometimes end their sentences with things like "☆" or "♪" instead of normal punctuation marks.

Throughout the patch, with a few exceptions this is just... gone? And it's not replaced with normal punctuation, so instead there's just awkward blank spaces and run-ons.

I'm inclined to believe this is an oversight rather than a purposeful choice, so I'm adding those back in. There are a few places where the punctuation *is* replaced for something reading as more "normal," but it's something you would see if you're reading any other version of Umineko (including the original Japanese), so I'm modifying that as well for consistency. If Ryukishi says Maria can say ☆ out loud who are we to deny that

<details>
   <summary>Sentences with ☆</summary>
   8678<br>
   14694<br>
   22298<br>
   23119<br>
   23128<br>
   23132<br>
   23181<br>
   23185<br>
   23190<br>
   23230<br>
   24128<br>
   32583<br>
   32618<br>
</details>

<details>
   <summary>Sentences with ♪</summary>
   8653<br>
   24135<br>
   24138<br>
   24145<br>
   24267<br>
   24309<br>
   24393<br>
   24496<br>
   25602<br>
   26079<br>
   27118<br>
   28728<br>
   32614<br>
   32623<br>
   32636<br>
</details>

<details>
   <summary>Sentences that had their punctuation change reverted</summary>
   9785 ("really...?" => "really♪")<br>
   23935 ("you knowwww?" => "you knowwww♪")<br>
   24265 ("secret from Mama!" => "Mama♪")<br>
</details>

Remaining minor misc changes:

<details>
   <summary>Extra spaces</summary>
   Mostly found with the regex string "@k (@v...........\. )" and replaced with "@k\1"<br>
   479<br>
   1967<br>
   2084<br>
   2109<br>
   2195<br>
   3177<br>
   3269<br>
   6731<br>
   11917<br>
   11923<br>
   11925<br>
   12327<br>
   12561<br>
   13169<br>
   13367<br>
   13372<br>
   13373<br>
   13798<br>
   14581<br>
   10181<br>
   15169<br>
   19300<br>
   20034<br>
   22282<br>
   15546<br>
   15811<br>
   15865<br>
   16960<br>
   17359<br>
   26220<br>
   33720<br>
   34643<br>
   36839<br>
   36986<br>
   41679<br>
   42135<br>
   42162<br>
   42199<br>
   42232<br>
   43589<br>
   43665<br>
   43669<br>
   44188<br>
   44210<br>
   44599<br>
   44884<br>
   45119<br>
   45397<br>
   46077<br>
   46463<br>
   46607<br>
   46618<br>
   46622<br>
   46694<br>
   46703<br>
   46741<br>
   46745<br>
   47009<br>
   47236<br>
   47263<br>
   48936<br>
   49332<br>
   50122<br>
   50804<br>
   50941<br>
   51807<br>
   52697<br>
   53006<br>
   53241<br>
   53786<br>
   54342<br>
   54968<br>
   55994<br>
   56000<br>
   56213<br>
   56878<br>
   57283<br>
   57598<br>
   57692<br>
   57941<br>
   58151<br>
   58353<br>
   58401<br>
   58855<br>
   59515<br>
   60112<br>
   60136<br>
   61406<br>
   64115<br>
   64212<br>
   64329<br>
   64453<br>
   64574<br>
   64635<br>
   65048<br>
   65466<br>
</details>

* Missing period: 31560
* Missing line break: 27434
* Lines that have the japanese end quote character 」 in Episode 3 instead of the ending quotation mark: 18603, 19189
* "You knew that George slipped out of the mansion!!" This should be guesthouse (21228)
    * This was actually a mistake originating from Umineko Project that no one had changed before I found it, so I submitted a pull request to get it fixed there too. Love wins
* "it's a good view.Uu!" (23245)
* Reference to a "* shape" rather than an "× shape", in a reference to being "sewn" (21525)
* "instantly.]" (32174)
* "whatsover" -> "whatsoever" (2257)
* "payed" (a real word meaning "to seal up a ship to prevent leaks") => "paid" any notice (10936)
* Typos in the Umineko Project script that this patch was based on, that were fixed in Umipro but not here (504, 826, 16303, 19616, 24625, 24906, 27212, 30167)
    * Sourced from the following commits:
    * https://github.com/umineko-project/umineko-scripting/commit/23784ec431385d81238dea23a5e86c7442ba6d75
    * https://github.com/umineko-project/umineko-scripting/commit/134a267165adce3e15dce672e9d07cc9a8f74077
    * https://github.com/umineko-project/umineko-scripting/commit/c347ddb894e804e2926a1b0c0090f606527d1416
