# Chapter 3: Unlocking Insights with Advanced KQL Operators

In today's data-driven landscape, the ability to query vast amounts of information is not just an advantage but a necessity. As we become more dependent on data to make informed decisions, the tools we use to interrogate this data must evolve in complexity and capability. Enter Kusto Query Language (KQL), a powerful language designed to make querying large and complex datasets both efficient and accessible.

As you may already know, KQL is utilized across various Microsoft services, including Azure Data Explorer, Application Insights, and Log Analytics. While basic KQL operators can handle a wide array of query requirements, the full power of KQL lies in its advanced operators. These provide nuanced control, increased efficiency, and deeper insights into the data being explored.

In this chapter, we will delve into the world of Advanced KQL operators. These operators enable intricate manipulations and analysis of data that are simply not possible with the basic operators alone. From pattern recognition to statistical evaluations, Advanced KQL operators facilitate a higher level of data understanding.

Some of the topics we'll cover in this chapter include:

Joins and Data Relationships: How to relate and combine data from different sources or tables.

Time Series Analysis: Utilizing specific operators that allow for in-depth examination of data across time intervals.

Pattern Recognition and Machine Learning: Understanding the integration of KQL with machine learning algorithms.

Custom Functions: Crafting your functions using KQL for tailored data manipulation.

Optimization Techniques: Learning the subtle arts of query tuning and optimization to handle vast datasets efficiently.

Through a mixture of theory, examples, and real-world scenarios, this chapter will equip you with the knowledge and skills required to harness the full capabilities of Advanced KQL operators. Whether you're a data scientist seeking to unearth new insights or an IT professional striving for optimized performance, these operators offer tools to take your querying abilities to the next level.

Prepare to dive into an engaging exploration of the Advanced KQL landscape, where data becomes not just a raw resource but a wellspring of knowledge and understanding.

By the end of this chapter, the mysteries of Advanced KQL operators will be unraveled, providing you with a robust set of tools to approach data in ways you might never have thought possible.

# Using KQL Variables

## Introduction to KQL Variables

### What are variables in KQL?

KQL variables are used to store and reference values within a query. They act as placeholders that can be assigned different values, such as constants or calculated results, and then used throughout the query. This allows for better organization, readability, and reusability of code.

### Why use variables in KQL queries?

Variables in KQL queries offer several advantages. They allow for the creation of reusable code snippets, promote better code organization, enhance query readability, and facilitate easier maintenance and debugging. Additionally, variables can be used to parameterize queries, making them more flexible and adaptable to different scenarios.

### Benefits of using variables

Reusability: Variables allow you to define values or functions that can be used multiple times within a query or even across multiple queries.

Code organization: By using variables, you can break down complex expressions into smaller, more manageable parts, improving the overall structure and organization of your code.

Readability: Variables make queries easier to read and understand, as they provide descriptive names for values and functions.

Flexibility: With variables, you can easily modify or update values in a single place, rather than searching for and changing them throughout your query.

Debugging: Variables can be helpful during the debugging process, as you can easily inspect and analyze their values at different stages of the query execution.

## Creating Constants with let

### Syntax for creating constants

To create a constant variable in KQL, you use the let statement followed by the variable name, an equal sign, and the value you want to assign. Constants are useful for storing values that remain constant throughout the query execution.

### Example: Setting a constant value

Let's say we want to filter our data based on a specific region. We can use a constant variable to store the region name and easily change it whenever needed. Here's an example:

let regionName = "Asia";

AppAvailabilityResults \| where Location contains regionName

In this example, the regionName variable is set to "Asia". We then use the variable in the where clause to filter the data based on the region.

### Advantages of using constants

Easy modification: Constants allow you to change a value in a single place, making it simpler to update or modify the query behavior.

Improved readability: Constants provide descriptive names, enhancing the clarity and understanding of the query logic.

Code maintenance: By using constants, you reduce the risk of introducing errors during manual value changes, ensuring the consistency and correctness of your queries.

### Calculated Values with let

#### Syntax for creating calculated values

In addition to constants, you can use the let statement to create variables that hold calculated values. These values are derived from expressions or functions and can be used in various parts of your query.

#### Example: Calculating time differences

Let's say we want to calculate the time difference in seconds between two timestamps. We can use a calculated value to store this result and reuse it throughout the query. Here's an example:

let startTime = datetime(2023-06-01);

let endTime = now();

let timeDiffInSeconds = (endTime - startTime) / 1s;

AppAvailabilityResults

\| extend ElapsedSeconds = timeDiffInSeconds

In this example, we calculate the time difference in seconds between the startTime and endTime variables. We then use the extend operator to create a new column called ElapsedSeconds and assign the calculated value to it.

#### Flexibility and reusability of calculated values

Calculated values provide flexibility by allowing you to reuse complex calculations in multiple parts of your query. By storing the result in a variable, you can easily refer to it without having to repeat the calculation logic. This improves query readability and reduces the risk of errors.

#### Reusable Functions with let

Syntax for creating functions

Another powerful feature of the let statement is the ability to define reusable functions. Functions allow you to encapsulate complex logic and reuse it across queries.

Example: Creating a function to format names

Let's say we frequently need to concatenate the first name and last name of a country in our data. We can create a function to simplify this task. Here's an example:

let formatFullName = (firstName:string, lastName:string) {

strcat(firstName, " ", lastName)

};

AppAvailabilityResults

\| project CountryFullName = formatFullName(ClientCity, ClientStateOrProvince)

In this example, we define the formatFullName function that takes two parameters: firstName and lastName. The function uses the strcat operator to concatenate the two strings with a space in between. We then use the function in the project operator to create a new column called CountryFullName.

Benefits of using reusable functions

Code reusability: Functions allow you to define complex logic once and reuse it across multiple queries, improving code efficiency and reducing redundancy.

Readability and maintainability: Functions make queries more readable by abstracting complex operations into self-contained units. This improves code organization and makes it easier to understand and maintain.

Modular design: By using functions, you can break down complex queries into smaller, more manageable pieces, promoting a modular and scalable query design.

### Using Multiple Variables in Queries

#### Syntax for using multiple variables

KQL allows you to use multiple variables within a query. You can define and reference multiple variables to create more dynamic and flexible queries.

#### Example: Filtering data using multiple variables

Let's say we want to filter our data based on multiple criteria, such as country and city. We can use multiple variables to store these values and easily modify them as needed. Here's an example:

let country = "United States";

let city = "Washington";

AppAvailabilityResults

\| where ClientCountryOrRegion == country and ClientCity == city

In this example, we define two variables, country and city, and assign them specific values. We then use these variables in the where clause to filter the data based on the country and city.

#### Improved query readability and maintainability

Using multiple variables in queries improves readability by providing descriptive names for different criteria or parameters. It also enhances query maintainability, as you can easily modify the variable values without having to search and update them throughout the query.

### Working with Default Values in Functions

#### Syntax for specifying default values

KQL allows you to specify default values for function parameters. This feature provides flexibility and allows you to handle cases where certain parameters are not explicitly provided.

#### Example: Using default values in a function

Let's say we have a function that calculates the time difference in days between two timestamps. We can specify a default value for one of the timestamps to handle cases where it is not provided. Here's an example:

let timeDiffInDays = (startDate: datetime, endDate: datetime = now()) {

toscalar(endDate - startDate) / 1d

};

MyTable

\| extend ElapsedDays = timeDiffInDays(StartTime)

In this example, we define the timeDiffInDays function with two parameters: startDate and endDate. We specify a default value of now() for the endDate parameter. If the endDate is not provided explicitly when calling the function, it defaults to the current timestamp. We then use the function in the extend operator to calculate the elapsed days between the StartTime and the default endDate.

#### Considerations and best practices

When using default values in functions, it's important to document the default behavior and ensure it aligns with your intended functionality. Additionally, be mindful of any potential impact on query performance when using dynamic default values.

### Creating Views with let

#### Syntax for creating views

In addition to values and functions, the let statement can also be used to create views in KQL. Views are virtual tables based on the result set of a query, providing a convenient way to organize and reuse data.

#### Example: Creating a view based on a query

Let's say we frequently need to work with data from a specific region. We can create a view that filters the data based on the region and reuse it in our queries. Here's an example:

let AsiaRegion = view () {

AppAvailabilityResults

\| where ClientCountryOrRegion == "Asia"

};

AsiaRegion

\| project Name, OperationName

In this example, we define the AsiaRegion view using the let statement. The view includes a query that filters the data based on the region. We then use the view in a subsequent query to project specific columns from the filtered data.

#### Leveraging views for data organization and reuse

Views provide a powerful way to organize and reuse query logic. By encapsulating complex queries into views, you can simplify your subsequent queries and promote code reuse and maintainability.

### Optimizing Queries with Materialization

#### Syntax for using the materialize() function

KQL provides the materialize() function to cache the results of a subquery during query execution, improving performance by avoiding redundant computations.

#### Example: Caching subquery results for performance

Let's say we have a complex query that involves computing a total count and then using it multiple times. We can use the materialize() function to cache the subquery results and reuse them efficiently. Here's an example:

let totalEventsPerDay = AppAvailabilityResults

\| summarize TotalEvents = count() by Day = startofday(TimeGenerated);

let cachedResult = materialize(totalEventsPerDay);

cachedResult

\| project Day, Percentage = TotalEvents / toscalar(cachedResult \| summarize sum(TotalEvents))

In this example, we compute the total count of events per day and store it in the totalEventsPerDay variable. We then use the materialize() function to cache the results of the subquery. By doing so, subsequent invocations of the cachedResult variable will use the cached data, improving query performance.

#### Enhancing query performance with materialization

Using the materialize() function can significantly improve query performance by eliminating redundant computations. However, it's important to use it judiciously and consider the trade-off between query performance and memory usage.

### Best Practices for Using Variables in KQL

#### Naming conventions for variables

When naming variables in KQL, it's a best practice to use descriptive and meaningful names that convey their purpose or value. This promotes code readability and understanding.

#### Avoiding naming conflicts

To avoid naming conflicts, it's important to choose variable names that are unique within the scope of your query. Be mindful of potential clashes with reserved keywords or existing column names.

#### Organizing and documenting your variables

To improve code maintainability, organize your variables logically within your query. Additionally, consider documenting the purpose and usage of each variable to facilitate collaboration and future modifications.

### Conclusion

In this section, we explored the power and versatility of variables in the Kusto Query Language. We learned how to create constants, calculated values, and reusable functions using the let statement. Additionally, we explored the benefits of using multiple variables, creating views, optimizing queries with materialization, and best practices for variable usage. By leveraging variables effectively, you can enhance the readability, maintainability, and performance of your KQL queries.

Now that you have a solid understanding of using variables in KQL, it's time to apply this knowledge to your own queries and unlock the full potential of the language. Experiment with different scenarios, explore advanced features, and continue to refine your skills. Happy querying!

# Uniting Queries with KQL Unions

## Understanding the Union Operator

### Introduction to the Union Operator

The union operator in KQL allows you to combine data from multiple tables into a single result set. Unlike the join operator, which combines columns into a single row, the union operator simply appends rows from one table to another. This is particularly useful when you want to merge datasets that have similar structures but different records.

### Syntax and Parameters

The syntax of the union operator is straightforward. It consists of the keyword union followed by the tables or table references you want to combine. Here is the basic syntax:

Table1 \| union Table2

