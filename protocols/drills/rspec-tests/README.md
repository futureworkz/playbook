# RSpec Tests
Test case is a mandatory requirements in all our projects. 
At the minimum, we require all critical paths of the application to be covered with a test case.

Here's the list of basic testing gems we use:
- gem 'rspec-rails'
- gem 'shoulda'
- gem 'factory_girl_rails'
- gem 'capybara'

We do not use minitests.

## Testing Philosophies
We are classical testers and only use mocking/stubbing/doubles for cases of performances or isolation from external resources.
In short, classical testers use real objects (through factory girl in our case).
Mockist testers use mocking/stubbing/doubles to isolate objects/methods instead of creating them.
We believe that classical testing gives us real feedbacks and enable us to enjoy all the benefits of test cases such as refactoring and being able to sleep at night.

A full rspec should always run fast and a benchmark we can follow is 15 seconds per 100 test cases.
Note that benchmark varies widely with different projects.
The point is that a full rspec should be fast enough that coders won't think twice about running it before deploying the code.

We do not require a 100% test coverage but critical paths of the application MUST be covered by test cases. 
Critical paths are defined as happy path of users and high business value features of the application.

A test case enables us to do refactoring. Refactoring is the path of improvement.
We love refactoring and we actively seek to refactor our code.

## Common Refactoring of Test Cases
We separate setup part of a test case from the expectation part of the test.

```ruby
# Wrong
describe '#calculate_total_amount' do
  it 'returns total amount' do
    cart = FactoryGirl.create(:cart, :with_products)
    expect(cart.calculate_total_amount).to eq 100
  end
end

# Correct 
describe '#calculate_total_amount' do
  let(:cart) { FactoryGirl.create(:cart, :with_products) }

  it 'returns total amount' do
    expect(cart.calculate_total_amount).to eq 100
  end
end
```

We use `describe` for methods or objects and `context` for everything else.
We also use '#' to indicate a method.

```ruby
# Correct usages
describe Product do
end

describe '#calculate_total_amount' do
end

context 'Validation' do
end

# Wrong usages
describe 'Validation' do
end

context Product do
end
```

In complex database structure, the setup of the testing data becomes very unmanageable.
We use factory girl `traits` or lifecycle methods to extract and simplify the data structure.
Read more about using [factory girl](https://github.com/thoughtbot/factory_girl/blob/master/GETTING_STARTED.md)
