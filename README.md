# Complete Splunk Test Questions Collection

This collection contains all unique questions from multiple Splunk certification tests, organized by topic for easy studying. Duplicates have been removed, and corrections have been applied where necessary.

## Table of Contents
- [Field Extraction](#field-extraction)
- [Commands and Functions](#commands-and-functions)
  - [Eval Command](#eval-command)
  - [Transaction Command](#transaction-command)
  - [Stats and Chart Commands](#stats-and-chart-commands)
  - [Timechart Command](#timechart-command)
  - [Search Command](#search-command)
  - [Other Commands](#other-commands)
- [Knowledge Objects](#knowledge-objects)
- [Security and Role-Based Access Control](#security-and-role-based-access-control)
- [Deployment Architecture](#deployment-architecture)
- [Dashboard Creation and Customization](#dashboard-creation-and-customization)
- [Performance Optimization](#performance-optimization)
- [Troubleshooting](#troubleshooting)
- [Advanced Searching](#advanced-searching)
- [Data Onboarding and Management](#data-onboarding-and-management)
- [Miscellaneous](#miscellaneous)

## Field Extraction

<details>
<summary><b>Which of the following statements describes the use of the Field Extractor (FX)?</b></summary>

- a) The Field Extractor automatically extracts all fields at search time.
- b) The Field Extractor uses PERL to extract fields from the raw events.
- c) Fields extracted using the Field Extractor persist as knowledge objects.
- d) Fields extracted using the Field Extractor do not persist and must be defined for each search.

**✅ ANSWER: c) Fields extracted using the Field Extractor persist as knowledge objects.**
</details>

<details>
<summary><b>Which delimiters can the Field Extractor (FX) detect? (Choose all that apply)</b></summary>

- a) Tabs
- b) Pipes
- c) Spaces
- d) Commas

**✅ ANSWER: Multiple selections: a) Tabs, b) Pipes, c) Spaces, d) Commas**
</details>

<details>
<summary><b>When using the Field Extractor (FX), which of the following delimiters will work? (Choose all that apply)</b></summary>

- a) Pipes
- b) Tabs
- c) Spaces
- d) Colons

**✅ ANSWER: Multiple selections: a) Pipes, b) Tabs, c) Spaces, d) Colons**
</details>

<details>
<summary><b>There are several ways to access the field extractor. Which option automatically identifies the data type, source type, and sample event?</b></summary>

- a) Event Actions > Extract Fields
- b) Fields sidebar > Extract New Fields
- c) Settings > Field Extractions > New Field Extraction
- d) Settings > Field Extractions > Open Field Extractor

**✅ ANSWER: a) Event Actions > Extract Fields**
</details>

<details>
<summary><b>When performing a regular expression (regex) field extraction using the Field Extractor (FX), what happens when the require option is used?</b></summary>

- a) The regex can no longer be edited.
- b) The field being extracted will be required for all future events.
- c) The events without the required field will not display in searches.
- d) Only events with the required string will be included in the extraction.

**✅ ANSWER: d) Only events with the required string will be included in the extraction.**
</details>

<details>
<summary><b>Which of the following file formats can be extracted using a delimiter field extraction?</b></summary>

- a) XML
- b) CSV
- c) JSON
- d) PDF

**✅ ANSWER: b) CSV**
</details>

## Commands and Functions

### Eval Command

<details>
<summary><b>The eval command allows you to do which of the following? (Choose all that apply)</b></summary>

- a) Format values
- b) Convert values
- c) Perform calculations
- d) Use conditional statements

**✅ ANSWER: Multiple selections: a) Format values, b) Convert values, c) Perform calculations, d) Use conditional statements**
</details>

<details>
<summary><b>Which of the following actions can the eval command perform?</b></summary>

- a) Remove fields from results.
- b) Create or replace an existing field.
- c) Group transactions by one or more fields.
- d) Save SPL commands to be reused in other searches.

**✅ ANSWER: b) Create or replace an existing field.**
</details>

<details>
<summary><b>Where are the results of eval commands stored?</b></summary>

- a) In a field.
- b) In an index.
- c) In a KV Store.
- d) In a database.

**✅ ANSWER: a) In a field.**
</details>

<details>
<summary><b>In the following eval statement, what is the value of description if the status is 503?</b></summary>

```
index=main | eval description=case(status==200, "OK", status==404, "Not found", status==500, "Internal Server Error")
```

- a) The description field would contain no value.
- b) The description field would contain the value 0.
- c) The description field would contain the value "Internal Server Error".
- d) This statement would produce an error in Splunk because it is incomplete.

**✅ ANSWER: a) The description field would contain no value.**

**Explanation:** According to Splunk's documentation on the case() function, if none of the boolean expressions is true, the result evaluates to NULL. Since there's no condition for status=503, the description field would contain no value (NULL).
</details>

<details>
<summary><b>Which of the following can be used with the eval command tostring function? (Choose all that apply)</b></summary>

- a) "hex"
- b) "commas"
- c) "decimal"
- d) "duration"

**✅ ANSWER: Multiple selections: a) "hex", b) "commas", d) "duration"**
</details>

<details>
<summary><b>What type of command is eval?</b></summary>

- a) Non-streaming command
- b) Centralized streaming
- c) Distributed streaming
- d) Orchestrating

**✅ ANSWER: c) Distributed streaming**
</details>

### Transaction Command

<details>
<summary><b>What does the transaction command do?</b></summary>

- a) Groups a set of transactions based on time.
- b) Creates a single event from a group of events.
- c) Separates two events based on one or more values.
- d) Returns the number of credit card transactions found in the event logs.

**✅ ANSWER: b) Creates a single event from a group of events.**
</details>
<details>
<summary><b>When using the transaction command, what does the argument maxspan do?</b></summary>

- a) Sets the maximum length of all the events within a transaction.
- b) Sets the maximum length that any single event can reach to be included in the transaction.
- c) Sets the maximum total time between events in a transaction.
- d) Sets the maximum total time between the earliest and latest events in a transaction.

