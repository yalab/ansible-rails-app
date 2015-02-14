# A small Rails server playbook for Ansible

**Bastardised from https://github.com/dodecaphonic/ansible-rails-app**

It installs:

- Ruby 2.2
- PostgreSQL 9.3
- nginx
- Unicorn

1. Change the app name and deploy directory in <code>vars/defaults.yml</code>.
2. Rename `hosts.example` to `staging` or `production` and change it to your hosts.

To run:

    $ ansible-playbook -i staging ruby-webapp.yml -t ruby,deploy,postgresql,nginx
    $ <deploy your app>
    $ ansible-playbook -i staging ruby-webapp.yml -t unicorn

Add the library to your rails app Gemfile:

    group :development do
      gem 'capistrano3-unicorn'
    end

To run:

    $ cap install

Add the library to your Capfile:

    require 'capistrano3/unicorn'

Add line your config/deploy.rb to require this deploy.rb 

    require PATH/TO/THIS/REPOS/deploy.rb

To run:

    $ cap staging deploy

    

