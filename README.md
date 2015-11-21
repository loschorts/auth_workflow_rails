#Authentication Workflow

## 1. Configure
  1. Add Gems to Gemfile
    * 'bcrypt'
    * 'better_errors'
    * 'binding_of_caller'
    * 'pry-rails'
    * 'quiet_assets'
    * 'faker'
  1. useful methods:
    * BCrypt::Password.new(password_digest)
      * .is_pasword?(password)
    * BCrypt::Password.create(password)
    * SecureRandom.urlsafe_base64(16)
    * Faker:: ?
      * Name.name
      * Internet.email
      * Lorem.words, .sentence, .paragraph

## 2. Setup
  1. Generate models and controller
    * User model & UsersController
    * SessionsController

  2. Edit Migration
    1. add table columns & null constraints
    2. add indices & unique constraints

  2. General setup
    2. add route resources
    1. add validations
    2. define controller actions
      * show, new, create, edit, update, destroy

## 3. Password Handling
  1. User: add validations
    * :password_digest, presence: true
    * :password, allow_nil: true
  2. User: override 'password=' to create password_digest
    * attr_reader :password
    * 'password=' assigns password_digest
  3. User: add password functions
    * is_password?(password)
    * self.find_by_credentials(username, password)

## 2. Session Handling
  1. In the User Model
    1. validates :session_token
    1. add authentication methods
      * after_initialize :ensure_session_token
      * self.generate_session_token
      * reset_session_token!
    2. In the ApplicationController
      * define login methods: login!(user), define current_user, define require_current_user!
      * helper_method :current_user

## 3. Controller Actions
  1. UsersController
    * before_action: require_current_user!
    * user_params
      * params.require().permit()
  2. SessionController
    1. actions
      * new, create, destroy
    2.
