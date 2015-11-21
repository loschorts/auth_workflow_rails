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
  3. Edit Model
    1. Handle the password
      1. add validations
        * :password_digest, presence: true
        * :password, allow_nil: true
      2. override 'password=' to render digest
        * attr_reader :password
        * 'password=' assigns password_digest
      3. password functions
        * is_password? password
        * self.find_by_credentials(username, password)
    2. Handle the Session Token
  4. Edit Controller
    1.


  2. Handle the session token
      1.
