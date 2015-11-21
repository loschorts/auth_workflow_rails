#Authentication Workflow

This document is meant to serve as a rough map of what needs to be defined and specified
for creating users, passwords, and sessions.

Please let me know of anything incorrect or incomplete. I'd love to hear your feedback!


## 1. Configure / FYI
  1. Gemfile
    * 'bcrypt'
    * 'better_errors'
    * 'binding_of_caller'
    * 'pry-rails'
    * 'quiet_assets'
    * 'faker'
  1. Methods
    * BCrypt::Password.new(password_digest)
      * .is_pasword?(password)
    * BCrypt::Password.create(password)
    * SecureRandom.urlsafe_base64(16)
    * Faker:: ?
      * Name.name
      * Internet.email
      * Lorem.words, .sentence, .paragraph

## 2. Setup
  1. Generate
    * User model & UsersController
    * SessionsController
  2. Migrate
    1. table columns & null constraints
    2. indices & unique constraints
  2. General Setup
    2. config/route resources
    1. validations
    2. controller actions
      * show, new, create, edit, update, destroy
      * user_params

## 3. Password Handling
  1. User: add validations
    * :password_digest, presence: true
    * :password, allow_nil: true
  2. User: password sets password_digest
    * attr_reader :password
    * password= assigns password_digest
  3. User: add password functions
    * is_password?(password)
    * self.find_by_credentials(username, password)

## 4. Session Handling
  1. User
    1. validates :session_token
    1. add authentication methods
      * after_initialize :ensure_session_token
      * self.generate_session_token
      * reset_session_token!
  2. ApplicationController
    * define login methods: login!(user), current_user, require_current_user!
    * helper_method :current_user

## 5. Controller Actions
  1. UsersController
    * before_action: require_current_user!
  2. SessionController
    1. actions: new, create, destroy
