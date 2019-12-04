# Protractor with Grunt

Sometimes or most time we don't get to choose tools we want to work with (or I don't know I only had jobs that I had) and there are alterations we have to make to the tool to work within our workplace. It could be due to coporate network, proxy, limited priviledges etc.

This is here to help guide you if your predecesor implemented Protractor with Grunt or you chose to implement it this way to limit confrontations with people.
## Connecting to the browser. 

In your conf.js if you followed the tutorial you might have something like 
```
    seleniumAddress: 'http://localhost:4444/wd/hub'
```
This is great if you're trying to your test across multiple browsers on multiple systems and there are other keys indicating what tool you are using like 
- sauceUser/sauceKey if you're using SauceLAbs
- browserstackUser/browserstackKey if you're running remote Selenium Servers via BrowserStack 
- seleniumServerJar for running standalone server locally. 
more about this topic @https://stackoverflow.com/questions/30600738/difference-running-protractor-with-without-selenium

Let's say you see ``` directConnect: true ``` and none of the above keywords because that's what I saw in my project. I think default Angular project created using ng-cli has ```directConnect: True``` as well . 

And this means it's connecting directly to the chrome or firefox browser. And it might be limited in running multiple or in variation but it's also the fastest option. Whichever option it's set up as just know how it's set up and how it's running so you don't have useless lines cluttering spaces and having extra messages like ``` W/driverProviders - Using driver provider directConnect, but also found extra driver provider parameter(s): seleniumAddress ```

### 199 whatever driver supports only whatever version 

Okay, in my case it's saying this version of ChromeDriver only supports Chrome version 75, so obviously we need to either change the ChromeDriver version or the Chrome version or set both to whatever version you want it to be. 

#### My command is not recognized as the name of a cmdlet, function, script file, or operable program.
Request the command to be added but if you don't want to or they deny it you use the full path of where your global package is installed. For example, ```C:/some_path/npm/webdriver-manager update```  

Here I will I'm get webdriver-manager locallly in the project and use that. 
The version of driver is going to be 77.0 variant and let's get the updated version. 
find and get whatever chrome version you have on your machine. 
```
npm install -D webdriver-manager  
node node_modules/webdriver-manager/bin/webdriver-manager --versions.chrome=77.0.3865.40 update
```

You can also run protractor by project's local package 
```
node ./node_modules/protractor/bin/protractor conf.js
```

## Adding Grunt 

Following the tutorial on Grunt, let's add Grunt and Grunt plugins to the project.  
```
npm i -D grunt grunt-contrib-jshint grunt-contrib-nodeunit grunt-contrib-uglify
```

And we're gonna set up so that running `grunt` command will run protractor 
