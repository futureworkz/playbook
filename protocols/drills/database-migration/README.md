# Database Migration
Every app requires a database. Data in database can sometimes be more important than the app itself. For example, a million dollar marketing campaign captured one million users in the app.

## Database of Choice
Futureworkz uses PostgreSQL as the default database for every project unless client specified a different database.

## Rails Migration
All database schema changes are done through rails migration and only through rails migration. This ensure that the database schema is tracked in git and duplicable to other developers or environments.

You must understand clearly and fully Rails migration at: http://guides.rubyonrails.org/active_record_migrations.html

Try doing the exercises to practice your rails migration.

## Rake db:seed
We use `db/seeds.rb` to store data that is needed for production or development. We avoid inputting data manually through a database tool (eg. PHPMyAdmin or `rails console`) for two reasons:
- the next coder will have to re-enter the data in order to start working on the app
- when launching to a new environment (eg. staging or production), the data has to be re-entered again

Examples of production data are default categories of products, admin accounts, initial (small) set of products, etc. This is the basic data that is needed for the app to function properly when launched.

Examples of development data are admin accounts, sample product data, etc. This is mainly for user testing purposes.

If we have production data and development data, we can separate them easily from this [tip](http://dennisreimann.de/blog/seeds-for-different-environments/).

Db seed must be [idempotent](https://en.wikipedia.org/wiki/Idempotence). In simple terms, it means that one can run `rake db:seed` many times but the data is not repeated in the database.

### Making db:seed indempotent
The easiest way is to simply delete all records and then create them again:
```ruby
# db/seeds.rb
Product.destroy_all
Category.destroy_all

book_category = Category.create!(title: 'Books')
stationary_category = Category.create!(title: 'Stationary')
Product.create!(title: 'Ruby book', price: 12.99, category: book_category)
Product.create!(title: 'Pen', price: 2.99, category: stationary_category)
```

Obviously, the above approach will not work if there are other data especially in production environment.

Futureworkz's recommended practise is to [`first_or_create`](http://apidock.com/rails/ActiveRecord/Relation/first_or_create):
```ruby
# db/seeds.rb
Product.destroy_all
Category.destroy_all

book_category = Category.where(title: 'Books').first_or_create!(title: 'Books')
stationary_category = Category.where(title: 'Stationary').first_or_create!(title: 'Stationary')
Product.where(title: 'Ruby book').first_or_create!(title: 'Ruby book', price: 12.99, category: book_category)
Product.where(title: 'Pen').first_or_create!(title: 'Pen', price: 2.99, category: stationary_category)
```
User.where(email: 'super@mysite.com').first_or_create(age: 20, name: 'SuperAdmin', [...])

## Exercises
TODO
