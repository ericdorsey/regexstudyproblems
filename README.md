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
