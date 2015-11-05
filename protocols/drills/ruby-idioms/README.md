# Ruby Idioms
This is a collection Ruby idioms that we adopted in our coding style.
This is the style in which Futureworkz recommends for greater readability between coders.

## No use of while or for loop or loops of any kinds
We highly discourage usage of loops.
Instead we prefer block iterator methods.

```ruby
products = Products.all
products.each do |product|
  puts product.title
end
```