You can also specify additional parameters to modify the behavior of the union operator. These parameters include kind, withsource, and isfuzzy. Let's explore each parameter in detail:

kind: This parameter determines how the columns are combined in the result set. The inner option retains only the columns that are common to all input tables, while the outer option includes all columns from any input table. The default is outer.

withsource: When specified, this parameter adds a column to the output that indicates the source table for each row. It can be useful for tracking the origin of the data in the result set.

isfuzzy: Setting this parameter to true allows fuzzy resolution of union legs. It means that even if some of the tables referenced in the union do not exist or are inaccessible, the query will still execute. The default is false.

Now that we have a basic understanding of the union operator, let's explore its usage with some practical examples.

## Basic Usage of Union Operator

### Combining Two Tables

To illustrate the basic usage of the union operator, let's consider a scenario where we have two tables: Sales_2022 and Sales_2023. We want to combine the sales data from both tables into a single result set.

Sales_2022 \| union Sales_2023

This query will append the rows from Sales_2023 to the rows from Sales_2022 and return the combined result set.

### Handling Columns with Different Names

In some cases, the tables you want to union may have columns with different names. The union operator handles this situation by aligning the columns based on their positions in the query. Let's consider the following example:

Table1

\| project Name, Age

Table2

\| project FullName, YearsOld

Table1 \| union Table2

In this example, Table1 has columns Name and Age, while Table2 has columns FullName and YearsOld. When we union these tables, the columns will be aligned as follows:

| Name     | Age      |
|----------|----------|
| FullName | YearsOld |

As you can see, the columns with different names are still included in the result set, but they are aligned based on their positions in the query.

## Advanced Techniques with the Union Operator

### Filtering and Sorting Unioned Data

The union operator allows you to apply filters and sorting to the unioned data. You can use the where clause to filter the rows based on specific conditions, and the order by clause to sort the rows based on one or more columns. Let's see an example:

Table1

\| where Category == "Electronics"

Table2

\| where Category == "Clothing"

(Table1 \| union Table2)

\| order by Price desc

In this example, we filter Table1 to include only rows where the Category is "Electronics", and Table2 to include only rows where the Category is "Clothing". Then we union the filtered tables and sort the result set in descending order based on the Price column.

### Using Let Statements with Union

You can also use let statements with the union operator to create named variables for the tables you want to union. This can make your query more readable and easier to maintain. Let's see an example:

let Table1 = Sales_2022 \| where Region == "North"

let Table2 = Sales_2023 \| where Region == "South"

(Table1 \| union Table2)

\| summarize sum(Revenue) by Region

In this example, we use let statements to create variables Table1 and Table2, which contain the filtered data from Sales_2022 and Sales_2023 tables, respectively. Then we union these tables and summarize the total revenue by region.

## Best Practices for Using the Union Operator

### Avoiding Wildcards in Table References

When specifying table references in the union operator, it is recommended to avoid using wildcards, especially in large databases. Using wildcards can lead to inefficient execution and unpredictable results, as new tables may be added over time. Instead, explicitly list the tables you want to union.

### Optimizing Union Performance

To optimize the performance of the union operator, consider the following best practices:

Reduce the number of columns in the result set by using the project operator to select only the necessary columns.

Use filters (where clause) to limit the number of rows processed by the union operator.

Ensure that the columns being unioned have compatible data types to avoid potential errors.

By following these best practices, you can improve the efficiency and reliability of your union queries.

## Real-World Example

### Tracking Security Incidents

Suppose you have two tables, SecurityIncidents and SecurityAlerts, containing information about security incidents and alerts in your system. You want to track the number of incidents and alerts reported by each user. Here's how you can use the union operator to accomplish this:

let SecurityIncidents = datatable(User: string, IncidentType: string)["Alice", "Data Breach", "Bob", "Unauthorized Access"];

let SecurityAlerts = datatable(User: string, AlertType: string)["Alice", "Suspicious Activity", "Charlie", "Malware Detection"];

(SecurityIncidents \| union SecurityAlerts)

\| summarize count() by User

In this example, we create two variables, SecurityIncidents and SecurityAlerts, which contain the sample data for the respective tables. Then we union these tables and count the number of incidents and alerts reported by each user.

## Union Operator vs Join Operator

### Key Differences

While the union and join operators are both used to combine data from multiple tables, they have some key differences:

The union operator combines rows from different tables into a single result set, while the join operator combines columns from different tables into a single row.

The union operator does not require a common column between the tables, while the join operator relies on a common column for matching records.

The union operator appends rows from one table to another, while the join operator combines rows based on matching values in the common column(s).

### Choosing the Right Operator

The choice between the union and join operators depends on the nature of your data and the desired outcome of your query. If you want to combine rows from different tables or datasets, the union operator is the appropriate choice. On the other hand, if you need to combine columns from different tables based on a common column, the join operator is the way to go.

## Conclusion

The union operator in Azure Data Explorer (Kusto) is a powerful tool for combining data from multiple tables into a single result set. By understanding its syntax, parameters, and best practices, you can leverage the full potential of the union operator in your data analysis and querying tasks. Whether you need to merge datasets, track incidents, or analyze sales data, the union operator provides a flexible and efficient solution.

In this section, we have explored the various aspects of the union operator, including its syntax, parameters, usage examples, and best practices. Armed with this knowledge, you can confidently incorporate the union operator into your KQL queries and unlock new insights from your data.

# The Power of Joining Data

## Understanding the Basics of Joining Data

Before diving into the different flavors of KQL joins, let's start with the basics. The join operator in KQL allows you to merge rows from two or more tables based on matching values in specified columns. This enables you to combine data from different sources and create new relationships between data points.

To perform a join, you need two tables with at least one column containing matching values. The join operator then matches the rows in these tables based on the specified conditions and creates a new table with the merged results.

It's important to note that the join operation in KQL is similar to the join operation in SQL. However, KQL provides additional flavors of joins that offer more flexibility and control over the merging process.

## Joining Tables with the Innerunique Flavor

The innerunique flavor is the default join flavor in KQL. It performs an inner join on the tables, combining rows that have matching values in the specified columns. The resulting table includes all columns from both tables, with duplicate rows from the left table removed.

To illustrate the innerunique join, let's consider a scenario where we have two tables: Fruit and Preparation. The Fruit table contains information about different fruits, including their names and corresponding numbers. The Preparation table contains information about various preparations for these fruits. We want to join these tables based on the common number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

1, "Pear"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice"

];

Fruit

\| join kind=innerunique Preparation on number

The resulting table will include the columns number, fruit, and preparation, with the duplicate row for the number 1 removed. This innerunique join allows us to combine the information from both tables and obtain a merged dataset.

## Exploring the Inner Join Flavor

In addition to the innerunique flavor, KQL provides the inner join flavor, which performs a standard inner join on the tables. This means that only the rows with matching values in the specified columns are included in the resulting table.

To demonstrate the inner join flavor, let's continue with our previous example of joining the Fruit and Preparation tables. We will use the same tables and join them based on the number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

1, "Pear"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice"

];

Fruit

\| join kind=inner Preparation on number

The resulting table will include the columns number, fruit, and preparation, but only the rows with matching numbers will be included. This inner join allows us to obtain the common records between the two tables and analyze them together.

## Unleashing the Power of Leftouter Join

The leftouter join flavor in KQL allows you to include all rows from the left table and only the matching rows from the right table. This means that even if there are no matching values in the specified columns, the rows from the left table will still be included in the resulting table.

To illustrate the power of the leftouter join, let's consider a scenario where we have two tables: Fruit and Preparation. The Fruit table contains information about different fruits, including their names and corresponding numbers. The Preparation table contains information about various preparations for these fruits. We want to join these tables based on the common number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice"

];

Fruit

\| join kind=leftouter Preparation on number

The resulting table will include the columns number, fruit, and preparation, with all rows from the Fruit table and only the matching rows from the Preparation table. This leftouter join allows us to include all fruits, even if they don't have any preparations associated with them.

## Going Beyond with Rightouter Join

Similar to the leftouter join, the rightouter join flavor in KQL allows you to include all rows from the right table and only the matching rows from the left table. This means that even if there are no matching values in the specified columns, the rows from the right table will still be included in the resulting table.

To demonstrate the power of the rightouter join, let's continue with our previous example of joining the Fruit and Preparation tables. We will use the same tables and join them based on the number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=rightouter Preparation on number

The resulting table will include the columns number, fruit, and preparation, with all rows from the Preparation table and only the matching rows from the Fruit table. This rightouter join allows us to include all preparations, even if there are no corresponding fruits.

## The Complete Picture with Fullouter Join

The fullouter join flavor in KQL combines the power of the leftouter and rightouter joins. It includes all rows from both the left and right tables, regardless of matching values in the specified columns. This means that even if there are no matching values, the rows from both tables will still be included in the resulting table.

To illustrate the complete picture provided by the fullouter join, let's consider a scenario where we have two tables: Fruit and Preparation. The Fruit table contains information about different fruits, including their names and corresponding numbers. The Preparation table contains information about various preparations for these fruits. We want to join these tables based on the common number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

4, "Banana"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=fullouter Preparation on number

The resulting table will include the columns number, fruit, and preparation, with all rows from both the Fruit and Preparation tables. This fullouter join allows us to see the complete picture of all fruits and preparations, regardless of matching values.

## Simplifying with Leftsemi Join

The leftsemi join flavor in KQL allows you to include all rows from the left table that have matching values in the specified columns, while excluding the non-matching rows from both tables. This means that only the rows from the left table that have matches in the right table will be included in the resulting table.

To simplify the join operation with the leftsemi join, let's consider a scenario where we have two tables: Fruit and Preparation. The Fruit table contains information about different fruits, including their names and corresponding numbers. The Preparation table contains information about various preparations for these fruits. We want to join these tables based on the common number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

4, "Banana"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=leftsemi Preparation on number

The resulting table will include the columns number and fruit, with only the rows from the Fruit table that have matching numbers in the Preparation table. This leftsemi join allows us to simplify the join operation and focus on the relevant rows in the left table.

## Finding Matches with Rightsemi Join

Similar to the leftsemi join, the rightsemi join flavor in KQL allows you to include all rows from the right table that have matching values in the specified columns, while excluding the non-matching rows from both tables. This means that only the rows from the right table that have matches in the left table will be included in the resulting table.

To find matches with the rightsemi join, let's continue with our previous example of joining the Fruit and Preparation tables. We will use the same tables and join them based on the number column.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

4, "Banana"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=rightsemi Preparation on number

The resulting table will include the columns number and preparation, with only the rows from the Preparation table that have matching numbers in the Fruit table. This rightsemi join allows us to find the relevant matches in the right table and focus on those rows.

## Excluding Matches with Leftanti Join

The leftanti join flavor in KQL allows you to exclude the rows from the left table that have matching values in the specified columns, while including all the rows from both tables. This means that only the rows from the left table that do not have matches in the right table will be included in the resulting table.

To exclude matches with the leftanti join, let's consider a scenario where we have two tables: Fruit and Preparation. The Fruit table contains information about different fruits, including their names and corresponding numbers. The Preparation table contains information about various preparations for these fruits. We want to join these tables based on the common number column and exclude the matching rows from the left table.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

4, "Banana"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=leftanti Preparation on number