**✅ ANSWER: d) Sets the maximum total time between the earliest and latest events in a transaction.**
</details>

<details>
<summary><b>To identify all of the contributing events within a transaction that contain at least one REJECT event, which syntax is correct?</b></summary>

- a) index=main REJECT | transaction sessionid
- b) index=main | transaction sessionid | search REJECT
- c) index=main | transaction sessionid | where transaction=reject
- d) index=main | transaction sessionid | where transaction="REJECT*

**✅ ANSWER: b) index=main | transaction sessionid | search REJECT**
</details>

<details>
<summary><b>What do events in a transaction have in common?</b></summary>

- a) All events in a transaction must have the same timestamp.
- b) All events in a transaction must have the same sourcetype.
- c) All events in a transaction must have the exact same set of fields.
- d) All events in a transaction must be related by one or more fields.

**✅ ANSWER: d) All events in a transaction must be related by one or more fields.**
</details>

<details>
<summary><b>Which of the following statements describe the command below? (Choose all that apply)</b></summary>

```
sourcetype=access_combined | transaction JSESSIONID
```

- a) An additional field named maxspan is created.
- b) An additional field named duration is created.
- c) An additional field named eventcount is created.
- d) Events with the same JSESSIONID will be grouped together into a single event.

**✅ ANSWER: Multiple selections: b) An additional field named duration is created, c) An additional field named eventcount is created, d) Events with the same JSESSIONID will be grouped together into a single event.**
</details>

<details>
<summary><b>Which of the following statements describe the search below? (Choose all that apply)</b></summary>

```
index=main | transaction clientip host maxspan=30s maxpause=5s
```

- a) Events in the transaction occurred within 5 seconds.
- b) It groups events that share the same clientip and host.
- c) The first and last events are no more than 5 seconds apart.
- d) The first and last events are no more than 30 seconds apart

**✅ ANSWER: Multiple selections: a) Events in the transaction occurred within 5 seconds, b) It groups events that share the same clientip and host, d) The first and last events are no more than 30 seconds apart**
</details>

<details>
<summary><b>When should transaction be used?</b></summary>

- a) Only in a large distributed Splunk environment.
- b) When calculating results from one or more fields.
- c) When event grouping is based on start/end values.
- d) When grouping events results in over 1000 events in each group.

**✅ ANSWER: c) When event grouping is based on start/end values.**
</details>

<details>
<summary><b>Consider the following search: index=web sourcetype=access_combined The log shows several events that share the same JSESSIONID value (SD421K26502F783). View the events as a group. From the following list, which search groups events by JSESSIONID?</b></summary>

- a) index-web sourcetype=access_combined | transaction JSESSIONID | search SD42IK26502F783
- b) index-web sourcetype=access_combined | highlight JSESSIONID | search SD421K26502F783
- c) index=web sourcetype=access_combined SD42IK26502F783 | table JSESSIONID
- d) index=web sourcetype=access_combined JSESSIONID <SD421K26502F783>

**✅ ANSWER: a) index-web sourcetype=access_combined | transaction JSESSIONID | search SD42IK26502F783**
</details>

<details>
<summary><b>When should you use the transaction command instead of the stats command?</b></summary>

- a) When you need to group on multiple values.
- b) When duration is irrelevant in search results.
- c) When you have over 1000 events in a transaction.
- d) When you need to group based on start and end constraints.

**✅ ANSWER: d) When you need to group based on start and end constraints.**
</details>

### Stats and Chart Commands

<details>
<summary><b>Which of the following statements is true, especially in large environments?</b></summary>

- a) Use the stats command when you need to group events by two or more fields.
- b) The stats command is faster and more efficient than the transaction command.
- c) The transaction command is faster and more efficient than the stats command.
- d) Use the transaction command when you want to see the results of a calculation

**✅ ANSWER: b) The stats command is faster and more efficient than the transaction command.**
</details>

<details>
<summary><b>Which of the following searches would return a report of sales by product_name?</b></summary>

- a) chart sales by product_name
- b) chart sum(price) as sales by product_name
- c) stats sum(price) as sales over product_name
- d) timechart list(sales), values(product_name)

**✅ ANSWER: b) chart sum(price) as sales by product_name**
</details>

<details>
<summary><b>What does the following search do: index=corndog type=mysterymeat action=eaten | stats count as corndog_count by user?</b></summary>

- a) Creates a table of the total count of users and split by corndogs.
- b) Creates a table of the total count of mysterymeat corndogs split by user.
- c) Creates a table with the count of all types of corndogs eaten split by user.
- d) Creates a table that groups the total number of users by vegetarian corndogs.

**✅ ANSWER: b) Creates a table of the total count of mysterymeat corndogs split by user.**
</details>

<details>
<summary><b>Which command can include both an over and a by clause to divide results into sub-groupings?</b></summary>

- a) chart
- b) stats
- c) xyseries
- d) transaction

**✅ ANSWER: a) chart**
</details>

<details>
<summary><b>What other syntax will produce exactly the same results as | chart count over vendor_action by user?</b></summary>

- a) | chart count by vendor_action, user
- b) | chart count over vendor_action, user
- c) | chart count by vendor_action over user
- d) | chart count over user by vendor_action

**✅ ANSWER: a) | chart count by vendor_action, user**
</details>

<details>
<summary><b>In most large Splunk environments, what is the most efficient command that can be used to group events by fields?</b></summary>

- a) join
- b) stats
- c) streamstats
- d) transaction

**✅ ANSWER: b) stats**
</details>

<details>
<summary><b>Which of the following commands support the same set of functions?</b></summary>

- a) stats, eval, table
- b) search, where, eval
- c) stats, chart, timechart
- d) transaction, chart, timechart

**✅ ANSWER: c) stats, chart, timechart**
</details>

<details>
<summary><b>How does a user display a chart in stack mode?</b></summary>

- a) By using the stack command.
- b) By turning on the Use Trellis Layout option.
- c) By changing Stack Mode in the Format menu.
- d) You cannot display a chart in stack mode, only a timechart.

