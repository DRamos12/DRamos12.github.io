---
layout: post
title: Setting Up Karma and Jasmine with AngularJs
---

First things what are Karma and Jasmine? Karma is a Javascript test runner who's goal is bring productive test environment to developers, an environment in which you don't have to load configurations you simply write code and get instant feedback from tests. Jasmine is an open source testing framework for Javascript. It is designed for easy to read syntax and to run on any Javascript-enabled platform.

In order to install these programs the first you'll want to do is install karma globally and it's dependencies.


    $npm install -g karma-cli
    $npm install karma --save-dev
    $npm install karma-jasmine --save-dev


If you are using Karma and Jasmine with angular you'll need to install Angular as well as Angular Mocks. Angular mocks provides convenient mock services that makes unit testing on Angular easier. You can do so by running:


    $bower install angular-mocks --save-dev


After that you'll create your Karma configuration file with:


    $karma init


When running init, you'll received many prompts to cycle through but you can mostly go with the defaults (by repeatedly hitting enter).

The prompts are as follows:

**Which testing framework do you want to use? **

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Default value, Jasmine

**Do you want to use Require.js ? **

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Default value, No

**Do you want to capture any browsers automatically ?**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Default value, Chrome

**What is the location of your source and test files ?**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Enter location of your test files

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Don't worry if you don't remember just yet, we can directly edit the config file at a later stage.

**Should any of the files included by the previous patterns be excluded ? **

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Default value, No

**Do you want Karma to watch all the files and run the tests on change ? **

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Default value, Yes

**The config file called karma.conf.js will be created in the root folder.**

After the init script has completed, you'll be able to manually append the files in you need.  The order you append the files is very important. You must


    files: [
      //files pointing to angular
      'bower_components/angular/angular.js',
      'bower_components/angular-mocks/angular-mocks.js',

      //files to be tested
      'js/app.js',

      //location of tests
      'tests/*.js'
    ],


The above configuration assumes that your application depends on the Angular core and that your main application logic resides in js/app.js, and that your Jasmine unit tests are kept in the tests/ directory.

To test things out, create an example test file called example.js in the tests/ directory with the following contents:


    describe('test', function() {
      it('should be true', function() {
        expect('example').toBe('example');
      });
    });


When you’re done, save the file, and run Karma:


    $karma start


Happy testing!
