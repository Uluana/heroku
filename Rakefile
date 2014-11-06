require "rubygems"

PROJECT_ROOT = File.expand_path("..", __FILE__)
$:.unshift "#{PROJECT_ROOT}/lib"

require "heroku/version"
begin
  require "rspec/core/rake_task"
  RSpec::Core::RakeTask.new(:spec)
rescue LoadError
end

task :default => :spec

def version
  require "heroku/version"
  Heroku::VERSION
end

Dir[File.expand_path("../dist/**/*.rake", __FILE__)].each do |rake|
  import rake
end

desc "Release the latest version"
task "release" => ["tgz:release", "zip:release", "manifest:update", "gem:release"] do
  puts("Released v#{version}")
end
