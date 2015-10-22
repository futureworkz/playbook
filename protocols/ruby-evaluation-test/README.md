# Ruby Evaluation Test
We conduct frequent evaluation tests to ensure the standard of our coder. The test is aimed to be completed in 4 hours and covers both frontend and backend development. Generally, the test will be to build single-serving website which is both fun and satisfying.

We generally do the evaluation on a non-working day (eg. Saturday) so that it does not impact client projects. Coder who cannot finish in 4 hours will continue on the project until he finish the basic requirements. This is to ensure that the tester has enough code to evaluate the coder's work.

## Rules
Coder will be given a project to code and the code will be the basis of evaluation. Coder is expected to follow the rules below:

- 4 hours to finish
- You can ask any question to the tester anytime
- Can use Internet and any of your previous codes
- No remote git - No copying others - No discussion
- Work like you will continue the project for another 10 sprints

## Submission of work
After you have finished your work, please submit it as followed:
- Deploy to Heroku as `<project-name>-<your-name>.herokuapp.com`
- Give tester collaborator access to your Heroku
- Push all commits on the master branch only

Tester will draw your git commits to evaluate your code and also test your app on Heroku.

## Evaluation Criterion
Coder must finished at least 50% of the requirements to be given a pass.  
Evaluation will be based on speed, code quality (using our [code review standard](../code-review/README.md)) and critical thinking.  
Grading is pessimistic - You will not get an A unless you clearly show you are an A. Some signs of an A is not enough.  

The general grading is such that  

Grade | What it means
------|------------------------
A     | Above our standard  
B     | Met our standard
C     | Not good enough
D     | This is seriously not good
E     | Why did we hire you?


The evaluation form for a coder is as below:
```
Name:
Date of Evaluation:

Completeness of project (%):
Bonus completeness (%):
Overall Grade:

Git Commits
A – Great commit messages and structure
B – Good commit messages and structure
C – Okay commit messages and structure
D – Poor commit messages and strucuture
E – No use of git

Test Coverage
A – Critical paths are covered
B – Some critical paths are covered
C – Few critical paths are covered
D – Little or no test cases
E – No test cases!!!

Ruby on Rails
A – Above minimum standard
B – Met all minimum standard
C – Met some minimum standard
D – Fail to meet minimum standard
E – Disappointing standard

HTML
A – Well-structured and easy to read
B – Readable and some structure
C – Hard to read but can still understand
D – Messy and very difficult to read
E – Impossible to read and understand

CSS
A – Well-structured and easy to read
B – Readable and some structure
C – Hard to read but can still understand
D – Messy and very difficult to read
E – Impossible to read and understand

Javascript
A – Well-structured and easy to read
B – Readable and some structure
C – Hard to read but can still understand
D – Messy and very difficult to read
E – Impossible to read and understand

Difficulties faced by candidate:

Comments by tester:
```

## Test Result
Based on the evaluation result, we will grade 3 aspects of the coder's skills - speed, code quality, critical thinking.

*Speed* is how fast the coder can finish a task. This is determined by the experience and typing speed of the coder. A good coder should be fast in his work especially when the task given is not complex. Client should not be paying us for slow work.

*Code quality* is how maintainable the code is. A maintainable code is readable and easy to understand. It follows coding convention in naming, structure and patterns. It must have test cases. Good code quality ensures that the app can be extended, scale or maintain.

*Critical thinking* is how well the code solves the problem. We look for potential issues that the code will cause such as N+1 queries, damaging performance issues, wrong solution to the problem, etc. A solution should not create other problems.

The test result of a coder is the lowest grade of 3 aspects.

> Example:  
> A coder is graded B for speed, B for code quality and C for critical thinking.  
> The coder test result is C.

The grading basis for the 3 aspects are as below:

```
Speed
A – Above 10 points a week
B – Around 10 points a week
C – Around 5-8 points a week
D – Less than 5 points a week
E – Why did we hire you again?

Code Quality
A – Above minimum standard
B – Met all minimum standard
C – Met some minimum standard
D – Fail to meet minimum standard
E – Disappointing standard

Critical Thinking
A – Solved the problem exceptionally well
B – Solved the problem well
C – Workable solution but not ideal
D – Solution is not workable
E – Is this even a solution?
```

## Coder Rank
A coder's rank is the lowest grade of the last two evaluation tests.

> Example:  
> A coder received a C and B in the last two tests.  
> The coder rank is C.

## Re-Evaluation Cycle
The next evaluation test for the coder will be based on the coder's rank.

Rank | Re-evaluation Cycle
-----|------------------------------
A    | Once every 6 months
B    | Once every 2 months
C    | Once every 2 weeks
D    | Once every 2 weeks
E    | Immediate