**✅ ANSWER: c) By changing Stack Mode in the Format menu.**
</details>

### Timechart Command

<details>
<summary><b>When using the timechart command, how can a user group the events into buckets based on time?</b></summary>

- a) Using the span argument.
- b) Using the duration argument.
- c) Using the interval argument.
- d) Adjusting the fieldformat options.

**✅ ANSWER: a) Using the span argument.**
</details>

<details>
<summary><b>When using timechart, how many fields can be listed after a by clause?</b></summary>

- a) 0, because timechart doesn't support using a by clause.
- b) 1, because _time is already implied as the x-axis.
- c) 2, because one field would represent the x-axis and the other would represent the y-axis.
- d) There is no limit specific to timechart

**✅ ANSWER: b) 1, because _time is already implied as the x-axis.**
</details>

<details>
<summary><b>When using | timechart by host, which field is represented in the x-axis?</b></summary>

- a) date
- b) host
- c) time
- d) _time

**✅ ANSWER: d) _time**
</details>

### Search Command

<details>
<summary><b>Which one of the following statements about the search command is true?</b></summary>

- a) It does not allow the use of wildcards.
- b) It treats field values in a case-sensitive manner.
- c) It can only be used at the beginning of the search pipeline.
- d) It behaves exactly like search strings before the first pipe.

**✅ ANSWER: d) It behaves exactly like search strings before the first pipe.**
</details>

### Other Commands

<details>
<summary><b>If no value is specified with the fillnull command, what default value will be used?</b></summary>

- a) 0
- b) N/A
- c) —
- d) NULL

**✅ ANSWER: a) 0**
</details>

<details>
<summary><b>Which of the following statements would help a user choose between the transaction and stats commands?</b></summary>

- a) stats can only group events using IP addresses.
- b) The transaction command is faster and more efficient.
- c) There is a 1000 event limitation with the transaction command.
- d) Use stats when the events need to be viewed as a single correlated event.

**✅ ANSWER: c) There is a 1000 event limitation with the transaction command.**
</details>

<details>
<summary><b>A user wants to convert numeric field values to strings and also to sort on those values. Which command should be used first, the eval or the sort?</b></summary>

- a) It doesn't matter whether eval or sort is used first.
- b) Convert the numeric to a string with eval first, then sort.
- c) Use sort first, then convert the numeric to a string with eval.
- d) You cannot use the sort command and the eval command on the same field.

**✅ ANSWER: c) Use sort first, then convert the numeric to a string with eval.**
</details>
<details>
<summary><b>Which type of visualization shows relationships between discrete values in three dimensions?</b></summary>

- a) Pie chart
- b) Line chart
- c) Bubble chart
- d) Scatter chart

**✅ ANSWER: c) Bubble chart**
</details>

## Knowledge Objects

### Field Aliases

<details>
<summary><b>In what order are the following knowledge objects/configurations applied?</b></summary>

- a) Field Aliases, Field Extractions, Lookups
- b) Field Extractions, Field Aliases, Lookups
- c) Field Extractions, Lookups, Field Aliases
- d) Lookups, Field Aliases, Field Extractions

**✅ ANSWER: b) Field Extractions, Field Aliases, Lookups**
</details>

<details>
<summary><b>Which of the following statements describes field aliases?</b></summary>

- a) Field alias names replace the original field name.
- b) Field aliases can be used in lookup file definitions.
- c) Field aliases only normalize data across sources and sourcetypes.
- d) Field alias names are not case sensitive when used as part of a search.

**✅ ANSWER: b) Field aliases can be used in lookup file definitions.**
</details>

<details>
<summary><b>A field alias has been created based on an original field. A search without any transforming commands is then executed in Smart Mode. Which field name appears in the results?</b></summary>

- a) Both will appear in the All Fields list, but only if the alias is specified in the search.
- b) Both will appear in the Interesting Fields list, but only if they appear in at least 20 percent of events.
- c) The original field only appears in All Fields list and the alias only appears in the Interesting Fields list.
- d) The alias only appears in the All Fields list and the original field only appears in the Interesting Fields list.

**✅ ANSWER: b) Both will appear in the Interesting Fields list, but only if they appear in at least 20 percent of events.**
</details>

<details>
<summary><b>A user wants to create a new field alias for a field that appears in two sourcetypes. How many field aliases need to be created?</b></summary>

- a) One.
- b) Two.
- c) It depends on whether the original fields have the same name.
- d) It depends on whether the two sourcetypes are associated with the same index.

**✅ ANSWER: b) Two.**
</details>

### Calculated Fields

<details>
<summary><b>Which of the following statements describe calculated fields? (Choose all that apply)</b></summary>

- a) Calculated fields can be used in the search bar.
- b) Calculated fields can be based on an extracted field.
- c) Calculated fields can only be applied to host and sourcetype.
- d) Calculated fields are shortcuts for performing calculations using the eval command.

**✅ ANSWER: Multiple selections: a) Calculated fields can be used in the search bar, b) Calculated fields can be based on an extracted field, d) Calculated fields are shortcuts for performing calculations using the eval command.**
</details>

<details>
<summary><b>Which knowledge object represents the output of an eval expression?</b></summary>

- a) Eval fields
- b) Calculated fields
- c) Field extractions
- d) Calculated lookups

**✅ ANSWER: b) Calculated fields**
</details>

<details>
<summary><b>Calculated fields can be based on which of the following?</b></summary>

- a) Tags
- b) Extracted fields
- c) Output fields for a lookup
- d) Fields generated from a search string

**✅ ANSWER: b) Extracted fields**
</details>

<details>
<summary><b>Which of the following statements describes calculated fields?</b></summary>

- a) Calculated fields are only used on fields added by lookups.
- b) Calculated fields are a shortcut for repetitive and complex eval commands.
- c) Calculated fields are a shortcut for repetitive and complex calc commands.
- d) Calculated fields automatically calculate the simple moving average for indexed fields.

