#Authentication Workflow

## 1. Configure
  1. Add Gems to Gemfile
    * BCrypt
  2. Other steps

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

## 3. Handle the Password
  In the User Model
      1. Handle the Password
        1. add validations
          * :password_digest, presence: true
          * :password, allow_nil: true
        2. override 'password=' to create password_digest
          * attr_reader :password
          * 'password=' assigns password_digest
        3. password functions
          * is_password?(password)
          * self.find_by_credentials(username, password)

## 2. Handle the Session
  1. In the User Model
  2. In the UsersController
  2. In the SessionController