The resulting table will include the columns number and fruit, with only the rows from the Fruit table that do not have matching numbers in the Preparation table. This leftanti join allows us to exclude the matching rows from the left table and focus on the non-matching rows.

## Filtering Matches with Rightanti Join

Similar to the leftanti join, the rightanti join flavor in KQL allows you to exclude the rows from the right table that have matching values in the specified columns, while including all the rows from both tables. This means that only the rows from the right table that do not have matches in the left table will be included in the resulting table.

To filter matches with the rightanti join, let's continue with our previous example of joining the Fruit and Preparation tables. We will use the same tables and join them based on the number column, excluding the matching rows from the right table.

let Fruit = datatable(number:int, fruit:string)

[

1, "Apple",

2, "Pear",

4, "Banana"

];

let Preparation = datatable(number:int, preparation:string)

[

1, "Slices",

1, "Juice",

2, "Juice",

3, "Dry"

];

Fruit

\| join kind=rightanti Preparation on number

The resulting table will include the columns number and preparation, with only the rows from the Preparation table that do not have matching numbers in the Fruit table. This rightanti join allows us to filter out the matching rows from the right table and focus on the non-matching rows.

## Best Practices and Performance Optimization

When working with joins in KQL, it's important to follow best practices to optimize performance and ensure efficient query execution. Here are some tips to keep in mind:

Choose the appropriate join flavor: Select the join flavor that best suits your specific use case and requirements. Consider factors such as the desired output, data volume, and performance implications.

Optimize column selection: When performing joins, be mindful of the columns you select in the output. Only include the necessary columns to reduce the amount of data transferred and improve query performance.

Use appropriate filters: Apply filters to limit the data before performing the join operation. This can significantly reduce the amount of data processed and improve query performance.

Consider table sizes: Take into account the sizes of the tables involved in the join operation. If one table is significantly larger than the other, consider using it as the left table to optimize performance.

Review and optimize query execution plans: Monitor and analyze the query execution plans to identify potential performance bottlenecks. Consider using hints or other optimization techniques to improve query performance.

Following these best practices will help you optimize your join operations in KQL and ensure efficient and effective data analysis.

## Conclusion

In this section, we have explored the power and flexibility of KQL joins. We have learned about the various flavors of joins, including innerunique, inner, leftouter, rightouter, fullouter, leftsemi, rightsemi, leftanti, and rightanti joins. Each flavor offers unique capabilities and allows you to merge and analyze your data in different ways.

By understanding the basics of joining data, exploring each join flavor, and following best practices, you now have the knowledge and skills to effectively merge and analyze your data in KQL. Whether you're working with large datasets or performing cross-cluster joins, KQL provides the tools and capabilities to support your data analysis needs.

Remember to optimize your join operations, review query execution plans, and leverage the power of query-generated tables to unlock the full potential of KQL joins. With these insights and techniques, you can harness the power of joining data and gain valuable insights from your datasets.

Happy joining!

# Using the Externaldata KQL Operator

In today's digital landscape, businesses are increasingly relying on Azure as their infrastructure backbone. The ability to query Azure using the Kusto Query Language (KQL) has become essential for gaining insights into the Azure services organizations utilize. In this section, we will explore the concept of externaldata in KQL and how it empowers users to extract valuable information from external storage artifacts, such as Azure Blob Storage and Azure Data Lake Storage. By leveraging the externaldata operator, businesses can unlock the full potential of their data and make informed decisions based on deep analysis and patterns discovered within their Azure environment.

## Understanding the Externaldata Operator

The externaldata operator is a powerful tool within the KQL arsenal. It enables users to retrieve data from external storage artifacts, transforming it into a structured table format defined within the query itself. This operator supports a variety of storage services, including Azure Blob Storage and Azure Data Lake Storage, making it versatile and adaptable to different data sources.

## Syntax and Parameters

To utilize the externaldata operator, it is important to understand its syntax and parameters. The basic syntax for the externaldata operator is as follows:

externaldata (ColumnName: ColumnType [, ...])

[StorageConnectionString [, ...]]

[with (PropertyName = PropertyValue [, ...])]

The operator accepts the following parameters:

ColumnName and ColumnType: These parameters define the schema of the resulting table, specifying the names and types of the columns.

StorageConnectionString: This parameter specifies the connection string of the external storage artifact from which the data will be retrieved.

PropertyName and PropertyValue: These optional parameters allow for additional customization, such as specifying the data format or authentication methods.

## Use Cases for the Externaldata Operator

The externaldata operator can be employed in various scenarios to enhance data analysis and gain valuable insights. Let's explore two sample use cases to demonstrate the versatility of this operator.

### Basic Use Case: Analyzing Processor Utilization

Imagine a scenario where you have a set of servers and applications hosted in Azure, with logs and metrics collected using Azure monitoring services. To identify applications that are experiencing high processor utilization, you can utilize the externaldata operator. The following query demonstrates the basic use case:

InsightsMetrics

\| where TimeGenerated \> ago(30m)

\| where Origin == "vm.azm.ms"

\| where Namespace == "Processor"

\| where Name == "UtilizationPercentage"

\| summarize avg(Val) by bin(TimeGenerated, 5m), Computer

\| join kind=leftouter (ComputerGroup) on Computer

\| where isnotempty(Computer1)

\| sort by avg_Val desc nulls first

This query retrieves the average processor utilization for each computer and joins the results with a list of specified computers. The output provides valuable insights into the applications and servers experiencing high processor utilization.

### Enhanced Use Case: Dynamic Thresholds for Processor Utilization

In a more advanced use case, you may want to query logs for selected applications or servers that have different processor utilization thresholds. This requires dynamically updating the thresholds without modifying the KQL query itself. To achieve this, you can leverage the externaldata operator in conjunction with an external data file, such as a CSV, to store and retrieve threshold values. The following query demonstrates the enhanced use case:

let Thresholds = externaldata (Computer: string, Threshold: int)

[@"https://raw.githubusercontent.com/rod-trent/SentinelKQL/master/thresholds.csv"]

with (format="csv");

InsightsMetrics

\| where TimeGenerated \> ago(30m)

\| where Origin == "vm.azm.ms"

\| where Namespace == "Processor"

\| where Name == "UtilizationPercentage"

\| join kind=inner (Thresholds) on Computer

\| where Val \> Threshold

\| sort by Val desc nulls first

In this query, the externaldata operator retrieves the thresholds from the external CSV file, which contains the computer names and their respective utilization thresholds. The join operation allows for dynamic comparison of the processor utilization values with the corresponding thresholds.

## Best Practices and Considerations

When utilizing the externaldata operator, it is important to keep a few best practices and considerations in mind:

Ensure that the external storage artifact is accessible and the connection string is accurate.

Validate and sanitize the data retrieved from external sources to avoid security risks and maintain data integrity.

Consider performance implications when working with large datasets. The externaldata operator is optimized for small reference tables rather than large data volumes.

Familiarize yourself with the available data formats and authentication methods supported by the externaldata operator.

## Conclusion

The externaldata operator in KQL empowers users to harness the power of external storage artifacts in Azure, enabling deep analysis and insights. By utilizing this operator, businesses can extract valuable information, discover patterns, and make informed decisions based on their Azure data. Whether it's analyzing processor utilization or dynamically adjusting thresholds, the externaldata operator offers unparalleled flexibility and versatility. Embrace the power of externaldata in KQL and unlock the full potential of your Azure environment.

Remember, mastering the Kusto Query Language opens the door to endless possibilities and empowers you to extract actionable insights from your data. Stay curious, continue exploring, and make data-driven decisions with confidence.

# Query IP Ranges Using KQL

As businesses and organizations increasingly rely on digital infrastructure, the need to manage and analyze IP addresses becomes crucial. Thankfully, with the power of Kusto Query Language (KQL), it is now easier than ever to query IP ranges and gain insights from your data. In this section, we will explore the various functions available in KQL to query IP ranges, including ipv4_is_in_range(), ipv4_is_match(), ipv6_compare(), and ipv6_is_match(). We will delve into the syntax, parameters, and examples of each function, equipping you with the knowledge to effectively work with IP ranges in KQL.

## Understanding IP-Prefix Notation

Before we dive into the details of querying IP ranges using KQL, it's essential to understand IP-prefix notation. IP-prefix notation, also known as CIDR notation, is a concise way of representing an IP address and its associated network mask. It consists of the base IP address followed by a slash ("/") and the prefix length.

For IPv4, the prefix length ranges from 0 to 32, while for IPv6, it ranges from 0 to 128. The prefix length denotes the number of leading 1 bits in the netmask, determining the range of IP addresses belonging to the network.

For example, the IP address 192.168.2.0 with a netmask of 255.255.255.0 can be represented in IP-prefix notation as 192.168.2.0/24. In this case, the prefix length is 24, indicating that the first 24 bits of the IP address represent the network, leaving 8 bits for host addresses.

## ipv4_is_in_range() Function

The ipv4_is_in_range() function allows you to check if an IPv4 address falls within a specified IP range. It takes two parameters: the IPv4 address to check and the IPv4 range in IP-prefix notation. The function returns true if the address is within the range, false if it is not, and null if there is an issue with the IP address conversion.

### Syntax

The syntax for the ipv4_is_in_range() function is as follows:

ipv4_is_in_range(Ipv4Address, Ipv4Range)

Where:

Ipv4Address is a string representing the IPv4 address to check.

Ipv4Range is a string representing the IPv4 range or a list of ranges in IP-prefix notation.

### Example

Let's consider an example to understand how the ipv4_is_in_range() function works:

datatable(ip_address:string, ip_range:string)

[

'192.168.1.1', '192.168.1.1', // Equal IPs

'192.168.1.1', '192.168.1.255/24', // 24 bit IP-prefix is used for comparison

]

\| extend result = ipv4_is_in_range(ip_address, ip_range)

The above query compares two IP addresses, '192.168.1.1' and '192.168.1.255/24', using the ipv4_is_in_range() function. The result table shows that the first IP address is equal to the second IP address, and both fall within the specified range.

## ipv4_is_match() Function

The ipv4_is_match() function is used to match and compare two IPv4 strings, taking into account IP-prefix notation and an optional prefix length. It returns true if the two strings match, false if they don't, and null if there is an issue with the IP address conversion.

### Syntax

The syntax for the ipv4_is_match() function is as follows:

ipv4_is_match(ip1, ip2[, prefix])

Where:

ip1 and ip2 are strings representing the IPv4 addresses to compare.

prefix is an optional integer (0 to 32) that represents the number of most significant bits to consider.

### Example

Let's explore an example to understand how the ipv4_is_match() function works:

datatable(ip1_string:string, ip2_string:string)

[

'192.168.1.0', '192.168.1.0', // Equal IPs

'192.168.1.1/24', '192.168.1.255', // 24 bit IP-prefix is used for comparison

'192.168.1.1', '192.168.1.255/24', // 24 bit IP-prefix is used for comparison

'192.168.1.1/30', '192.168.1.255/24', // 24 bit IP-prefix is used for comparison

]

\| extend result = ipv4_is_match(ip1_string, ip2_string)

In the above example, we compare IP addresses using the ipv4_is_match() function. The results indicate whether the IP addresses match based on the specified IP-prefix notation and prefix length.

## ipv6_compare() Function

The ipv6_compare() function allows you to compare two IPv6 or IPv4 network address strings, considering IP-prefix notation and an optional prefix length. It returns 0 if the first string is equal to the second string, 1 if it is greater, -1 if it is less, and null if there is an issue with the IP address conversion.

