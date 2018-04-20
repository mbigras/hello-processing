desc 'Open index.html and run watch task'
task :default do
  `open index.html`
  Rake::Task[:watch].invoke
end

require 'filewatcher'
desc 'Watch sketch.js, refreshing chrome on changes'
task :watch do
  refresh_chrome = <<-APPLESCRIPT
  # https://gist.github.com/LawrenceJones/8906909
  tell application "Chrome" to tell the active tab of its first window
      reload
  end tell
  APPLESCRIPT
  puts "watching sketch.js, refreshing chrome on changes..."
  Filewatcher.new(['sketch.js']).watch do
    `osascript -e '#{refresh_chrome}'`
  end
end