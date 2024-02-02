---
title: Data
tags:
- cmsc320
- wip
---

**Data:** Data is raw information, facts, or statistics that can be in various forms such as numbers, text, images, or more.

data types -> quantitative -> discrete or continous
     	   -> Qualitative -> Structued data, unstrucctured data

Types of Data

| Types of Data | Defintion |
| -- | -- |
| Tabular Data | (things that are in tables): Structured data organized into rows and columns, often resembling a spreadsheet or database table. |
| Text | Human Readable text |
| Graph | Represents relationships between entities using nodes (verticies) and edges. |
| Unstructured Data |  lacks of predefined structure or format, challening to analyze and process |

## Data Formats
* CSV / TSV
* Images
  * .jpg
  * .png
* Audio
  * .wav
  * .mpg
* SQL Databasae
  * mySQL
  * Postgres
  * etc..
* No SQL Database
  * Bigtable
  * Accumulo
* JSON
* XML/HTML

# Data Format: Images

**Pixel Structure:** Images are organized as grids of pixels (tiny building block).  
**Pixel Data:** Each pixel holds color information  
**Color Channels:** In color images, pixels have red, green, and blue (RGB) channels  
      * Channel -> is like a sperated layer of information about color  
**Channel Values:** each channel ranges from 0 (no intensity) to 255 (maximum intensity)  
**Intensity Values:** Vales between 0 and 255 create varying shades of color

Images can be compress to save storage space
* Lossy Compression
  * Sacrificces some data to reduce file size
    * Suitable for photos where minor quality loss is acceptable (e.g., JPEG).
* Lossless Compression
  * Reduces file size without any loss of quality
    * Ideal for preserving images quality in medical imaging, digital arts, or graphics (e.g., PNG, GIF).

> Varying underyling resolutions (level of detail and clarity).

# Databases

**Defintion:** Organized collection of structured information/data, typically stored electronically in a computer system.
* Hanle more commpelx data relationships, often organzied in tables.
* Effeciently manages and allows retrieval. updating, and manipulation of info for various apps.

# JSON

Java Script Object Notion

* A lightweight data interchange format
* A text format for storing and transporting data (ex: Web API's)
* "Self-describing" and easily to understand
  * Easy for humans and machines to read and write.
  * For Representing data in web APIs, mobile app development, configuration files, and client-serve communication

Represents data as key-value paris; organized in a hierarchical structure using objects and arrays
* Objects (collections of key-value pairs)
* Arrays (ordered lists of values)

Json accommodates various data types, such as strings, numbers, arrays, objects, booleans, and nul, allowing for nested structures

#### Json in Python

In Python, the json module is commonly used to wrok with JSON data
* Use json.dumps() to convert pythong objects to json format
* Use json.loads9) to convert JSON data back to Python Objects

## XML/HTML

| Type | Name |
| -- | -- |
| HTML | Hypertext Markup Language |
| XML | extensible Markup Language |

Both are markup languages( define the text document with tag which defines the structure of web pages).
Used for structuring and organizing content on the web and other digital documents, but they serve different purposes.

#### HTML

HTML is primarily usesd for creating web pages and presetnign content on the internet.
HTML has a fixed set of predefined tags for structure content, emphasizing elements like headings, paragraphs,links, etc.


#### XML

XML is designed to transport and store data, with a focus on describing the structure of the data and is not concerned with presenetation

* XML allows users to defined custom tags ,allowing flexibility to create custom structures

