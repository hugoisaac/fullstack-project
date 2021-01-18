# Rails Backend
<!-- TODO: Add abstract here. -->

## Setting Up the Development Environment on Ubuntu 18.04

1. [Install PostgreSQL](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04) and set up user role.

    ```bash
        sudo apt update
        sudo apt install postgresql postgresql-contrib
        # the service should be running now
        service postgresql status
        # need to create a role and DB for the logged in user
        sudo -u postgres createuser --superuser $USER
        sudo -u postgres createdb $USER
        # psql should allow access using the created role and DB
        psql
        # useful psql commands:
        # help
        # \?
        # \conninfo
        # \du
        # \l
        # \d
        # \c <db_name>
        # \c <db_name>
        # \set
        # \x auto
        # \q
    ```

1. Install Ruby and [RubyGems](https://github.com/rubygems/rubygems) using [rbenv](https://github.com/rbenv/rbenv) and [rbenv-installer](https://github.com/rbenv/rbenv-installer).

    ```bash
      curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash
      echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
      ~/.rbenv/bin/rbenv init
      echo 'eval "$(rbenv init -)"' >> ~/.bashrc
      source ~/.profile
      curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
      rbenv install
      # NOTE: May receive an error because extensions cannot be compiled, and a suggestion to install missing dependencies.
      # sudo apt install -y libssl-dev libreadline-dev zlib1g-dev
      rbenv version
      ruby -v
      gem env home
    ```

1. Install [Bundler](https://bundler.io/). **Note**: To work around Bundler / RubyGems compatibility issues, install the version from the lockfile. More info in this [Bundler blog post](https://bundler.io/blog/2019/01/04/an-update-on-the-bundler-2-release.html).

    ```bash
      gem install bundler -v '2.1.4'
    ```

1. Install the `libpq-dev` dependency, which is needed to build the native extensions for the `pg` gem. See [this helpful SO answer](https://stackoverflow.com/a/58961362/3390323) for more info.

    ```bash
      sudo apt install libpq-dev
    ```

## Setting Up or Updating the Rails Application

  ```bash
    bin/setup
  ```

## Runing the Rails Server and Console

  ```bash
    rails s
    rails c
  ```

## Running the Test Suite
<!-- TODO -->
