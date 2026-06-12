source "https://rubygems.org"

# --- should alert (top-level, no pin, not on RubyGems) ---
gem "acme-internal-helpers", "~> 1.0"
gem "corp-private-gem"

# --- should NOT alert (pinned inline) ---
gem "my-local-lib", path: "../my-local-lib"
gem "unreleased-fork", git: "https://github.com/corp/unreleased-fork"
gem "another-fork", github: "corp/another-fork"

# --- should NOT alert (inside source block — Bundler pins to that source) ---
source "https://gems.internal.corp.com" do
  gem "corp-internal-sdk", "~> 2.0"
  gem "corp-auth-middleware"
end

# --- should NOT alert (inside git block) ---
git "https://github.com/corp/monorepo" do
  gem "corp-shared-utils"
  gem "corp-api-client"
end

# --- should NOT alert (inside path block) ---
path "../vendor" do
  gem "vendored-internal-gem"
end

# --- should alert (gems in group block are NOT pinned — group is not a source pin) ---
group :development, :test do
  gem "acme-dev-tools-private"
  gem "rspec", "~> 3.12"
end

# --- edge: nested source blocks ---
source "https://gems2.internal.corp.com" do
  source "https://gems.internal.corp.com" do
    gem "deeply-nested-internal"
  end
end