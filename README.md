#Authentication Workflow

## 1. Setup
  1. Add Gems to Gemfile
    * BCrypt
  2. Other steps

## 2. User Model
  1. Generate model and controller
  2. Edit Migration
    1. add table columns
    2. add indices
  3. Handle the Password
    1. In the User Model
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
    2. In the UsersController
      1.


  2. Handle the Session Token
    1.
