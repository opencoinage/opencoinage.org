task :default => [:build]

desc "Opens the generated index.html page in the default browser"
task :open do
  sh "open .html/index.html"
end

desc "Builds the static HTML version of the site"
task :build do
  sh "markdoc build"
  sh "rm -rf .html/Rakefile .html/README.* .html/tmp"
  sh "find .html -name '*~' | xargs rm"
end

desc "Deletes all files from markdoc's .html and .tmp directories"
task :clean do
  sh "markdoc clean-html && markdoc clean-temp"
end

desc "Starts up a markdoc server on http://127.0.0.1:8008/"
task :serve => :build do
  sh "markdoc serve"
end

desc "Uploads the static HTML output to http://opencoinage.org/"
task :upload do
  sh "rsync -azv .html/ opencoinage@opencoinage.org:sites/opencoinage.org/"
end
