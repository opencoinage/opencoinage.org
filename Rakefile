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

file 'rdf.n3' => 'rdf.ttl' do
  sh "cp rdf.ttl rdf.n3"
end

file 'rdf.nt' => 'rdf.ttl' do
  sh "rapper -i turtle -o ntriples rdf.ttl | sort > rdf.nt"
end

file 'rdf.json' => 'rdf.ttl' do
  sh "rapper -i turtle -o json rdf.ttl | jsonpretty > rdf.json"
end

file 'rdf.rdf' => 'rdf.ttl' do
  sh "rapper -i turtle -o rdfxml-abbrev rdf.ttl > rdf.rdf"
end

file 'rdf.xml' => 'rdf.nt' do
  require 'rdf/trix' # @see http://rubygems.org/gems/rdf-trix
  RDF::TriX::Writer.open('rdf.xml') do |writer|
    RDF::NTriples::Reader.open('rdf.nt') do |reader|
      reader.each_statement { |statement| writer << statement }
    end
  end
end

file 'rdf.dot' => 'rdf.ttl' do
  sh "rapper -i turtle -o dot rdf.ttl > rdf.dot"
end

file 'rdf.png' => 'rdf.dot' do
  sh "dot rdf.dot -Tpng -o rdf.png"
end

desc "Generates rdf.{n3,nt,json,rdf,xml,dot,png} from rdf.ttl."
task :rdf => %w(rdf.n3 rdf.nt rdf.json rdf.rdf rdf.xml rdf.dot rdf.png)
