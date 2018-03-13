### Steps to reproduce
1. create a new rails application
2. add to `config/environments/development.rb`:
```ruby
config.after_initialize do
  puts '**************** in config.after_initialize *********************'
  puts "Rails.application.initialized?: #{Rails.application.initialized?}"
  puts '*****************************************************************'
end
```
3. cd to app folder
4. run `rake routes`

### Expected behavior
It should print
```
**************** in config.after_initialize *********************
Rails.application.initialized?: true
*****************************************************************
```
### Actual behavior
It prints
```
**************** in config.after_initialize *********************
Rails.application.initialized?: false
*****************************************************************
```
### System configuration

#### Rails version: 5.1.5

#### Ruby version: 2.5.0

The docs say

https://apidock.com/rails/Rails/Configuration/after_initialize

> Adds a block which will be executed after rails has been fully initialized. Useful for per-environment configuration which depends on the framework being fully initialized.

http://guides.rubyonrails.org/configuring.html

> config.after_initialize takes a block which will be run after Rails has finished initializing the application. That includes the initialization of the framework itself, engines, and all the application's initializers in config/initializers. Note that this block will be run for rake tasks. Useful for configuring values set up by other initializers:
