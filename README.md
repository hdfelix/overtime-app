# Overtime App

* Key requirements: Company needs documentation that salaried employees did or did not get overtime each week

## Models
* Post: date (date) rationale (text)
* x User: (Devise gem)
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

### RSpec
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

### Devise
* Add the `Devise` gem and run `rails g devise:install`
* Follow the post-installation instructions printed on the console.
* Update the email address in `config/initializers/devise.rb` to the email address
  your emails will be sent from.
  ```
  config.mailer_sender = '<your-email@here.com>'
  ```
* Generate the devise views with `rails g devise:views`
* Convert the views to haml with `rails haml:erb2haml`
* Generate the User model
  ```
  rails g devise User first_name:string last_name:string type:string
  ```
