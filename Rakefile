require 'tmpdir'

task :build do
  # Dir.mktmpdir("mutt-") do |tmpdir|
  tmpdir = Dir.mktmpdir("mutt-")
    Dir.chdir(tmpdir) do |dir|
      sh "curl ftp://ftp.mutt.org/mutt/devel/mutt-1.5.21.tar.gz -s -o - | tar zxf -"

      build_command = [
        "mkdir /app/Mail",
        "./configure --enable-imap --prefix=/app/mutt-1.5.21 --with-mailpath=/app/Mail",
        "make",
        "make install",
        "mv /app/mutt-1.5.21 /app/vendor/mutt-1.5.21"
      ].join(" && ")

      sh "vulcan build -v -o mutt-1.5.21.tgz --source mutt-1.5.21 -c \"#{build_command}\""
    end
  # end
end
