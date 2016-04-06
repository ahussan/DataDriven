# DataDriven

## What is Data Driven Testing?
Data-driven testing is creation of test scripts where test data and/or output values are read from data files instead of using the same hard-coded values each time the test runs. This way, testers can test how the application handles various inputs effectively.
Data-Driven testing generally means executing a set of steps with multiple sets of data.

## Data Provider
Selenium does not provide any out-of-the box solution for data driven testing but leaves it up to the user to implement this on his own. But with the help of **TestNG**, we can build a **Data Driven Testing Framework**. To implement, we need to use **@DataProvider** annotation along with **@Test** annotation. @Data Provider basically get the data or process the data and provide two dimensional array to the @Test method.

In other words, DataProvider is data feeder method defined in class that supplies data to a test method. We can hook up any test method with a DataProvider and make the test method execute once for every row of your test data.

In this project, I will show how to read data from an external **.xlsx** file and provide data to our test method. I have used **POI** in Java to read the data from an external .xlsx file. 

## What is POI?
Excel is the very popular file format created by Microsoft. Although it is not an opened file format, Java applications can still read and write Excel files using the **Apache POI** - the Java API for Microsoft Documents, because the development team uses reverse-engineering to understand the Excel file format. Hence the name POI stands for *Poor Obfuscation Implementation*.

To start with POI, we need to ad Dependency in our Maven project. 

For **Excel 2007** format, Add following dependency:

```
<dependency>
    <groupId>org.apache.poi</groupId>
    <artifactId>poi-ooxml</artifactId>
    <version>VERSION</version>
</dependency>
```
As of 04/2016, latest version of poi-ooxml is 3.14

## The Apache API Basics
There are two main prefixes which we will encounter when working with Apache POI:
HSSF: denotes the API is for working with Excel 2003 and earlier.
XSSF: denotes the API is for working with Excel 2007 and later.
In this project, I will use poi-ooxml that handles Excel 2007 and later.

To Jump in Apache POI API, we need to understand and use the following 4 interfaces:
- Workbook: high level representation of an Excel workbook. Concrete implementations are: HSSFWorkbook and XSSFWorkbook.
- Sheet: high level representation of an Excel worksheet. Typical implementing classes are HSSFSheet and XSSFSheet.
- Row: high level representation of a row in a spreadsheet. HSSFRow and XSSFRow are two concrete classes.
- Cell: high level representation of a cell in a row. HSSFCell and XSSFCell are the typical implementing classes.

## Reading an excel file
Reading an excel file is  very simple if we divide this in steps.
- Create workbook instance from excel sheet
- Get to the desired sheet
- Increment row number
- Iterate over all cells in a row
- Repeat step 3 and 4 until all data is read

Once we read the data and our data provider method provides two dimensional array to our @Test method, our Data Driven Testing Framework is ready to use!

Any Question? Shout out loud!
