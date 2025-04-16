---

copyright:
  years: 2024, 2025
lastupdated: "2025-04-01"

subcollection: Db2onCloud

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Using the Db2 database assistant
{: #database-assistant}

Chat with the IBM Db2 database assistant to help you complete tasks, find out about your system status and statistics, or ask general questions about Db2.
{: shortdesc}

Open the database assistant from the Db2 web console, and then ask it to help you with a range of Db2 tasks, including:
- Answering your questions about Db2
- Detecting and helping to resolve lock contention issues
- Monitoring your Db2 instance, including getting information about:
    - Active connections
    - SQL activity
    - Resource usage
    - Schemas, table spaces, indexes, and tables in the system
    - Users
    - Backups
    - Compute scaling
    - Storage scaling

The database assistant uses built-in skills and is trained on the official IBM Db2 documentation so that it can provide you with the most accurate responses.

## Starting the database assistant
{: #assistant-getstarted}

To get started with the database assistant:

1. Open your Db2 web console.

1. Click the database assistant chat icon.

   ![database assistant icon](images/assistant-icon.png "database assistant icon"){: iih}

1. Type your questions and requests in the chat.

## What can the database assistant do?
{: #assistant-skills}

You can ask the database assistant to complete the actions listed in the following table.

Depending on the database workload, the database assistant might take some time to respond to certain prompts, such as requesting a database summary or getting details about the largest tables by storage size.
{: note}

| Category | Action | Description | Example prompt phrases |
| --- | --- | --- | --- |
| **Product information** | Answer your questions about Db2 | Ask the assistant anything about Db2 and it will generate an answer based on its knowledge of the product. The assistant is trained on the official IBM Db2 documentation | - What's new in Db2?</br> - Tell me about the MON_GET_PKG_CACHE_STMT table function</br> - How do I troubleshoot Db2?</br> - What is error code SQL0911N?</br> - How can I manage my database workload? |
| **Instance information** | Show backups | Get information about available backups in the system | - Get the list of backups</br> - What backups are available?</br> - Show me my backups |
|  | Show database summary | Get a summary of basic database details such as name, version, size, number of tables, number of schemas, uptime, and more | - Report on my database</br> - Check my database details</br> - Tell me about this instance |
|  | Show database version | Get the version of Db2 | - What Db2 version am I running?</br> - What is the database version?</br> - Current Db2 database version</br> - Show me the database version |
|  | Show scaling resources | Get information about how system resources are configured for scaling | 	- Show me the system scaling settings</br> - What is the scaling configuration?</br> - Display compute scaling settings |
|  | Show system settings | Get a summary of the host names and endpoints configured in your system | - Show my system settings</br> - Display database endpoint settings</br> - Describe db connection details |
|  | Show users | Get a list of all users from the console | - Display users in the console.</br> - Get me a list of users</br> - Who is using the console? |
| **Workload information** | Show active connections | Get a list of all current connections to the system | - Show me all connections</br> - Display inflight connections</br> - List the current applications |
|  | Show running queries | Get a list of all currently running SQL queries and in-flight executions in the system | - Show me current SQL queries</br> - Get all current queries</br> - Show me in-progress SQL |
| **Storage information** | Show table spaces | Get a list of table spaces in the system and their storage utilization | - Obtain the table spaces list</br> - List all tablespace names</br> - Show table spaces |
|  | Show total storage | Get storage details about the system | - Display my storage utilization statistics</br> - How much disk storage capacity have I used?</br> - Report on my storage consumption |
| **Resource utilization** | Show CPU usage summary | Get a summary of how much CPU the system is using | - Show me CPU usage for the past 3 days</br> - What was the system CPU load between August 14 and 15 2024?</br> - Analyze processor utilization from the last 24 hours |
|  | Show IO usage summary | Get a summary of disk usage over a specified period | - Analyze IO usage from the last 48 hours</br> - Display IO utilization for the last 7 days</br> - Show me I/O usage  |
|  | Show memory usage summary | Get a summary of how much memory was used by the system over a specified period | - Analyze memory usage for the last 15 days</br> - Get a summary of memory details</br> - Show me memory usage from 6 September 2024 |
| **Database objects** | Show indexes for a specified schema | Get a list of indexes for a given schema | - Get index details</br> - Show indexes for the schema schema-name-1</br> - Fetch indexes |
|  | Show largest tables by rows | Get a ranked list of the largest tables in the system based on row count | - Get the largest 10 tables</br> - Display the 3 largest tables by row count</br> - What is my largest table? |
|  | Show largest tables by rows for a specified schema | Get a ranked list of the largest tables in a given schema | - What are the top 3 tables for the schema "schema-name"?</br> - Get the largest tables by row count from the schemas "schema-name-1" and "schema-name-2"</br> - Show me the 3 biggest tables by rows from schema-name-1, schema-name-2 schemas |
|  | Show largest tables by storage | Get a ranked list of the largest tables in the system based on storage size | - Rank the top 10 tables by storage size</br> - Identify my largest tables by storage</br> - Which table uses the largest amount of storage? |
|  | Show largest tables by storage for a specified schema | Get a ranked list of the largest tables in a given schema based on storage size | - Get the top 4 tables by storage for the schema schema-name-1</br> - What is the largest table by storage size in the schema schema-name-1?</br> - Show the top 10 largest tables by storage from the schema-name-1 schema |
|  | Show schemas | Get a list of schemas in the system | - Display all schemas</br> - Provide a list of schemas</br> - Fetch me a list of schemas in the database |
|  | Show tables | Get a list of tables in the system | - View the tables in the schema "schema-name-1"</br> - Get a tables list from the schema-name-1, schema-name-2, and schema-name-3 schemas</br> - List my tables |
|  | Show views | Get a list of views in the system | - List my views</br> - Display the views for the schema-name-1 schema</br> - Collect all views |
| **Troubleshooting** | Show most active connections | Get details about the most active connections | - What are the top 5 active connections</br> - Display the top 8 connections in the database</br> - Get the most active connections |
|  | Show how time is spent | Get details about how much time was spent by the system on various tasks | - List wait times and bottlenecks</br> - How is time being spent in my database?</br> - Get time spent details |
|  | Show lock waits | Get a list of blocking and waiting connections in the system | - Troubleshoot lock waits and deadlocks</br> - Report all lock waits</br> - Show me lock waits from the last two hours |
|  | Show longest running queries | Get information about the top queries in the system ranked by how long they have been running | - Display the longest running SQL queries</br> - What are the top 5 queries?</br> - Show long running SQL statements |

{: caption="Db2 database assistant skills" caption-side="top"}

## Troubleshooting the Db2 database assistant
{: #assistant-troubleshooting}

If you find that you are not getting the answers and results that you expect from the Db2 database assistant, try one or more of the following troubleshooting strategies:
- Rephrase the question. The assistant might not understand your phrasing. Try using different wording, if possible.
- Restart the conversation. The assistant might be getting confused by other things you have discussed with it.
- Ensure that you are asking about Db2. If you are asking about something else, it might be outside of the assistant's capabilities.
- Try asking about something specific. If your question is too broad, the assistant is more likely to return results that aren't relevant to your request.
- Ensure that you are not filtering by version. If an answer to your question isn't available in the current documentation release, the assistant won't find it. If you're filtering by version, some content might be missing. To broaden the search, type "change version" and then choose "Any".

## Data privacy and opting out
{: #assistant-data-privacy}

When you interact with the Db2 database assistant, your questions and requests are processed by IBM watsonx Orchestrate, which is outside of your Db2 instance. Only the text that you input into the assistant gets processed by watsonx Orchestrate. None of your actual data or metrics leave your Db2 instance at any time.

To opt out of the Db2 database assistant, contact IBM Support.
