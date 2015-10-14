## Purpose of Deploy.rb
This document for who using Mina gem at https://github.com/mina-deploy/mina

This document describle how to use 1 deploy.rb file for multible environment.

##Install mina gem
Open gem file, add mina gem in development group

    group :development do
      gem 'mina'
    end
    
Then, open terminal, install it

    $ bundle install

After installation is finished, run

    $ mina init
    Created config/deploy.rb.

##Initialize Amazon web services for deploy.
Contact adminstrator to setting up deploy environment on AWS.

#Setting mina for environment
    
    $ mina setup to=your_app_environment

E.g: mina setting for staging environment
    
    $ mina setup to=staging

##Setting common config for both Production environment and Staging environment.
Open config/deploy.rb

    app               = 'your_app_name'
    production_domain = 'your_app_production_domain'
    staging_domain    = 'your_app_staging_domain'
    user              = 'ec2-user'
    ruby_version      = 'your_app_ruby_version'
    ruby_gemset       = 'your_app_gemset'

    set :term_mode, nil
    set :shared_paths, ['config/database.yml', 'log']
    set :app, app
    set :repository, "ssh://#{user}@#{domain}/~/git/#{app}.git"
    set :user, user
    set :rvm_path, "/usr/local/rvm/bin/rvm"

##Setting individual config for each environment

    stage = ENV['to'] || 'staging'
    case stage
      when 'staging'
        set :branch, 'master'
        set :domain, staging_domain
      when 'production'
        set :branch, 'master'
        set :domain, production_domain
      else
        print_error "Please specify a stage. eg. mina deploy to=production"
        exit
    end

    set :rails_env, stage
    set :deploy_to, "/home/#{user}/#{stage}"

    invoke :"rvm:use[#{ruby_version}@#{ruby_gemset}]"

##Push code to server
After finish config, push your code to staging

    $ git remote add your_environment ssh://ec2-user@[your_app_domain]/~/git/[your_app_name].git
    $ git push your_environment master

E.g:

For staging environment

    $ git remote add staging ssh://ec2-user@[your_app_domain]/~/git/[your_app_name].git
    $ git push staging master


#Finish deploy

    $ mina deploy to=your_app_environment

E.g: mina deploy for staging environment
    
    $ mina deploy to=staging

##Full mina deploy script

    require 'mina/bundler'
    require 'mina/rails'
    require 'mina/git'
    require 'mina/rvm'

    app               = 'your_app_name'
    production_domain = 'your_app_production_domain'
    staging_domain    = 'your_app_staging_domain'
    user              = 'ec2-user'
    ruby_version      = 'your_app_ruby_version'
    ruby_gemset       = 'your_app_gemset'

    set :term_mode, nil
    set :shared_paths, ['config/database.yml', 'log']
    set :app, app
    set :repository, "ssh://#{user}@#{domain}/~/git/#{app}.git"
    set :user, user
    set :rvm_path, "/usr/local/rvm/bin/rvm"

    task :environment do

      stage = ENV['to'] || 'staging'
      case stage
        when 'staging'
          set :branch, 'master'
          set :domain, staging_domain
        when 'production'
          set :branch, 'master'
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


