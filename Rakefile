require 'rake'
require File.join(File.dirname(__FILE__), "_blueprint", "lib", "blueprint", "blueprint")

desc "Generate and compress stylesheets from Blueprint CSS source"
task :build_css do
  ARGV = %w{-f _blueprint_settings.yml -p default}
  Blueprint::Compressor.new.generate!
  FileUtils.rm_rf 'stylesheets/src'
  FileUtils.rm_rf 'stylesheets/print.css' #rm blueprint's print stylesheet since I don't use it
end
