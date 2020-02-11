## Table of Contents
[Match Times or "n/a"](#match-times-or-na)  
[Match Title, Edition, Author](#match-title-edition-author)  
[Match Spaces Between First and Last Names And Substitute with `_`](#match-spaces-between-first-and-last-names-and-substitute-with-_)  
[Match Only Numbers Surrounded By |](#match-only-numbers-surrounded-by-)  
[Match Only Subdomains](#match-only-subdomains)  
[Picky `m` Matching](#picky-m-matching)  
["Select the Definite Article and the Indefinite Articles"](#select-the-definite-article-and-the-indefinite-articles)  

### Match Times or "n/a"
> Beginner regex question, example within
> I have the text:

Given
```
"openingHoursMonday";s:9:"3pm - 7pm"
```
> and want to match the 3pm - 7pm portion only. 
> In other cases, this portion would be marked as "n/a" and I would want to match that instead. 

(From https://www.reddit.com/r/regex/comments/f0i29z/beginner_regex_question_example_within/)

#### Goal
Match and Capture `3pm - 7pm`, allowing for other times too, like `10am - 2pm` 

If `n/a` appears instead of the time range in the quotes, match & capture that instead 

#### Text To Test Against
```
"openingHoursMonday";s:9:"3pm - 7pm"
"openingHoursMonday";s:9:"n/a"
"openingHoursMonday";s:9:"10am - 2pm"
"openingHoursMonday";s:9:"9pm - 3am"
```

#### Bonus
Match and Capture each time (ie, `3pm` and `7pm`) distinctly

### Match Title, Edition, Author

Given the mostly-but-not-always consistent text below:

```
Ebook for; Solutions Manual For; Test Bank for Development Through the Lifespan, 7e Laura Berk
Ebook for; Solutions Manual For Essentials of Business Communication, 9th Canadian Edition, 9e Mary Ellen Guffey, Richard Almonte
Ebook for; Test Bank for Cognitive Psychology Connecting Mind, Research and Everyday Experience 4e Bruce Goldstein
Ebook for; Solutions Manual For; Test Bank for Introduction to Clinical Psychology, 4e Catherine Lee
Ebook for; Solutions Manual For; Test Bank for Business Math, 11e Cheryl Cleaves, Jeffrey Noble
Ebook for; Solutions Manual For; Test Bank for Developmental Mathematics, 9e Marvin Bittinger, Judith Beecher
Ebook for; Solutions Manual For; Test Bank for Business Law and the Legal Environment, 2.0 Mayer, Warner, Siedel, Lieberman foo bar baz 
Ebook for; Solutions Manual For; Test Bank for Meteorology Today An Introduction to Weather, Climate, and the Environment, 12e Donald Ahrens
Ebook for; Solutions Manual For; Test Bank for Organizational Behavior Bridging Science and Practice, 3.0 Talya Bauer, Berrin Erdogan
Ebook for; Solutions Manual For; Test Bank for Architectural Drafting and Design, 7e Alan Jefferis, David Madsen, David Madsen
Ebook for; Test Bank for Life in the Universe, 4e Jeffrey  Bennett, Seth Shostak
Ebook for; Solutions Manual For; Test Bank for Foundations of Astronomy, 14e Michael Seeds, Dana Backman
Ebook for; Solutions Manual For; Test Bank for Foundations of Astronomy, 13e Michael Seeds, Dana Backman
Ebook for; Solutions Manual For; Test Bank for Integrated Science, 7e Bill Tillery, Eldon Enger, Frederick Ross
Ebook for; Solutions Manual For; Differential Equations 2e James  Brannan, William Boyce
Ebook for; Solutions Manual For; Test Bank for Anatomy, Physiology, and Disease An Interactive Journey for Health Professions, 2e Bruce Colbert, Jeff Ankney, Karen Lee
Ebook for; Solutions Manual For; Test Bank for Management A Practical Introduction, 8e Angelo Kinicki, Brian  Williams
Ebook for; Solutions Manual For; Test Bank for Prehospital Emergency Care 11e Joseph Mistovich Keith Karren
Ebook for; Test Bank for Businesss Intelligence and Analytics Systems for Decision Support 10e Ramesh Sharda?
Ebook for; Solutions Manual For Fundamentals of Electrical Circuits, 6e Charles Alexander, Matthew Sadiku
Ebook for; Solutions Manual For Fundamentals of engineering design, 2e Barry Hyman
```

(From spam posted to PyTutor Google group mailing list)

#### Goal
Match and Capture book title, edition, and author(s) 

### Match Spaces Between First and Last Names And Substitute with `_`
Given:

```
Roy Mitchell
Tricia Willis
Veronica Brooks
Jimmy Tucker
Johnnie Stokes
Kristine Day
Teri James
Marcia Moran
Judy Barnett
Nelson Nunez
Cheryl Washington
Dwight Norton
Bob Sandoval
Shelly Meyer
```

#### Goal
Match every name in the list, substituting the space in between first and last name with an underscore (`_`)

### Match Only Numbers Surrounded By `|`
Given:

```
145O2911mS2blzjez3|20555898|640s5b833L182eWlP0
v020Rf6M9g5351p8sy|11947269|06s0v73BCM15128A37
5731iMvwnn5KO47Q6m|38101594|46JE98156u80544LBO
IlA38V3mB9d72DOryS|34151278|R6252r2903yM2c2106
13VVGNF6QD36CG94j6|49926532|08A4fK6m1aM91YTKDO
94Uf03M53z8082nDs9|04914075|z42DhL70YG58074376
8ESiv3H4U94F7Oodpg|69280910|9gCqvbJ84q57u5L76F
T1RB164oG46RfyDm3u|65945168|63u5vy3ues3998S43F
25Sj5Ko67375ER5ZAO|88148946|d1BZI323ElK4bo4av9
```

#### Goal
Match and Capture only numbers between pipes (`|` and `|`)

Result should look like:  
```
20555898
11947269
38101594
...continues...
```

#### Bonus
What if there was no pipes (`|`) surrounding the numbers?
```
cV7B4E9F0405lp6b7S181865969kr9sl3Z586i2K64d2
725Y0nHM4Qsv3u1vF762159744j412162NVN4961AS7Z
47t15n498OQG1329F6534864545uKn82d79733Rz548h
4498UEN5KPj9F55T0G488184603rD57U038KMpL98T5C
l3YI3l29WF5p2vH3MR48780280dt2Ydb9Vbsq6l34C2F
640dKn8147463N1g9V60033183u5WO16qH45jF92U1I3
90DC180I0335lQ9r495600392430Y03H8nn3L62t5Aab
24TPLfTe02bnf5GE6E50819394S4919Q6f8d5C838gNd
```

Can we somehow use the fact that that the thing we care about starts at the 19th character? ie:  

cV7B4E9F0405lp6b7S&#8594;181865969kr9sl3Z586i2K64d2

Can we still Match & Capture `18186596` from the first row, `62159744` from the 2nd, etc? 

### Match Only Subdomains
Given:
```
foo.mydomain.com
mydomain.com
set user settings at user.mydomain.com/settings
signup.mydomain.com
google.com
hello.net
whatever.mydomain.net
what if we're testing.mydomain.com
```

#### Goal
Match only the subdomains of `mydomain.com`, such as `foo` and `testing`, etc.

### Picky 'm' Matching
Given:
```
m is
the .m. filter
is m the 
m is
the 'm filter
the m. filter
the .m filter

the m. bison filter
the i'm filter
the them filter
```
(From https://www.reddit.com/r/regex/comments/f1uovo/a_regex_filter_with_a_bunch_of_different/)

#### Goal
Match and capture only the `m`'s in the first seven lines, but nothing (and certainly not the `m`'s!) in the last 3 lines.

### "Select the Definite Article and the Indefinite Articles"
Given:
> I need to select "The" or "the", "An" or "an", and "A" or "a" in a paragraph, without selecting these letters in the middle of a word.

(From https://www.reddit.com/r/regex/comments/f0m8y0/regex_to_select_the_definite_article_and_the/)

#### Goal
Match and capture `the`, `The`, `an`, `An`, `a` or `A` (don't match if these appear inside other words) in the below:
```
Now is the time.
The quick brown fox had a bad day.
Theodore took a long time.
Theodore took an long time.
Theodore took the long time.
A stitch in time.
An extraordinary day.
The extraordinary day.
```

But not below (`a`, `an`, `the` should not match within `Another`):
```
Another time
Bad syntax the.
Bad syntax a.
Bad syntax an.
Bad syntax the
Bad syntax a
Bad syntax an
```
