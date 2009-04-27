require 'rake/testtask'
require 'rake/gempackagetask'

task :default => :test

Rake::TestTask.new("test") do |t|
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.warning = true
  t.verbose = true
end

desc "Generate file list for .gemspec"
task :gem_file_list do
  f = FileList.new
  f.include('lib/**/**')
  f.include('rdoc/**/**')
  f.exclude('rdoc/test/**/**')
  print "%w(" + f.to_a.select{|file| !File.directory? file }.join(' ') + ")\n"
end

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "sdoc"
    gem.summary = "rdoc html with javascript search index."
    gem.email = "voloko@gmail.com"
    gem.homepage = "http://github.com/voloko/sdoc"
    gem.authors = ["Volodya Kolesnikov"]
    gem.add_dependency("json", ">= 1.1.3")
    gem.add_dependency("rdoc", ">= 2.4.2")
    gem.add_dependency("rubigen")

    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
rescue LoadError
  puts "Jeweler not available. Install it with: sudo gem install technicalpickles-jeweler -s http://gems.github.com"
end
