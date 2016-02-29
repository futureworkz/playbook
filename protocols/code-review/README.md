# Code Review Practice
This protocol states how we do code review in Futureworkz.

## Code Review System
Every coder must have another coder to review his code. This ensures high quality on the code deployed to production and also maximise learning for the coder and the reviewer.

To know your assigned coder to review your code, please ask James.

## What to Review
We code review everything including bug fixes, HTML/CSS/JS and of course, feature development.

The code review should be done before the code is pushed to staging or production.

## Code Review Steps
- Coder write new code on a new feature branch based off master
- Coder push feature branch to Gitlab.com and open a merge request
- Reviewer review/refactor code with coder
- Reviewer comment 👍  and merge the request
- Coder refactor code
- Coder can ask for second review or push to staging

## Review Standard
The minimum standard we based on to review the code are:

###Test driven development
We don’t have test case for everything but we definitely have test cases to cover critical parts of the application. Test cases ensure that our app is working and without bugs whenever we introduce new features into it. Test cases also gives us the affordance to refactor and improve our code quality. With refactoring, we learn better coding practices and improve ourselves as a coder.

### Don’t Repeat Yourself (DRY)
We remove any duplications in our code, files and any other relevant stuff. Duplication is a consequence of lazy and untidy coding style. It is a mark of messy mind. We should be disciplined to refactor our code to remove duplications so as to ensure that our code is clean and easy to read.

Common DRY violations are:
- Un-needed files and folders created from generators eg. `/test` folder
- Using `resources :products` but only use a single route: `/products/index`

### Naming Reveals Intention
Ruby is an amazingly expressive programming language. We avoid using comments in our code and instead, let our code be clear enough to express what it does. Ruby allows us to do this and we should make full use of it. We put deliberation into the naming of our variables, classes, files, methods, etc so that it expresses what it does clearly. This distills our intention in our code and create better quality code.

### Single Responsibility Principle
Every class and method should only do one thing. We should not lump every logic and responsibility into a God class or a super method. This makes code difficult to understand and hard to change.

### Others
This is never meant to be an exhaustive list. Code quality is a life-long pursue. We strive to learn more about refactoring, design patterns and workflows to improve our skills.

## Dos & Don'ts of Code Review
- Review the code, don't review the coder
- Check for correctness of code, not how you would do it
- Discuss possibilities & trade-offs, not what's right & what's wrong
- Try not to go into lengthy discussion and keep code review to less than 30 minutes
- Code makes the final decision to change the code unless it is a security concern
- For style guide, you can refer to [Rails style guide](https://github.com/bbatsov/rails-style-guide)
