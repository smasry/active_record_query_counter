require "bundler/gem_tasks"

task :release do
  unless `git rev-parse --abbrev-ref HEAD`.chomp == "master"
    warn "Gem can only be released from the master branch"
    exit 1
  end
end

require "rspec/core/rake_task"
require "standard/rake"

RSpec::Core::RakeTask.new(:spec)

task default: :appraisals

desc "run the specs using appraisal"
task :appraisals do
  exec "bundle exec appraisal rake spec"
end

namespace :appraisals do
  desc "install all the appraisal gemspecs"
  task :install do
    exec "bundle exec appraisal install"
  end
end
