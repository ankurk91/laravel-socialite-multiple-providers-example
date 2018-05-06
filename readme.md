# Laravel Socialite with Multiple Providers

> An example project that covers login with multiple social providers.

## Setup
Follow Laravel installation [steps](https://laravel.com/docs/5.6/installation#installation)

### What has been covered?
* Login/Sign-up with Google and Github, you can add as many as you can.
* Fire `RegisteredEvent` on new user creation same as default `RegistratonController`.
* Create and associate social account when email address already exists.
* Create user if email address does not exists in `users` table.

### What has not been covered?
* Storing access token.
* Storing user avatar.
* Providers that does not return `email` address for example Facebook.
* Allow users to change their email address.
* Allow users to disconnect from their social account.
* Allow logged-in users to connect to their social account.
* Allow users to change their account password without knowing the current, because they have logged-in via socialite.

### How to add new provider?
* Add provider name in routes `where()` method, for example - `twitter`
```php
->where('provider', 'google|github|twitter');
```
* Make room for new credentials in `config/services.php`
```php
'twitter' => [
        'client_id' => env('TWITTER_OAUTH_CLIENT_ID'),
        'client_secret' => env('TWITTER_OAUTH_CLIENT_SECRET'),
        'redirect' => env('TWITTER_OAUTH_REDIRECT'),
    ],
```
* Update `.env.example` and `.env`
```.dotenv
# Twitter OAuth
# https://developer.twitter.com
TWITTER_OAUTH_CLIENT_ID=
TWITTER_OAUTH_CLIENT_SECRET=
TWITTER_OAUTH_REDIRECT=${APP_URL}/oauth/github/callback
```
* That's it. You are done.

### License
Same as Laravel, [MIT license](https://opensource.org/licenses/MIT)