**✅ ANSWER: b) Calculated fields are a shortcut for repetitive and complex eval commands.**
</details>

### Macros

<details>
<summary><b>Which of the following statements describes macros?</b></summary>

- a) A macro is a reusable search string that must contain the full search.
- b) A macro is a reusable search string that must have a fixed time range.
- c) A macro is a reusable search string that may have a flexible time range.
- d) A macro is a reusable search string that must contain only a portion of the search.

**✅ ANSWER: c) A macro is a reusable search string that may have a flexible time range.**
</details>

<details>
<summary><b>When can a pipe follow a macro?</b></summary>

- a) A pipe may always follow a macro.
- b) The current user must own the macro.
- c) The macro must be defined in the current app.
- d) Only when sharing is set to global for the macro.

**✅ ANSWER: a) A pipe may always follow a macro.**
</details>

<details>
<summary><b>Which of the following statements about macros is true? (Choose all that apply)</b></summary>

- a) Arguments are defined at execution time.
- b) Arguments are defined when the macro is created.
- c) Argument values are used to resolve the search string at execution time.
- d) Argument values are used to resolve the search string when the macro is created.

**✅ ANSWER: Multiple selections: b) Arguments are defined when the macro is created, c) Argument values are used to resolve the search string at execution time.**
</details>

<details>
<summary><b>What is required for a macro to accept three arguments?</b></summary>

- a) The macro's name ends with (3).
- b) The macro's name starts with (3).
- c) The macro's argument count setting is 3 or more.
- d) Nothing, all macros can accept any number of arguments.

**✅ ANSWER: a) The macro's name ends with (3).**

**TIP:** `function_name(no_of_arguments)`
</details>

<details>
<summary><b>When defining a macro, what are the required elements?</b></summary>

- a) Name and a validation error message.
- b) Definition and arguments.
- c) Name and arguments.
- d) Name and definition.

**✅ ANSWER: d) Name and definition.**
</details>

<details>
<summary><b>In which Settings section are macros defined?</b></summary>

- a) Fields
- b) Tokens
- c) Advanced Search
- d) Searches, Reports, Alerts

**✅ ANSWER: c) Advanced Search**
</details>
### Event Types

<details>
<summary><b>Which of the following statements about event types is true? (Choose all that apply)</b></summary>

- a) Event types can be tagged.
- b) Event types must include a time range.
- c) Event types categorize events based on a search.
- d) Event types can be a useful method for capturing and sharing knowledge.

**✅ ANSWER: Multiple selections: a) Event types can be tagged, c) Event types categorize events based on a search, d) Event types can be a useful method for capturing and sharing knowledge.**

**Note:** There's some doubt about this question in the original document.
</details>

<details>
<summary><b>In which of the following scenarios is an event type more effective than a saved search?</b></summary>

- a) When a search should always include the same time range.
- b) When a search needs to be added to other users' dashboards.
- c) When the search string needs to be used in future searches.
- d) When formatting needs to be included with the search string.

**✅ ANSWER: c) When the search string needs to be used in future searches.**
</details>

<details>
<summary><b>When multiple event types with different color values are assigned to the same event, what determines the color displayed for the event?</b></summary>

- a) Rank
- b) Weight
- c) Priority
- d) Precedence

**✅ ANSWER: c) Priority**
</details>

<details>
<summary><b>Which are valid ways to create an event type? (Choose all that apply)</b></summary>

- a) By using the searchtypes command in the search bar.
- b) By editing the event_type stanza in the props.conf file.
- c) By going to the Settings menu and clicking Event Types > New.
- d) By selecting an event in search results and clicking Event Actions > Build Event Type.

**✅ ANSWER: Multiple selections: c) By going to the Settings menu and clicking Event Types > New, d) By selecting an event in search results and clicking Event Actions > Build Event Type.**
</details>

<details>
<summary><b>Tags can be added to Event Types?</b></summary>

- a) TRUE
- b) FALSE

**✅ ANSWER: a) TRUE**
</details>

### Tags

<details>
<summary><b>What is the correct syntax to search for a tag associated with a value on a specific field?</b></summary>

- a) tag=<field>
- b) tag=<field>(<tagname>)
- c) tag=<field>::<tagname>
- d) tag::<field>=<tagname>

**✅ ANSWER: d) tag::<field>=<tagname>**
</details>

<details>
<summary><b>Which of the following statements about tags is true? (Choose all that apply)</b></summary>

- a) Tags are case-insensitive.
- b) Tags are based on field/value pairs.
- c) Tags categorize events based on a search.
- d) Tags are designed to make data more understandable.

**✅ ANSWER: Multiple selections: b) Tags are based on field/value pairs, d) Tags are designed to make data more understandable.**
</details>

<details>
<summary><b>Which of the following searches will return events containing a tag named Privileged?</b></summary>

- a) tag=Priv
- b) tag=Priv*
- c) tag=priv*
- d) tag=privileged

**✅ ANSWER: b) tag=Priv***
</details>

<details>
<summary><b>What is the correct syntax to find events associated with a tag?</b></summary>

- a) tag:<field>=<tagname>
- b) tag=<tagname>
- c) tag=<field>::<tagname>
- d) tag=<field>

**✅ ANSWER: b) tag=<tagname>**
</details>

### Data Models and Pivot

<details>
<summary><b>What is the relationship between data models and pivots?</b></summary>

- a) Data models provide the datasets for pivots.
- b) Pivots and data models have no relationship.
- c) Pivots and data models are the same thing.
- d) Pivots provide the datasets for data models.

**✅ ANSWER: a) Data models provide the datasets for pivots.**
</details>

<details>
<summary><b>A data model can consist of what three types of datasets?</b></summary>

- a) Pivot, events, and transactions.
- b) Searches, transactions, and pivot.
- c) Pivot, searches, and events.
- d) Events, searches, and transactions

**✅ ANSWER: d) Events, searches, and transactions**
</details>

<details>
<summary><b>Which statement is true?</b></summary>

