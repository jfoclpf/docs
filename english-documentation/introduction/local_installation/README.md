# Local installation

Before installing Consul and having it up and running make sure you all [prerequisites](prerequisites.md) installed.

1. First, clone the [Consul Github repository](https://github.com/consul/consul/) and enter the project folder:

```bash
git clone https://github.com/consul/consul.git
cd consul
```

1. Install the Ruby version we need with your Ruby version manager. Here are some examples:

```bash
rvm install `cat .ruby-version` # If you're using RVM
rbenv install `cat .ruby-version` # If you're using rbenv
asdf install ruby `cat .ruby-version` # If you're using asdf
```

1. Check we're using the Ruby version we've just installed:

```bash
ruby -v
=> # (it should be the same as the version in the .ruby-version file)
```

1. Install [Bundler](http://bundler.io/):

```bash
gem install bundler --version 1.17.1
```

1. Install the required gems using Bundler:

```bash
bundle
```

1. Copy the environment example configuration files inside new readable ones:

```bash
cp config/database.yml.example config/database.yml
cp config/secrets.yml.example config/secrets.yml
```

And setup database credentials with your `consul` user in your new `database.yml` file.

1. Run the following [Rake tasks](https://github.com/ruby/rake) to create and fill your local database with the minimum data needed to run the application:

```bash
rake db:create
rake db:setup
rake db:dev_seed
rake db:test:prepare
```

1. Check everything is fine by running the test suite \(beware it might take more than an hour\):

```bash
bin/rspec
```

1. Now you have all set, run the application:

```bash
bin/rails s
```

Congratulations! Your local Consul application will be running now at `http://localhost:3000`.

In case you want to access the local application as admin, a default user verified and with admin permissions was created by the seed files with **username** `admin@consul.dev` and **password** `12345678`.

If you need an specific user to perform actions such as voting without admin permissions, a default verified user is also available with **username** `verified@consul.dev` and **password** `12345678`.

