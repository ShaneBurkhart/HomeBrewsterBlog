desc "Pings PING_URL to keep a dyno alive"
task :dyno_ping do
  require "net/http"
  if ENV['PING_URL']
    puts "Running upkeep ping!"
    uri = URI(ENV['PING_URL'])
    Net::HTTP.get_response(uri)
  else
    puts "No PING_URL found..."
  end
end

task :post do
  require "date"

  STDOUT.puts "What is the title of your post?:"
  post_name = STDIN.gets.chomp
  doc = [
    "---",
    "layout: post",
    "published: false",
    "title: #{post_name}",
    "---"
  ].join("\n")
  post_name  = post_name.downcase.chomp(".").chomp(" ").gsub(" ", "-")
  today = Date.today
  file_name = "#{today.year}-#{today.month}-#{today.day}-#{post_name}.md"
  STDOUT.puts "Creating file #{file_name}"
  File.open("_posts/#{file_name}", 'w') {|f| f.write(doc) }
end
