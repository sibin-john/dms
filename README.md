# Document Manage System Using AWS DocumentDB and NodeJS.


## Testing

* The API uses basic auth. 
  Test user: api_user
  Test pass: api_user_1
  Note: read the 'Local development' section for setting another password in .env

* The API is hosted at: http://3.0.90.225:3000/api
  Now https is disabled. Once we have the domain and ssl certificates, 
  setting some .env variables and enable_https=true in config will enable https.

* Most of the API methods require a user id. Given below is a test user:
  name: user1
  id: 606b3326f8640a61b8d02127
  
  e.g. list files: http://3.0.90.225:3000/api/files/606b3326f8640a61b8d02127

* The Postman collection describing API methods is added to the repo: 'DMS.postman_collection.json'
  Download the file and import in postman.

## Local development

* First clone this repository and `cd` into its directory:

* Install dependencies: `$ npm install`

* Copy the sample configuration file and edit it to match your configuration.
  `$ cp .env.example .env`

  Replace following environment variables in .env file:

  Ports to listen: HTTP_PORT, HTTPS_PORT

  Session secret: SESSION_SECRET // A strong secret key to encrypt session data.

  (If https enabled) SSL certificate paths: SSL_PRIVATE_KEY_PATH, SSL_CERTIFICATE_PATH, SSL_CHAIN_PATH

  App mode: 'development' Or 'production'.  
  // 'development' will give descriptive logs & errors in webpages/console.

  Database configuration: DB_USER,  DB_PASS,  DB_DATABASE,  DB_HOST,  DB_DIALECT

  API basic auth password: API_PASS

  Run `source .env` to export the environment variables

  (For windows environment, you may use .bat files)
* Run the application.

  Install pm2 globally and run it on startup: 
  `$ npm install pm2 -g` 
  `$ pm2 startup systemd`

  Run the app: `$ pm2 start ./bin/www`

  (optional) Restart and update environment variables: `$ pm2 restart ./bin/www --update-env`

  View logs in windows command line: `$ pm2 logs`


## Code Formatting

* Use 2 spaces for indenting your code and swear an oath to never mix tabs and spaces.

* Use UNIX-style newlines (\n), and a newline character as the last character of a file.

* No trailing whitespace.

* 100 characters per line.

* Use single quotes, unless you are writing JSON.

* Your opening braces go on the same line as the statement.

* The ternary operator should not be used on a single line. Split it up into multiple lines instead.

## Naming Conventions

* Variables, properties and function names should use lowerCamelCase. 
  They should also be descriptive. Single character variables and uncommon abbreviations should -
  generally be avoided. e.g. var adminUser = db.query('SELECT * FROM users ...');

* Class names should be capitalized using UpperCamelCase.
  e.g. function BankAccount() { ... }

* Constants should be declared as regular variables or static class properties, 
  using all uppercase letters.
  e.g. var SECOND = 1 * 1000;
       var FULL_PERMISSIONS = 0777;
