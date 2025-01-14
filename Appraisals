# frozen_string_literal: true

ruby_30_or_higher = Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.0')
ruby_31_or_higher = Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.1')
jruby = RUBY_PLATFORM.include?('java')

unless ruby_31_or_higher # https://github.com/rails/rails/issues/44090#issuecomment-1007686519
  appraise "rails-6.1" do
    gem "rails", "~> 6.1.0"
    gem "traces", "~> 0.9.1"
    gem "puma", "~> 5.6"
  end
end

if ruby_30_or_higher && !ruby_31_or_higher && !jruby
  appraise "rails-7.0" do
    gem "rails", "~> 7.0.0"
    gem "selenium-webdriver", "~> 4.0" # https://github.com/rails/rails/pull/43498
  end
end

if ruby_31_or_higher
  appraise "rails-7.0-ruby-3.1" do
    gem "capybara", "~> 3.36" # For Ruby 3.1 support https://github.com/teamcapybara/capybara/pull/2468
    gem "rails", "~> 7.0.1" # Ruby 3.1 requires Rails 7.0.1+
    gem "selenium-webdriver", "~> 4.0" # https://github.com/rails/rails/pull/43498
  end

  unless jruby
    appraise "rails-7.1-ruby-3.1" do
      gem "capybara", "~> 3.36" # For Ruby 3.1 support https://github.com/teamcapybara/capybara/pull/2468
      gem "rails", "~> 7.1.0"
      gem "selenium-webdriver", "~> 4.0" # https://github.com/rails/rails/pull/43498
    end

    appraise "rails-head" do
      gem "capybara", "~> 3.36" # For Ruby 3.1 support https://github.com/teamcapybara/capybara/pull/24
      gem "rails", github: "rails/rails", branch: "main"
      gem "selenium-webdriver", "~> 4.0" # https://github.com/rails/rails/pull/43498
    end
  end
end
