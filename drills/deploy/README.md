# Mina
Really fast deployer and server automation tool.

Mina works really fast because it's a deploy Bash script generator. It generates an entire procedure as a Bash script and runs it remotely in the server.

Read more: https://github.com/mina-deploy/mina

## How to config to use it with multi environment?

### Step 1: Install Mina
```ruby
  group :development do
    gem 'mina'
  end
```

### Step 2: Create a config/deploy.rb
In your project, type mina init to create a sample of this file.
```ruby
  $ mina init
  Created config/deploy.rb.
```

### Step 3: Setup your server on AWS

### Step 4: Pre-deployment
Let's open config/deploy.rb and configure the server for both production and staging environment. This is a Rakefile invoked by Rake. We have to configure the server and define tasks that we later invoke using mina.

Open config/deploy.rb
```ruby
  require 'mina/bundler'
  require 'mina/rails'
  require 'mina/git'
  require 'mina/rvm'

  app               = 'your_app_name'
  production_domain = 'production.com'
  staging_domain    = 'staging.com'
  user              = 'ec2-user'
  ruby_version      = 'ruby-2.x.x'
  ruby_gemset       = 'your_app_gemset'

  set :term_mode, nil
  set :shared_paths, ['config/database.yml', 'log']
  set :app, app
  set :repository, "ssh://#{user}@#{domain}/~/git/#{app}.git"
  set :user, user
  set :rvm_path, "/usr/local/rvm/bin/rvm"

  # This task is the environment that is loaded for most commands, such as
  # `mina deploy` or `mina rake`.
  
  task :environment do
    stage = ENV['to']
    case stage
      when 'staging'
        set :branch, 'staging' # Staging uses staging branch
        set :domain, staging_domain
      when 'production'
        set :branch, 'master'  # Production uses master branch
        set :domain, production_domain
      else
        print_error "Please specify a stage. eg. mina deploy to=production"
        exit
    end

    set :rails_env, stage
    set :deploy_to, "/home/#{user}/#{stage}"

    invoke :"rvm:use[#{ruby_version}@#{ruby_gemset}]"
  end

  task :setup => :environment do
    queue! %[mkdir -p "#{deploy_to}/#{shared_path}/log"]
    queue! %[chmod g+rx,u+rwx "#{deploy_to}/#{shared_path}/log"]

    queue! %[mkdir -p "#{deploy_to}/#{shared_path}/config"]
    queue! %[chmod g+rx,u+rwx "#{deploy_to}/#{shared_path}/config"]

    queue! %[touch "#{deploy_to}/#{shared_path}/config/database.yml"]
    queue  %[echo "-----> Be sure to edit '#{deploy_to}/#{shared_path}/config/database.yml'."]
  end

  desc "Deploys the current version to the server."
  task :deploy => :environment do
    deploy do
      invoke :'git:clone'
      invoke :'deploy:link_shared_paths'
      invoke :'bundle:install'
      invoke :'rails:db_migrate'
      invoke :'rails:assets_precompile'
      invoke :'deploy:cleanup'

      to :launch do
        queue "mkdir -p #{deploy_to}/#{current_path}/tmp/"
        queue "touch #{deploy_to}/#{current_path}/tmp/restart.txt"
      end
    end
  end

  task :restart do
    queue "#{settings.nginx_path!} restart"
  end
```

### Step 5: Run 'mina setup'
```ruby  
  $ mina setup to=[your_app_environment]
```

### Step 6: Push code from your local repository to server
```ruby
  $ git remote add [your_environment] ssh://ec2-user@[your_app_domain]/~/git/[your_app_name].git
  $ git push [your_environment] master
```

### Step 7: Deploy!
```ruby
  $ mina deploy to=[your_app_environment]
```