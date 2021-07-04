#WebApp #Blazor


https://www.youtube.com/watch?v=gPkKxY8838E
On set up select Blazor Server App

- it sends less packets
- it is more secured
- it allows to have more control for content

```ad-warning
title: While you adding new component
collapse: open

When you adding new component you must import it:
Go to Shared/Import.razor
Write here
```dotnet

@using BlazorApp.[Name of import folder]

It allows you to create pages in the folder as a component
And then use them as components anywhere.
```

For every razor page you can create .cs code behind

```ad-example
title: Creating code behind
collapse: open

We have a page with name Counter.razor
For this page create .cs file with name: Counter.razor.cs
This action will create hierarcy of files and will move
your .cs file as a child of razor page

To use this class you need to inherits from ComponentBase:



```

```ad-info
title: Counter.razor
collapse: open
```dotnet

@page "/counter"  
@inherits CounterRazor  
<h1>Counter</h1\>  
  
<p>Current count: @currentCount</p>  
<button class="btn btn-primary" @onclick="IncrementCount">Click</button\>
<select @onchange="Callback">
```

```ad-info
title: CounterRazor.cs
collapse: open
```dotnet
using Microsoft.AspNetCore.Components;  
  
namespace BlazorApp.Pages  
{  
 public class Counter_razor: ComponentBase  
 {  
   protected int currentCount \= 0;  

//method than increment value:
	protected void IncrementCount()  
	{  
		currentCount++;  
	}  
  
//to catch changes event:  
	protected void Callback(ChangeEventArgs obj)  
	{  
	 	var result= obj.Value.ToString();  
	}       
 }  
}
```

