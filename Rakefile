require 'rake'
require File.join(File.dirname(__FILE__), "_vendor", "blueprint-css", "lib", "blueprint", "blueprint")

desc "Generates and compresses stylesheets from Blueprint CSS source"
task :build_css do
  ARGV = %w{-f _blueprint_settings.yml -p default}
  Blueprint::Compressor.new.generate!
  FileUtils.rm_rf 'stylesheets/print.css' #rm blueprint's print stylesheet since I don't use it
end

desc "Generates PDF resume from HTML"
task :build_pdf do
  system 'jekyll --server &'
  jekyll_pid = `ps | grep jekyll`.match(/^(\d+)/)[1]
  `~/sandbox/wkpdf/bin/wkpdf --source http://localhost:4000/resume.html --output dandofter.pdf --stylesheet-media print --margin 30`
  `kill #{jekyll_pid}`
end

desc "Generates 404 page since github pages requires
 an non-jekyll 404.html"
task :build_404 do
  FileUtils.cp '_404.html', '404.html'
  `jekyll`
  FileUtils.cp '_site/404.html', '404.html'
end