### Syntax

The syntax for the ipv6_compare() function is as follows:

ipv6_compare(ip1, ip2[, prefix])

Where:

ip1 and ip2 are strings representing the IPv6 or IPv4 addresses to compare.

prefix is an optional integer (0 to 128) that represents the number of most significant bits to consider.

### Example

Let's consider an example to understand how the ipv6_compare() function works:

datatable(ip1_string:string, ip2_string:string, prefix:long)

[

'192.168.1.1', '192.168.1.0', 31, // 31 bit IP-prefix is used for comparison

'192.168.1.1/24', '192.168.1.255', 31, // 24 bit IP-prefix is used for comparison

'192.168.1.1', '192.168.1.255', 24, // 24 bit IP-prefix is used for comparison

]

\| extend result = ipv6_compare(ip1_string, ip2_string, prefix)

In the above example, we compare IPv6 and IPv4 addresses using the ipv6_compare() function. The result table shows the comparison results based on the specified IP-prefix notation and prefix length.

## ipv6_is_match() Function

The ipv6_is_match() function is used to match and compare two IPv6 or IPv4 network address strings, considering IP-prefix notation and an optional prefix length. It returns true if the two strings match, false if they don't, and null if there is an issue with the IP address conversion.

### Syntax

The syntax for the ipv6_is_match() function is as follows:

ipv6_is_match(ip1, ip2[, prefix])

Where:

ip1 and ip2 are strings representing the IPv6 or IPv4 addresses to compare.

prefix is an optional integer (0 to 128) that represents the number of most significant bits to consider.

### Example

Let's explore an example to understand how the ipv6_is_match() function works:

datatable(ip1_string:string, ip2_string:string)

[

// IPv4 are compared as IPv6 addresses

'192.168.1.1', '192.168.1.1', // Equal IPs

'192.168.1.1/24', '192.168.1.255', // 24 bit IP4-prefix is used for comparison

'192.168.1.1', '192.168.1.255/24', // 24 bit IP4-prefix is used for comparison

'192.168.1.1/30', '192.168.1.255/24', // 24 bit IP4-prefix is used for comparison

// IPv6 cases

'fe80::85d:e82c:9446:7994', 'fe80::85d:e82c:9446:7994', // Equal IPs

'fe80::85d:e82c:9446:7994/120', 'fe80::85d:e82c:9446:7998', // 120 bit IP6-prefix is used for comparison

'fe80::85d:e82c:9446:7994', 'fe80::85d:e82c:9446:7998/120', // 120 bit IP6-prefix is used for comparison

'fe80::85d:e82c:9446:7994/120', 'fe80::85d:e82c:9446:7998/120', // 120 bit IP6-prefix is used for comparison

// Mixed case of IPv4 and IPv6

'192.168.1.1', '::ffff:c0a8:0101', // Equal IPs

'192.168.1.1/24', '::ffff:c0a8:01ff', // 24 bit IP-prefix is used for comparison

'::ffff:c0a8:0101', '192.168.1.255/24', // 24 bit IP-prefix is used for comparison

'::192.168.1.1/30', '192.168.1.255/24', // 24 bit IP-prefix is used for comparison

]

\| extend result = ipv6_is_match(ip1_string, ip2_string)

In the above example, we compare IPv6 and IPv4 addresses using the ipv6_is_match() function. The result table showcases the comparison results based on the specified IP-prefix notation and prefix length.

## Conclusion

In this section, we explored the functions available in KQL for querying IP ranges. We learned about ipv4_is_in_range(), ipv4_is_match(), ipv6_compare(), and ipv6_is_match(), understanding their syntax, parameters, and examples. Armed with this knowledge, you can now effectively query and analyze IP ranges in your data using KQL. Remember to leverage IP-prefix notation to represent IP addresses and their associated network masks accurately. Happy querying!

# Using the ipv4_is_private() KQL Function

## Introduction to the ipv4_is_private() Function

The ipv4_is_private() function is a powerful tool in the Kusto Query Language (KQL) that allows us to determine if an IPv4 address belongs to a private network. But what exactly is a private network address, and why is it important to identify them?

### What is a Private Network Address?

A private network address is an IP address that has been reserved for use within private networks. These addresses are not routable over the public internet, meaning they cannot be used to communicate directly with devices outside the private network. Instead, private network addresses are used for internal communication within a specific network.

### Purpose of Private Network Addresses

The purpose of using private network addresses is to conserve public IP address space. With the increasing number of devices connected to the internet, the availability of public IP addresses is limited. By using private network addresses, organizations can create their own internal networks without consuming public IP addresses.

## Understanding Private IPv4 Address Ranges

The Internet Engineering Task Force (IETF) has designated specific IP address ranges as private network addresses. These ranges are reserved and should not be used on the public internet. Let's explore the three primary private IPv4 address ranges:

| IP Address Range              | Number of Addresses | Largest CIDR Block (Subnet Mask) |
|-------------------------------|---------------------|----------------------------------|
| 10.0.0.0 – 10.255.255.255     | 16,777,216          | 10.0.0.0/8 (255.0.0.0)           |
| 172.16.0.0 – 172.31.255.255   | 1,048,576           | 172.16.0.0/12 (255.240.0.0)      |
| 192.168.0.0 – 192.168.255.255 | 65,536              | 192.168.0.0/16 (255.255.0.0)     |

These ranges are reserved and should not be used on the public internet. Any IP address falling within these ranges is considered a private network address.

## Syntax and Parameters of the ipv4_is_private() Function

To effectively use the ipv4_is_private() function in Kusto Query Language (KQL), it's essential to understand its syntax and parameters.

### Syntax Conventions

The syntax for the ipv4_is_private() function is as follows:

ipv4_is_private(ip)

The ip parameter represents the IPv4 address that you want to check for private network membership. The function returns a boolean value: true if the IP address belongs to any of the private network ranges, false if it doesn't, and null if the input is not a valid IPv4 address string.

### Parameters of the Function

The ipv4_is_private() function accepts only one parameter:

ip (string): An expression representing an IPv4 address. IPv4 strings can be masked using IP-prefix notation.

## How to Use the ipv4_is_private() Function

To demonstrate the usage of the ipv4_is_private() function, let's look at some examples of checking the membership of IPv4 addresses in private networks.

ipv4_is_private('192.168.1.1/24') == true

ipv4_is_private('10.1.2.3/24') == true

ipv4_is_private('202.1.2.3') == false

ipv4_is_private("127.0.0.1") == false

In the above examples, we pass different IP addresses to the ipv4_is_private() function. The function returns true if the IP address belongs to any of the private network ranges, and false otherwise.

### Sample Code and Output

To further illustrate the usage of the ipv4_is_private() function, let's run a query using the Kusto Query Language (KQL):

datatable(ip_string:string) [

'10.1.2.3',

'192.168.1.1/24',

'127.0.0.1',

]

\| extend result = ipv4_is_private(ip_string)

The above query creates a datatable with three IP addresses. We then extend the datatable with a new column called result, which uses the ipv4_is_private() function to check the private network membership of each IP address. The output will indicate whether each IP address belongs to a private network.

## Deep Dive into IP-Prefix Notation

In the context of the ipv4_is_private() function, it's essential to understand IP-prefix notation, also known as CIDR notation. This notation is used to represent IP addresses and their associated network masks.

### Understanding CIDR Notation

CIDR notation is a concise way of representing an IP address and its network mask. The notation uses a forward slash (/) followed by the prefix length, which represents the number of leading 1 bits in the netmask. The prefix length determines the range of IP addresses that belong to the network.

For example, the IP address 192.168.2.0/24 represents the IP address 192.168.2.0 with a netmask of 255.255.255.0. The prefix length in this case is 24, indicating that the first 24 bits of the IP address are fixed, while the last 8 bits can vary.

### IPv4 vs. IPv6 Prefix Lengths

In IPv4, the prefix length ranges from 0 to 32, while in IPv6, it ranges from 0 to 128. The larger the prefix length, the smaller the range of IP addresses that belong to the network. For example, a prefix length of 32 represents a single IP address,

## Leveraging the ipv4_is_private() Function in Real-World Scenarios

The ipv4_is_private() function can be incredibly useful in various real-world scenarios. Let's explore two common use cases:

### Network Security and Access Control

By leveraging the ipv4_is_private() function, organizations can enhance network security and access control measures. They can validate incoming IP addresses to ensure they belong to the expected private network ranges. This helps prevent unauthorized access attempts and ensures that only trusted IP addresses are allowed to communicate with the internal network.

### Network Monitoring and Troubleshooting

Network administrators can also use the ipv4_is_private() function for network monitoring and troubleshooting purposes. By analyzing network traffic and identifying private network addresses, they can gain insights into the internal communication patterns of their network. This information can be valuable for identifying bottlenecks, diagnosing network issues, and optimizing network performance.

The ipv4_is_private() function in Kusto Query Language (KQL) provides a powerful tool for identifying private network addresses. By leveraging this function, organizations can enhance network security, optimize network performance, and gain valuable insights into their network infrastructure.

## EXTRA: Getting Geolocation from an IP Address Using KQL

In today's digital age, understanding the geographical location of IP addresses has become a crucial aspect of data analysis. Whether it's identifying the origin of network traffic or determining the location of users or devices, having geolocation information can provide valuable insights. In this article, we will explore how to retrieve geolocation information from IP addresses using KQL (Kusto Query Language), a powerful query language used in Azure Data Explorer.

### The geo_info_from_ip_address() Function

KQL provides a function called geo_info_from_ip_address() that allows you to retrieve geolocation information about IPv4 or IPv6 addresses. This function takes an IP address as a parameter and returns a dynamic object containing information about the IP address's whereabouts, if available.

The function returns the following fields:

country: The country name where the IP address is located.

state: The state or subdivision name.

city: The city name.

latitude: The latitude coordinate of the location.

longitude: The longitude coordinate of the location.

It's important to note that IP geolocation is inherently imprecise, and the provided location is often near the center of the population. Therefore, it should not be used to identify specific addresses or households.

### Syntax

The syntax for the geo_info_from_ip_address() function is as follows:

geo_info_from_ip_address(IpAddress)

The IpAddress parameter is a string representing the IPv4 or IPv6 address for which you want to retrieve geolocation information.

### Examples

Let's explore some examples to understand how the geo_info_from_ip_address() function works.

#### Example 1: Retrieving Geolocation from an IPv4 Address

Suppose we want to retrieve geolocation information from the IPv4 address '20.53.203.50'. We can use the following query:

print ip_location=geo_info_from_ip_address('20.53.203.50')

The output will be:

ip_location{"country": "Australia", "state": "New South Wales", "city": "Sydney", "latitude": -33.8715, "longitude": 151.2006}

From the output, we can see that the IP address '20.53.203.50' is located in Sydney, New South Wales, Australia, with latitude -33.8715 and longitude 151.2006.

#### Example 2: Retrieving Geolocation from an IPv6 Address

Now, let's retrieve geolocation information from an IPv6 address. Consider the IPv6 address '2a03:2880:f12c:83:face:b00c::25de'. We can use the following query:

print ip_location=geo_info_from_ip_address('2a03:2880:f12c:83:face:b00c::25de')

The output will be:

ip_location{"country": "United States", "state": "Florida", "city": "Boca Raton", "latitude": 26.3594, "longitude": -80.0771}

