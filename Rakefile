require "rake"
require "rake/testtask"



task :test do
  Dir.glob('./test/**/*_test.rb') { |file| require file }
end

task default: [:test]


task :create do  # rake create project_name
  name = ARGV.last

  puts "Creating #{name} project files."
  task name.to_sym do
    name = name.downcase

    Dir.glob(["./**/*.rb", "./*.md", ".ruby-gemset"]) do |file_name|
      puts "working on: #{file_name}..."

      text = File.read(file_name)

      if text.match(/class NAME/)
        new_contents = text.gsub(/class NAME/, "class #{name.capitalize}")
        File.open(file_name, "w") {|file| file.puts new_contents }
        text = File.read(file_name)
      end

      if text.match(/NAME\.new/)
        new_contents = text.gsub(/NAME\.new/, "#{name.capitalize}.new")
        File.open(file_name, "w") {|file| file.puts new_contents }
        text = File.read(file_name)
      end

      if text.match(/NAMETest/)
        new_contents = text.gsub(/NAMETest/, "#{name.capitalize}Test")
        File.open(file_name, "w") {|file| file.puts new_contents }
        text = File.read(file_name)
      end

      if text.match(/NAME\.rb/)
        new_contents = text.gsub(/NAME\.rb/, "#{name.downcase}.rb")
        File.open(file_name, "w") {|file| file.puts new_contents }
        text = File.read(file_name)
      end

      if text.match(/NAME_test/)
        new_contents = text.gsub(/NAME_test/, "#{name.downcase}_test")
        File.open(file_name, "w") {|file| file.puts new_contents }
        text = File.read(file_name)
      end

      if text.match(/NAME/)
        new_contents = text.gsub(/NAME/, "#{name.downcase}")
        File.open(file_name, "w") {|file| file.puts new_contents }
      end
    end
  end

  name = name.downcase
  mv("./test/NAME_test.rb", "./test/#{name}_test.rb")
  mv("./lib/NAME.rb", "./lib/#{name}.rb")

  #mv("./lib/NAME/", "./lib/#{name}")
  #mv("./lib/#{name}/NAME.rb", "./lib/#{name}/#{name}.rb")

end
