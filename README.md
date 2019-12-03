# Protractor with Grunt

Sometimes or actually most time we don't get to choose tools we want to work with and there are alterations we have to make the tool to work within our workplace. It could be due to coporate network, proxy, limited priviledges etc.

This is here to help guide you if your predecesor implemented this or you chose to implement it this way to limit confrontations with people. 

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

But you see ``` directConnect: true ``` and none of the above keywords. 

I think default Angular project created using ng-cli has it set to this setting as well. 

And this means it's connecting directly to the chrome or firefox browser. And it might be limited in running multiple or in variation but it's also the fastest option. Whichever option it's set up as just know how it's set up and how it's running so you don't have useless lines cluttering spaces and having extra messages like 

``` W/driverProviders - Using driver provider directConnect, but also found extra driver provider parameter(s): seleniumAddress ```

### 199 whatever driver supports only whatever version 

Okay, in my case it's saying this version of ChromeDriver only supports Chrome version 75, so obviously we need to either change the ChromeDriver version or the Chrome version. If you have a specific version you have in mind try to set both to use that version of the browser. 


