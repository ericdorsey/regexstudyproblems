### Match Times or "n/a"
> Beginner regex question, example within
> I have the text:

```
"openingHoursMonday";s:9:"3pm - 7pm"
```
> and want to match the 3pm - 7pm portion only. 
> In other cases, this portion would be marked as "n/a" and I would want to match that instead. 

(From https://www.reddit.com/r/regex/comments/f0i29z/beginner_regex_question_example_within/)

#### Goal
* Match and capture `3pm - 7pm`, allowing for other times too, like `10am - 2pm`
  * Bonus: Capture each time (ie, `3pm` and `7pm` distinctly)
* If `n/a` appears instead of the time range in the quotes, match & capture that instead 

#### Example Match Text
```
"openingHoursMonday";s:9:"3pm - 7pm"
"openingHoursMonday";s:9:"n/a"
"openingHoursMonday";s:9:"10am - 2pm"
"openingHoursMonday";s:9:"9pm - 3am"
```

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
* Match and capture book title, edition, and author(s) 

### Match Spaces And Substitute with `_`
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
* Match every name in the list, substituting the space in between first and last with a `_`

### Match Only Numbers Surrounded by `|`
Given:
```
178r48173yj1mt0n8w|72501851|ccz4n77oja856r0nq7
98stcdd224p180b6r6|90545377|6k3224v77d7edwkmjp
1n696w31qi86417l9e|22578129|57d7n3y98we2v028ki
z0h5vegk2atg29994m|48238338|v01id6yjme45sgfy4b
bp759sly5wy59256r1|55426475|5212qymse487aw1l75
854osj4eu455e3n585|27080295|2j87yn55br0wjt9d1k
725j62068a33ucst13|63057682|9uyze6lor531c2u975
jr27yh6s27608453s6|60882646|b117t2f47pz80p8554
82f44o2c9cg1iuowc0|96469770|w6cyj3ii972kdw4310
60y17gz39voty4j4ev|79845428|lreudgs0dzww2a48r7
has34yfij675u73w00|28311720|4pgp3334t5v4d37g4d
w9am0umj8tcar86121|32788422|5q495wg4l4g5l4rsa6
f1w9fsqoo7zf6g63tk|37087961|z8ibf0vaevyv070l61
```

#### Goal
* Match and capture only numbers between `|`, so in line 1 get only `72501851` in entire text