From the output, we can see that the IPv6 address '2a03:2880:f12c:83:face:b00c::25de' is located in Boca Raton, Florida, United States, with latitude 26.3594 and longitude -80.0771.

### Limitations and Considerations

It's important to understand the limitations and considerations when using the geo_info_from_ip_address() function:

IP geolocation is not always accurate and can be affected by various factors such as proxy servers and VPNs. The location provided should be used as a general indication rather than an exact address.

The function utilizes GeoLite2 data created by MaxMind, a leading provider of IP intelligence and online fraud prevention tools. However, the data may not always be up-to-date, and the accuracy may vary.

The function is built on the MaxMind DB Reader library provided under the ISC license.

### Conclusion

Retrieving geolocation information from IP addresses using KQL can provide valuable insights in data analysis. By leveraging the geo_info_from_ip_address() function, you can enrich your data with geographic context, identifying the origin of network traffic or the location of users or devices. However, it's important to consider the limitations and understand that IP geolocation is inherently imprecise. With KQL and the geo_info_from_ip_address() function, you can unlock the power of geolocation analysis in your data exploration.

To learn more about the syntax and usage of the geo_info_from_ip_address() function, refer to the [official documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/geo-info-from-ip-address-function).

# Working with Multivalued Strings in KQL

In the world of data analysis, dealing with multivalued strings can be challenging. Fortunately, the Kusto Query Language (KQL) offers powerful operators like mv-expand and parse to help extract and manipulate data from these complex string structures. In this guide, we will explore the functionality of these operators and learn how to effectively work with multivalued strings in KQL.

## Understanding the mv-expand Operator

The mv-expand operator is a versatile tool in KQL that allows you to expand multivalued dynamic arrays or property bags into multiple records. Unlike aggregation operators that pack multiple values into a single array, such as summarize and make-list(), mv-expand generates a new record for each element in the array or property bag. This operator duplicates all non-expanded columns to ensure data consistency in the output.

Syntax:

T \| mv-expand [bagexpansion=(bag\|array)] [with_itemindex=IndexColumnName] ColumnName [to typeof(Typename)] [, ColumnName ...] [limit Rowlimit]

The mv-expand operator takes several parameters, including bagexpansion, with_itemindex, ColumnName, Typename, and Rowlimit. These parameters allow you to control the expansion behavior and data types of the expanded columns. You can also limit the number of rows generated from each original row using the limit parameter.

Modes of expansion:

bagexpansion=bag or kind=bag: Property bags are expanded into single-entry property bags.

bagexpansion=array or kind=array: Property bags are expanded into [key, value] array structures for uniform access to keys and values.

## Examples of mv-expand

Let's dive into some examples to see mv-expand in action:

### Example 1: Single column - array expansion

Suppose we have a datatable with two columns: a (integer) and b (dynamic array).

datatable (a: int, b: dynamic)

[

1, dynamic([10, 20]),

2, dynamic(['a', 'b'])

]

\| mv-expand b

Output:

a b

1 10

1 20

2 a

2 b

In this example, the b column is expanded, creating new rows for each element in the dynamic array.

### Example 2: Single column - bag expansion

Consider a datatable with two columns: a (integer) and b (dynamic property bag).

datatable (a: int, b: dynamic)

[

1, dynamic({"prop1": "a1", "prop2": "b1"}),

2, dynamic({"prop1": "a2", "prop2": "b2"})

]

\| mv-expand b

Output:

a b

1 {"prop1": "a1"}

1 {"prop2": "b1"}

2 {"prop1": "a2"}

2 {"prop2": "b2"}

In this example, the b column is expanded, creating new rows with separate property bag entries.

### Example 3: Single column - bag expansion to key-value pairs

Let's expand a bag into key-value pairs using the mv-expand operator and extend to create new columns.

datatable (a: int, b: dynamic)

[

1, dynamic({"prop1": "a1", "prop2": "b1"}),

2, dynamic({"prop1": "a2", "prop2": "b2"})

]

\| mv-expand bagexpansion=array b

\| extend key = b[0], val = b[1]

Output:

a b key val

1 ["prop1","a1"] prop1 a1

1 ["prop2","b1"] prop2 b1

2 ["prop1","a2"] prop1 a2

2 ["prop2","b2"] prop2 b2

In this example, the bag is expanded into key-value pairs, allowing uniform access to the properties.

### Example 4: Zipped two columns

We can expand two columns simultaneously by using mv-expand consecutively.

datatable (a: int, b: dynamic, c: dynamic)

[

1, dynamic({"prop1": "a", "prop2": "b"}), dynamic([5, 4, 3])

]

\| mv-expand b, c

Output:

a b c

1 {"prop1":"a"} 5

1 {"prop1":"a"} 4

1 {"prop1":"a"} 3

1 {"prop2":"b"} 5

1 {"prop2":"b"} 4

1 {"prop2":"b"} 3

In this example, both the b and c columns are expanded, resulting in a cartesian product of the two expanded columns.

### Example 5: Cartesian product of two columns

To get a Cartesian product of expanding two columns, we can expand one after the other.

datatable (a: int, b: dynamic, c: dynamic)

[

1, dynamic({"prop1": "a", "prop2": "b"}), dynamic([5, 6])

]

\| mv-expand b

\| mv-expand c

Output:

a b c

1 {"prop1": "a"} 5

1 {"prop1": "a"} 6

1 {"prop2": "b"} 5

1 {"prop2": "b"} 6

In this example, the b column is expanded first, followed by the expansion of the c column, resulting in the Cartesian product of the two expanded columns.

### Example 6: Convert output

To force the output of mv-expand to a specific type, we can use the to typeof() clause.

datatable (a: string, b: dynamic, c: dynamic)

[

"Constant", dynamic([1, 2, 3, 4]), dynamic([6, 7, 8, 9])

]

\| mv-expand b, c to typeof(int)

\| getschema

Output:

ColumnName ColumnOrdinal DateType ColumnType

a 0 System.String string

b 1 System.Object int

c 2 System.Object int

In this example, the b and c columns are expanded and explicitly cast to the int data type using the to typeof() clause.

TIP: Name/Alias: Franck Heilmann (franckh)

Why it should be run: For Token Protection in Conditional Access deployment, to minimize the likelihood of user disruption due to applications or device incompatibility, we highly recommend doing staged deployment and actively monitoring the sign-in logs. This query gives admin a per Token Protection CA rules user impact view

SigninLogs

\| where TimeGenerated \> ago(7d)

\| project Id,ConditionalAccessPolicies, Status,UserPrincipalName

\| where ConditionalAccessPolicies != "[]"

\| mv-expand todynamic(ConditionalAccessPolicies)

\| union (

AADNonInteractiveUserSignInLogs

\| where TimeGenerated \> ago(7d)

\| project Id,ConditionalAccessPolicies, Status,UserPrincipalName

\| where ConditionalAccessPolicies != "[]"

\| mv-expand todynamic(ConditionalAccessPolicies)

)

\| where ConditionalAccessPolicies.enforcedSessionControls contains "Binding" or ConditionalAccessPolicies.enforcedSessionControls contains "SignInTokenProtection"

\| where ConditionalAccessPolicies.result !="reportOnlyNotApplied" and ConditionalAccessPolicies.result !="notApplied"

\| extend SessionNotSatisfyResult = ConditionalAccessPolicies["sessionControlsNotSatisfied"]

\| extend Result = case (SessionNotSatisfyResult contains 'Binding' or SessionNotSatisfyResult contains 'SignInTokenProtection' , 'Block','Allow')

\| extend CADisplayName = ConditionalAccessPolicies.displayName

\| extend CAId = ConditionalAccessPolicies.id

\| summarize by Id,tostring(CAId),tostring(CADisplayName), UserPrincipalName, Result

\| summarize Requests = count(), Block = countif(Result == "Block"), Allow = countif(Result == "Allow"), Users = dcount(UserPrincipalName), BlockedUsers = dcountif(UserPrincipalName, Result == "Block") by tostring(CADisplayName),tostring(CAId)

\| extend PctAllowed = round(100.0 \* Allow/(Allow+Block), 2)

\| sort by Requests desc

## Understanding the parse Operator

The parse operator is another powerful tool in KQL that allows you to extract specific parts of a string based on a defined pattern. Unlike regular expressions, which can be complex and challenging to work with, the parse operator provides a simpler and more intuitive approach to string extraction. It is particularly useful when dealing with well-formatted strings that have recurring text patterns.

Syntax:

parse ColumnName with Pattern [default DefaultResult]

The parse operator takes the name of the column to parse, followed by the keyword with and the pattern to match within the string. You can also provide a default result to handle cases where the pattern doesn't match.

## Examples of parse

Let's explore some examples to see how the parse operator can be used effectively:

### Example 1: Extracting data from a well-formatted string

Suppose we have a datatable with a column called Name, which always begins with the text GET followed by the requested data.

datatable (Name: string)

[

"GET /api/users",

"GET /api/products",

"GET /api/orders"

]

\| parse Name with "GET " Data

Output:

Name Data

GET /api/users /api/users

GET /api/products /api/products

GET /api/orders /api/orders

In this example, the parse operator extracts the data following the GET text and places it in a new column called Data.

### Example 2: Extracting multiple parts from a string

Consider a datatable with a column called Message, which follows a consistent format for certain categories and levels. We can use parse to extract the ID and duration from the Message column.

datatable (Message: string)

[

"Executed 'Function2' (Failed, Id=123, Duration=500ms)",

"Executed 'Function2' (Failed, Id=456, Duration=750ms)"

]

\| parse Message with "Executed 'Function2' (Failed, Id=" ID ", Duration=" Duration "ms)"

Output:

Message ID Duration

Executed 'Function2' (Failed, Id=123, Duration=500ms) 123 500

Executed 'Function2' (Failed, Id=456, Duration=750ms) 456 750

In this example, the parse operator extracts the ID and duration from the Message column using a specific pattern. The extracted values are placed in the ID and Duration columns.

## When to Use mv-expand and parse

The mv-expand operator is ideal for expanding multivalued arrays or property bags into separate records, allowing for more granular analysis and aggregation. It is particularly useful when dealing with structured data that can be expanded into meaningful columns.

On the other hand, the parse operator is handy when you have well-formatted strings with recurring patterns and need to extract specific parts. It simplifies the extraction process and avoids the complexity of regular expressions.

It's important to note that mv-expand and parse work best when the data follows a consistent format. If the data varies significantly, additional filtering or preprocessing may be required to ensure accurate results.

## Conclusion

Working with multivalued strings in KQL can be challenging, but operators like mv-expand and parse make it easier to extract and manipulate data from these complex structures. By leveraging these powerful tools, you can expand arrays, extract specific parts of strings, and gain deeper insights from your data. Whether you need to analyze dynamic arrays or extract information from formatted strings, KQL has the operators to help you accomplish your data analysis goals.

Remember to experiment with different scenarios and explore the full capabilities of mv-expand and parse. With practice, you'll become more proficient in working with multivalued strings and unlocking valuable insights from your data.

# Using the base64_decode_tostring() KQL Function

## Introduction to the base64_decode_tostring() Function

### What is base64 Encoding?

