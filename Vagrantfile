# Vagrant 1.5.1 <http://www.vagrantup.com/downloads.html>
# VirtualBox 4.3.8 <https://www.virtualbox.org/wiki/Downloads>

Vagrant.require_version '~> 1.5'

Vagrant.configure('2') do |config|
    config.vm.box = 'chef/ubuntu-13.10'
    config.vm.box_version = '~> 1.0'

    config.vm.provision :shell, inline: <<-'SH'
        set -e -x
        apt-get update
        apt-get -y install haskell-platform haskell-platform-doc
    SH

    config.vm.provision :shell, inline: <<-'SH', privileged: false
        set -e -x
        echo 'PATH="$HOME/.cabal/bin:$PATH"' > .bash_profile
        cabal update
        cabal install cabal-install
        cabal install hi hlint pointful scan stylish-haskell
        cabal install pointfree
    SH
end
