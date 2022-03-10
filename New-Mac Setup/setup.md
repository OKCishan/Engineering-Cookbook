* Setting up Sublime:
``` sudo ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/.``` creates a symlink for subl command

* To install and setup services on your machine directly, please follow the below steps:

* Start with installing Xcode (```xcode-select --install``` or you can install directly from apple app store, CLI preffered) (might take some time~30 mins)

* Later installing Homebrew using ```https://www.digitalocean.com/community/tutorials/how-to-install-and-use-homebrew-on-macos```
  (if already installed check version using ```brew config```)
  (Note: rake gets installed with homebrew default so would not be needed to installed specially)

* Setup go env - 
  For M1 chip laptops, install arm64 based go pkg, add your PATH to your ~/.zshrc file , ```export PATH=$PATH:/usr/local/go/bin``` ```source ~/.zshrc```
