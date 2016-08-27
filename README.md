# Deploying Rails 5.0 On Digitalocean

Follow this guide: https://www.digitalocean.com/community/tutorials/how-to-use-the-ruby-on-rails-one-click-application-on-digitalocean

## Notes
This guide doesn't work out-of-the-box for Rails 5.0 with Ruby 2.3.0

### Default rails app location
The location of the already installed rails app isn't correct in the guide. It is:

```
/home/rails
```
instead of
```
~/rails
```

### Install and set Ruby 2.3.0 as default

```
rvm install 2.3.0
rvm use ruby-2.3.0 --default
```

### Install Bundler

```
gem install Bundler
```

### Add SWAP

Follow this guide:
```
https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04
```

### Install libgmp3

```
sudo apt-get install libgmp3-dev
```

### Install gems

```
bundle install
```

### Set database password and app secret as environment variable before creating and migrating the database

```
cat /etc/default/unicorn
export SECRET_KEY_BASE=<secret from file above>
export SECRET_KEY_BASE=<password from file above>
```

### Set the correct gem path for unicorn
```
nano /etc/default/unicorn
service unicorn restart
```
