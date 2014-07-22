require 'rubygems'
require 'bundler/setup'

# Immediately sync all stdout so that tools like buildbot can
# immediately load in the output.
# 这个功能我很想学习的 以前使用ruby写的脚本在jenkins控制台不能实时输出
# 将标准输输出 标准错误实时输出
$stdout.sync = true
$stderr.sync = true

# Load all the rake tasks from the "tasks" folder. This folder
# allows us to nicely separate rake tasks into individual files
# based on their role, which makes development and debugging easier
# than one monolithic file.
task_dir = File.expand_path("../tasks", __FILE__)
# http://www.w3cschool.cc/ruby/ruby-variable.html 伪变量
# __FILE__: 当前源文件的名称
# puts __FILE__
# /Users/stallman/gnuhub/git/vagrant/Rakefile

# puts task_dir
# /Users/stallman/gnuhub/git/vagrant/tasks

# puts Dir["#{task_dir}/**/*.rake"].class
# Array

# puts Dir["#{task_dir}/**/*.rake"].inspect
# ["/Users/stallman/gnuhub/git/vagrant/tasks/acceptance.rake", "/Users/stallman/gnuhub/git/vagrant/tasks/bundler.rake", "/Users/stallman/gnuhub/git/vagrant/tasks/test.rake"]
# http://ruby-doc.org/core-2.1.2/Dir.html
# Dir[string] = Dir.glob(string)

Dir["#{task_dir}/**/*.rake"].each do |task_file|
  load task_file
end
# https://github.com/gnuhub/rake/blob/master/doc/rakefile.rdoc
task default: "test:unit"
