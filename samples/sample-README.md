*-- This is a sample README file. Please read through carefully, add, remove, edit any parts (including this line) as necessary for your app. --*

# Project Name README

## Introduction
You are going to maintain or develop this app. This README is to help you to understand what this app is about, design decisions made and why, gotchas, etc so that you can quickly get up-to-speed on the app.

As with every document, please update this README based on your changes so that the next developer can benefit.

## What is This App About?
*-- Add the background information for the app here --*

## Technical Background
We use `rvm` to manage the ruby version and git to manage the source code. The app is based on Rails and tested via `rspec`.

## How To Setup The App
We assume you are using Macbook for development. To setup the app, follow the below instructions:
- git clone this repository
- setup your rvm gemset
- run `bundle install`
- run `rspec`

If rspec passes, the app is working fine.

## Code Structure
The app is built on Ruby on Rails and we follow Rails conventions and best practices as much as possible.

File/Folder | Purpose
---|---
app/ | Contains the controllers, models, views, helpers, mailers and assets for the application. 
bin/ | Contains the rails script that starts your app and can contain other scripts you use to setup, deploy or run your application.
config/ | Configure your application's routes, database, and more. 
config.ru | Rack configuration for Rack based servers used to start the application.
db/ | Contains your current database schema, as well as the database migrations.
Gemfile, Gemfile.lock | These files allow you to specify what gem dependencies are needed for your Rails application. 
lib/ | Extended modules for your application.
log/ | Application log files.
public/ | The only folder seen by the world as-is. Contains static files and compiled assets.
Rakefile | This file locates and loads tasks that can be run from the command line. Custom rake tasks are added in the lib/tasks.
README.md | This is a brief instruction manual for your application and is what you are reading now.
spec/ | Test cases for the app.
tmp/ | Temporary files (like cache, pid, and session files).
vendor/ | A place for all third-party code. In a typical Rails application this includes vendored gems.

## Main Objects Roles
*-- Describe the main roles of each major objects in the system --*

Name        | Type  | Purpose
------------|-------|-------------------------------------------
Product     | Model | This model handles the products data
Search::Log | Model | This model logs the user keyword searches

## Design Decisions and Considerations
*-- Add any special design considerations here --*

## Available Rake Tasks
*-- Add any custom rake tasks for the app here --*

## How to Deploy on Production
The app is deployed on AWS.

To deploy it, you would need to first add your SSH public key into the production server.

Next, push your changes to the production git server at `<AWS-Production-Git-Address>`.

Thereafter, from your development, run `mina deploy` to deploy the app into the production server.

The deployment is based on the gem mina and all deployment information can be found in `config/deploy.rb`

## TODOs
*-- Add any outstanding TODOs for the app here --*

## Outstanding Issues Upon Completion of Project
*-- Add any outstanding issues with the client upon completion of the project --*