- a) Pivot is used for creating datasets.
- b) Data models are randomly structured datasets.
- c) Pivot is used for creating reports and dashboards.
- d) In most cases, each Splunk user will create their own data model.

**✅ ANSWER: c) Pivot is used for creating reports and dashboards.**
</details>

<details>
<summary><b>Which of the following statements describe the search string below?</b></summary>

```
| datamodel Application_State All_Application_State search
```

- a) Events will be returned from dataset named Application_State.
- b) Events will be returned from the data model named Application_State.
- c) Events will be returned from the data model named All_Application_State.
- d) No events will be returned because the pipe should occur after the datamodel command.

**✅ ANSWER: b) Events will be returned from the data model named Application_State.**
</details>

<details>
<summary><b>Which of the following statements about data models and pivot are true? (Choose all that apply)</b></summary>

- a) They are both knowledge objects.
- b) Data models are created out of datasets called pivots.
- c) Pivot requires users to input SPL searches on data models.
- d) Pivot allows the creation of data visualizations that present different aspects of a data model.

**✅ ANSWER: Multiple selections: a) They are both knowledge objects, d) Pivot allows the creation of data visualizations that present different aspects of a data model.**

**Note:** There's some doubt about this question in the original document regarding option A vs (A and D).
</details>

<details>
<summary><b>Which of the following is the correct way to use the datamodel command to search fields in the Web data model within the Web dataset?</b></summary>

- a) | datamodel Web Web search | fields Web*
- b) | search datamodel Web Web | fields Web*
- c) | datamodel Web Web fields | search Web*
- d) datamodel=Web | search Web | fields Web*

**✅ ANSWER: a) | datamodel Web Web search | fields Web***
</details>

<details>
<summary><b>What are the two parts of a root event dataset?</b></summary>

- a) Fields and variables.
- b) Fields and attributes.
- c) Constraints and fields.
- d) Constraints and lookups.

**✅ ANSWER: c) Constraints and fields.**
</details>

<details>
<summary><b>Data model fields can be added using the Auto-Extracted method. Which of the following statements describe Auto-Extracted fields? (Choose all that apply)</b></summary>

- a) Auto-Extracted fields can be hidden in Pivot.
- b) Auto-Extracted fields can have their data type changed.
- c) Auto-Extracted fields can be given a friendly name for use in Pivot.
- d) Auto-Extracted fields can be added if they already exist in the dataset with constraints.

**✅ ANSWER: Multiple selections: a) Auto-Extracted fields can be hidden in Pivot, b) Auto-Extracted fields can have their data type changed, c) Auto-Extracted fields can be given a friendly name for use in Pivot, d) Auto-Extracted fields can be added if they already exist in the dataset with constraints.**
</details>

<details>
<summary><b>Which of the following statements describe data model acceleration? (Choose all that apply)</b></summary>

- a) Accelerated data models cannot be edited.
- b) Private data models cannot be accelerated.
- c) Root events cannot be accelerated.
- d) You must have administrative permissions or the accelerate_datamodel capability to accelerate a data model.

**✅ ANSWER: Multiple selections: a) Accelerated data models cannot be edited, b) Private data models cannot be accelerated, d) You must have administrative permissions or the accelerate_datamodel capability to accelerate a data model.**
</details>

<details>
<summary><b>Which group of users would most likely use pivots?</b></summary>

- a) Users
- b) Architects
- c) Administrators
- d) Knowledge Managers

**✅ ANSWER: a) Users**
</details>

### Workflow Actions

<details>
<summary><b>Which of the following statements describes Search workflow actions?</b></summary>

- a) By default, Search workflow actions will run as a real-time search.
- b) Search workflow actions can be configured as scheduled searches.
- c) The user can define the time range of the search when created the workflow action.
- d) Search workflow actions cannot be configured with a search string that includes the transaction command.

**✅ ANSWER: c) The user can define the time range of the search when created the workflow action.**
</details>

<details>
<summary><b>When is a GET workflow action needed?</b></summary>

- a) To send field values to an external resource.
- b) To retrieve information from an external resource.
- c) To use field values to perform a secondary search.
- d) To define how events flow from forwarders to indexes.

**✅ ANSWER: b) To retrieve information from an external resource.**
</details>

<details>
<summary><b>When creating a Search workflow action, which field is required?</b></summary>

- a) Search string
- b) Data model name
- c) Permission setting
- d) An eval statement

**✅ ANSWER: a) Search string**
</details>

<details>
<summary><b>What is a limitation of searches generated by workflow actions?</b></summary>

- a) Searches generated by workflow actions cannot use macros.
- b) Searches generated by workflow actions must be less than 256 characters long.
- c) Searches generated by workflow actions must run in the same app as the workflow action.
- d) Searches generated by workflow actions run with the same permissions as the user running them.

**✅ ANSWER: d) Searches generated by workflow actions run with the same permissions as the user running them.**
</details>

<details>
<summary><b>Which workflow uses field values to perform a secondary search?</b></summary>

- a) POST
- b) Action
- c) Search
- d) Sub-search

**✅ ANSWER: c) Search**
</details>
<details>
<summary><b>Which of the following statements describes POST workflow actions?</b></summary>

- a) Configuration of a POST workflow action includes choosing a sourcetype.
- b) POST workflow actions can be configured to send email to the URI location.
- c) By default, POST workflow actions are shown in both the event and field menus.
- d) POST workflow actions can be configured to send POST arguments to the URI location.

**✅ ANSWER: d) POST workflow actions can be configured to send POST arguments to the URI location.**
</details>

<details>
<summary><b>Information needed to create a GET workflow action includes which of the following? (Choose all that apply)</b></summary>

- a) A name for the workflow action.
- b) A URI where the user will be directed at search time.
- c) A label that will appear in the Event Action menu at search time.
- d) A name for the URI where the user will be directed at search time.

**✅ ANSWER: Multiple selections: a) A name for the workflow action, b) A URI where the user will be directed at search time, c) A label that will appear in the Event Action menu at search time.**
</details>