Before diving into the details of the base64_decode_tostring() function, it's essential to understand the concept of base64 encoding. Base64 is a binary-to-text encoding scheme that represents binary data in an ASCII string format. It is commonly used to transmit binary data over text-based protocols such as email and HTTP. The base64 encoding scheme uses a set of 64 characters to represent the 256 possible values of a binary sequence.

### Understanding UTF-8 Encoding

UTF-8 (Unicode Transformation Format 8-bit) is a variable-width character encoding that can represent any character in the Unicode standard. It is widely used in computer systems for encoding and representing text. UTF-8 uses a variable number of bytes to represent each character, with ASCII characters represented by a single byte. This flexibility allows UTF-8 to support a vast range of characters from different languages and scripts.

## Syntax and Parameters of base64_decode_tostring()

### Syntax Conventions

When using the base64_decode_tostring() function in KQL, it is essential to follow the syntax conventions to ensure accurate and error-free execution. The syntax for the base64_decode_tostring() function is as follows:

base64_decode_tostring(base64_string)

The function takes a single parameter, base64_string, which is the base64-encoded string that you want to decode into a UTF-8 string.

### Exploring the Parameters

Let's take a closer look at the parameters of the base64_decode_tostring() function:

base64_string: This parameter is of type string and is required. It represents the base64-encoded string that you want to decode into a UTF-8 string.

## Examples and Applications

### Decoding a Simple Base64 String

To illustrate the usage of the base64_decode_tostring() function, let's consider a simple example. Suppose you have a base64-encoded string "S3VzdG8=". Using the function, you can decode it into the corresponding UTF-8 string. Here's how you can do it:

print Quine = base64_decode_tostring("S3VzdG8=")

The output of the above query will be:

Kusto

In this example, the base64-encoded string "S3VzdG8=" is decoded into the UTF-8 string "Kusto".

### Handling Invalid UTF-8 Encoding

It's important to note that when decoding a base64 string, there might be cases where the resulting UTF-8 encoding is invalid. In such cases, the base64_decode_tostring() function returns null. Let's consider an example where we try to decode a base64 string generated from invalid UTF-8 encoding:

print Empty = base64_decode_tostring("U3RyaW5n0KHR0tGA0L7Rh9C60LA=")

The output of the above query will be:

Empty

\-----

null

In this example, the base64-encoded string "U3RyaW5n0KHR0tGA0L7Rh9C60LA=" represents an invalid UTF-8 encoding, and hence the function returns null.

## Related Functions and Use Cases

### base64_decode_toarray()

In addition to the base64_decode_tostring() function, KQL also provides the base64_decode_toarray() function. This function allows you to decode a base64 string into an array of long values. It can be particularly useful when dealing with binary data or numeric representations encoded in base64 format.

### base64_encode_tostring()

On the other hand, if you need to encode a string into base64 format, you can use the base64_encode_tostring() function. This function takes a UTF-8 string as input and returns the base64-encoded representation of the string.

## Best Practices for Using base64_decode_tostring()

### Performance Considerations

While using the base64_decode_tostring() function, it's important to consider performance implications, especially when dealing with large datasets or frequent decoding operations. Here are a few best practices to optimize performance:

Minimize unnecessary decoding: Only decode base64 strings when necessary. Avoid redundant or excessive decoding operations to improve query performance.

Data type considerations: Ensure that the data type of the base64-encoded string field is consistent throughout your data set. Using consistent data types can facilitate efficient decoding and processing.

Query optimization: Optimize your queries by leveraging query filters and aggregations to reduce the amount of data processed during decoding operations.

### Error Handling and Validation

When working with the base64_decode_tostring() function, it's crucial to handle errors and validate the input data to ensure the integrity of your results. Here are some best practices for error handling and validation:

Error handling: Handle potential errors caused by invalid base64 strings or unexpected input. Use appropriate error-handling mechanisms, such as try-catch blocks, to gracefully handle exceptions.

Input validation: Validate the input data to ensure that it adheres to the expected format and encoding. Implement input validation checks to prevent potential issues caused by invalid or malformed data.

## Tips and Tricks for Advanced Usage

### Chaining Functions for Complex Decoding

In some scenarios, you may need to perform complex decoding operations that involve multiple steps or transformations. KQL allows you to chain functions together to achieve these complex decoding tasks. For example, you can combine the base64_decode_tostring() function with other KQL functions to perform additional data manipulations or transformations.

### Handling Large Base64 Strings

When dealing with large base64-encoded strings, it's important to consider memory and performance implications. To handle large base64 strings efficiently, you can leverage KQL's streaming and chunking capabilities. By processing the data in smaller chunks, you can minimize memory usage and optimize performance.

## Case Studies: Real-World Examples

### Decoding Base64 Strings in Log Analysis

One common use case for the base64_decode_tostring() function is in log analysis. Many log files contain base64-encoded strings that need to be decoded for further analysis. By using the base64_decode_tostring() function in your log analysis queries, you can easily decode these strings and extract valuable insights from your log data.

### Base64 Decoding in Data Transformation Pipelines

Data transformation pipelines often involve processing data from various sources, including base64-encoded strings. By incorporating the base64_decode_tostring() function into your data transformation pipelines, you can efficiently decode these strings and transform them into a more usable format for downstream processing.

The base64_decode_tostring() function in KQL provides a powerful tool for decoding base64-encoded strings into UTF-8 format. By understanding the syntax, parameters, and best practices for using this function, you can unlock its full potential in your data exploration and analysis tasks. Whether you're working with log data, data transformation pipelines, or any other use case, the base64_decode_tostring() function will undoubtedly prove to be a valuable asset in your data processing toolkit. So, start leveraging its capabilities today and take your data analysis to new heights!

# Working with JSON

## Querying JSON Data

Once you've ingested JSON data, you can unleash the power of Kusto Query Language (KQL) to query and analyze the data.

### Extracting JSON Properties

To extract specific JSON properties, you can use the extract_json function. This function allows you to extract values from JSON properties based on a JSONPath-like expression. Let's consider an example:

SensorData

\| extend Name = extract_json("\$.name", Data)

\| extend Index = extract_json("\$.index", Data)

In this example, we extract the "name" and "index" properties from the "SensorData" table's "Data" column using the extract_json function. This enables you to work with specific JSON properties in your queries.

### Filtering JSON Data

When querying JSON data, you can apply filters to narrow down your results. For example, if you want to retrieve data where the "temperature" property is above a certain threshold, you can use the where operator:

SensorData

\| where Temperature \> 25

This query filters the "SensorData" table to only include records where the "Temperature" property is greater than 25. By applying filters, you can focus on the specific data that meets your criteria.

### Aggregating JSON Data

KQL allows you to aggregate JSON data using various aggregation functions. For example, you can calculate the average temperature and humidity for each device in the "SensorData" table:

SensorData

\| summarize AvgTemperature = avg(Temperature), AvgHumidity = avg(Humidity) by DeviceId

By using the summarize operator with aggregation functions like avg, you can derive meaningful insights from your JSON data. Aggregating data helps you understand trends and patterns within your dataset.

## Best Practices for Optimizing JSON Processing

To optimize JSON processing, it's essential to follow best practices that improve query performance and reduce resource consumption. Here are some key recommendations:

### Early Filtering

When working with CPU-intensive functions like parsing JSON or XML, it's best to apply filtering conditions early in your query. By filtering out irrelevant records before executing CPU-intensive functions, you can significantly improve performance. For example:

SensorData

\| where EventID == 8002

\| where EventData !has "%SYSTEM32"

\| extend Details = parse_xml(EventData)

\| extend FilePath = tostring(Details.UserData.RuleAndFileData.FilePath)

\| extend FileHash = tostring(Details.UserData.RuleAndFileData.FileHash)

\| where FileHash != "" and FilePath !startswith "%SYSTEM32"

\| summarize count() by FileHash, FilePath

In this query, the where conditions are applied before parsing XML, filtering out irrelevant records early in the process.

### Use Effective Aggregation Functions

When aggregating JSON data, choose the most efficient aggregation functions for your specific use case. KQL provides functions like max, sum, count, and avg that have low CPU impact. Utilize these functions whenever possible. Additionally, consider using functions like dcount, which provide approximate distinct count values without counting each value individually.

### Avoid Full JSON Parsing

Full parsing of complex JSON objects can consume significant CPU and memory resources. In cases where you only need a few parameters from the JSON data, it's more efficient to parse them as strings using the parse operator or other text parsing techniques. This approach can provide a significant performance boost, especially when dealing with large JSON datasets.

## Advanced JSON Processing Techniques

KQL offers advanced JSON processing capabilities beyond basic querying and filtering. Let's explore some of these techniques:

### Handling JSON Arrays

When working with JSON arrays, you can use functions like mv-expand to expand array elements into separate records. This allows you to perform operations on individual array elements. For example:

SensorData

\| mv-expand Data

\| extend Name = extract_json("\$.name", Data)

In this query, the mv-expand function expands the JSON array elements in the "Data" column, enabling you to extract specific properties from each array element.

### Working with Nested JSON Objects

KQL supports querying and manipulating nested JSON objects. You can access nested properties using dot notation or JSONPath-like expressions. For example:

SensorData

\| extend NestedProperty = Data.NestedObject.NestedProperty

This query accesses the "NestedProperty" within a nested JSON object in the "Data" column.

### Joining JSON Data

KQL allows you to join JSON data from multiple tables using the join operator. This enables you to combine data from different JSON sources based on common properties. For example:

Table1

\| join kind=inner (Table2) on \$left.CommonProperty == \$right.CommonProperty

By joining JSON data, you can perform more complex analysis and derive insights from multiple data sources.

## Conclusion

Optimizing JSON processing is crucial for efficient data analysis and improved query performance.

# Time Series Analysis

In the era of cloud services and IoT devices, businesses generate massive amounts of telemetry data. This data holds valuable insights that can be leveraged to monitor service health, track physical production processes, and identify usage trends. However, analyzing this data can be challenging without the right tools and techniques. This is where time series analysis comes into play. By utilizing the power of the Kusto Query Language (KQL), businesses can unlock the full potential of their time series data.

In this section, we will delve into the world of time series analysis using KQL. We will explore the process of creating and analyzing time series, and highlight the key functions and operators that KQL offers for time series manipulation. By the end, you will have a solid understanding of how to harness the power of KQL to gain valuable insights from your time series data.

## Time Series Creation: Transforming Data into Actionable Insights

The first step in time series analysis is to transform your raw telemetry data into a structured format that is suitable for analysis. KQL provides the make-series operator to simplify this process. It allows you to create a set of time series by partitioning the data based on specific dimensions and aggregating the values within each partition.

Let's consider an example where we have a table demo_make_series1 containing web service traffic records. To create time series representing the traffic count partitioned by the operating system (OS), we can use the following KQL query:

let min_t = toscalar(Perf \| summarize min(TimeGenerated));

let max_t = toscalar(Perf \| summarize max(TimeGenerated));

Perf

\| make-series num=count() default=0 on TimeGenerated from min_t to max_t step 1h by ObjectName

\| render timechart

In this query, we use the make-series operator to create a set of time series, with each series representing the traffic count at regular intervals of 1 hour. The by ObjectName clause partitions the data based on the OS version. The resulting time series can be visualized using the render timechart command.

## Time Series Analysis Functions: Unveiling Patterns and Anomalies

Once you have created the time series, KQL provides a range of functions to process and analyze them. These functions enable you to identify patterns, detect anomalies, and perform regression analysis on your time series data.

