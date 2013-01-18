require 'fileutils'

base_dir = File.expand_path(File.dirname(__FILE__))
book_filename = "chef_cap_guide"

desc 'setup the output folder'
task :setup do
  FileUtils.mkdir_p File.join(base_dir, 'output')
end

desc 'build the book'
task :pandoc => :setup do
  files = []
  dir = File.join(base_dir, 'content')
  Dir[File.join(dir, '**', '*.md')].sort.each do |input|
    files << input
  end

  epub_file = File.join(base_dir, 'output', "#{book_filename}.epub")
  html_file = File.join(base_dir, 'output', "#{book_filename}.html")

  common_settings = "--toc --data-dir=#{base_dir} -S"
  epub_settings = "-o #{epub_file} --epub-stylesheet=style/common.css --epub-stylesheet=style/epub.css"
  html_settings = "-o #{html_file} --self-contained -t html5 --css=style/common.css --css=style/html.css"
  file_string = files.join(' ')

  [epub_settings, html_settings].each do |settings|
    `pandoc #{common_settings} #{settings} #{file_string}`
  end
end

task :default => :pandoc