<details>
<summary><b>Which of the following statements describe GET workflow actions?</b></summary>

- a) GET workflow actions must be configured with POST arguments.
- b) Configuration of GET workflow actions includes choosing a sourcetype.
- c) Label names for GET workflow actions must include a field name surrounded by dollar signs.
- d) GET workflow actions can be configured to open the URI link in the current window or in a new window.

**✅ ANSWER: d) GET workflow actions can be configured to open the URI link in the current window or in a new window.**
</details>

<details>
<summary><b>Which of the following statements describes POST workflow actions?</b></summary>

- a) POST workflow actions are always encrypted.
- b) POST workflow actions cannot use field values in their URI.
- c) POST workflow actions cannot be created on custom sourcetypes.
- d) POST workflow actions can open a web page in either the same window or a new window.

**✅ ANSWER: d) POST workflow actions can open a web page in either the same window or a new window.**
</details>

<details>
<summary><b>Which of the following are required to create a POST workflow action?</b></summary>

- a) Label, URI, search string.
- b) XML attributes, URI, name.
- c) Label, URI, post arguments.
- d) URI, search string, time range picker.

**✅ ANSWER: c) Label, URI, post arguments.**
</details>

<details>
<summary><b>Which workflow action method can be used when the action type is set to link?</b></summary>

- a) GET
- b) PUT
- c) Search
- d) UPDATE

**✅ ANSWER: a) GET**
</details>

<details>
<summary><b>When using a field value variable with a Workflow Action, which punctuation mark will prevent escape of URL or HTTP form field values?</b></summary>

- a) $!
- b) $
- c) ^
- d) #

**✅ ANSWER: a) $!**
</details>

### Common Information Model (CIM)

<details>
<summary><b>Which of the following is a function of the Splunk Common Information Model (CIM)?</b></summary>

- a) Normalizing data across a Splunk deployment.
- b) Providing templates for reports and dashboards.
- c) Algorithmically shifting events to other indexes.
- d) Reingesting previously indexed data with new field names.

**✅ ANSWER: a) Normalizing data across a Splunk deployment.**
</details>

<details>
<summary><b>Which of the following data models are included in the Splunk Common Information Model (CIM) add-on? (Choose all that apply)</b></summary>

- a) Alerts
- b) Email
- c) Databases
- d) User permissions

**✅ ANSWER: Multiple selections: a) Alerts, b) Email, c) Databases**
</details>

<details>
<summary><b>Which of the following statements describe the Common Information Model (CIM)? (Choose all that apply)</b></summary>

- a) CIM is a methodology for normalizing data.
- b) CIM can correlate data from different sources.
- c) The Knowledge Manager uses the CIM to create knowledge objects.
- d) CIM is an app that can coexist with other apps on a single Splunk deployment.

**✅ ANSWER: Multiple selections: a) CIM is a methodology for normalizing data, b) CIM can correlate data from different sources, c) The Knowledge Manager uses the CIM to create knowledge objects, d) CIM is an app that can coexist with other apps on a single Splunk deployment.**
</details>

<details>
<summary><b>Which Knowledge Object does the Splunk Common Information Model (CIM) use to normalize data, in addition to field aliases, event types, and tags?</b></summary>

- a) Macros
- b) Lookups
- c) Workflow actions
- d) Field extractions

**✅ ANSWER: Multiple selections: b) Lookups, d) Field extractions**
</details>

<details>
<summary><b>By default, how is acceleration configured in the Splunk Common Information Model (CIM) add-on?</b></summary>

- a) Turned off.
- b) Turned on.
- c) Determined automatically based on the sourcetype.
- d) Determined automatically based on the data source.

**✅ ANSWER: a) Turned off.**
</details>

<details>
<summary><b>What does the Splunk Common Information Model (CIM) add-on include? (Choose all that apply)</b></summary>

- a) Custom visualizations
- b) Pre-configured data models
- c) Fields and event category tags
- d) Automatic data model acceleration

**✅ ANSWER: Multiple selections: b) Pre-configured data models, c) Fields and event category tags**
</details>

<details>
<summary><b>Which of the following is true about the Splunk Common Information Model (CIM)?</b></summary>

- a) The CIM contains 28 pre-configured datasets.
- b) The data models included in the CIM are configured with data model acceleration turned on.
- c) The data models included in the CIM are configured with data model acceleration turned off.
- d) The CIM is an app that needs to run on the indexer.

**✅ ANSWER: c) The data models included in the CIM are configured with data model acceleration turned off.**
</details>

<details>
<summary><b>Which of the following is one of the pre-configured data models included in the Splunk Common Information Model (CIM) add-on?</b></summary>

- a) Access
- b) Accounting
- c) Authorization
- d) Authentication

**✅ ANSWER: d) Authentication**
</details>

<details>
<summary><b>The CIM Add-on indexes extra data and will affect license usage?</b></summary>

- a) TRUE
- b) FALSE

**✅ ANSWER: b) FALSE**
</details>

## Security and Role-Based Access Control

<details>
<summary><b>Which of the following describes the principle of least privilege in Splunk?</b></summary>

- a) Users should have the minimum permissions needed to do their jobs
- b) Users should have access to all data but only use what they need
- c) Only admins should have access to Splunk
- d) Least privilege requires implementing third-party authentication

**✅ ANSWER: a) Users should have the minimum permissions needed to do their jobs**
</details>

<details>
<summary><b>What level of permission is needed to accelerate a data model?</b></summary>

- a) User
- b) Power user
- c) Admin or accelerate_datamodel capability
- d) Knowledge Manager

**✅ ANSWER: c) Admin or accelerate_datamodel capability**
</details>

<details>
<summary><b>Which of the following is true about role inheritance in Splunk?</b></summary>

- a) Roles cannot inherit from other roles
- b) A role can inherit from multiple roles
- c) Only admin roles can inherit from other roles
- d) Role inheritance is only available in Splunk Enterprise Security

**✅ ANSWER: b) A role can inherit from multiple roles**
</details>

## Deployment Architecture

