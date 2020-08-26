# Overtime App

* Key requirements: Company needs documentation that salaried employees did or did not get overtime each week

## Models
* Post: date (date) rationale (text)
* User: (Devise gem)
* AdminUser (STI)

## Features
* Approval workflow
* SMS - Send a link to approval or overtime input
* Admin dashboard for managers to review, accept overtime entries, view logs, etc.
* Email summary to to managers for approval
* Important: keep record (document) if an employee did not log overtime hours
* Use Bootstrap for simple layout formatting

## Project setup notes

* create the project with the `--database=postgresql` flag:

  ```bash
  rails new Overtime --database=postgresql
  ```

* Remove comments in Gemfile and add gems for tests in `:development, :test` block:

  ```
  gem 'rspec-rails'
  gem 'capybara'
  gem 'database_cleaner'
  ```
* run `bundle` to install gems
* run the `RSpec` installer
```bash
rails g rspec:install
```

* Customize the `rails_helper.rb` file to work with Capybara and DatabaseCleaner
  ```
  # spec/rails_helper.rb

  # other code...
  RSpec.configure do |config|
    # other config...

    config.before(:suite) { DatabaseCleaner.clean_with(:truncation) }
    config.before(:each) { DatabaseCleaner.strategy = :transaction }
    config.before(:each, js: true) { DatabaseCleaner.strategy = :truncation }
    config.before(:each) { DatabaseCleaner.start }
    config.after(:each) { DatabaseCleaner.clean } 

    # rest of config...
  end