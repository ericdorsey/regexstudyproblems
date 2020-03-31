## Table of Contents
[Match Times or "n/a"](#match-times-or-na)  
[Match Title, Edition, Author](#match-title-edition-author)  
[Match Spaces Between First and Last Names And Substitute with `_`](#match-spaces-between-first-and-last-names-and-substitute-with-_)  
[Match Only Numbers Surrounded By |](#match-only-numbers-surrounded-by-)  
[Match Only Subdomains](#match-only-subdomains)  
[Picky `m` Matching](#picky-m-matching)  
["Select the Definite Article and the Indefinite Articles"](#select-the-definite-article-and-the-indefinite-articles)  
[Fix Your Boss\'s Ugly Notes](#fix-your-bosss-ugly-notes)  
[Number With Upper Limit and Optional Decimal](#number-with-upper-limit-and-optional-decimal)  
[Grab The Font Family Name From A URL](#grab-the-font-family-name-from-a-url)  
[Regex Pattern To Account For All The Options In A Config File](#regex-pattern-to-account-for-all-the-options-in-a-config-file)  
[Match Certain c's and v's Followed by Numbers](#match-certain-cs-and-vs-followed-by-numbers)  
[Match Letters With Spaces](#match-letters-with-spaces)  
[Remove Everything After The Second Colon](#remove-everything-after-the-second-colon)  
[Capture Price And Vendor](#capture-price-and-vendor)  
[Match Full Path Up To, But Not After, Final ](#match-full-path-up-to-but-not-after-final-&#47;)  

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
Ebook for; Solutions Manual For; Test Bank for Business Law and the Legal Environment, 2.0 Mayer, Warner, Siedel, Lieberman 
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
Ebook for; Test Bank for Businesss Intelligence and Analytics Systems for Decision Support 10e Ramesh Sharda
Ebook for; Solutions Manual For Fundamentals of Electrical Circuits, 6e Charles Alexander, Matthew Sadiku
Ebook for; Solutions Manual For Fundamentals of engineering design, 2e Barry Hyman
```

(From spam posted to PyTutor Google group mailing list)

#### Goal
Match and Capture book title, edition, and author(s) 

#### Bonus
Match this extra text, which also introduces digits into titles

```
Ebook for; Solutions Manual For; Test Bank for Principles of Macroeconomics, 6e Robert  Frank, Ben  Bernanke, Kate Antonovics, Ori Heffetz
Ebook for; Solutions Manual For; Test Bank for Principles of Macroeconomics, 7e Robert  Frank, Ben  Bernanke, Kate Antonovics, Ori Heffetz
Ebook for; Solutions Manual For; Test Bank for Sociology, 17e John  Macionis
Ebook for; Solutions Manual For; Test Bank for Technology In Action Complete, 15e Alan Evans, Kendall Martin, Jonathan Weyers, Mary Anne Poatsy
Ebook for; Solutions Manual For; Test Bank for Accounting What the Numbers Mean , 12e David Marshall, Wayne McManus, Daniel Viele
Ebook for; Solutions Manual For; Test Bank for Advanced Accounting 4e Robert Halsey Patrick Hopkins
Ebook for; Solutions Manual For; Test Bank for Technology In Action Complete, 16e Alan Evans, Kendall Martin, Jonathan Weyers, Mary Anne Poatsy
Ebook for; Solutions Manual For; Test Bank for The World of Psychology, 8th Canadian Edition, DSM-5 Update Edition, 8e Samuel  Wood, Ellen Green Wood, Denise Boyd, Eileen Wood, Serge Desmarais
Ebook for; Test Bank for Canada's Politics, Democracy, Diversity and Good Government, 3e Eric Mintz, Livianna Tossutti, Christopher Dunn
Ebook for; Solutions Manual For Biology Laboratory Manual, 12e Darrell  Vodopich, Moore
Ebook for; Solutions Manual For; Test Bank for Consumer Behavior Buying, Having, and Being, 12e Michael Solomon
Ebook for; Solutions Manual For; Test Bank for Criminal Behavior A Psychological Approach, 11e Curt Bartol, Anne Bartol
Ebook for; Solutions Manual For; Test Bank for Using Sage 50 Accounting 2018 by Mary Purbhoo
Ebook for; Solutions Manual For; Test Bank for Biochemistry, 1e Roger Miesfeld, Megan McEvoy
Ebook for; Solutions Manual For; Test Bank for Principles of Animal Behavior, 3e Lee Alan Dugatkin
Ebook for; Solutions Manual For; Test Bank for Sociology in Action A Canadian Perspective, 2e Diane Symbaluk, Tami Bereska
Ebook for; Solutions Manual For; Test Bank for Principles of Marketing, 17e, Philip Kotler, Gary Armstrong
Ebook for; Solutions Manual For; Test Bank for Horngren's Financial & Managerial Accounting, The Managerial Chapters, 6e Tracie  Nobles Brenda  Mattison Ella Mae Matsumura
Ebook for; Solutions Manual For Introduction to Sports Medicine and Athletic Training, 2e Robert France
Ebook for; Solutions Manual For; Test Bank for Sociology in Action A Canadian Perspective, 3e Diane Symbaluk, Tami Bereska
Ebook for; Solutions Manual For; Test Bank for Financial Accounting and Reporting, A Global Perspective, 5e Hervé Stolowy, Michel  Lebas, Yuan Ding
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
Ebook for; Solutions Manual For; Test Bank for Looking Out, Looking In, 15e Ronald  Adler, Russell  Proctor
Ebook for; Solutions Manual For; Test Bank for Economics, 13e Roger A. Arnold
Ebook for; Solutions Manual For; Test Bank for Economics for Today, 10e Irvin B. Tucker
Ebook for; Solutions Manual For Physics for Scientists and Engineers with Modern Physics, Technology Update 9e Raymond  Serway, John Jewett
Ebook for; Solutions Manual For; Test Bank for Mass Media Law, 20e Clay Calvert, Dan Kozlowski
Ebook for; Solutions Manual For; Test Bank for Strategic Management Concepts and Cases, 2e Dyer, Godfrey, Jensen, Bryce
Ebook for; Test Bank for Child Psychology A Canadian Perspective, 3e Alastair Younger, Scott Adler, Ross Vas
Ebook for; Solutions Manual For Electrochemical Engineering, 1e Thomas Fuller
Ebook for; Solutions Manual For; Test Bank for Corporate Finance, 4th Canadian Edition, 4e Jonathan Berk, Peter DeMarzo, David Stangeland
Ebook for; Solutions Manual For; Test Bank for College Accounting, Chapters 1-27, 23e James Heintz, Robert Parry
Ebook for; Solutions Manual For; Test Bank for Corporate Finance, 4e Jonathan Berk, Peter DeMarzo
```

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

### Fix Your Boss's Ugly Notes
Your boss comes to you with some monthly bills tracking they've been doing in `Notepad.exe`. But the problem is your boss has 
been really inconsistent with the formatting! Your boss said they sometimes added a `*` to some entries, but they don't remember
why, so it's safe to just get rid of that. Also, your boss wasn't very consistent with format, sometimes using `mo.`, or a `/`
instead of a space between the dollar amount and month. And sometimes the exact amount including cents isn't there, just the 
dollar amount. They want each dollar & cents amount printed out, followed by a comma, folowed by "monthly", followed by a comma, 
then "for {purpose}". 

Can you help clean this up? 

```
$65.37 mo. Internet
*$114 month Phone
$10 mo Netflix
$750/mon. Mortgage
*$8.40/month Spotify
```

#### Goal
```
$65.37, monthly, for Internet
$114, monthly, for Phone
$10, monthly, for Netflix
$750, monthly, for Mortgage
$8.40, monthly, for Spotify
```

### Number With Upper Limit and Optional Decimal
> i am new to regex and need help in trying to achieve this. we have number input from user in the range of 0 to 120 with 1 decimal value. so user can enter 0,10,10.5,10.7,100.8,120 But the max value should be 120 and only one decimal allowed. can some of the experts help?

#### Goal
These should match:
```
0
75.2
120
120.0
119
117
85.7
92
1
22
```

These should not:
```
119.9827492749
92.50779
120.00000
121
120.248957
120.7
120.1
50.378
```

(From: https://www.reddit.com/r/regex/comments/f3wmkn/regex_number_with_one_decimal_help/)

### Grab The Font Family Name From A URL
Given:

> The regex should extract everything between ...family=<what I want>

```
https://fonts.googleapis.com/css?family=Roboto+Condensed:300,300i,400,400i,700,700i&display=swap

https://fonts.googleapis.com/css?family=Roboto+Condensed+word:300,300i,400,400i,700,700i&display=swap

https://fonts.googleapis.com/css?family=Roboto+Condensed&display=swap

what if it's in the middle https://fonts.googleapis.com/css?family=Roboto+Condensed of some other text, though? 

https://fonts.googleapis.com/css?family=Roboto&display=swap

What if the font is in the middle of other text and has more parts to it https://fonts.googleapis.com/css?family=Roboto+Condensed+Radical+Hurray and still followed by some other text?

https://fonts.googleapis.com/css?family=Roboto+Rad+Okay+Zoom+Derp+Test+Okay+Eight+Starbucks+Bold&display=swap
```

#### Goal

Match & Capture only the Font names from the HTML above, the `Font+Plus+Parts`, ie:

```
Roboto+Condensed
Roboto+Condensed+word
Roboto
Roboto+Condensed+Radical+Hurray
Roboto+Rad+Okay+Zoom+Derp+Test+Okay+Eight+Starbucks+Bold
```

etc.

(From: https://www.reddit.com/r/regex/comments/f4qi4n/please_can_someone_fix_my_regex/)

### Regex Pattern To Account For All The Options In A Config File
Given:

> Using Python 3.7, I'm writing a script to parse out options from a config file

```
# a_commented_out_option_with_no_value =
an_enabled_binary_option = false
an_enabled_binary_option = "true"
# a_commented_out_binary_option = true
an_integer_option = 1
a_decimal_option = 1.1
a_string_option = "with-quotes"
another_string_option = withoutquotes
a_path_option = "/path/to/file1.txt"
a_really_really_really_really_long_option = "sigh"
```

#### Goal
Match and capture both the configuration option, and configuration value from the text above (but don't capture quotes (`"`) if present in the config values).

Example desired match / capture output from above (note that in the first config option, `a_commented_out_option_with_no_value`, there is no config value to be captured, so only capture the config option itself in this case):

```
a_commented_out_option_with_no_value 
an_enabled_binary_option false
an_enabled_binary_option true
a_commented_out_binary_option true
an_integer_option 1
a_decimal_option 1.1
a_string_option with-quotes
another_string_option withoutquotes
a_path_option /path/to/file1.txt
a_really_really_really_really_long_option sigh
```

(From: https://www.reddit.com/r/regex/comments/f7joy2/trying_to_find_a_regex_pattern_or_patterns_to/)


### Match Certain c's and v's Followed by Numbers

> Need a regex in python to match c/v or both and a number between 1-5 but im struggling a little.

Given:

Examples of matching strings:

```
c1
c4
v2
v5
cv3
vc5
```


Examples of non matching strings:

```
vv3
cc2
vvc2
cv
c
v
cv9
vc8
v8
c6
```

#### Goal
Match and capture `c` followed by a digit in the range of 1 through 5, or `v` followed by a digit in the range of 1 through 5, or `cv` or `vc` followed by a digit in the range of 1 through 5. Don't match if preceded by an extra `c` or `v`, and don't match if 

(use examples of matching and non matching above)

(From: https://www.reddit.com/r/regex/comments/fd7i20/basic_python_matching_regex_help/)

### Match Letters With Spaces

> Letters with spaces
> I know its quite easy stuff but I dont work with regex much. Say I want something like "e e e e e" to be caught by the rule, how would I do it? "e e e" and " e e e e e e e e " could get caught in the rule aswell.

Examples of matching strings:

```
e e e e e
e e e
b b b
e e e e e e e e
a a a
z z z
```

Examples of non matching strings:

```
eeeeeeeeeeeeeeee
ee
eeeeeeeee
```

#### Goal
Match and capture the matching strings above, but not the non matching strings.

(From: https://www.reddit.com/r/regex/comments/fpca5k/letters_with_spaces/)

### Remove Everything After The Second Colon

Given 

> I want to remove everything after the second colon

```
test:test@test.com:0.00sfs000:0.035r000:0.035rtg00
```

#### Goal
Match and capture `test:test@test.com` from the above example data

(From: https://www.reddit.com/r/regex/comments/foes77/remove_everything_after_second_colon_help/)


### Capture Price And Vendor 

Given 

```
Your credit card purchase for $15.99 at NETFLIX.COM was approved.
Your credit card purchase for $5.03 at FOO.NET was approved.
Your 
```

#### Goal
Match and capture the price and vendor in the above lines (ie, $15.99 and "NETFLIX.COM" from the first line)

(From: https://www.reddit.com/r/regex/comments/fr8jlr/trying_to_remove_everything_except_price_1599_and/)

### Match Full Path Up To, But Not After, Final `/`

Given 
```
/path/to/directory/is/3xtre3ml3y/l0ng/it/w0n/t/st0o/p/all/the/time
/path/to/l0ng/it/direct0ry/w0n/t/st0o/p/all/the/-279
/path/to/directory/is/3xtre3ml3y/l0ng/it/w0n/t/st0p/a/even/longer/path/?foo
/short/one/barbaz
```

#### Goal
Match and capture up until the last `/`, but nothing after it. 

For example, in line one, match and capture `/path/to/directory/is/3xtre3ml3y/l0ng/it/w0n/t/st0o/p/all/the/`

(From: https://www.reddit.com/r/regex/comments/fpk97s/pulling_directory_path_it_trails_on_some_paths/)
