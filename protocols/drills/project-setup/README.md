# Drill: Project Setup
This drill is about how we setup a Ruby on Rail project.

Let's assume your project is called `awesome-project`.

## Setup directory
We usually have a `Workspace` folder in our home directory to hold all our projects.

```sh
$ mkdir ~/Workspace/awesome-project
$ cd ~/Workspace/awesome-project
```

Make sure you are in your project directory `~/Workspace/awesome-project` for the rest of this drill.

## Setup RVM
We use [RVM](http://rvm.io/) to manage our ruby dependencies.

```sh
$ echo ruby-2.2.3 > .ruby-version
$ echo awesome-project > .ruby-gemset
$ cd .
```

Please use the latest (or second latest) stable version of Ruby.  
The gemset name is normally chosen as the project name.  
You need to do the last step `cd .` so that RVM will create your gemset.

## Install Rails
```sh
$ gem install rails --no-rdoc --no-ri
$ rails new . -T -d=postgresql
```

The options `-T` and `-d=postgresql` will remove the test folder and set the database to be postgres respectively.

## Edit .gitignore
Add the following git ignore rules in your `.gitignore` file.  
Alternatively, you can add the following in your [global git ignore file](http://devoh.com/blog/2013/01/global-gitignore) so that you don't have to do again for each project.

```
# Ignore mac stupid DS_Store
*.DS_Store

# Ignore Rubymine if you use Rubymine
/.idea

# Ignore VIM swp files if you use VIM
*.swp
*.swo
```

## Install RSpec and gems
We use rspec for our test cases (not minitest) so let's install that right away.

```ruby
# Gemfile
group :development, :test do
  gem 'rspec-rails'         # Rails testing
  gem 'shoulda'             # rspec model testing
  gem 'factory_girl_rails'  # Generate fixtures for testing
  gem 'capybara'            # Feature testing

  gem 'better_errors'       # Display a better error page on development webpage
  gem 'binding_of_caller'   # Required by better_errors gem
  gem 'awesome_print'       # Pretty prints Ruby objects for inspection
end
```

After bundle, you need to run `rails generate rspec:install` for rspec gem.  
You also need to add `require 'capybara/rails'` to your `/spec/rails_helper.rb`.

## Setup Git
We use [Gitlab](http://gitlab.com) as a remote repository to store our code.  
We have Futureworkz group in Gitlab and all projects should be parked under the Futureworkz namespace.  
Please approach the system administrator to create and get the respository url.

```sh
git init .
git add .
git commit -m "Inital Commit"
git remote add origin <respository_url>
git push origin master
```

## Further good practices
- Set your timezone explicity in `config/application.rb` eg. `config.time_zone = 'Singapore'`

## How to practise this drill?
Setup 3 different projects or more. You should be familiar with command line, RVM and bundling the default gems.
