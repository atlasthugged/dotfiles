# dotfiles

These dotfiles are refinements on the thoughtbot [dotfiles][thoughtbot dotfiles], and are managed using their config file managment utility, [Rcm][rcm github].

### Installation Instructions
 Clone thoughtbot [dotfiles][thoughtbot dotfiles] into home directory. 
 
    mkdir thoughtbot
    cd thoughtbot
    git clone https://github.com/thoughtbot/dotfiles.git

Install [Rcm][rcm github] using instructions on github repo.

Run rcm on thoughtbot dotfiles to copy them into your home directory

    rcup -d thoughtbot/dotfiles -x README.md -x LICENSE  

Clone this repo into dotfiles_local

    mkdir ~/dotfiles_local
    git clone https://github.com/atlasthugged/dotfiles.git "$HOME/dotfiles_local"

Run rcm on personal dotfiles.

    rcup -d $HOME/dotfiles_local -x README.md
    
### Prezto
If you need to redo the [Prezto][prezto github] installation, the installation instructions must be modified to work with the thoutbot dotfiles and rcm.

First, clone Prezto into the personal dotfiles directory:

    git clone --recursive https://github.com/sorin-ionescu/prezto.git "$$HOME/dotfiles_local/.zprezto"

Then run the following in the command line to create the proper .local files for rcm to use:

    setopt EXTENDED_GLOB
    for rcfile in "${ZDOTDIR:-$HOME}"/dotfiles_local/zprezto/runcoms/^README.md(.N); do
      ln -s "$rcfile" "${ZDOTDIR:-$HOME}/dotfiles_local/${rcfile:t}.local"
    done

Run rcm on local dotfiles directory

    rcup -d $HOME/dotfiles_local


[thoughtbot dotfiles]: https://github.com/thoughtbot/dotfiles
[rcm github]: https://github.com/thoughtbot/rcm
[prezto github]: https://github.com/sorin-ionescu/prezto
