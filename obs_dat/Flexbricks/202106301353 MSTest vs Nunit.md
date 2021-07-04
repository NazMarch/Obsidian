#flexbricks 
```ad-quote
title: 1. Type of project
collapse: open
#### MsTest 
`Needs a specific project type.`

‘Test Project’, which means you will automatic have the right reference and the correct project type guid.

#### Nunit
`Does not require any specific project type.`

But most of the time people will add a class library to separate their code from their unit tests. You need to reference the nunit.framework.dll yourself. But if you use nuget this will be done for you automatic while installing NUnit.


**Conclusion**: If you go for out of the box experience i would say MsTest wins this section, otherwise i would say a draw between MsTest and NUnit.
```

```ad-quote
title: 2. Attributes
collapse: open

Both frameworks separate blocks of code trough attributes.

#### MsTest

-   AssemblyInitialize, AssemblyCleanup are two special attributes that can be used to bootstrap or teardown your test assembly
-   TestClass with ClassInitialize -> TestInitialize -> TestMethod -> TestCleanup -> ClassCleanup

#### NUnit

-   TestFixture with TestFixtureSetup -> Setup -> Test -> TearDown -> TestFixtureTearDown


**Conclusion**: Apart for the missing AssemblyInitialize and Cleanup both frameworks are on par with each other, i must admit MsTest wins this section also, but i would like to point out the fact that having to bootstrap or teardown your test assembly is probably a smell that you are doing something wrong.

```


```ad-quote
title: 3. Categorize, Ignore
collapse: open

#### MsTest

-   TestCategory
-   Ignore
-   Timeout
-   ExpectedException

#### NUnit

-   Category
-   Ignore
-   Timeout
-   ExpectedException : Although this attribute has been deprecated and replaced by Assert.Throws it has more options than the MsTest version

**Conclusion**: I think both frameworks are on par with each other if you look at the basic attributes, but NUnit still has some gems, like Explicit, which will make the test run only when explicitly told so, but there are many more like SetCulture and SetUiCulture. In terms of language completeness i think NUnit wins this section.

```


```ad-quote
title: 4. Assert
collapse: open
#### MsTest

-   Assert, StringAssert and CollectionAssert

#### NUnit

-   Assert, StringAssert and CollectionAssert, Exception Asserts ( Assert.Throws, Assert.Catch etc), File Asserts, Directory Asserts

**Conclusion**: Again the basics are present in both frameworks but the language richness of NUnit makes it to win this section.

```

```ad-quote
title: 5. Extensibility
collapse: open

Clearly NUnit wins this section see [http://www.nunit.org/index.php?p=extensibility&r=2.5.10](http://www.nunit.org/index.php?p=extensibility&r=2.5.10)

```

```ad-quote
title: 6. Data driven tests
collapse: open


#### MsTest

-   Takes a file based approach with DataSource to provide testing values, which is nice but you will always have to need to add csv, excel or xml data file

#### NUnit

-   Does not have a build in support for filebased datasources but it does have many attributes that can be used to provide values in your test code directly like TestCase and TestCaseSource

**Conclusion**: This section depends on personal preference. For me i prefer the easy way of NUnit because i see no real point in using a file based approach

```