<details>
<summary><b>Which component is responsible for parsing and indexing data in a distributed Splunk environment?</b></summary>

- a) Search Head
- b) Indexer
- c) Heavy Forwarder
- d) Deployment Server

**✅ ANSWER: b) Indexer**
</details>
<details>
<summary><b>What is the primary function of a Universal Forwarder?</b></summary>

- a) Indexing data
- b) Executing searches
- c) Collecting and forwarding data with minimal resource usage
- d) Creating dashboards

**✅ ANSWER: c) Collecting and forwarding data with minimal resource usage**
</details>

<details>
<summary><b>In a Search Head Cluster, which component maintains the captain state?</b></summary>

- a) KV Store
- b) Artifact replication
- c) Configuration replication
- d) Job scheduling

**✅ ANSWER: a) KV Store**
</details>

<details>
<summary><b>What is the purpose of a Deployment Server in Splunk?</b></summary>

- a) To distribute configurations to forwarders and other Splunk components
- b) To analyze search performance
- c) To handle search requests
- d) To store indexed data

**✅ ANSWER: a) To distribute configurations to forwarders and other Splunk components**
</details>

## Dashboard Creation and Customization

<details>
<summary><b>Which of the following is required to edit a dashboard in Dashboard Studio?</b></summary>

- a) HTML knowledge
- b) XML knowledge
- c) JavaScript knowledge
- d) No coding knowledge is required

**✅ ANSWER: d) No coding knowledge is required**
</details>

<details>
<summary><b>When creating a dashboard, which panel type would be most appropriate for displaying geographic data?</b></summary>

- a) Single Value
- b) Line Chart
- c) Choropleth Map
- d) Table

**✅ ANSWER: c) Choropleth Map**
</details>

<details>
<summary><b>Which of the following options allows you to add interactivity to a dashboard?</b></summary>

- a) Time Range Picker
- b) Token Usage
- c) Drilldowns
- d) All of the above

**✅ ANSWER: d) All of the above**
</details>

## Performance Optimization

<details>
<summary><b>Which of the following search practices would likely improve performance the most?</b></summary>

- a) Using "*" wildcards at the beginning of search terms
- b) Adding more OR statements to broaden the search
- c) Specifying a narrow time range and using index/sourcetype filters
- d) Using subsearches instead of joins

**✅ ANSWER: c) Specifying a narrow time range and using index/sourcetype filters**
</details>

<details>
<summary><b>What is the purpose of summary indexing in Splunk?</b></summary>

- a) To copy data from one index to another
- b) To create pre-computed summaries of data for faster reporting
- c) To validate data integrity
- d) To duplicate data for backup purposes

**✅ ANSWER: b) To create pre-computed summaries of data for faster reporting**
</details>

<details>
<summary><b>Which of the following commands is more resource-intensive and should be used sparingly?</b></summary>

- a) search
- b) where
- c) stats
- d) join

**✅ ANSWER: d) join**
</details>

## Troubleshooting

<details>
<summary><b>If a search is running slowly, which of the following should you check first in the Job Inspector?</b></summary>

- a) The number of mappers
- b) The search syntax for errors
- c) The execution costs section
- d) The data model acceleration status

**✅ ANSWER: c) The execution costs section**
</details>

<details>
<summary><b>When data is not appearing in search results, which of the following is NOT a likely cause?</b></summary>

- a) Data is outside the time range being searched
- b) Index permissions restrict access to the data
- c) The search is case-sensitive by default
- d) Data may not be indexed yet

**✅ ANSWER: c) The search is case-sensitive by default**
</details>

<details>
<summary><b>What tool would you use to diagnose issues with a forwarder not sending data?</b></summary>

- a) Job Inspector
- b) Monitoring Console
- c) Search Job Performance
- d) Splunk Web

**✅ ANSWER: b) Monitoring Console**
</details>

## Advanced Searching

<details>
<summary><b>Which search command can be used to identify patterns in your data over time?</b></summary>

- a) anomalousvalue
- b) cluster
- c) rare
- d) highlight

**✅ ANSWER: a) anomalousvalue**
</details>

<details>
<summary><b>What does the | sistats command do differently from the | stats command?</b></summary>

- a) Performs statistical operations across multiple indexes
- b) Calculates simple moving averages
- c) Uses a different computation algorithm
- d) Maintains the original order of events while calculating statistics

**✅ ANSWER: d) Maintains the original order of events while calculating statistics**
</details>

<details>
<summary><b>When using the predict command, which of the following algorithms is NOT available?</b></summary>

- a) LLP (Local Linear Prediction)
- b) LL (Linear Regression)
- c) K-means
- d) HW (Holt-Winters)

**✅ ANSWER: c) K-means**
</details>

<details>
<summary><b>Which command would you use to extract fields at search time for a one-time search?</b></summary>

- a) rex
- b) extract
- c) erex
- d) kvform

**✅ ANSWER: a) rex**
</details>

## Data Onboarding and Management

<details>
<summary><b>Which of the following is NOT a valid method for getting data into Splunk?</b></summary>

- a) Using a Universal Forwarder
- b) Monitoring HTTP Event Collector (HEC)
- c) Direct file upload through Splunk Web
- d) Using the stats command

**✅ ANSWER: d) Using the stats command**
</details>

<details>
<summary><b>What is the purpose of setting a sourcetype when ingesting data?</b></summary>

- a) To specify which index the data should go to
- b) To identify the source of the data
- c) To help Splunk parse the data correctly
- d) To set access permissions on the data

**✅ ANSWER: c) To help Splunk parse the data correctly**
</details>

<details>
<summary><b>Which configurations can be set in props.conf? (Choose all that apply)</b></summary>

- a) Field extractions
- b) Timestamp configurations
- c) Line breaking
- d) Index time field transformations

**✅ ANSWER: Multiple selections: a) Field extractions, b) Timestamp configurations, c) Line breaking, d) Index time field transformations**
</details>

## Miscellaneous