## Termination
Futureworkz will only keep rank A and B coders.

Rank C coders who did not improve to rank B after 6 tests will be considered for termination.  
Rank D coders who did not improve to rank C after 2 tests will be considered for termination.  
Rank E coders will be considered for termination immediately.

## Passing the Test
Futureworkz wants as many coders to pass the test as possible without affecting the integrity of the test. Here's a compiled list of tips to assist you to improve your test results:

### Typing Speed
If you type very slowly, there is no way you can code fast. Not convinced? Read this: [We Are Typists First, Programmers Second](http://blog.codinghorror.com/we-are-typists-first-programmers-second/)

The speed of typing is determined by words per minute (WPM).  
For a coder, your typing speed should be at least 40 WPM.  
Great coders generally clock more than 60 WPM.  
You should strive to at least reach 50 WPM.

#### Touch Typing
To start typing fast, make sure you know the fundamentals of touch typing. Touch typing is being able to type without looking at your keyboard. See wikipedia definition: https://en.wikipedia.org/wiki/Touch_typing

Next, you can learn touch typing at http://www.ratatype.com/  

You know you can touch type (even though at a very low WPM) when you can type with all 10 fingers and you do not look at the keyboard at all when you type.

#### Practice, Practice, Practice
Once you know how to touch type, set aside 10 minutes every morning or evening to practise. You will be amazed how fast you will improve in just one month! 

Here's a list of websites you can use to practise:

Website | Link | Description
--------|------|------------
Type Racer | http://play.typeracer.com/ | Simple fun website to test your typing against other players
Key Hero   | http://www.keyhero.com/    | Another site like Type Racer
Typing.io  | http://typing.io           | Typing test is based on real codes! Please note that your WPM will drop as real code has more special characters than normal English text

### Keyboard Productivity
Beyond typing fast, knowing a lot of keyboard shortcuts dramatically improves your coding speed. Train yourself to use important keyboard shortcuts until it becomes muscle memory.

Here's a list of essential keyboard shortcuts in Mac:

Environment    | Keys                 | Description
---------------|----------------------|----------------------------------
Mac            |`CMD` + `space`       | Display spotlight
Mac            |`CMD` + `tab`         | Jump to next app
Mac            |`CMD` + `n`           | New window/file in most app
Browser        |`CMD` + `t`           | Open a new tab
Browser        |`CMD` + `r`           | Reloads the page
Browser        |`backspace`           | Go back to previous page
Browser        |`Ctrl` + `tab`        | Go to next tab
Text           |`CMD` + `Z`           | Undo last operation 
Text           |`CMD` + `Y`           | Redo last operation
Text           |`CMD` + `O`           | Open file 
Text           |`CMD` + `S`           | Save 
Text           |`CMD` + `W`           | Close active window or file
Text           |`CMD` + `Q`           | Quit application
Text           |`CMD` + `A`           | Select all in active window; e.g., select all text on page
Text           |`CMD` + `X`           | Cut to clipboard
Text           |`CMD` + `C`           | Copy
Text           |`CMD` + `V`           | Paste
Text           |`CMD` + `F`           | Find
Text           |`CMD` + `Shift` + `right` | Select until end of line
Text           |`CMD` + `Shift` + `left`  | Select until beginning of line 
Text           |`CMD` + `up`          | Move cursor to top/start of document
Text           |`CMD` + `down`        | Move cursor to bottom/end of document

You should have a habit of finding keyboard shortcuts in the common things that you do and train yourself to use it. This way, you will become faster over time.

### Cheatsheets
There are many things which you will perform over and over again in every test and in every project. Create your own cheatsheet helps you to reference the information you need quickly.

When you write your own cheatsheet, you help yourself to remember that exact information better. Furthermore, you will find that information faster when you need it (because you wrote it!)

You can create your own cheatsheet using pen and paper/book or using online websites like [Github Gists](https://gist.github.com/), [GistBoxApp](http://www.gistboxapp.com), [Trello](http://www.trello.com), etc.

A list of common things to create a cheatsheet for:
- Command line commands
- Common RSpec code for model/controller/etc
- Project setup
- ActiveRecord validation
- Common Rails methods such as view helpers, routes, etc

### Practice on Previous Test Again
You can redo your previous test from scratch again. This way, you will get to practice every thing again. The more time you do it, the faster you will become. You also memorize the fundamentals very quickly.

### Drills
- Drills
-- project setup (RVM)
-- migration + db seed
-- model + rspec
-- controller + rspec
-- view + capybara
-- HTML
-- CSS
-- JS (graceful degradation)
-- git commits
