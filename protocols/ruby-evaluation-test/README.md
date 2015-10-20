# Ruby Evaluation Test

We conduct frequent evaluation tests to ensure the standard of our coder. The test is aimed to be completed in 4 hours and covers both frontend and backend development. Generally, the test will be to build single-serving website which is both fun and satisfying.

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

## Coder Rank
A coder's rank is the lowest grade of the last two evaluation tests.

> Example:  
> A coder received a C and B in the last two tests.  
> The coder rank is C.

## Re-Evaluation Cycle
The next evaluation test for the coder will be based on the coder's rank.

Rank | Re-evaluation Cycle
-----|------------------------------
A    | 6 months
B    | 2 months
C    | 2 weeks | Not more than 6 RET
D    | 2 weeks | Not more than 2 RET
E    | Immediate

## Termination
Futureworkz will only keep rank A and B coders.

Rank C coders who did not improve to rank B after 6 tests will be considered for termination.  
Rank D coders who did not improve to rank C after 2 tests will be considered for termination.  
Rank E coders will be considered for termination immediately.