<details>
<summary><b>By default, which of the following fields would be listed in the fields sidebar under interesting Fields?</b></summary>

- a) host
- b) index
- c) source
- d) sourcetype

**✅ ANSWER: b) index**
</details>

<details>
<summary><b>What is a Splunk Job? (Select all that apply)</b></summary>

- a) A user-defined Splunk capability.
- b) Searches that are subjected to some usage quota.
- c) A search process kicked off via a report or an alert.
- d) A child OS process manifested from the splunkd process.

**✅ ANSWER: Multiple selections: c) A search process kicked off via a report or an alert, d) A child OS process manifested from the splunkd process.**
</details>

<details>
<summary><b>Which of the following are correct about search job inspector? (Choose all that apply)</b></summary>

- a) Allows you to examine overall stats of search.
- b) Use to troubleshoot search's performance and understand impact of knowledge objects on processing.
- c) Contains three components.
- d) Any existing (i.e., not expired) search job can be inspected.

**✅ ANSWER: Multiple selections: a) Allows you to examine overall stats of search, b) Use to troubleshoot search's performance and understand impact of knowledge objects on processing, c) Contains three components, d) Any existing (i.e., not expired) search job can be inspected.**
</details>

<details>
<summary><b>The Field Extractor (FX) is used to extract a custom field. A report can be created using this custom field. The created report can then be shared with other people in the organization. If another person in the organization runs the shared report and no results are returned, why might this be? (Choose all that apply)</b></summary>

- a) Fast mode is enabled.
- b) The dashboard is private.
- c) The extraction is private.
- d) The person in the organization running the report does not have access to the index.

**✅ ANSWER: Multiple selections: c) The extraction is private, d) The person in the organization running the report does not have access to the index.**

**Note:** There was a note in the original document stating that option b is incorrect.
</details>

## Quick Reference: Key Splunk Commands

<details>
<summary><b>Search Commands</b></summary>

| Command | Description | Usage |
|---------|-------------|-------|
| `search` | Filter results | `search error` |
| `where` | Filter results using eval expressions | `where status>=500` |
| `rex` | Extract fields using regex | `rex field=_raw "from=(?<source_ip>\d+\.\d+\.\d+\.\d+)"` |
| `fields` | Include or exclude fields | `fields host, source, status` |
| `table` | Create a tabular display | `table host, status, count` |
| `rename` | Rename fields | `rename JSESSIONID as session_id` |
| `sort` | Sort results | `sort -count` |
| `dedup` | Remove duplicates | `dedup user_id` |
| `head` | Return first N results | `head 10` |
| `tail` | Return last N results | `tail 5` |
</details>

<details>
<summary><b>Aggregation Commands</b></summary>

| Command | Description | Usage |
|---------|-------------|-------|
| `stats` | Calculate statistics | `stats count by host` |
| `chart` | Create a chart | `chart count over host by status` |
| `timechart` | Create a time-based chart | `timechart span=1h count by status` |
| `top` | Find most common values | `top limit=10 user` |
| `rare` | Find least common values | `rare limit=10 user` |
| `contingency` | Create a contingency table | `contingency host status` |
</details>

<details>
<summary><b>Data Manipulation Commands</b></summary>

| Command | Description | Usage |
|---------|-------------|-------|
| `eval` | Calculate and manipulate fields | `eval is_error=if(status>=400, "yes", "no")` |
| `fillnull` | Replace null values | `fillnull value="-"` |
| `lookup` | Enrich data with lookup tables | `lookup userinfo user_id OUTPUT full_name, dept` |
| `join` | Join results of subsearches | `join type=inner user_id [search index=user_logs]` |
| `appendcols` | Append columns from subsearch | `appendcols [search index=app_status]` |
| `makemv` | Convert field to multivalue | `makemv delim="," tags` |
| `mvexpand` | Expand multivalue field | `mvexpand tags` |
</details>

<details>
<summary><b>Memory Guide: Important Knowledge Objects</b></summary>

1. **Field Extractions**
   - Created with Field Extractor (FX)
   - Persist as knowledge objects
   - Can use regex or delimiters

2. **Field Aliases**
   - Normalize field names across sourcetypes
   - Applied after field extractions but before lookups
   - Need separate alias for each sourcetype

3. **Calculated Fields**
   - Shortcut for complex eval expressions
   - Based on extracted fields
   - Can be used in search bar

4. **Macros**
   - Reusable search strings
   - Can accept arguments if named with (N) suffix
   - Requires name and definition

5. **Event Types**
   - Categorize events based on a search
   - Can be tagged
   - Used when search strings need to be reused

6. **Tags**
   - Based on field/value pairs
   - Make data more understandable
   - Searched with tag=<tagname> syntax

7. **Data Models**
   - Provide datasets for pivots
   - Consist of events, searches, and transactions
   - Need admin permissions to accelerate
</details>

<details>
<summary><b>Command Pipeline Processing Order</b></summary>

1. **Data retrieval commands** (first in pipeline)
   - `search`, `inputlookup`, `dbxquery`, etc.

2. **Streaming commands** (process events one at a time)
   - `eval`, `where`, `rex`, `fields`, etc.

3. **Transforming commands** (change structure of results)
   - `stats`, `chart`, `timechart`, `transaction`, etc.

4. **Generating commands** (create new events)
   - `loadjob`, `datamodel`, etc.

5. **Formatting commands** (affect display)
   - `table`, `rename`, etc.
</details>

<details>
<summary><b>Search Best Practices for Performance</b></summary>

1. **Specify narrow time ranges**
   - The most important optimization factor

2. **Use indexes and sourcetypes**
   - Filter early in search pipeline

3. **Avoid wildcards at the beginning of terms**
   - `*error` is much slower than `error*`

4. **Use fields instead of keywords**
   - `status=500` is faster than `"500"`

5. **Use stats instead of transaction when possible**
   - Transaction has 1000 event limitation

6. **Use efficient commands**
   - Avoid `join`, use `lookup` when possible

7. **Limit results early**
   - Use `head` when you only need top results
</details>
