require 'rubygems'
require 'rake'
require 'cucumber'
require 'cucumber/rake/task'

PROJECT_CEEDLING_ROOT = "vendor/ceedling"
load "#{PROJECT_CEEDLING_ROOT}/lib/rakefile.rb"

task :default => %w[ test:all ]

class BuildFailure < Exception
  def initialize(message = nil)
    message ||= "Build failed"
    super(message)
  end
end

# Cucumber::Rake::Task.new do |t|
#   t.cucumber_opts = "--format progress"
# end

namespace :features do
  desc "Run finished features"
  Cucumber::Rake::Task.new(:finished) do |t|
    t.cucumber_opts = "--format progress --tags ~in-progress"
    # t.pattern = 'test/features/*.features'
  end

#   desc "Run in-progress features"
#   Cucumber::Rake::Task.new(:in_progress) do |t|
#     t.cucumber_opts = "--require formatters/ --format Cucumber::Formatter::InProgress --tags in-progress"
#     t.pattern = 'test/features/*.features'
#   end

#   desc "Re-run failed features"
#   Cucumber::Rake::Task.new(:failed) do |t|
#     unless File.exist?(File.join(Rails.root, 'build/tmp/rerun.txt'))
#       File.open(File.join(Rails.root, 'build/tmp/rerun.txt'), 'w+').close
#     t.profile = 'rerun'
#   	t.cucumber_opts = "--format rerun --out build/tmp/rerun.txt"
#     t.pattern = 'test/features/*.features'
#   end
end

# desc "Run complete feature build"
# task :cruise do
#   finished_successful = run_and_check_for_exception("finished")
#   in_progress_successful = run_and_check_for_exception("in_progress")

#   unless finished_successful && in_progress_successful
#     puts
#     puts("Finished features had failing steps") unless finished_successful
#     puts("In-progress Scenario/s passed when they should fail or be pending") unless in_progress_successful
#     puts
#     raise BuildFailure
#   end
# end

# def run_and_check_for_exception(task_name)
#   puts "*** Running #{task_name} features ***"
#   begin
#     Rake::Task["features:#{task_name}"].invoke
#   rescue Exception => e
#     return false
#   end
#   true
# end
