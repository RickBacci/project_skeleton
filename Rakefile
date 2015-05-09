require "rake"
require "rake/testtask"



task :test do
  Dir.glob('./test/**/*_test.rb') { |file| require file }
end

task default: [:test]


task :create do  # rake create project_name
  name = ARGV.last


  `cp("../copy_only_project_skeleton", "../#{name}")`
  `cd("../#{name}")`

  puts "Creating #{name} project files."
  task name.to_sym do

    Dir.glob(["./**/*.rb", "./*.md", ".ruby-gemset"]) do |file_name|
      puts "working on: #{file_name}..."

      text = File.read(file_name)

      if text.match(/class NAME/)
        text = text.gsub(/class NAME/, "class #{name.capitalize}")
      end

      if text.match(/NAME\.new/)
        text = text.gsub(/NAME\.new/, "#{name.capitalize}.new")
      end

      if text.match(/NAMETest/)
        text = text.gsub(/NAMETest/, "#{name.capitalize}Test")
      end

      if text.match(/NAME\.rb/)
        text = text.gsub(/NAME\.rb/, "#{name.downcase}.rb")
      end

      if text.match(/NAME_test/)
       text = text.gsub(/NAME_test/, "#{name.downcase}_test")
      end

      if text.match(/NAME/)
        text = text.gsub(/NAME/, "#{name.downcase}")
      end
      File.open(file_name, "w") {|file| file.puts text }
    end
  end

  name = name.downcase
  mv("./test/NAME_test.rb", "./test/#{name}_test.rb")
  mv("./lib/NAME.rb", "./lib/#{name}.rb")

  #cp("../copy_only_project_skeleton", "../#{name}")
end
