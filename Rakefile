desc "Builds the static HTML version of the site"
task :build do
  sh "markdoc build"
  sh "rm -rf .html/Rakefile .html/README.* .html/tmp"
  sh "find .html -name '*~' | xargs rm"
end
