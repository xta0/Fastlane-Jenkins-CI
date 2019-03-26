# Fastlane-Jenkins-CI

A guideline for setting up the CI environment for iOS with Fastlane and Jenkins in macOS.

### Jenkins

- Install Jenkins via Homebrew

```
brew install jenkins
```
- start jenkins server by typing `jenkins` in commandline. Open your browser and go to `http://localhost:8080`. Enter password for the first time use, jenkins will create a configuration file under user's root folder. To see the initial password, type command

```
cat ~/.jenkins/secrets/initialAdminPassword
```

- Login to Jenkins and finish the configuration process
  1. Select `Install suggested plugins` option that will cover the most important plugins
  2. Go to **admin > Configure** to change the initial password.
  3. Ready to go
  
### Fastlane

[Fastlane](https://github.com/fastlane/fastlane) is an automation tool for mobile developers to build, deploy and release their apps in a simpy way. To install fastlane, type `brew` command:

```
brew cask install fastlane
```
Go to the root folder of project on terminal and launch next command line:

```
fastlane init
```

After running this command, you'll have to select which option you want to, In this case, we'll select fourth option **manual setup (4)**. This will generate a `fastlane` folder and inside that you will find two files called `Appfile` and `Fastfile`. Well, now we are going to replace all content of your Fastfile with the code below:

```ruby
default_platform(:ios)
platform :ios do
  desc "Description of what the lane does"
  lane :generate_ipa_develop do
    build_ios_app(
      configuration: "Debug",
      scheme: "Test",
      clean: true,
      export_method: 'development',
      output_directory: "~/Desktop", # Destination directory. Defaults to current directory.
      output_name: "fastlane_jenkins.ipa",
    )
  end
end
```
This script enable a fastlane command - `fastlane generate_ipa_develop` that generates a file .ipa and locate it on Desktop.

### Ngrok

[Ngrok]() is a tool that can let you expose your local server to public, such that your jenkins server can handle the webhook from Github. Follow the steps in [documentation page](https://dashboard.ngrok.com/get-started).

### Setup the Github webhook and the everything else

Follow the setup in this [article](https://medium.com/@litoarias/continous-integration-continous-delivery-for-ios-with-jenkins-and-fastlane-fd2906956b20)



