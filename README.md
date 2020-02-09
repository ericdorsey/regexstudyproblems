## Table of Contents
[Match Times or "n/a"](#match-times-or-na)  
[Match Title, Edition, Author](#match-title-edition-author)  

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
(Bonus: Capture each time (ie, `3pm` and `7pm` distinctly))

If `n/a` appears instead of the time range in the quotes, match & capture that instead 

#### Text To Test Against
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
Match and Capture book title, edition, and author(s) 

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

(From: This was needed to adjust a query where names were given in one format, but needed to be input in another)

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