### Filtering: Smoothing the Noise

Filtering is a common practice in time series analysis to remove noise and highlight underlying trends. KQL offers two filtering functions: series_fir() and series_iir().

series_fir(): This function applies a finite impulse response (FIR) filter to the time series. It is useful for calculating moving averages and detecting changes in the time series.

series_iir(): This function applies an infinite impulse response (IIR) filter to the time series. It is commonly used for exponential smoothing and cumulative sum calculations.

To demonstrate the filtering capabilities of KQL, let's apply a moving average filter to our time series:

let min_t = toscalar(Perf \| summarize min(TimeGenerated));

let max_t = toscalar(Perf \| summarize max(TimeGenerated));

Perf

\| make-series num=count() default=0 on TimeGenerated from min_t to max_t step 1h by ObjectName

\| extend ma_num=series_fir(num, repeat(1, 5), true, true)

\| render timechart

In this example, we use the series_fir() function to calculate a moving average of the traffic count. The repeat(1, 5) argument specifies a filter of size 5, and true, true indicate that the filter is centered and symmetric. The resulting time series can be visualized using the render timechart command.

## Conclusion: Unleash the Power of Time Series Analysis with KQL

Time series analysis is a powerful technique that allows businesses to gain valuable insights from their telemetry data. By leveraging the capabilities of the Kusto Query Language (KQL), you can transform raw data into actionable insights, identify patterns, detect anomalies, and make informed decisions based on the trends in your time series data.

Now armed with this knowledge, you can unlock the power of time series analysis with KQL and gain valuable insights that drive your business forward. So go ahead, dive into your time series data, and discover the hidden patterns and anomalies that will propel your organization to new heights.

# Exploring the Power of Regular Expressions in KQL

## Understanding Regular Expressions and their Syntax

A regular expression is a sequence of characters that defines a pattern to be searched for within a piece of text. It provides a flexible and concise way to describe complex search patterns. In KQL, regular expressions are enclosed in forward slashes (/). For example, to search for a string that ends with the character "a", the query would look like this: sun:/.\*a/.

To include special characters in a regex query, they must be escaped using the backslash (\\) character. For instance, to search for a string that ends with a dollar sign (\$), the query would be: sun:/.\*\\\\\$/.

When dealing with multiple strings in a specific sequence, quotes can be used to enclose the strings. For example, to search for the sequence of strings "513", "10", and "512" within the TargetAttributeValue field, the query would be: rv43:(+"513"+"10"+"512").

## The Power of Regular Expressions in Microsoft Sentinel

In Microsoft Sentinel, regular expression queries are incredibly useful for filtering and searching events that match specific patterns. However, it's important to note that regular expression queries utilize more system resources compared to other types of queries, as they can't leverage the efficient data structures available in the index. Therefore, it's crucial to narrow the breadth of the search as much as possible by using time range and non-regex criteria terms.

## Leveraging the RE2 Syntax and Microsoft's RE2 Library

To make the most of regular expressions in KQL, it's essential to familiarize yourself with the RE2 syntax. The RE2 syntax is the foundation for regex queries in Microsoft Sentinel. You can find a comprehensive guide to the RE2 syntax in the RE2 Syntax Wiki. <https://github.com/google/re2/wiki/Syntax>

Additionally, Microsoft provides a dedicated RE2 library for Azure Data Explorer (ADX), which includes a wide range of regex functions and operators. This library allows you to perform advanced pattern matching and extraction operations in KQL. You can find detailed information about the RE2 library in the Microsoft Documentation. <https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/re2-library>

By leveraging the RE2 syntax and Microsoft's RE2 library, you can harness the full power of regular expressions in KQL, enabling you to perform complex searches and data extractions with ease.

## Testing Regular Expressions in KQL

To ensure the accuracy and effectiveness of regex patterns, it's crucial to test them before incorporating them into your queries. While various online tools are available for regex testing, you can also test your regex patterns directly within the KQL query window.

Here's an example of how you can test a regex pattern in KQL:

let Regex=@"(?i)attrib.\*\\+h\\\\";

let TestString="attribute +h\\";

print(iif(TestString matches regex Regex, true,false));

In this example, the Regex variable holds the regex pattern, and the TestString variable contains the string you want to test against the pattern. The print statement checks if the TestString matches the regex pattern and returns either true or false.

By testing your regex patterns in KQL, you can ensure their accuracy and reliability before utilizing them in your production queries.

## Enhancing Detection Rules and Migrating from Other SIEM Tools

Regular expressions are integral to creating effective detection rules in Microsoft Sentinel. When creating regex-based detection rules or migrating from other SIEM tools, it's crucial to thoroughly test your regex patterns. While regex queries provide powerful filtering capabilities, they also consume more system resources. Therefore, it's essential to strike a balance by combining time range and non-regex criteria terms to optimize performance.

To ensure a smooth transition to Microsoft Sentinel, it's recommended to test and validate your regex patterns to ensure they work seamlessly within the Microsoft Sentinel environment. This will help you maintain the integrity and effectiveness of your detection rules while leveraging the power of regular expressions.

TIP: Explore recent behavior of a specific service principal

Name (Alias): Kristopher Bash (krbash)

