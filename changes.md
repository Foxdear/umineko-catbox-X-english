# Story spoilers ahead.

Where possible[^1] I will list all changes and give specific line numbers for the line I have modified. When I say I have modified a line number, I mean the line with the YAML ID `[number]`. The first line of Episode 1 is line 1 of umi1_0.yml, but its ID is `109`.
[^1]:This is professional-speak for "unless I forgot."

I've written a little about the things that made me want to look into modifying the patch in the first place.

## The red truth
The first one is that the "red truth" (and later "blue truth") throughout has inconsistent spacing, usually when the sentence before it ends with a period.

<details>
   <summary>Example</summary>
    This isn't the most egeregious example, but this is probably the first one you'd see in the story.

   <img width="1999" height="512" alt="red text" src="https://github.com/user-attachments/assets/814b506e-6b28-40a4-bee0-d1b4febd63fb" />
   <br>
   This looks pretty clearly off in-game, but this line in the code looks like this.
   
   ```'BEATRICE@r@v27/20701286."And I\'ll say more.@k@v27/20701287.@|@y@c900.@[No method exists by which the doors can be locked from the outside without using a key.@]@c.@k @v27/20701288.@|@y@c900.@[Regarding the windows, no method exists by which they could somehow be locked from the outside.@]@c."'```

   The line becomes *really* hard to read. As long as there is one space after the `@k` in-between all those instructions, you fix this issue, but it's hard to tell at a glance exactly what you're looking at. This sometimes leads to redundant spaces as well, which are even harder to perceive but are still a formatting issue.
</details>

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
   Chapter 5 - Done, fixed 16872<br>
   Chapter 9 - Done, fixed 18181<br>
   Chapter 10 & Chapter 11 are one-liners and fine<br>
   Chapter 13 - Done, fixed 19461<br>
   Chapter 17 - Done, fixed 21712, 21767, 21787, 21831, 21933, 21942 (several), 21955, 21962 (whew)<br>
   Episode 4:<br>
   Chapter 4 - Done, 24002 had an extra space actually<br>
   Chapter 17 - Done, fixed 30500, 30523, 30529<br>
   Chapter 19 - Done, fixed 31481 (extra spaces)<br>
   Chapter 20 (Tea Party) - 32162, 32168, 32169, 32180, 32181, 32182, 32340, 32351, 32364, 32365, 32366, 32372, 32384, 32386, 32390, 32391, 32400, 32409, 32411, 32413, 32441, 32501, 32503, 32550, 32552, 32556. God they talk so much<br>
   Chapter 21 (???) - 32590, 32591, 32595, <br>
</details>

## "Uu♪"
Certain characters sometimes end their sentences with things like "☆" or "♪" instead of normal punctuation marks.

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
   23054<br>
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

## " -  -  - "
This isn't something I caught the underlying cause for until I started fixing things, but it did strike me as odd.

Umineko Project uses em dashes (—) pretty frequently, both as used in the original Japanese and stylistically. To represent an unheard part of a sentence, the Japanese versions use either ＊＊ or …… depending on which version you're looking at, but (as is common in English writing) Umipro uses em dashes for those.

The em dash is used in English literature, but due to most keyboards not having a specific em dash key (it's mainly inserted by the program you're writing in), it's not something you'd typically come across in casual writing on the internet. In my personal writing - sort of like this - I use spaced dashes rather than spaced (or unspaced) em dashes.

The original patch made the decision to blanket replace almost all "—" with " - ". Space-dash-space. I consider this valid syntax, but not really a necessary change. The issue is how much trouble this creates for every scenario where more than one em dash is used.

This turns "———" into " -  -  - ". Space-dash-double-space-dash and so on.

To grab the theoretically least spoilery example, compare this effort noise to the unpatched Japanese text. It just doesn't look right. There have been many times reading this patch I saw something like this and felt like something was off.

<img width="577" height="236" alt="kh" src="https://github.com/user-attachments/assets/47014be5-e3ee-49db-afdf-0b989cee6845" />

To make it easy on myself, I'm blanket *un*replacing " - " with "—", but handling certain cases (mainly "———" in place of a word) specially as I come across them so they follow English spacing. For the most part, Umipro uses the em dash properly.

<details>
<summary>Lines requiring special handling</summary>
443<br>
4851<br>
8607<br>
21502<br>
25832<br>
25837<br>
25878<br>
26339<br>
26341<br>
27909<br>
29284<br>
30506<br>
</details>

