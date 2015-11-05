# Rails Model
We require our coding standard to follow SRP (Single Responsibility Principle). Therefore, it is very important to understand the responsibility of a model - what a model should do and what a model should not do.

In the architecture of MVC, model plays the role of business logic and data management. 
The primary responsibility of model is to provide the data management which are data access and data validation. 
The secondary responsibility of the model is to provide additional methods that encapsulate the business logic of the app and also acts as an extension of the data that is required by other objects.

## Data Access
Following Rails convention, we use ActiveRecord for our model. 
ActiveRecord pattern provides all the necessary CRUD access of a model. 
Read about the [ActiveRecord basics](http://guides.rubyonrails.org/active_record_basics.html).

You must also be familiar with query interface of ActiveRecord in order to be effective in accessing data.
Understanding how to extract complex queries or common queries into scoped methods is good in keeping code DRY and reveals good intention.
Read about the [ActiveRecord query interface](http://guides.rubyonrails.org/active_record_querying.html).

## Validation
Validation is a very important responsibility of a model. 
Know all the common [ActiveRecord validations](http://guides.rubyonrails.org/active_record_validations.html).

Read about [ActiveRecord Association](http://guides.rubyonrails.org/association_basics.html) to understand how to setup associations between models.

Note that it is very important to validate association too, not just data.

## Business Logic
Model also provide methods for other object to access the data that must be restricted by the application business rules and logic.

## Common Refactoring of Models
We generally keep to the 'skinny controllers, fat models' thinking.
However, making our models too fat results in unreadable code.

Business logic in model can be encapsulated in [ActiveRecord callbacks](Active Record Callbacks).
Alternatively, we can use [ActiveRecord Observer](https://github.com/rails/rails-observers) to better separate the logic.

We also use [ActiveSupport concerns](http://api.rubyonrails.org/classes/ActiveSupport/Concern.html) to extract methods into concerns.

Multiple associations usually leads to code smell that violate [law of demeter](https://en.wikipedia.org/wiki/Law_of_Demeter). 
We can use [delegate](http://samurails.com/tutorial/rails-delegate-dont-break-the-law-of-demeter/) to prevent such code smell.

## Testing Models
We use the [gem shoulda](https://github.com/thoughtbot/shoulda) to test our models validation rules.

We *ALWAYS* write test cases for *model validations AND associations* as this provides basic test coverage and uses test cases as a specification to determine how our models work.
For example, when we run `rspec -f d`, the test results will display clearly how the models function and related to each other.

Furthermore, we highly recommend that any custom methods in the model to be covered with a test case. 
Model testing is one of the easiest and it provides the most fundamental protection to your code base.

## Exercises
TODO