Why it should be run: This query looks at Microsoft Graph API requests in the past 3 days, for a specific service principal. To characterize the types of requests the service principal is used for, the query summarizes the count of requests for combinations of HTTP request method, and the segments of the RequestUri that identify the target of the operation. The URI is parsed by first cleaning the RequestUri string for consistency, and then extracting alpha characters following a ‘/’, and concatenating these segments. This transforms a RequestUri from: [https://graph.microsoft.com/beta/users/{id}/manager?\$select=displayName](https://graph.microsoft.com/beta/users/%7bid%7d/manager?$select=displayName) to: users/manager.

Query:

MicrosoftGraphActivityLogs

\| where TimeGenerated \> ago(3d)

\| where ServicePrincipalId == '9d6399dd-e9f6-4271-b3cb-c26e829ea3cf'

\| extend path = replace_string(replace_string(replace_regex(tostring(parse_url(RequestUri).Path), @'(\\/)+','//'),'v1.0/',''),'beta/','')

\| extend UriSegments = extract_all(@'\\/([A-z2]+\|\\\$batch)(\$\|\\/\|\\(\|\\\$)',dynamic([1]),tolower(path))

\| extend OperationResource = strcat_array(UriSegments,'/')\| summarize RequestCount=count() by RequestMethod, OperationResource

## Conclusion

Regular expressions are a powerful tool for searching and filtering patterns within text data. In Microsoft Sentinel, the combination of regular expressions and KQL allows operators to extract valuable insights from deployed Azure resources. By understanding the syntax and performance characteristics of regular expressions, leveraging the RE2 library, and testing patterns in KQL, you can harness the full potential of regular expressions in your Microsoft Sentinel workflows. Whether you're creating detection rules or exploring log data, regular expressions in KQL provide a robust and flexible solution for pattern matching and data analysis.

# Using the bin() KQL Function

individual data points. Data analysts often need to aggregate data and calculate summary statistics to gain meaningful insights. One powerful tool for data aggregation in the Kusto Query Language (KQL) is the bin() function. We will explore the various applications of the bin() function and learn how to leverage its capabilities to analyze and summarize data effectively.

## What is the bin() Function?

The bin() function in KQL is used to round values down to a specific bin size. It is commonly used in combination with the summarize by operator to group scattered data points into specific values. The syntax of the bin() function is as follows:

bin(value, roundTo)

Here, value represents the data point that needs to be rounded down, and roundTo indicates the bin size that divides the value. The bin() function returns the nearest multiple of roundTo below value. Null values, a null bin size, or a negative bin size will result in null.

## Numeric Binning with the bin() Function

One common use case of the bin() function is to perform numeric binning. Let's consider an example to understand this better. Suppose we have a dataset that contains the sales revenue for each day. We want to group the revenue into bins based on a specific bin size, such as \$1000. We can achieve this using the bin() function in combination with the summarize by operator. Here's an example query:

datatable(Date: datetime, Revenue: real)

[

datetime(2023-01-01), 1200.50,

datetime(2023-01-02), 2500.75,

datetime(2023-01-03), 1800.25,

datetime(2023-01-04), 3100.80,

datetime(2023-01-05), 900.10

]

\| summarize TotalRevenue = sum(Revenue) by bin(Revenue, 1000)

The bin() function divides the revenue values into bins of size \$1000. The summarize operator calculates the total revenue for each bin. The output of this query will provide insights into the distribution of revenue across different bins, helping us identify trends and patterns in the data.

## Timespan Binning with the bin() Function

In addition to numeric values, the bin() function can also be applied to timespan data. Let's say we have a dataset that contains the duration of phone calls made by customers. We want to group the call durations into specific time intervals, such as 5 minutes. We can achieve this using the bin() function with timespan values. Here's an example query:

datatable(CallDuration: timespan)

[

time(0h, 2m, 30s),

time(0h, 7m, 45s),

time(0h, 4m, 20s),

time(0h, 10m, 15s),

time(0h, 1m, 30s)

]

\| summarize Count = count() by bin(CallDuration, 5m)

In this query, the bin() function divides the call durations into bins of 5 minutes. The summarize operator calculates the count of calls for each bin. This analysis can help us identify the distribution of call durations and uncover any patterns or anomalies in the data.

## Datetime Binning with the bin() Function

The bin() function is also useful for binning datetime values. Consider a scenario where we have a dataset that contains the timestamps of customer orders. We want to group the orders into specific time intervals, such as daily bins. We can accomplish this using the bin() function with datetime values. Here's an example query:

datatable(OrderTime: datetime)

[

datetime(2023-01-01 10:00:00),

datetime(2023-01-01 14:30:00),

datetime(2023-01-02 11:45:00),

datetime(2023-01-02 13:15:00),

datetime(2023-01-03 09:20:00)

]

\| summarize Count = count() by bin(OrderTime, 1d)

In this query, the bin() function divides the order timestamps into daily bins. The summarize operator calculates the count of orders for each bin. This analysis provides insights into the daily order volume, helping us understand customer behavior and plan inventory accordingly.

## Pad a Table with Null Bins

In some cases, there may be missing data points for certain bins in a table. To ensure a complete representation of all bins, we can pad the table with null values for the missing bins. Let's consider an example where we have a dataset of website visits, and we want to analyze the number of visits for each day of the week. Here's an example query:

datatable(Date: datetime, Visits: int)

[

datetime(2023-01-01), 500,

datetime(2023-01-03), 800,

datetime(2023-01-04), 600,

datetime(2023-01-06), 1200,

datetime(2023-01-07), 900

]

\| summarize Visits = sum(Visits) by bin(Date, 1d)

\| range d from datetime(2023-01-01) to datetime(2023-01-07) step 1d

\| join kind=leftouter (datatable(Date: datetime) [d]) on Date

\| order by Date asc

In this query, we first use the summarize operator with the bin() function to calculate the total visits for each day. Then, we use the range operator to generate a table with all the dates in the desired range. Finally, we join the generated table with the summarized data using a left outer join to include null values for the missing days. This ensures that all days of the week are represented in the output, even if there were no visits on certain days.

## Conclusion

The bin() function in KQL is a powerful tool for data aggregation and summarization. It allows us to group data into specific bins based on numeric, timespan, or datetime values. By leveraging the bin() function in combination with other operators like summarize, we can gain valuable insights from our data and uncover trends and patterns. Whether it's analyzing sales revenue, call durations, or customer orders, the bin() function provides a flexible and efficient way to aggregate and summarize data in KQL.

So, the next time you're working with data in KQL, remember to harness the power of the bin() function to unlock deeper insights and make more informed decisions based on your data.

# Understanding Functions in Kusto Query Language

## Introduction to Functions

In Kusto, functions are reusable subqueries or query parts that can be defined as part of the query itself or stored as part of the database metadata. Functions are invoked through a name, provided with input arguments, and produce a single value based on their body. They can be categorized into two types: built-in functions and user-defined functions.

## Built-in Functions in Kusto

Built-in functions are hard-coded functions defined by Kusto and cannot be modified by users. These functions provide a wide range of functionalities, such as mathematical operations, string manipulations, date and time calculations, and aggregations. Kusto provides a comprehensive library of built-in functions that can be directly used in queries.

## User-defined Functions in Kusto

User-defined functions are created by users and can be divided into two types: stored functions and query-defined functions.

### Stored Functions

Stored functions are user-defined functions that are stored and managed as database schema entities, similar to tables. They can be used across multiple queries and provide a way to encapsulate complex logic or calculations. To create a stored function, the .create function command is used.

### Query-defined Functions

Query-defined functions are user-defined functions that are defined and used within the scope of a single query. These functions are created using the let statement and are not stored as separate entities in the database schema. Query-defined functions are useful when a specific calculation or subquery needs to be reused multiple times within a single query.

## Syntax and Naming Conventions for User-defined Functions

User-defined functions in Kusto follow a specific syntax and naming conventions. The function name must follow the same identifier naming rules as other entities in Kusto. The name of the function should be unique within its scope of definition.

let function_name = (input_arguments) {

// Function body

};

The function name is followed by a set of parentheses enclosing the input arguments, and the function body is defined within curly braces. The input arguments can be scalar or tabular, and their types need to be specified. Scalar arguments can also have default values.

## Scalar Functions in KQL

Scalar functions are user-defined functions that have zero input arguments or all input arguments as scalar values. These functions produce a single scalar value and can be used wherever a scalar expression is allowed. Scalar functions can only refer to tables and views that are in the accessible schema and can utilize the row context in which they are defined.

## Tabular Functions in KQL

Tabular functions, on the other hand, accept one or more tabular input arguments and zero or more scalar input arguments. They produce a single tabular value as output. Tabular functions are useful when working with complex data structures or when multiple rows of data need to be returned.

## Creating and Declaring User-defined Functions

To create a user-defined function in Kusto, the let statement is used. The let statement allows us to define variables and functions within a query. Here's an example of creating a simple user-defined function:

let addNumbers = (a: int, b: int) {

a + b

};

In this example, the function addNumbers takes two integer input arguments, a and b, and returns their sum. The function can be invoked by calling its name and passing the required arguments.

## Invoking User-defined Functions

User-defined functions can be invoked within a query by calling their name and providing the required arguments. The invocation syntax varies depending on whether the function expects scalar or tabular arguments.

### Invoking Functions without Arguments

To invoke a function that doesn't require any arguments, simply call the function's name followed by parentheses:

let helloWorld = () {

"Hello, World!"

};

print helloWorld()

In this example, the function helloWorld doesn't require any arguments. It returns the string "Hello, World!" when invoked.

### Invoking Functions with Scalar Arguments

For functions that expect scalar arguments, the arguments should be provided within the parentheses when invoking the function:

let addNumbers = (a: int, b: int) {

a + b

};

print addNumbers(5, 3)

In this case, the function addNumbers expects two integer arguments, a and b. When invoked with the values 5 and 3, it returns the sum of the two numbers, which is 8.

## Default Values in Functions

User-defined functions in Kusto can have default values for their scalar input arguments. Default values are specified after the argument type and are used when the argument is not provided during the function invocation. Here's an example:

let greetUser = (name: string = "Guest") {

strcat("Hello, ", name, "!")

};

print greetUser()

In this case, the function greetUser has a default value for the name argument, which is "Guest". If the function is invoked without providing a value for name, it will use the default value and return the string "Hello, Guest!".

By understanding the concept of functions in Kusto Query Language and how to create and use them effectively, you can enhance the reusability and organization of your queries. Functions provide a way to encapsulate complex logic and calculations, making your queries more efficient and maintainable. Experiment with different types of functions and explore the vast library of built-in functions to unleash the full power of KQL in your data analysis workflows.

Remember, functions are just one aspect of KQL, and there is much more to explore and learn. As you delve deeper into Kusto, your ability to leverage its capabilities will expand, enabling you to extract valuable insights from your data with ease. Happy querying!

# How to Use the KQL Materialize Function

In the world of data analysis and query optimization, finding efficient ways to speed up queries and improve performance is crucial. One powerful tool that can help achieve this is the KQL Materialize Function. In this comprehensive guide, we will explore the ins and outs of using the Materialize Function in Kusto Query Language (KQL) and how it can significantly enhance query execution speed.

## What is the KQL Materialize Function?

The Materialize Function in KQL is designed to capture the value of a tabular expression for the duration of a query execution. By caching the results of a tabular expression, the Materialize Function allows you to reference the cached data multiple times without the need for recalculation. This can be particularly useful when dealing with heavy calculations or non-deterministic expressions.

### Syntax and Parameters

The syntax of the Materialize Function in KQL is straightforward:

materialize(expression)

The only parameter required by the Materialize Function is the tabular expression that you want to evaluate and cache during query execution. The expression can be any valid KQL query or operation that generates a tabular result.

## Advantages of Using the Materialize Function

The Materialize Function offers several advantages that can significantly improve query performance and optimize resource usage. Let's explore some key benefits:

### Speeding up Queries with Heavy Calculations

Queries that involve complex calculations can be time-consuming, especially when the same calculations need to be repeated multiple times within the query. By using the Materialize Function, you can avoid redundant calculations by evaluating the expression only once and referencing the cached result throughout the query. This can lead to substantial time savings, especially for queries with computationally intensive operations.

### Efficient Evaluation of Non-Deterministic Expressions

Non-deterministic expressions, such as those involving the rand() or dcount() functions, can produce different results each time they are evaluated. In such cases, it is crucial to evaluate the expression only once and use the same result throughout the query. The Materialize Function allows you to achieve this by caching the tabular expression and referencing it multiple times. This ensures consistent results and avoids unnecessary recalculations.

### Reduced Resource Consumption

By caching the results of a tabular expression, the Materialize Function reduces the overall resource consumption during query execution. Instead of recalculating the expression each time it is referenced, the cached result is used, resulting in lower CPU and memory usage. This can be particularly beneficial in scenarios where large datasets or complex calculations are involved, as it helps optimize resource allocation and improves query performance.

## Performance Improvement Examples

To better understand how the Materialize Function can improve query performance, let's explore a couple of examples:

### Example 1: Speeding up Queries with Heavy Calculations

Suppose you have a query that performs heavy calculations on a tabular expression and uses the result multiple times. Without using the Materialize Function, the query would recalculate the expression for each reference, leading to redundant computations. However, by applying the Materialize Function, you can evaluate the expression once and reference the cached result, significantly reducing the query execution time.

NOTE: Run the following at <https://dataexplorer.azure.com/>

let \_detailed_data = materialize(StormEvents \| summarize Events=count() by State, EventType);

\_detailed_data

\| summarize TotalStateEvents=sum(Events) by State

\| join (_detailed_data) on State

\| extend EventPercentage = Events\*100.0 / TotalStateEvents

\| project State, EventType, EventPercentage, Events

\| top 10 by EventPercentage

In this example, the \_detailed_data tabular expression is defined using the Materialize Function. As a result, the expression is calculated only once, improving the overall query performance.

### Example 2: Efficient Evaluation of Non-Deterministic Expressions

Consider a scenario where you need to generate a set of random numbers and perform various calculations on the set. Without using the Materialize Function, each reference to the random number set would generate a new set of numbers, resulting in different results for each reference. However, by applying the Materialize Function, you can generate the random number set once and use the same set throughout the query, ensuring consistent results.

let randomSet = materialize(range x from 1 to 3000000 step 1 \| project value = rand(10000000));

randomSet

\| summarize Dcount=dcount(value)

; randomSet

\| top 3 by value

; randomSet

\| summarize Sum=sum(value)

In this example, the randomSet tabular expression is generated using the Materialize Function. The same set of random numbers is used in multiple calculations, ensuring consistent results and optimizing query performance.

## Using Materialize() in Let Statements

The Materialize Function can also be used in conjunction with let statements to give cached results a name. This can be particularly useful when you want to reference the cached result multiple times within the same query. Let's take a look at an example:

let materializedData = materialize(AppAvailabilityResults \| where TimeGenerated \> ago(1d));

union (materializedData \| where AppRoleName !has "somestring" \| summarize dcount(ClientOS)),

(materializedData \| where AppRoleName !has "somestring" \| summarize dcount(ClientCity))

In this example, the materializedData tabular expression is created using the Materialize Function. The cached result is then referenced twice within the union statement, allowing for efficient evaluation and improved query performance.

## Best Practices for Using Materialize()

To make the most out of the Materialize Function in KQL, consider following these best practices:

Push Operators that Reduce the Materialized Dataset: Whenever possible, apply operators that reduce the size of the materialized dataset. For example, use common filters on top of the same materialized expression. This helps optimize query performance by minimizing the amount of data that needs to be cached and processed.

Use Materialize with Join or Union Operations: If your query involves join or union operations with mutual subqueries, make use of the Materialize Function. By materializing the shared subqueries, you can execute them once and reuse the results throughout the query. This can lead to significant performance improvements, especially when dealing with large datasets.

Name Cached Results in Let Statements: When using the Materialize Function in let statements, give the cached result a name. This makes it easier to reference the cached data multiple times within the same query and improves query readability.

## Common Mistakes to Avoid

While using the Materialize Function can greatly enhance query performance, it's important to be aware of common mistakes that can hinder its effectiveness. Here are some pitfalls to avoid:

Exceeding the Cache Size Limit: The Materialize Function has a cache size limit of 5 GB per cluster node. Keep this in mind when designing queries that use the Materialize Function. If the cache reaches its limit, the query will abort with an error, impacting performance.

Overusing Materialize: While the Materialize Function can improve performance, it should be used judiciously. Applying materialization to every expression in a query can lead to excessive resource consumption and may not always result in performance gains. Analyze your query requirements and apply materialization selectively where it provides the most benefit.

Neglecting Query Semantics: When using the Materialize Function, it's essential to ensure that the semantics of your query are preserved. Be mindful of the operators and filters applied to the materialized expression, as they may affect the final results. Carefully review your query to ensure that the desired semantics are maintained.

## Conclusion

The KQL Materialize Function is a powerful tool that can significantly enhance query performance and optimize resource usage. By caching the results of a tabular expression, the Materialize Function allows for efficient evaluation of heavy calculations and non-deterministic expressions. It reduces redundant computations, speeds up query execution, and improves resource allocation.

When using the Materialize Function, remember to follow best practices, such as pushing operators that reduce the materialized dataset and using it with join or union operations. Avoid common mistakes like exceeding the cache size limit and neglecting query semantics.

By harnessing the power of the Materialize Function, you can unlock the full potential of Kusto Query Language and take your data analysis and query optimization to new heights.