<details>
<summary>Lines where " - " was replaced automatically</summary>
147<br>
159<br>
160<br>
204<br>
243<br>
368<br>
466<br>
477<br>
485<br>
520<br>
546<br>
598<br>
641<br>
660<br>
679<br>
757<br>
815<br>
881<br>
904<br>
934<br>
991<br>
1084<br>
1088<br>
1109<br>
1115<br>
1119<br>
1129<br>
1176<br>
1209<br>
1239<br>
1350<br>
1378<br>
1401<br>
1409<br>
1414<br>
1416<br>
1419<br>
1437<br>
1448<br>
1514<br>
1552<br>
1568<br>
1691<br>
1795<br>
1818<br>
1903<br>
1938<br>
1940<br>
1951<br>
1960<br>
1973<br>
1985<br>
1989<br>
2036<br>
2099<br>
2108<br>
2224<br>
2282<br>
2423<br>
2484<br>
2557<br>
2610<br>
2703<br>
2724<br>
2729<br>
2746<br>
2945<br>
2960<br>
2964<br>
3011<br>
3143<br>
3148<br>
3165<br>
3174<br>
3252<br>
3686<br>
3808<br>
3877<br>
3903<br>
4006<br>
4010<br>
4111<br>
4123<br>
4205<br>
4240<br>
4310<br>
4311<br>
4364<br>
4412<br>
4498<br>
4556<br>
4562<br>
4571<br>
4578<br>
4634<br>
4727<br>
4738<br>
4746<br>
4764<br>
4889<br>
4939<br>
4945<br>
4957<br>
5139<br>
5173<br>
5331<br>
5332<br>
5401<br>
5482<br>
5513<br>
5578<br>
5602<br>
5631<br>
5655<br>
5715<br>
5871<br>
5935<br>
6046<br>
6066<br>
6220<br>
6253<br>
6380<br>
6385<br>
6424<br>
6428<br>
6471<br>
6484<br>
6593<br>
6619<br>
6674<br>
6714<br>
6731<br>
6759<br>
6770<br>
6843<br>
6975<br>
7086<br>
7107<br>
7138<br>
7205<br>
7219<br>
7229<br>
7291<br>
7353<br>
7448<br>
7470<br>
7491<br>
7493<br>
7519<br>
7543<br>
7589<br>
7609<br>
7611<br>
7622<br>
7681<br>
7739<br>
7752<br>
7765<br>
7843<br>
7883<br>
7962<br>
7979<br>
7991<br>
8010<br>
8023<br>
8091<br>
8127<br>
8164<br>
8169<br>
8185<br>
8209<br>
8268<br>
8315<br>
8411<br>
8429<br>
8488<br>
8543<br>
8573<br>
8612<br>
8625<br>
8692<br>
8836<br>
8855<br>
8901<br>
8903<br>
8935<br>
9009<br>
9155<br>
9168<br>
9233<br>
9243<br>
9425<br>
9491<br>
9756<br>
9789<br>
9866<br>
9899<br>
9962<br>
10006<br>
10072<br>
10105<br>
10116<br>
10180<br>
10335<br>
10360<br>
10418<br>
10458<br>
10548<br>
10637<br>
10645<br>
10744<br>
10753<br>
10824<br>
10866<br>
10889<br>
10898<br>
10937<br>
10974<br>
11051<br>
11059<br>
11126<br>
11156<br>
11303<br>
11327<br>
11507<br>
11512<br>
11514<br>
11542<br>
11569<br>
11574<br>
11666<br>
11706<br>
11740<br>
11754<br>
11791<br>
11872<br>
11880<br>
11882<br>
11887<br>
11930<br>
11983<br>
11992<br>
11993<br>
12008<br>
12024<br>
12081<br>
12266<br>
12270<br>
12303<br>
12343<br>
12374<br>
12377<br>
12527<br>
12548<br>
12558<br>
12589<br>
12601<br>
12633<br>
12827<br>
12885<br>
12907<br>
12970<br>
12974<br>
13079<br>
13124<br>
13126<br>
13143<br>
13145<br>
13211<br>
13233<br>
13341<br>
13352<br>
13399<br>
13518<br>
13526<br>
13691<br>
13751<br>
13770<br>
13885<br>
13892<br>
13952<br>
13968<br>
13978<br>
13983<br>
14018<br>
14547<br>
14616<br>
14751<br>
14839<br>
15018<br>
15055<br>
15067<br>
15073<br>
15089<br>
15269<br>
15453<br>
15528<br>
15867<br>
15893<br>
15979<br>
16113<br>
16160<br>
16201<br>
16312<br>
16637<br>
16668<br>
16835<br>
16984<br>
17267<br>
17301<br>
17305<br>
17335<br>
17511<br>
17810<br>
17831<br>
17833<br>
17855<br>
17946<br>
18162<br>
18252<br>
18644<br>
19153<br>
19271<br>
19282<br>
19302<br>
19309<br>
19401<br>
19467<br>
19481<br>
19485<br>
19498<br>
19527<br>
19542<br>
19770<br>
19881<br>
20079<br>
20140<br>
20146<br>
20152<br>
20234<br>
20316<br>
20413<br>
20686<br>
20781<br>
20977<br>
20991<br>
21283<br>
21421<br>
21591<br>
21601<br>
21604<br>
21816<br>
21818<br>
21983<br>
22034<br>
22086<br>
22127<br>
22215<br>
22274<br>
22317<br>
22326<br>
22346<br>
22389<br>
22393<br>
22566<br>
22664<br>
22665<br>
22774<br>
22844<br>
22980<br>
23330<br>
23411<br>
23415<br>
23492<br>
23523<br>
23598<br>
23625<br>
23733<br>
23754<br>
23785<br>
23787<br>
23790<br>
23791<br>
23830<br>
23832<br>
23833<br>
23940<br>
23969<br>
24002<br>
24022<br>
24085<br>
24158<br>
24183<br>
24434<br>
24472<br>
24609<br>
24644<br>
24685<br>
24701<br>
24708<br>
24711<br>
24733<br>
24779<br>
24846<br>
24954<br>
25002<br>
25009<br>
25021<br>
25024<br>
25053<br>
25081<br>
25102<br>
25131<br>
25137<br>
25179<br>
25196<br>
25208<br>
25240<br>
25275<br>
25276<br>
25426<br>
25453<br>
25455<br>
25459<br>
25465<br>
25470<br>
25531<br>
25544<br>
25553<br>
25592<br>
25595<br>
25733<br>
25746<br>
25753<br>
25830<br>
25837<br>
25859<br>
25861<br>
25867<br>
25874<br>
25887<br>
25890<br>
25962<br>
25971<br>
25987<br>
26132<br>
26242<br>
26301<br>
26414<br>
26426<br>
26461<br>
26510<br>
26514<br>
26518<br>
26519<br>
26594<br>
26606<br>
26618<br>
26621<br>
26635<br>
26695<br>
26721<br>
26783<br>
26843<br>
26946<br>
26967<br>
26989<br>
27007<br>
27276<br>
27289<br>
27295<br>
27297<br>
27325<br>
27353<br>
27367<br>
27397<br>
27459<br>
27526<br>
27557<br>
27562<br>
27621<br>
27699<br>
27727<br>
27831<br>
28104<br>
28112<br>
28190<br>
28401<br>
28494<br>
28967<br>
29096<br>
29188<br>
29216<br>
29259<br>
29272<br>
29292<br>
29297<br>
29304<br>
29463<br>
29467<br>
29674<br>
29759<br>
29902<br>
29916<br>
30007<br>
30200<br>
30368<br>
30369<br>
30471<br>
30515<br>
30527<br>
30530<br>
30673<br>
30724<br>
30766<br>
30771<br>
30878<br>
30984<br>
30985<br>
31058<br>
31077<br>
31116<br>
31190<br>
31276<br>
31278<br>
31315<br>
31397<br>
31404<br>
31414<br>
31423<br>
31482<br>
31498<br>
31507<br>
31561<br>
31636<br>
31645<br>
31647<br>
31783<br>
31817<br>
31837<br>
31881<br>
31904<br>
32005<br>
32017<br>
32107<br>
32209<br>
32210<br>
32223<br>
32227<br>
32245<br>
32349<br>
32415<br>
32456<br>
32481<br>
32494<br>
32553<br>
32611<br>
32738<br>
33021<br>
33142<br>
33213<br>
33247<br>
33793<br>
34033<br>
34233<br>
34439<br>
34658<br>
35350<br>
35376<br>
35565<br>
35647<br>
35683<br>
35685<br>
35688<br>
35715<br>
35763<br>
35851<br>
35872<br>
35876<br>
36143<br>
36237<br>
36358<br>
36939<br>
37252<br>
37253<br>
37454<br>
37628<br>
37643<br>
37824<br>
37874<br>
38092<br>
38220<br>
38303<br>
38382<br>
38405<br>
38457<br>
38501<br>
38541<br>
38593<br>
38702<br>
38807<br>
38822<br>
38837<br>
39033<br>
39175<br>
39177<br>
39206<br>
39280<br>
39505<br>
39508<br>
39604<br>
39625<br>
39800<br>
39801<br>
39802<br>
39803<br>
39850<br>
39879<br>
39912<br>
40029<br>
40119<br>
40309<br>
40333<br>
40551<br>
40609<br>
40663<br>
40897<br>
41250<br>
41272<br>
41273<br>
41464<br>
41466<br>
41480<br>
41568<br>
41574<br>
41614<br>
41727<br>
42003<br>
42071<br>
42141<br>
42207<br>
42217<br>
42320<br>
42410<br>
42414<br>
42525<br>
42902<br>
43030<br>
43160<br>
43187<br>
43303<br>
43452<br>
43465<br>
43501<br>
43634<br>
43698<br>
43709<br>
43771<br>
43911<br>
43914<br>
43976<br>
44008<br>
44139<br>
44150<br>
44197<br>
44210<br>
44344<br>
44359<br>
44362<br>
44366<br>
44468<br>
44505<br>
44669<br>
44724<br>
44726<br>
44745<br>
44756<br>
44773<br>
45049<br>
45065<br>
45089<br>
45158<br>
45178<br>
45547<br>
45575<br>
45585<br>
45701<br>
45721<br>
45769<br>
45822<br>
45878<br>
45964<br>
45968<br>
46019<br>
46124<br>
46165<br>
46172<br>
46178<br>
46352<br>
46363<br>
46457<br>
46492<br>
46519<br>
46580<br>
46719<br>
46741<br>
46850<br>
46869<br>
46904<br>
47026<br>
47043<br>
47045<br>
47056<br>
47066<br>
47069<br>
47077<br>
47103<br>
47105<br>
47107<br>
47157<br>
47158<br>
47284<br>
47303<br>
47406<br>
47529<br>
47718<br>
47721<br>
47796<br>
47932<br>
47974<br>
48059<br>
48098<br>
48100<br>
48102<br>
48106<br>
48308<br>
48403<br>
48500<br>
48554<br>
48773<br>
48861<br>
49031<br>
49040<br>
49061<br>
49068<br>
49129<br>
49134<br>
49184<br>
49377<br>
49460<br>
49471<br>
49481<br>
49827<br>
49828<br>
49848<br>
49898<br>
49903<br>
50100<br>
50320<br>
50448<br>
50459<br>
50639<br>
50718<br>
50786<br>
50852<br>
51090<br>
51123<br>
51300<br>
51458<br>
51462<br>
51463<br>
51507<br>
51628<br>
51664<br>
51729<br>
51734<br>
51765<br>
51809<br>
51810<br>
51818<br>
52288<br>
52522<br>
52527<br>
52534<br>
52717<br>
52791<br>
52876<br>
52879<br>
52922<br>
52962<br>
52990<br>
52994<br>
53024<br>
53054<br>
53114<br>
53208<br>
53323<br>
53573<br>
54455<br>
54556<br>
54594<br>
54610<br>
54616<br>
54637<br>
54706<br>
55065<br>
55223<br>
55309<br>
55331<br>
55701<br>
56035<br>
56073<br>
56113<br>
56311<br>
56562<br>
56727<br>
56789<br>
56796<br>
56798<br>
56821<br>
56827<br>
56869<br>
56935<br>
57167<br>
57256<br>
57311<br>
57656<br>
57743<br>
57817<br>
57900<br>
57953<br>
58034<br>
58115<br>
58517<br>
58833<br>
58854<br>
59094<br>
59318<br>
59599<br>
59756<br>
59845<br>
59906<br>
60348<br>
60902<br>
60903<br>
61003<br>
61028<br>
61178<br>
61223<br>
61253<br>
61317<br>
61340<br>
61609<br>
61773<br>
61837<br>
61850<br>
61956<br>
62003<br>
62023<br>
62180<br>
62342<br>
62367<br>
62398<br>
62399<br>
62457<br>
62660<br>
62833<br>
63077<br>
63439<br>
63513<br>
63651<br>
63932<br>
63972<br>
64026<br>
64277<br>
64437<br>
64617<br>
64798<br>
64827<br>
64868<br>
65046<br>
65062<br>
65468<br>
120A<br>
424A<br>
495A<br>
760A<br>
815A<br>
846A<br>
2559A<br>
3069A<br>
6937A<br>
</details>

