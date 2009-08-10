require 'rake'
require File.join(File.dirname(__FILE__), "_vendor", "blueprint-css", "lib", "blueprint", "blueprint")

desc "Generates and compresses stylesheets from Blueprint CSS source"
task :build_css do
  ARGV = %w{-f _blueprint_settings.yml -p default}
  Blueprint::Compressor.new.generate!
  FileUtils.rm_rf 'stylesheets/src'
  FileUtils.rm_rf 'stylesheets/print.css' #rm blueprint's print stylesheet since I don't use it
end

desc "Generates PDF resume from HTML"
task :build_pdf do
  `jekyll`
  `~/sandbox/wkpdf/bin/wkpdf --source _site/resume.html --output dandofter.pdf --stylesheet-media print --margin 30`
end
