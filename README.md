# Star Wars API

Ruby on Rails API that allows the user to get information from Star Wars through an authenticated user.

## Getting Started

### Requirements

- `ruby 3.1.2`

### Installation

#### With Docker (recommended)

- If it's the first time running the project, execute: `sh ./docker/initialize.sh`
- Then only start the container when needed with: `docker compose up`

#### Standalone

- `bundle install`
- `rails db:create db:migrate db:seed`
- `brew update && brew install mailhog` (More info on: [https://github.com/mailhog/MailHog#installation](https://github.com/mailhog/MailHog#installation))

### Running

#### With Docker (recommended)

- `docker compose up`

#### Standalone

- To run the web server, run: `rails s`
- To run the mail server, run the following on another tab: `mailhog`

## API Documentation

API documentation can be found on the following [Postman workspace link](https://www.postman.com/hepu1308/workspace/star-wars-api/overview)

## About the code

This is a Ruby on Rails API mode application that uses Devise as authentication and Fast JSON API + Oj for structuring and serializing of the API responses.

Mails are served through MailHog package and UI can be accessed by going to [http://localhost:8025](http://localhost:8025) with or without Docker.

### Authentication

Authentication endpoints can be used to sign up, log in and log out from the API.

- It all starts with signing up using the `POST /signup` endpoint, which returns the user details
- Authenticating into the API its possible by using the `POST /login` endpoint, which returns the Bearer token on the response's Header (after a successful login)
- Logging out its done by the `DELETE /logout` endpoint, which safely deletes the user session on the API

### Resetting password

By using the **Reset Password** (`POST /password`) endpoint, a `reset_password_token` is returned and also sent via a link to the User's email.
This token allows the user to reset his password via the **Create Password** (`PUT /password`) endpoint