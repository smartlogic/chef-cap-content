require 'fileutils'

def base_dir
  File.expand_path(File.dirname(__FILE__))
end

book_filename = "chef_cap_guide"

def loop_over_content_files
  dir = File.join(base_dir, 'content')
  Dir[File.join(dir, '**', '*.md')].sort.each do |file|
    yield file
  end
end

desc 'setup the output folder'
task :setup do
  FileUtils.mkdir_p File.join(base_dir, 'output')
end

desc 'build the book'
task :pandoc => :setup do
  pandoc_path = `which pandoc`.chomp
  raise 'pandoc not installed' if pandoc_path.length == 0
  puts "Building output"
  files = []
  loop_over_content_files do |file|
    content = File.read(file)
    if content.scan(/TODO/).length > 0
      puts "WARNING: TODO left in #{file}"
    end
    files << file
  end

  epub_file = File.join(base_dir, 'output', "#{book_filename}.epub")
  html_file = File.join(base_dir, 'output', "#{book_filename}.html")
  odt_file = File.join(base_dir, 'output', "#{book_filename}.odt")

  common_settings = "--data-dir=#{base_dir} -S"

  epub_settings = "-o #{epub_file} --epub-stylesheet=style/common.css --epub-stylesheet=style/epub.css"
  html_settings = "-o #{html_file} --self-contained -t html5 --css=style/common.css --css=style/html.css"
  odt_settings = "-o #{odt_file} --self-contained -t odt"

  file_string = files.join(' ')

  formats = [epub_settings, html_settings, odt_settings]

  formats.each do |settings|
    `pandoc #{common_settings} #{settings} #{file_string}`
  end
  puts "Done"
end

task :default => :pandoc

desc 'make a pdf from the html'
task :pdf do
  wkhtmltopdf_path = `which wkhtmltopdf`.chomp # check for dependency before trying to make pdf
  raise 'wkhtmltopdf not installed. brew install wkhtmltopdf' if wkhtmltopdf_path.length == 0

  html_file = File.join(base_dir, 'output', "#{book_filename}.html")
  pdf_file = File.join(base_dir, 'output', "#{book_filename}.pdf")

  Rake::Task["pandoc"].execute unless File.exists?(html_file)

  puts "you may need to ctrl-c this, but it will still work"

  `wkhtmltopdf #{html_file} #{pdf_file}`
end

desc 'check style'
task :style do
  ok = true
  loop_over_content_files do |file|
    content = File.read(file)
    if content.scan(/TODO/).length > 0
      puts "TODO left in #{file}"
      ok = false
    end
    if content.scan(/\.  /).length > 0
      puts "Two spaces after a period in #{file}"
      ok = false
    end
    if content.scan(/ chef /).length > 0
      puts "Lowercase Chef in #{file}"
      ok = false
    end
    if content.scan(/ capistrano /).length > 0
      puts "Lowercase Capistrano in #{file}"
      ok = false
    end
  end
  puts "Everything checks out" if ok
end

