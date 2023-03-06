# README

Rails 7 code along with DHH.(using bootstrap)

* Some notes from the sessions:
  * How to download JS package and pin it in importmaps
    ```
    # download package
    ./bin/importmap pin local-time --download # this downloads it in the vendor file
    ```
  * How to pin JS package in importmap using the jspm CDN
    ```
    ./bin/importmap pin local-time
    ```

* WIP
  - Active storage not working with turbo streams. Need to check

* Intalling bootstrap with rails 7 and importmaps. Found the simplest version which works with the default rails setup - sprockets and importmaps.
    - install bootstrap and sassc-rails gems in your broject
    - rename app/assets/stylesheets.css to app/assets/stylesheets.scss
    - add line `@import "bootstrap";` to the application.scss file
    - then open `config/initializers/assets.rb` and add these line
    ```
    Rails.application.config.assets.precompile += %w( bootstrap.min.js popper.js )
    ```
    - goto `config/importmap.rb` and add the following lines
    ```
    pin "popper", to: 'popper.js', preload: true
    pin "bootstrap", to: 'bootstrap.min.js', preload: true
    ```
    - goto `app/javascript/application.js` and add following lines
    ```
    import "popper"
    import "bootstrap"
    ```
* Install Redis (for turbo-stream to work)
    ```
    sudo apt update
    sudo apt install redis-server
    sudo service redis-server start
    # test installation using
    redis-cli ping
    ```
* Install postgres from here: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-20-04
* Using active storage requires some extra setup
    ```
    # this is used by image-processing gem
    sudo apt install libvips42
    ```
* Install rbenv
    - `sudo apt update`
    - `sudo apt install git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev`
    - `curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash`
    - `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`
    - `echo 'eval "$(rbenv init -)"' >> ~/.bashrc`
    - `source ~/.bashrc`

