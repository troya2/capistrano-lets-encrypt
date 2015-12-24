# Capistrano::LetsEncrypt [![Gem Version](https://badge.fury.io/rb/capistrano-lets-encrypt.png)](http://badge.fury.io/rb/capistrano-lets-encrypt)

Let's encrypt support for Capistrano 3.x

Thanks to @unixcharles and @zealot128 for their libraries,
[acme-client](https://github.com/unixcharles/acme-client/) and
[letsencrypt-cli](https://github.com/zealot128/ruby-letsencrypt-cli) to manage
part of the workflow to work with Let's encrypt. This library use both to create
a series of capistrano tasks that should help you create certs on your projects
deployed with capistrano

## Installation

Add this line to your application's Gemfile:

    gem 'capistrano-lets-encrypt', '~> 1.0'
    gem 'capistrano'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install capistrano-lets-encrypt

## Usage

Require in `Capfile` to use the default task:

```ruby
require 'capistrano/lets-encrypt'
```

You will get the following tasks

```ruby
cap lets_encrypt:register            # Register a Let's encrypt account
cap lets_encrypt:check_certificate   # Check for validity of certificates
cap lets_encrypt:authorize           # Authorize a domain using ACME protocol
cap lets_encrypt:cert                # Create certificates and private keys
```

Configurable options (copy into deploy.rb), shown here with examples:

```ruby
# default value: :web
set :lets_encrypt_roles, :lets_encrypt

# default value: false
set :lets_encrypt_test, true

# default value: nil
set :lets_encrypt_email, nil

# default value: nil
set :lets_encrypt_domains, nil

# default value: "#{release_path}/public"
set :lets_encrypt_challenge_public_path, "#{release_path}/public"

# default value: "#{shared_path}/ssl/certs"
set :lets_encrypt_output_path, "#{shared_path}/ssl/certs"

# default value: "#{fetch(:lets_encrypt_email)}.account_key.pem"
set :lets_encrypt_account_key, "#{fetch(:lets_encrypt_email)}.account_key.pem"

# default value: 30
set :lets_encrypt_days_valid, 30

# default value: "~/certs"
set :lets_encrypt_local_output_path, "~/certs"
```

## Requirements

This tool needs Ruby >= 2.1 (as the dependency acme-client needs that because of use of keyword arguments).

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## Credits

Thank you [contributors](https://github.com/platanus/capistran-lets-encrypt/graphs/contributors)!

<img src="http://platan.us/gravatar_with_text.png" alt="Platanus" width="250"/>

capistrano-lets-encrypt is maintained by [platanus](http://platan.us).

## License

Guides is © 2014 platanus, spa. It is free software and may be redistributed under the terms specified in the LICENSE file.