There is a reason I can understand why this change might have been made initially, and that is:

## The textbox layout function

Every textbox calls the function `s.layout()` (in `layout.rb`) in order to make sure the text actually fits in the box. It inserts `@r` (the new line command) automatically in appropriate places. This script has a pretty difficult job, determining the width of every line, what special `@` commands are present, and so on, and breaking to the next line when appropriate.

There was an oversight in the original layout code that meant sometimes it did this badly. For example, in Episode 1 Chapter 1:

<img width="2016" height="425" alt="before" src="https://github.com/user-attachments/assets/b6ef3700-2800-44cd-8a8b-24a624a5acae" />
<br>
The input for this line is as follows:

`@rGirls at Maria's age tend to be very impressionable.@k@rShe's just about the age when many girls start to get excited about sixth senses and whether they have any psychic potential and stuff.`

The issue in this particular case lies in how `@k@r` is processed. Technically speaking, `s.layout()` looks for spaces in the input string and separates the words and spaces into "elements". So `@rGirls`, `at`, `Maria's`, and all the spaces in-between get their own elements. If the line is too long, it moves the element to the next line by adding `@r`, trims excess whitespace, and continues until the text is entirely processed. 

...But if you're only breaking on spaces, `impressionable.@k@rShe's` is one element. We started a new line manually in the middle of the string, but it was counting the whole length of that element for the line length. You shouldn't *need* to put a space in between, it's a new line, after all, but I found that `@k@r` and `@k @r` both were processed differently, and this was the cause. I made it so that `@r` always separates itself into a new element when the text is being processed.

I compared the output of putting the script into `s.layout()` before and after, to make sure my changes weren't destructive. `@k@r` is used so often in the narration that this change affects over **two thousand** lines. In the best case, it fixes those lines that seem to break in the middle for no reason. In the most minimal cases, it fits one or two extra words on the previous line, sometimes meaning it doesn't need to create another line at all. 

<img width="2017" height="419" alt="after" src="https://github.com/user-attachments/assets/f0dd52de-6d6d-4df0-a98f-69e1dfa3b312" />
<br>
This also meant em dashes would potentially make very long elements (since they're not spaces), so I added special handling for them to allow line breaks (without being deleted like whitespace would be). This only affects about ~90 lines, but anything that improves the reading experience is a win.

## Other stuff

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
   10181<br>
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
   15169<br>
   15546<br>
   15811<br>
   15865<br>
   16960<br>
   17359<br>
   19300<br>
   20034<br>
   21988<br>
   22282<br>
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
* This is technically changing the translation, but Battler says "e.g. Kumasawa-san" in a blue truth in Episode 4 (32390). "e.g." isn't used anywhere else in the text and it's not really something you would say out loud. I think it's okay to rephrase this as "*like* Kumasawa-san", but I might revert this. The original line is "熊沢さんを始め、当時アリバイがない人間が存在した。"
* Added ruby text (furigana) to the "fast talking shiritori" in Episode 4 Chapter 8 (25641, 25642, 25646, 25649, 25651). I know how shiritori works but I don't know Japanese so I can't keep up otherwise. This bit lasts for like two seconds but it's IMPORTANT ok
* Also added ruby text for the following:
   * "asougi"/"nayuta" (1553) and the Japanese eras in Episode 1 (1636, 1637) 
   * Kanon's "boku" in Episode 2 (8753)
   * "yandere" (22292) and "ta nuki" (18416) in Episode 3
      * there's ruby for "tsundere" that I adjusted to match Umipro, because she says "dere" but the ruby said "deredere" (to match "tsuntsun" but like, she didn't say that) (22291/32650)
   * "110" (27844)/"Shotoku Taishi" (23289)/"gaooo" (23252, 24496) in Episode 4
   * These aren't strictly necessary (though the fact Kanon says boku is mentioned in the text) but I think they're nice and don't take away from anything. (Also I personally had no clue who Shotoku Taishi was.)
   * Added pronunciation ruby text to the discussion of the epitaph in Episode 3 (18372, 18377, 18463, 18591) because that section is so kanji heavy and it seems helpful
   * I also added "99.99% (four nines)" (2192) <strike>but I had to switch "four nines" to the ruby text. It's not ideal and I spent a while trying to force it to work the other way (including investigating the font itself) but `.` doesn't work in the ruby text and nothing else looked right</strike> it works if you use full-width characters. I'll allow myself to feel a little smart for that one
   * I wanted to add more of the missing ruby text from Umipro, but I can't tell why it's there in the first place in some cases. Unfortunately a lot of Japanese cultural references also can't be addressed in the same way Umipro does (adding them to the tips section) without further modding the game.
* Fixed lipsync for one of Natsuhi's lines in Episode 5 (34789)
   * This taught me something interesting about how the engine works: Which sprite is lipsyncing is based on the numbered folder the voiceline is in. Natsuhi's voice folder is `03`, but the files for this line were in `30`, which is normally VIRGILIA's folder. I thought I'd need to change the scripting or something complicated like that, but I just needed to copy the files to the right folder.
