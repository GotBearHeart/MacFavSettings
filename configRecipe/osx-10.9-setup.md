# Mac OS X 10.9 Mavericks

Custom recipe to get OS X 10.9 Mavericks running from scratch, setup applications and developer environment. I use this gist to keep track of the important software and steps required to have a functioning system after a semi-annual fresh install.

## Install Software

The software selected is software that is "tried and true" --- software I need after any fresh install. I often install other software not listed here, but is handled in a case-by-case basis.

### Install from App Store

* [Airmail](https://itunes.apple.com/us/app/airmail/id573171375?mt=12&uo=4)
* [Aperture](https://itunes.apple.com/us/app/aperture/id408981426?mt=12&uo=4)
* [Degrees](https://itunes.apple.com/us/app/degrees/id430173763?mt=12&uo=4)
* [Divvy](https://itunes.apple.com/us/app/divvy-window-manager/id413857545?mt=12&uo=4)
* [Opera](https://itunes.apple.com/us/app/opera/id404764921?mt=12&uo=4)
* [Pages](https://itunes.apple.com/us/app/pages/id409201541?mt=12&uo=4)
* [Skitch](https://itunes.apple.com/us/app/skitch-snap.-mark-up.-share./id425955336?mt=12&uo=4)
* [Twitter](https://itunes.apple.com/us/app/twitter/id409789998?mt=12&uo=4)
* [WiFi Explorer](https://itunes.apple.com/us/app/wifi-explorer/id494803304?mt=12&uo=4)
* [WiFi Signal](https://itunes.apple.com/us/app/wifi-signal/id525912054?mt=12&uo=4)
* [Todoist](https://itunes.apple.com/us/app/todoist-to-do-list-task-list/id585829637?mt=12&uo=4)
* [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12&uo=4)

### Install from Third-Party Websites

* Browsers
	* Chrome (installed via Cask)
	* [Firefox](http://firefox.com)
	* Opera (installed via App Store)
	* [Webkit](http://webkit.org)

* Development
	* [Dropbox](https://www.dropbox.com/install2)
	* [GitHub](http://mac.github.com)
	* [LiveReload](http://livereload.com)
	* [LiveReload Extensions](http://help.livereload.com/kb/general-use/browser-extensions)
	* [Sublime Text 3](http://www.sublimetext.com/3)

* Utilities
	* [1Password](https://agilebits.com/onepassword/mac)
	* [GrandPerspective](http://grandperspectiv.sourceforge.net/)
	* [HipChat](https://www.hipchat.com/downloads)
	* iTerm 2 (installed via Cask)
	* [Little Snitch](http://www.obdev.at/products/littlesnitch/download.html)
	* [Quicksilver](http://qsapp.com)
	* [Skype](http://www.skype.com/en/download-skype/skype-for-computer/)
	* [Spotify](https://www.spotify.com/us/download/mac/)
	* [Transmit](http://panic.com/transmit)

* Virtualization
	* Parallels Desktop (installed via Cask)

Fonts
-----
[Mensch coding font](http://robey.lag.net/2010/06/21/mensch-font.html)

#Xcode Command Line Tools

`Xcode > Preferences > Downloads > Command Line Tools`


#Homebrew

## Install Homebrew
```bash
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
```

## Install Homebrew extension Cask
```bash
brew install caskroom/cask/brew-cask
```

## Install common applications via Homebrew
*Databases are installed later.*
```bash
brew install ack autojump automake colordiff curl git git-flow \
             hub icoutils imagemagick libmemcached memcached openssl ossp-uuid qt \
             readline redis tmux wget
```

## Install applications via Homebrew Cask
```bash
brew cask install anvil
brew cask install atom
brew cask install authy-bluetooth
brew cask install awareness
brew cask install bartender
brew cask install battery-guardian
brew cask install github
brew cask install google-chrome
brew cask install hipchat
brew cask install joinme
brew cask install iterm2
brew cask install parallels
brew cask install rescuetime
brew cask install rubymine
brew cask install satellite-eyes
brew cask install sidestep
brew cask install sonos
brew cask install spotify
brew cask install steam
brew cask install testflight
brew cask install vagrant
brew cask install vagrant-manager
brew cask install virtualbox
```

#Shell

Install custom .dotfiles
```bash
git clone git@github.com:kevinelliott/.dotfiles.git ~/.dotfiles
~/.dotfiles/install.sh
```

Update .bash_profile
```bash
echo 'source ~/.dotfiles/base.sh' >> ~/.bash_profile
```

# OS X Preferences

```bash

#Set a blazingly fast keyboard repeat rate
defaults write NSGlobalDomain KeyRepeat -int 0.02

#Set a shorter Delay until key repeat
defaults write NSGlobalDomain InitialKeyRepeat -int 12

#Add a context menu item for showing the Web Inspector in web views
defaults write NSGlobalDomain WebKitDeveloperExtras -bool true

#Show the ~/Library folder
chflags nohidden ~/Library

#Store screenshots in subfolder on desktop
mkdir ~/Desktop/Screenshots
defaults write com.apple.screencapture location ~/Desktop/Screenshots
```

Set hostname
------------
`sudo scutil --set HostName kevin-rmbp`


#Git

Setup Github
------------
```bash
ssh-keygen -t rsa -C "kevin@welikeinc.com"

# Copy ssh key to github.com
subl ~/.ssh/id_rsa.pub

# Test connection
ssh -T git@github.com

# Set git config values
git config --global user.name "Kevin Elliott"
git config --global user.email "kevin@welikeinc.com"
git config --global github.user kevinelliott
git config --global github.token your_token_here

git config --global core.editor "subl -w"
git config --global color.ui true
```


# Sublime Text

Add Sublime Text CLI
--------------------

```bash
mkdir -p ~/bin && ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" ~/bin/subl
```

Install Package Control
-----------------------
```python
import urllib2,os; pf='Package Control.sublime-package'; ipp=sublime.installed_packages_path(); os.makedirs(ipp) if not os.path.exists(ipp) else None; urllib2.install_opener(urllib2.build_opener(urllib2.ProxyHandler())); open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read()); print 'Please restart Sublime Text to finish installation'
```

Install Packages
----------------
[BracketHighlighter](https://github.com/facelessuser/BracketHighlighter)
[CoffeeScriptHaml](https://github.com/jisaacks/CoffeeScriptHaml)


Install Soda Theme
----------------------
```bash
git clone git://github.com/buymeasoda/soda-theme.git ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/Theme\ -\ Soda
```

Install Tomorrow Theme
----------------------
```bash
git clone git://github.com/chriskempson/textmate-tomorrow-theme.git ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/Color\ Scheme\ -\ Tomorrow
```

Settings
--------

**Sublime Text > Preferences > Settings - User**

```json
{
    "close_windows_when_empty": true,
    "color_scheme": "Packages/Color Scheme - Tomorrow/Tomorrow-Night-Eighties.tmTheme",
    "draw_indent_guides": false,
    "font_face": "Mensch",
    "font_size": 18,
    "highlight_modified_tabs": true,
    "show_tab_close_buttons": false,
    "tab_size": 2,
    "spell_check": false,
    "theme": "Soda Light.sublime-theme",
    "word_separators": "./\\()\"'-:,.;<>~!@#%^&*|+=[]{}`~?"
}
```

Key Bindings
------------

```json
[
	{ "keys": ["super+b"], "command": "expand_selection", "args": {"to": "brackets"} },
	{ "keys": ["super+f"], "command": "show_panel", "args": {"panel": "replace"} },
	{ "keys": ["super+alt+f"], "command": "show_panel", "args": {"panel": "find"} }
]
```


Snippets
--------
```bash
git clone git@github.com:bytestudios/sublime-snippets.git "/Users/Joel/Library/Application Support/Sublime Text 2/Packages/Byte"
```


## Server


### Docker
```bash
brew install docker boot2docker
boot2docker init
boot2docker up
```

### MySQL

```bash
brew install mysql
brew pin mysql
```

### MySQL Settings

```bash
# Copy launch agent into place
mkdir -p ~/Library/LaunchAgents && cp /usr/local/Cellar/mysql/VERSION/homebrew.mxcl.mysql.plist ~/Library/LaunchAgents/

# Edit launch agent and set both keepalive and launch at startup to false
vi ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist

# Inject launch agent
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist

# Set up databases to run as your user account
unset TMPDIR && mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp

# Start mysql
start mysql

# Secure mysql
/usr/local/Cellar/mysql/VERSION/bin/mysql_secure_installation
```


### PostgreSQL

```bash
brew install postgres --no-ossp-uuid
brew pin postgres
```

### PostgreSQL Settings

```bash
# Initialize db if none exists already
initdb /usr/local/var/postgres

# Create launchctl script
mkdir -p ~/Library/LaunchAgents
cp /usr/local/Cellar/postgresql/VERSION/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/

# Edit launchctl script (set to not start automatically and keepalive false)
subl ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

# Inject launchctl script
launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist

# Start PostgreSQL
start pg
```

### Ruby Gems

#### libv8
```bash
brew uninstall v8
gem uninstall libv8
wget https://dl.dropboxusercontent.com/u/7919548/gems/libv8/libv8-3.11.8.17-x86_64-darwin-13.gem
gem install libv8-3.11.8.17-x86_64-darwin-13.gem
```

#### capybara-webkit
```bash
brew install -v https://raw.github.com/cliffrowley/homebrew/patched_qt/Library/Formula/qt.rb --HEAD --without-ssse3
gem install capybara-webkit -v '0.9.0'
```

![aww yeah](http://i.imgur.com/AmFax.gif)