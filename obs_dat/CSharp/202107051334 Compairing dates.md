#Csharp 

```ad-info
title: New description
collapse: open
```dotnet
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Globalization;
using System.Linq;
using System.Text.Json;
using static System.Console;
using static System.DateTime;

namespace Dates
{
class Program
{
	static void Main(string[] args)
	{
		HashSet<string> expectedDates = new HashSet<string>
		{"2021-07-01 22:12 PM",
		"01.07.2021 21:02",
		"01.08.2021 09:04:04 AM"};
		
		HashSet<string> actualDates = new HashSet<string>
		{"2021-07-01 22:12 PM",
		"01.07.2021",
		"01.08.2021 09:04"};
		
		var convertedExpectedDates =
		expectedDates.Select(Convert.ToDateTime).ToList();
		
		var convertedActulDates =
		actualDates.Select(Convert.ToDateTime).ToList();

 		var Actual_Expected = convertedActulDates.Zip(
		convertedExpectedDates,
		(n, w) => new { 
			convertedActulDates = n,
			convertedExpectedDates = w });
		
		convertedExpectedDates.ForEach(
		c=>WriteLine($"\tExpected Dates:{c}"));

		WriteLine("------------------------------------------------");
		convertedActulDates.ForEach(
		a => WriteLine($"\tActualDates:{a}"));

		foreach(var a_e in Actual_Expected)
		{
			CompareDates(
				a_e.convertedActulDates,
				a_e.convertedExpectedDates);
		}
		var result = TestForNullsForNulls(null, null);
		WriteLine(result);
}

	private static void CompareDates(
	DateTime actualDate, DateTime expectedDate)
{
	WriteLine("\n---------------CompareDates-----------------");
	if (actualDate.TimeOfDay.Equals(TimeSpan.Zero))
		expectedDate = new DateTime(
			day:expectedDate.Day,
			month:expectedDate.Month,
			year:expectedDate.Year, hour:0,minute:0,second:0);
	
	ForegroundColor = ConsoleColor.Yellow;
	WriteLine(
	$"Params:\tActual:{actualDate}| Expected:{expectedDate}\n");
	ResetColor();

	ForegroundColor = ConsoleColor.Red;
	WriteLine(DateTime.Equals(actualDate, expectedDate)? 		
	$"\tDates are equal\nActual:{actualDate}\nExpected: {expectedDate}"
	: "Dates are not equal");
	ResetColor();

}

//check if method will get null params
	private static bool TestForNullsForNulls(string i, string a)
	{
		TryParseExact(
		i, "yyyy-MM-dd HH:mm", CultureInfo.InvariantCulture,
		DateTimeStyles.None, out var result1);
		
		TryParseExact(
		a, "yyyy-MM-dd HH:mm", CultureInfo.InvariantCulture,
		DateTimeStyles.None, out var result2);

		Write(result1);
		Write(result2);

 		var time1 = Convert.ToDateTime(
		i, CultureInfo.InvariantCulture);

 		var time2 = Convert.ToDateTime(
		a, CultureInfo.InvariantCulture);

 		WriteLine(time1.ToString(), time2.ToString());

 		return DateTime.Equals(time1, time2);

	}

 }

}
```
