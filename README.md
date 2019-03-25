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

- Login to Jenkins and start configuration process
  - select `Install suggested plugins` option will cover the most important plugins

### Ngrok

[Ngrok]() is a tool that can let you expose your local server to public, such that your jenkins server can handle the Github webhook and run the `fastlane`. Follow the [Setup & Installation](https://dashboard.ngrok.com/get-started) guidelines to setup the ngrok service



### Resources
- [Jenkins and Fastlane - for Continuous integration and continuous delivery in iOS](https://medium.com/@litoarias/continous-integration-continous-delivery-for-ios-with-jenkins-and-fastlane-fd2906956b20)
