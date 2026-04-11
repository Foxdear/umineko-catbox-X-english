# Story spoilers ahead.

Where possible I will give specific line numbers for the line I have modified. When I say I have modified a line number, I mean the line with the YAML index \[number\]. The first line of Episode 1 is line 1 of umi1_0.yml, but its index is 109.

There's two major things:
The first one is that the "red truth" (and later "blue truth") throughout has inconsistent spacing, usually when the sentence before it ends with a period.

<details>
   <summary>Truth fixes</summary>
   13136<br>
   13137<br>
   13180<br>
   16872<br>
</details>

<details>
   <summary>Example</summary>
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
