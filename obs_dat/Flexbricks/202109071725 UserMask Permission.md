#flexbricks 

```ad-info
title: Usage
collapse: open
```dotnet

Public Module Program
	Public Sub Main(args() As string)
		
		
		For index As Integer = 1 To 100
       Console.Write(index)
       Console.Write(" and 8 - ")
       Console.Write(index and 1<<3)
       
       Console.Write("  PLM# ")
       
       Console.Write(index)
       Console.Write(" and 1 - ")
       Console.Write(index and 1<<1)
       
       Console.Write("  VSM# ")
       
       Console.Write(index)
       Console.Write(" and 2 - ")
       Console.Write(index and 1<<2)
       Console.WriteLine()
		Next

	End Sub
End Module


//Result
1 and 8 - 0  PLM# 1 and 1 - 0  VSM# 1 and 2 - 0
2 and 8 - 0  PLM# 2 and 1 - 2  VSM# 2 and 2 - 0
3 and 8 - 0  PLM# 3 and 1 - 2  VSM# 3 and 2 - 0


Acess denied if in line: 
1 and 8 - 0  PLM# 1 and 1 - 0  VSM# 1 and 2 - 0

Convert.ToBoolean((1 and 8) = 0)) - acess denied

```


```ad-info
title: Some info
collapse: open
```sql

--	Usage Mask
--	2 - PLM users only
--	8 - SRM users only
--	10 - SRM+PLM users
-- etc

select * from sapplicationpage where id in ('1ee035b1-c5a1-43d0-90f5-54ed1e8506de','1f12d004-5045-4e89-9ae1-8322609abe7b','49aba1d4-ae4c-4591-b8ac-83b15dc145a4');
UPDATE public.sapplicationpage
SET usagemask=10
WHERE id='1ee035b1-c5a1-43d0-90f5-54ed1e8506de'::uuid;

```
