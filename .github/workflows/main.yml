# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.
# This workflow will download a prebuilt Ruby version, install dependencies and run tests with Rake
# For more information see: https://github.com/marketplace/actions/setup-ruby-jruby-and-truffleruby

name: CI

on: push

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: 2.7
      - name: Install dependencies
        run: bundle install
      - name: Run linter
        run: bundle exec rubocop
  test_rails6_0:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        ruby: [2.7]
    steps:
      - uses: actions/checkout@v2
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: ${{ matrix.ruby }}
      - name: Install dependencies
        run: bundle install
        env:
          RAILS_VERSION: 6.1.7
          BLACKLIGHT_VERSION: '~>7.0'
      - name: Run tests
        run: bundle exec rake ci
        env:
          RAILS_VERSION: 6.1.7
          BLACKLIGHT_VERSION: '~>7.0'
          ENGINE_CART_RAILS_OPTIONS: '--skip-git --skip-listen --skip-spring --skip-keeps --skip-action-cable --skip-coffee --skip-test'
  test_rails5_2_bl_7:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        ruby: [2.5]
    steps:
      - uses: actions/checkout@v2
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: ${{ matrix.ruby }}
      - name: Install dependencies
        run: bundle install
        env:
          RAILS_VERSION: 5.2.8.1
          BLACKLIGHT_VERSION: '~>7.0'
      - name: Run tests
        run: bundle exec rake ci
        env:
          RAILS_VERSION: 5.2.8.1
          BLACKLIGHT_VERSION: '~>7.0'
          ENGINE_CART_RAILS_OPTIONS: '--skip-git --skip-listen --skip-spring --skip-keeps --skip-action-cable --skip-coffee --skip-test'
  test_rails5_2_bl_6:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        ruby: [2.5]
    steps:
      - uses: actions/checkout@v2
      - name: Set up Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: ${{ matrix.ruby }}
      - name: Install dependencies
        run: bundle install
        env:
          RAILS_VERSION: 5.2.8.1
          BLACKLIGHT_VERSION: '~>6.0'
      - name: Run tests
        run: bundle exec rake ci
        env:
          RAILS_VERSION: 5.2.8.1
          BLACKLIGHT_VERSION: '~>6.0'
          ENGINE_CART_RAILS_OPTIONS: '--skip-git --skip-listen --skip-spring --skip-keeps --skip-action-cable --skip-coffee --skip-test'
