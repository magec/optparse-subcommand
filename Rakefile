$: << File.expand_path(File.join(File.dirname(__FILE__), 'lib'))

desc "Generate gemspec"
task :gemspec do
  require 'rubygems/specification'
  require 'date'

  spec = Gem::Specification.new do |s|
    s.specification_version = 3 if s.respond_to? :specification_version=
    s.required_rubygems_version = Gem::Requirement.new(">= 0") if s.respond_to? :required_rubygems_version=

    s.author            = "Bodaniel Jeanes"
    s.email             = "me@bjeanes.com"

    s.name              = 'optparse-subcommand'
    s.version           = '1.0.0.pre'
    s.summary           = 'Add subcommand parsing to Ruby\'s OptionParser class'
    s.description       = s.summary
    s.homepage          = 'http://github.com/bjeanes/optparse-subcommand'

    s.date              = Date.today.strftime

    s.files             = %w(LICENSE README.md) + Dir.glob("{lib,spec}/**/*")
    s.require_paths     = %w[lib]
    s.test_files        = s.files.select { |path| path =~ /^spec\// }
    s.autorequire       = "optparse/subcommand"
    s.has_rdoc          = false

    s.add_development_dependency "rake"
    s.add_development_dependency "rspec", "2.9.0"
  end

  File.open("optparse-subcommand.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end

desc "Release"
task :release => :gemspec do
  # TODO
end

desc "Run specs"
task :spec do
  Dir.chdir(File.expand_path(File.dirname(__FILE__))) do
    exec("bundle exec rspec -Ilib spec")
  end
end

task :default => :spec

