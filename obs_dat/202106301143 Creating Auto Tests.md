#flexbricks 

# First steeps in writing auto tests

```ad-example
title: Important classes
collapse: open
- namespace PlmonFuncTestNunit.Base_Classes: `SettingBrowser.cs`
- namespace SetUp: `DriverInitialize.cs`, `BaseFixture.cs`
```

==Each of tests must be tested in three languages: English, Chinese, German.==

To change language need go to:


```ad-success
title: BaseFixture class (Changing language for tests)
collapse: open
```c#
...Other code

InitWebDriverAndLogin(){
//Language is an enum. Change type of language and rebuild solution
	postGreSQL.ChangeLanguage(
		UserLocaleAndTime.GetLanguageString(Language.English),
		userNameApp,UserLocaleAndTime.CurrentTimeZone); 
}

...Other code

```


==I can't see the result of executing my test.==

Default settings allow to see results of testing only for running in debug mode, to change it, and allow showing results in usual mode (just running test) you need:
```ad-success
title: DriverInitialize class (Changing visibility of running your test)
collapse: open
```c#
...Other code

public IWebDriver LocalDriver(bool isDebuggerAttached = true)  
{

//this condition hide showing for usual mode
//comment this one and look at the result
	 if (!isDebuggerAttached)  
	 {  
		chromeOptions.AddArguments("headless");  
	 }

}
...Other code

```


==I was asked to run tests using only local settings==

Default settings execute all tests using `browserstack`. It means that you can use third-party resources and capacities during you run test. They allow to run test in different modes, and for different devices.

```ad-success
title: SettingBrowser class (Switching to local mode)
collapse: open
```c#
...Other code
//Look at the origin property
public static IEnumerable TestEnvironment{  

get
{
	yield return new TestFixtureData(Profile.browserstack, "chrome", "");
	//For local tests you can make the property like below:
  //yield return new TestFixtureData(Profile.local, "NOheadless", "");
}

}

...Other code

```

```ad-warning
title: Check before start testing
collapse: open

After changing don't forget to checkout `[TestFixtureSource]` attribute it the header of a test class.

Go to tests you need to run, and check if they use TestEnvironment property in the attribute. 

```dotnet
//Good Example
[TestFixtureSource(
	typeof(SettingBrowser),
	nameof(SettingBrowser.TestEnvironment)
)]

```
