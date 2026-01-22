source 'https://rubygems.org'

# 1. Standard Public Gems (Should exist -> NO Alert)
gem 'rails', '~> 7.0.0'
gem 'pg'
gem 'puma'

# 2. Private/Internal Gems (Should NOT exist -> TRIGGER Alert)
# These names look internal but likely don't exist on public RubyGems.org
gem 'deepbounty-internal-auth-v2'
gem 'corp-billing-sdk-private'
gem 'legacy-payments-connector-ruby'

# 3. Gems in blocks (Regex should handle indentation)
group :development, :test do
  gem 'rspec-rails'          # Public -> No Alert
  gem 'deepbounty-dev-utils' # Private -> TRIGGER Alert
end

# 4. Syntax Variations (Regex should handle quotes and spacing)
gem "sidekiq"      # Double quotes -> Public -> No Alert
gem    'redis'     # Extra spaces -> Public -> No Alert
  gem 'bcrypt'     # Indented -> Public -> No Alert

# 5. Invalid Names (Should be SKIPPED by VALID_GEM_NAME_REGEX)
# These should NOT trigger any network request or alert
gem 'invalid name with spaces'
gem '-starts-with-dash'
gem '$$$invalid-symbols'

# 6. Comments (Regex should IGNORE these)
# gem 'commented-out-vulnerable-gem'