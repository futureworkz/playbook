# Rails View
View is the frontend of the application.
The main responsibilty of view is presentation and it is concerned primarily with HTML, CSS and Javascript.
There should not have any business logic in the view.

## Rails Layouts and Views
We follow Rails convention in structuring the view files.
For example, `/controllers/ProductsController#new` will have a view file at `/views/products/new.html.slim`.

Read about [Rails layout and views](http://guides.rubyonrails.org/layouts_and_rendering.html).

## Common Refactoring of Views
Any business logic in views should be extracted away from views into controllers or models or others.
Business logic in views is a straight violation of basic MVC Single Responsibility Principle.

Presentation logic (eg. `.user_full_name = "Name: #{@user.first_name} #{@user.last_name} `) should be extracted to view helpers.
Read using about [Rails view helpers](http://mixandgo.com/blog/the-beginner-s-guide-to-rails-helpers).

Reusable chunks of HTML elements should be extracted into a partial.
When extracted into a partial, we view the partial as a completed self-containing reusable component.
This means that the CSS files and Javascript files associated with this partial should be isolated and work with the partial.
Read about [Rails partials](http://guides.rubyonrails.org/layouts_and_rendering.html#using-partials)
Understand more about our [HTML drill](../html-standard/README.md), [CSS drill](../css-standard/README.md) and [Javascript drill](../javascript-standard/README.md).
