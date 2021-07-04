#WebApp #Blazor

On set up select Blazor Server App

- it sends less packets
- it is more secured
- it allows to have more control for content


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
