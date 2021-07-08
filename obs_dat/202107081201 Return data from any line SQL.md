#Csharp 

```ad-success
title: Return method
collapse: open
```dotnet

/*
Allows to retund a single line from Db according columns you've set
IMPORTANT: Data that returns are strongly ordered by your sql query
You can get data using Tuple class
REMEMBER: 
you can get any value from list by list[index] starts from 0
Query example: SELECT code, name,..FROM
Tuple example: (string code, name) tuple = (code:keyValuePair.Value[0], name: keyValuePair.Value[1])
*/
        public Dictionary<string, List<string>> ReadSingleLineWithAnyParams(string sql, string ID=null, bool IsActive=true)
        {
            string selectSQL = sql.ToLower(), idColumnName = null;
            
            int firstIndex = selectSQL.IndexOf("select") + "select".Length, //get start index from SELECT word
                lastIndex = selectSQL.LastIndexOf("from"); //get end index before FROM
            
            string columnsLine = selectSQL.Substring(firstIndex, lastIndex - firstIndex); //cut row before two indexes
            char[] separators = new char[] {' ',','};

            StringBuilder stringBuilder = new StringBuilder(selectSQL);
            stringBuilder.Append(IsActive ? " where active=1 LIMIT 1" : " where active=0 LIMIT 1");

            LinkedList<string> parameters = new LinkedList<string>(); //list for parameters name
            List<string> dataTableRowData = new List<string>();

            string[] subs = columnsLine.Split(separators, StringSplitOptions.RemoveEmptyEntries);

            foreach (string sub in subs)
            {
                if (sub.Contains("id"))
                {
                    idColumnName = sub;
                    continue;
                }
                parameters.AddLast(sub);
            }
            
            if (string.IsNullOrEmpty(idColumnName)) throw new ArgumentNullException("ID column is not set");
            if (!string.IsNullOrEmpty(ID))
            {
                stringBuilder.Replace("where", $"where {idColumnName}='{ID}' AND ");
            }
            DataTable dt = ExecuteDB(stringBuilder.ToString());
            
            Dictionary<string, List<string>> resultsDictionary = new Dictionary<string, List<string>>();
            if (dt.Rows.Count > 0)
            {
                //get ID from dataTable row
                string IDKey = String.Empty;
                IDKey = ID ?? dt.AsEnumerable().Select(row => row[idColumnName].ToString()).First();
                //get other data from row
                foreach (var parName in parameters)
                {
                    var columnValue = dt.AsEnumerable().Select(row => row[parName].ToString()).First();
                    dataTableRowData.Add(columnValue);
                }
                resultsDictionary.Add(IDKey, dataTableRowData);
            }
 
            return resultsDictionary;
        }

```

```ad-info
title: Execute Db method
collapse: open
```dotnet

public DataTable ExecuteDB(string sql)
        {
            DataTable dataTable = new DataTable();
            using (NpgsqlConnection connection = new NpgsqlConnection(connstring))
            {

                connection.Open();
                using (var command = new NpgsqlCommand(sql, connection))
                {
                    NpgsqlDataAdapter dataAdapter = new NpgsqlDataAdapter(command);
                    dataAdapter.Fill(dataTable);
                }

            }
            return dataTable;
        }
	   
```
