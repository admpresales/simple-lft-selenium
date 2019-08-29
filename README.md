# simple-lft-selenium

# Usage
This is a simple script to show using a Selenium test being augmented with LeanFT.

It is also a very good example of how to use LeanFT reporting.

This script has been run using the Chrome driver 2.41.  You can choose others too but just be aware i havent verified it against others.

**NOTE:** You need to be connected to the internet the first time this is executed so the chromewebdriver gets cached to your .m2 cache

This sample script uses the LeanFT for Selenium extensions available https://search.maven.org/search?q=a:leanft-selenium-java-sdk
```
        <dependency>
            <groupId>com.microfocus.adm.leanft</groupId>
            <artifactId>leanft-selenium-java-sdk</artifactId>
            <version>1.0</version>
        </dependency>
```

Check which versions of libraries you have available and make the appropriate changes in the pom.xml

```
        <junit.ver>4.12</junit.ver>
        <se.ver>3.14.0</se.ver>
        <webdrivermanager.ver>3.0.0</webdrivermanager.ver>
        <slf4j.ver>1.7.25</slf4j.ver>
```
## Overview
The test starts by using LeanFT for Selenium, then connects using "pure" LeanFT

## Reporting
This script uses the LeanFT reporting mechanism. Note that it sets screen capture to every step, but this only applies to LeanFT steps, not Selenium steps. For the reporting to work, the test explicitly initializes the LeanFT sdk in @before and cleans up in @after

Sometimes it seems like the View last test result is disabled after running. If that occurs, the result is in the RunResults directory. It is easy to view within IntelliJ by opening a terminal, doing a 
```
        cd RunResults
        google-chrome runresults.html
```

### Selenium Web Driver Manager
This script makes use of a utility that simplifies getting and setting the webdriver (Chrome in this case).  Using this approach makes the assumption that you have access to the internet when this script is run the first time so the drivers can automatically be downloaded and added to your local .m2 cache.

More details about the utility can be found:

* https://github.com/bonigarcia/webdrivermanager#webdrivermanager-as-java-dependency
* https://stackoverflow.com/questions/7450416/selenium-2-chrome-driver
