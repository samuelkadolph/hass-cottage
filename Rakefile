RSYNC_OPTIONS = %w[--delete --human-readable --keep-dirlinks --prune-empty-dirs --recursive --times --verbose --whole-file --include=*/ --include=*.yaml --exclude=.git --exclude=*]

desc "Deploy to all"
task "deploy:all"

task default: "deploy:all"

%w[copper.cottage.kadolph.io].each do |h|
  desc "Deploy to #{h}"
  task "deploy:#{h}" do
    deploy(h)
  end
  task "deploy:all" => ["deploy:#{h}"]
end

def deploy(host)
  puts("Deploying to #{host}...")
  system("rsync", *RSYNC_OPTIONS, Dir.pwd, "#{host}:/homeassistant")
end
