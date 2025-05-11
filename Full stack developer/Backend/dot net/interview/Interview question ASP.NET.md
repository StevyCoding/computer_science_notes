## ASP.Net Interview Questions for Freshers

### ****1. What is ASP.NET?****

[ASP.NET](https://www.geeksforgeeks.org/introduction-to-asp-net/) (Active Server Pages . NET) is a progressive new programming framework that empowers the rapid improvement of powerful web applications and administrations. It is a part of the Microsoft .NET Platform, it gives the simplest and most versatile approach to creating, deploying and running web applications that can focus on any browser or device.ASP.NET is built on the CLR(Common Language Runtime) which allows the programmers to execute its code using any .NET language(C#, VB, etc.). It is specially designed to work with HTTP and for web developers to create dynamic web pages, web applications, websites, and web services as it provides a good integration of HTML, CSS, and JavaScript.

.NET Framework is used to create a variety of applications and services like Console, Web, and Windows, etc. But ASP.NET is only used to create web applications and web services. That’s why we termed ASP.NET as a subset of the .NET Framework.

### ****2. Write down the features of ASP.NET?****

There are a lot of reasons which make ASP.NET popular among developers. Some reasons are listed below:

- ****Extending .NET Framework:**** ASP.NET is a subset of the .NET Framework as it extends the .NET Framework with some libraries and tools to develop web apps. The thing that it adds to the .NET Framework is __Libraries for common web patterns like MVC__, __Editor Extensions__, __the base framework to process the web requests__, and __web-page templating syntax like Razor__, etc.
- ****Performance:**** It is faster than the other web frameworks available in the market.
- ****Backend Code:**** With the help of ASP.NET you can write the backend code for data access and any logic in C#.
- ****Dynamic Pages:**** In ASP.NET, Razor provides the syntax for developing dynamic web pages with the help of C# and HTML. ASP.NET can be integrated with JavaScript and it also includes the frameworks like React and Angular for the SPA(Single Page Application.)
- ****Supporting different OS:**** You can develop and execute ASP.NET apps on Windows, Linux, Docker, and macOS. The Visual Studio provides the tools to build .NET apps with different OS.

### ****3. What is Common Language Runtime (CLR)?****

CLR is the basic and Virtual Machine component of the .NET Framework. It is the run-time environment in the .NET Framework that runs the codes and helps in making the development process easier by providing various services such as remoting, thread management, type-safety, memory management, robustness, etc. Basically, it is responsible for managing the execution of .NET programs regardless of any .NET programming language. It also helps in the management of code, as code that targets the runtime is known as the Managed Code, and code that doesn’t target to runtime is known as Unmanaged code. 

> _****To read more, you can refer:****_ [__Common Language Runtime__](https://www.geeksforgeeks.org/common-language-runtime-clr-in-c-sharp/)

### ****4. What is ASP.NET MVC framework?****

ASP.MVC is a web application framework that is lightweight and has high testable features. ASP.NET supports 3 different types of components namely Model, View, and Controller.

- ****Model Layer:**** The Model component corresponds to all or any of the data-related logic that the user works with. This will represent either the info that’s being transferred between the View and Controller components or the other business logic-related data. For instance, a Customer object will retrieve the customer information from the database, manipulate it, and update its data back to the database or use it to render data.
- ****View Layer:**** The View component is employed for all the UI logic of the appliance. For instance, the Customer view will include all the UI components like text boxes, dropdowns, etc. that the ultimate user interacts with.
- ****Controller:**** Controllers act as an interface between Model and consider components to process all the business logic and incoming requests, manipulate data using the Model component, and interact with the Views to render the ultimate output. For instance, the Customer controller will handle all the interactions and inputs from the Customer View and update the database using the Customer Model. An equivalent controller is going to be wont to view the Customer data.

### ****5. Which would be the right framework to be used ASP.NET MVC or ASP.NET Web API?****

- ASP.Net MVC is used to make web applications that return the view and data but  Asp.Net Web API is used to make all  HTTP services in a simple and basic way that returns only information, not view.
- Web API helps to build REST-ful services over the .NET Framework, and it additionally supports content negotiation, self-facilitating which are not in MVC.
- Web API additionally deals with returning information specifically design like JSON, XML, or some other dependent on the Accept header in the solicitation, and you don’t stress over that. MVC just returns information in JSON design utilizing Json Result.

### ****6. What is Server control?****

ASP.NET has Server Controls features, Which provide facilities to manipulated values of the controls on the Server-Side. This is especially helpful while we want to create validating and dynamically web forms.

### ****7. What is the web.config file?****

A configuration file (web.config) is utilized to oversee different settings that characterize a website. The settings are store in XML files that are independent of your application code. In this manner, you can configure settings freely from your code. This file stored inside the application root directory.

![](https://media.geeksforgeeks.org/wp-content/uploads/20210611105455/web-285x300.jpg)

### ****8. Which compiler is used in ASP.NET?****

To complied an ASP.NET program  .NET framework used the Roslyn compiler.

### ****9. ASP.NET is open-source. Explain?****

ASP.NET is an open-source web framework for building web applications on the .NET (dotNET) framework. It is made by Microsoft and variant 1.0 was delivered in 2002 to allow users to develop dynamic web applications, services, and sites. The framework is designed to work with the standard HTTP convention, which is the standard protocol utilized across all web-based applications.  ASP.NET is the replacement to the ASP (Active Server Pages) innovation and was a significant update as far as adaptability and power. It is an expansion of the .NET framework with extra tools and libraries for building things on the web, including web applications and websites.  The ASP.NET cross-plate form version is known as ASP.NET Core, which was delivered in 2016. ASP.NET is still updated and supported.

### ****10. Explain the Global.asax file?****

Global.asax is an optional file that resides in the application root directory. This file is used to handle higher-level application events, for example, Application_Start, Application_End, Session_Start, Session_End, and so on. It is additionally known as the ASP.NET Application File..Global.asax contains a Class representing your application as a whole. At run time, this file is parsed and compiled into a dynamically created .NET Framework class derived from the HTTP Application base class. We can convey this file as an assembly in the \bin catalog of an ASP.NET application. The Global.asax record itself is designed so that if a user demands the document, the request is denied. External users can’t download or see the code written inside it.

![Global.asax file](https://media.geeksforgeeks.org/wp-content/uploads/20210611105537/global-299x300.jpg)

### ****11. How many types of Server controls are supported by ASP.NET?****

There are mainly four different types of  Server-side controls in ASP.NET :

- HTML server controls
- Web Server controls
- User controls
- Validation controls

### ****12. What does “PostBack” mean in ASP.NET?****

A PostBack is the process of presenting an ASP.NET page to the server for processing. PostBack is done if certain credentials of the page are to be checked against certain sources, (for example, confirmation of username and secret key/password using a database). This is something that a client machine can not able to achieve and subsequently, these details must be ‘posted back’ on the server. So we can say that a postback event occurs on the client-side but is handled by the code in a copy of the page running on the server.

### ****13. Explain the difference between Web.config and Machine.config file?****

There is some key difference between Web.config and Machine.config file below:

- The machine.config record is the master configuration document on your framework with a lot of default settings.And Web.config is the file for the local settings to be applied for a website which store configuration information in XML format.
- The settings of Machine.config file are applied to the entire asp.net applications on your server while the settings made in the Web.config file are applied to that specific web application only.
- Each .NET Framework form has only one machine.config file, simultaneously, each web application has its own web.config file. Directories inside a web application can have web.config files as well.
- The machine.config is shared values among numerous applications on the server, while Web.config documents contain application explicit things, for example, database connection strings.
- Suppose if you want any improvements in the web.config, then the web application will promptly load the changes but in the machine.config case you should restart the application.
- The machine.config document will automatically introduce when you install Visual Studio.Net and it resides in the c:\windows\microsoft.net\framework\version\config folder whereas web.config will automatically be made when you make an ASP.Net web application project.
- Machine.config is the design configuration file for all the applications in the IIS, but Web. config is a configuration file for a specific application.

### ****14. Explain the differences between GridView and DataGrid?****

|****Grid View****|****DataGrid****|
|---|---|
|It was introduced with Asp.Net 2.0.|It was introduced with Asp.Net 1.0.|
|Built-in supports for Paging and Sorting.|For sorting you need to handle SortCommand event and rebind grid required and for paging, you need to handle the PageIndexChanged event and rebind grid required.,|
|Built-in supports for Update and Delete operations.|Need to write code for implementing Update and Delete operations.|
|Supports auto-format or style features.|This feature is not supported.|
|Performance is slow as compared to DataGrid|Performance is fast as compared to GridView.|

### ****15. What is the difference between custom controls and user controls?****

|****User Control****|****Custom Control****|
|---|---|
|User controls are created just like a web form. They make use of the existing controls to define their own logic.|A custom control is one that is made or created by the programmer to serve the business needs, by extending the functionality of existing controls.|
|We can User control easily.|The creation of custom control is not easy as compare to user control|
|These control do not run on their own dll.|While these control can run on their own dl.|
|We can not add to the toolbox.|While we can add to the toolbox.we|
|This control is not flexible.|This control is more flexible.|
|Once we created a single copy of this control, we can use this copy to different projects as well.|We can not call or use a single copy of this control in different applications. For this, we need to create a control for each and every application.|

### ****16. What are web controls in ASP.NET?****

Web server controls are powerful than HTML server-side controls. The only difference is that they must have the ****runat = ”server”**** attribute set. This attribute makes the control available for server-side programming. Each ASP.NET Server Control is capable of exposing an object model containing properties, methods, and events. This object model can be utilized by the ASP.NET developers to modify and interact with the Web page. Web controls contain all basic controls of HTML controls as well as some new controls like as DataGrid, DataList, and Calendar.

|****WEB CONTROL****|****DESCRIPTION****|
|---|---|
|Label|Represents a label control|
|ListBox|Represents a list box control|
|CheckBox|Represents a Check box control|
|Calendar|Represents a calendar control|
|ImageButton|Represents an image button control|
|TableCell|Represents a table cell|
|Panel|Represents a panel control|
|DataList|Represents a data list control|
|TextBox|Represents a text box control|
|Image|Represents an image control|
|CheckBoxList|Represents a list box with checkboxes|
|Button|Represents a button control|
|HyperLink|Represents a hyperlink control|
|TableRow|Represents a row of a table|
|RadioButtonList|Represents a list box with radio button controls|
|DataGrid|Represents a data grid control|
|DropDownList|Represents a drop-down list control|
|AdRotator|Represents an ad rotator control|
|RadioButton|Represents a radio button control|
|LinkButton|Represents a link button control|
|Table|Represents a table control|
|Repeater|Represents a repeater control|

### ****17. Describe login Controls in ASP?**** 

The ASP.NET supports robust login controls for web-based application which does not require any program coding. These login controls coordinate with ASP.NET participation and form authentication to help automated client verification for a server webpage. By default, the ASP.NET login controls work in plain text over HTTP. The ASP.NET supports different types of Login Controls like:

- Login Control
- LoginView Control
- LoginStatus Control
- LoginName Control
- PasswordRecovery Control
- CreateUserWizard Control
- ChangePassword Control

![](https://media.geeksforgeeks.org/wp-content/uploads/20210611110337/login-245x300.jpg)![](https://media.geeksforgeeks.org/wp-content/uploads/20210615165519/createwizard.jpg)

### ****18. What are the different validation controls in ASP.NET?****

Validation controls in ASP.NET are one of the significant requirements for Web application creation. These controls give the facility to validate user input. By using these controls we can check as a required field, range, custom rules, conditions, etc. An asp.net has 5 different types of validation controls:

- ****RequiredFieldValidator****: If we want the user must fill certain compulsory fields then this validation control is used.
- ****CompareValidator****: This validation compares user input with a value using a comparison operator such as less than, greater than, and so on.
- ****RangeValidator****: This validation checks user’s input values lie within a certain range.
- ****RegularExpressionValidator****: It checks the user’s input string matches a defined pattern.
- ****CustomValidator****: This validation is used to check user-defined validation conditions.

### ****19. Why do we use CheckBox in .NET?****

This control creates a check box on a Web Forms page, allowing users to set a true or false value for the item associated with the control. The properties of the CheckBox are:

- ****Checked:**** This is true if the checkbox is checked, otherwise false. The default value is false.
- ****TextAlign:**** TextAlign is the position of the caption. The possible values are Right and Left. The default is Right to align.
- ****Text:**** This defines the checkbox caption.

<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm2.aspx.cs"  
 Inherits="WebApplication10.WebForm2" %>  

  
<!DOCTYPE html>  
  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head runat="server">  
    <title></title>  
    <style type="text/css">  
        #form1 {}  
    </style>  
</head>  
<body>  
    <form id="form1" runat="server">  
        <div>  
            <br />  
            Eligibility criteria for take admission in Master of Technology  
            <br />  
        </div>  
        <asp:CheckBox ID="CheckBox1" runat="server" Text="HSC" />  
        <br />  
        <asp:CheckBox ID="CheckBox2" runat="server" Text="SSC" />  
        / Polytechnic<br />  
        <asp:CheckBox ID="CheckBox3" runat="server" Text="BE" />  
        <br />  
        <br />  
        <asp:Button ID="Button1" runat="server"   
        OnClick="Button1_Click" Text="Submit " />  
  
        <asp:Label ID="Label1" runat="server" ForeColor="Lime"   
        Text="Label"></asp:Label>  
    </form>  
</body>  
</html>  
  
  
  

****Output 1:****

![](https://media.geeksforgeeks.org/wp-content/uploads/20210615191037/check1.png)

****Output 2:****

![](https://media.geeksforgeeks.org/wp-content/uploads/20210615191146/check2.png)

### ****20. Explain the HTML server controls in ASP.NET?****

****HTML Server Controls :**** HTML elements are exposed to the server. They expose an object model that maps very closely to the HTML elements that they render. You can run these controls on the server by defining the runat =”server” attribute.

|****CONTROL****|****DESCRIPTION****|
|---|---|
|HtmlForm|Create an HTML form control, used as a placeholder for other controls.|
|HtmlInputText|Creates an input text box control used to get input from the user.|
|HtmltextArea|Creates multi-line text box control.|
|HtmlAnchor|Creates Web navigation.|
|HtmlButton|Creates a button control.|
|HtmlImage|Creates an image control, which is used to display an image.|
|HtmlInputCheckBox|Creates a checkbox control.|
|HtmlInputRadioButton|Creates a radio button control.|
|HtmlTable|Creates a table control.|
|HtmlTableRow|Creates a row within a table.|
|HtmlTableCell|Creates a cell within a row.|

### ****21. What is LINQ?**** 

LINQ is known as ****Language Integrated Query**** and it is introduced in __.NET 3.5__ and Visual Studio 2008. The beauty of LINQ is it provides the ability to __.NET__ languages(like C#, VB.NET, etc.) to generate queries to retrieve data from the data source. For example, a program may get information from the student records or accessing employee records, etc. In, past years, such type of data is stored in a separate database from the application, and you need to learn different types of query language to access such types of data like SQL, XML, etc. And also you cannot create a query using C# language or any other __.NET__ language.

To overcome such types of problems Microsoft developed LINQ. It attaches one, more power to the C# or __.NET__ languages to generate a query for any LINQ compatible data source. And the best part is the syntax used to create a query is the same no matter which type of data source is used means the syntax of creating query data in a relational database is the same as that used to create query data stored in an array there is no need to use SQL or any other __non-.NET__ language mechanism. You can also use LINQ with SQL, with XML files, with ADO.NET, with web services, and with any other database.

### ****22. What is ASP.NET Core?****

ASP.NET Core is the open-source version of ASP.NET, that can be run on macOS, Linux, and Windows. ASP.NET Core was first delivered in 2016 and is a re-plan of prior Windows-just forms of ASP.NET.

In November 2015, Microsoft released the 5.0 version of ASP.NET which get separated later and known as ASP.NET Core. Also, it is considered as an important redesign of ASP.NET with the feature of open-source and cross-platform. Before this version, ASP.NET is only considered a Windows-only version.

### ****23. What is Razor in ASP.NET?****

In ASP.NET, Razor provides the syntax for developing dynamic web pages with the help of C# and HTML. ASP.NET can be integrated with JS(JavaScript) and it also includes the frameworks like React and Angular for the SPA(Single Page Application).

### ****24. What are the types of Authentication in ASP.NET?****

Authentication is the process of checking the identity of a user based on the user’s credentials. Generally, user’s credentials are in the form of user ID and password, and we check their credentials from a database or equivalent alternative if it exists then the user is a valid candidate for the next process – authorization. There are different types of Authentication available in ASP.NET namely:

- Form Authentication
- Passport Authentication
- Windows Authentication
- Custom Authentication

### ****25. What is Query String in ASP? And what are its advantages and disadvantages?****

A QueryString is a collection of characters input to a computer web browser. It is helpful when we want to transfer a value from one page to another page. If the sending data is in large quantity then we can not use Request.QueryString because it supports only 255 characters. We use the ‘&’ special character for separate multiple query strings. Any query string that was available to the calling ASPX page will be available to the called ASPX page.

### ****26. Briefly describe the difference between the Web Site and Web Application?****

A web application is a piece of software that can be accessed by the browser. A Browser is an application that is used to browse the internet. Web application needs authentication. The web application uses a combination of server-side scripts and client-side scripts to present information. It requires a server to manage requests from the users. For example, Google Apps

A website is a collection of related web pages that contains images, text, audio, video, etc. It can be consist of one page, two pages, and n number of pages. A website provides visual and text content that users can view and read. To view a website requires a browser(chrome, firefox). There are many types of websites like Archive website, Blog, Community website, Dating website, etc. For example, Amazon, youtube, etc.

### ****27. Explain View State?**** 

****View state**** is the method that the ****ASP****.****NET**** page framework uses to preserve page and control values between round trips.

<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm4.aspx.cs"   
Inherits="WebApplication9.WebForm4" %>  

  
<!DOCTYPE html>  
  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head runat="server">  
    <title></title>  
</head>  
<body>  
    <form id="form1" runat="server">  
         
         <div>  
            <h6>Example of View State:</B></h6>  
             <p><B><I><U>WELCOME TO GEEKSFORGEEKS</B></I></U></p>  
           
            Page Counter:  
              
             <br />  
             <br />  
              
         <asp:Label ID="lblCounter" runat="server" />  
             <br />  
             <br />  
             <br />  
             <asp:Button ID="btnIncrement" runat="server"   
             Text="Number of Visitors Count" OnClientClick="btnIncrement_Click"  />  
         </div>  
      </form>       
</body>  
</html>  
  
  
  

****Output:****

![](https://media.geeksforgeeks.org/wp-content/uploads/20210615144157/viewstate.jpg)

### ****28. Explain Cookies in ASP.NET?****

A Cookie can be defined as small pieces of information, which can be sent to a  browser by a server program and stored by the internet browser. The internet browser will then, at that point pass the Cookies back to the server each time it makes a request from that server. This is especially helpful for permitting verification/ authentication.

 Suppose, when a user signs in to a password-restricted system, a cookie stores user information (user name, password). So the client doesn’t need to re-type their details information for each new page they wish to download. The cookie property gets a collection of the client’s cookie variables.

### ****29. Explain the purpose of Web Services in ASP.NET?****

Web services are a web application that is fundamentally a class comprising of methods that could be utilized by different applications. It likewise follows a code-behind design, for example, the ASP.NET pages, despite the fact that it doesn’t have a user interface.

## ASP.NET Core Advanced Interview Questions

### ****30. Write a step for Request Flow in ASP.NET MVC framework?****

The sequence for Request Flow in ASP.NET MVC is as follows:

- ****Request****: In this step firstly request is received. After that,  in the Global.asax file, route objects are added to the Route table object.
- ****Routing****: At the second step routing is performed. After the application gets from the client, it uses URL Routing Module to deal with the request. The Route Table guides URLs to handlers. A routing is coordinating with a system that matches with the request’s URL against the URL patterns which are available in the Route Table. The Routing engine diverts the request to the relating IRouteHandler when the match is found in the pattern. Assuming relating mentioned URL is not found in the routing table, it will return a 404 HTTP status code.
- ****MVC Handler****: A RouteHandler responsible for deciding the HTTP handler that will serve the request, according to the received RequestContext.
- ****Controller****: In this step, the controller decides which action method is to be executed.
- ****Action Executed:**** After the controller gets instantiated ActionInvoker will determine which Action method needs to execute. ActionNameSelectorAttribute and ActionMethodSelectorAttribute methods used to select action method. The action method receives user input then executes the result and returning a result type to view.

### ****31. Explain the various modes for the Session state in ASP.NET?**** 

- ****InProc****: Sessions are stored within the application’s process on a web server. Depending on the IIS rendition utilized that could be aspnet_wp.exe or w3wp.exe.
- ****StateServer****: Sessions are stored by utilizing State Server windows administration service.
- ****SQLServer****: SQL Server database is utilized to store sessions’ information.
- ****Custom****: A custom session state provider manages all the session states.

### ****32. Write down different return types of a controller action method?****

- View Result
- Javascript Result
- Redirect Result
- JSON Result
- Content Result

### ****33. How to maintain sessions in MVC?****

We can maintain sessions in MVC using three different ways:

- Temp data
- Viewdata
- View bag

### ****34. How would you explain the differences between Repeater and ListView?****

Repeater control is derived from the Control class. A repeater simply repeats data given in templates. Repeated data is usually HTML code mixed with records from the data sources. Repeater’s output is not predefined. Because of that, Repeater demands most work to define the template. In return, it gives us the most flexibility to build the layout and optimize the presentation.

With the same template and same data set, Repeater usually works faster than Data List or GridView controls. This is mostly because of the DataReader class, which is used for read-only access. DataReader is faster than DataSet or DataTable classes commonly used with GridView.

Compared to GridView and DataList control, Repeater has limited features. By default, Repeater is good for displaying data. It is not the best choice if you need editing of data. Also, by default, it doesn’t provide paging and sorting of records.

ListView control is the newest data presentation control, introduced in ASP.NET 3.5. Previous controls (Repeater, DataList, and GridView) logically follow each other. For example, Repeater is simplest but fastest, then DataList has more features but more overheads too, and finally GridView is most complex, has most features, but heaviest and thus slowest on-page. Now, there is new ListView control that tries to provide the best from both sides: speed and flexibility in design, and also a lot of features like paging, updating or deleting of records, etc. Because of this, ListView control is often a better choice than Repeater or DataList.

### ****35. Describe loginStatus Controls in ASP?**** 

The ASP.NET supports a robust login controls for web-based application which does not require any program coding. The LoginStatus control is a very simple control, all it does is display a link that is different depending on whether the user is logged in or logged out. If a user is logged in then it displays a LogOut link and vice versa.

There are few properties that it supports, LogOutAction can be used to specify what happens when a user clicks on the LogOutLink, and the options are Redirect, RedirctToLoginPage, Refresh. If we set it to Redirect then we must set another property LogOutPage Url which a user is redirected to after logging out of the website.

<%@ Page Language="C#" AutoEventWireup="true"   
CodeBehind="WebForm1.aspx.cs" Inherits="WebApplication10.WebForm1" %>  

  
<!DOCTYPE html>  
  
<html xmlns="http://www.w3.org/1999/xhtml">  
<head runat="server">  
    <title></title>  
</head>  
<body>  
    <form id="form1" runat="server">  
        <div>  
            Welcome To GeeksForGeeks<br />  
  
            <asp:LoginStatus ID="LoginStatus1" runat="server"  
             ForeColor="#CC0000" LoginText="Click here for Login" />  
            <br />  
            <br />  
  
            <asp:LoginStatus ID="LoginStatus2" runat="server"   
            ForeColor="#CC0000" LoginText="Click here to Logout" />  
            <br />  
            </div>  
    </form>  
</body>  
</html>  
  
  
  

### ****Output:****

![](https://media.geeksforgeeks.org/wp-content/uploads/20210615173524/loginstatus.png)

### ****36. What do you know about JIT?****

Just-In-Time(JIT) Compiler: Just-In-Time compiler(JIT) is a part of Common Language Runtime (CLR) in .NET which is responsible for managing the execution of .NET programs regardless of any .NET programming language. A language-specific compiler converts the source code to the intermediate language. This intermediate language is then converted into the machine code by the Just-In-Time (JIT) compiler. This machine code is specific to the computer environment that the JIT compiler runs on. 

> __To read more, refer__ to __the article:__ [_****What is Just-In-Time(JIT) Compiler in .NET****_](https://www.geeksforgeeks.org/what-is-just-in-time-jit-compiler-in-dot-net/)_****?****_

### ****37. What is RedirectPermanent in ASP.Net?****

The RedirectPermanent(String) method overload gives a 301 HTTP status code in the reaction and incorporates the URL to divert the request. A 301 HTTP status code is a standard code in an HTTP reaction. It shows that a lasting redirection exists, and it gives the redirection area.

### ****38. What is AJAX in ASP.NET?****

The full form of ASP.NET AJAX is Asynchronous JavaScript and XML. ASP.NET AJAX also known as AJAX, is a bunch of augmentations of ASP.NET. It uses asynchronous data transfer between browser and webserver to allow web pages to request small bits of information from the server instead of entire pages. This technique makes Internet applications smaller, faster, and more user-friendly. It is created by Microsoft to execute AJAX functionalities in Web applications. The ASP.NET AJAX works with the AJAX Library that utilization object-arranged programming (OOP) to faster rich Web applications.

### ****39. What is Round Trip in ASP.NET?****

At the point when server-side processing is included, then there are four stages included:  

1. A user requests a Web form from the Web server.
2. Web Server reacts back with the mentioned Web form.
3. The user enters the information and submits the webform to the webserver.
4. Then Web Server processes the form structure and sends the outcomes back to the particular user.

Now, stage 3 is known as a page postback, while stages 3 and 4 are aggregately known as a “roundtrip”. We can say that- “A roundtrip includes making a total excursion over the network to the Web browser and getting the reaction back.  The Web applications use HTTP to build up correspondence between the Web program and the Web server. 

### ****40. What is the REST architecture?****

REST stands for ****RE****presentational ****S****tate ****T****ransfer.REST is an architectural style that doesn’t follow any strict standard but follows six constraints defined by Roy Fielding in 2000. Those constraints are – Uniform Interface, Client-Server, Stateless, Cacheable, Layered System, Code on Demand.REST is not restricted to XML and it’s the choice of implementer which Media-Type to use like XML, JSON, Plain-text. Moreover, REST can use SOAP protocol but SOAP cannot use REST.REST is easy to implement and requires less bandwidth such as smartphones.

****Architectural Constraints of RESTful API:**** There are six architectural constraints that make any web service are listed below:

- Uniform Interface
- Stateless
- Cacheable
- Client-Server
- Layered System
- Code on Demand

### ****41. What is Caching and its different types?****

In Asp.Net the caching method allows to store or cache Web Page output. This technic is used to avoiding the overhead of recreating the same data. There are three different caching types available in ASP.NET:

- Page Output Caching
- Page Fragment Caching
- Data Caching

Caching increases the performance parameter if the same data or information is requested by the user.

- ****Page Output Caching:**** It is implemented by placing an OutputCache directive at the top of the .aspx page at design time.
- ****Data Caching:**** It is used for quick retrieval of application data and implemented by the Cache object.
- ****Page Fragment Caching:**** It is used to store part of a Web form response in memory by caching a user control.

### ****42. What does the method Finalize do in ASP.NET?****

The Finalize technique is utilized to perform a cleanup procedure on unmanaged resources held by the current object before the object is destroyed. The strategy is ensured and subsequently is available just through this class or through a derived class.

### ****43. Write down the name of all steps in the ASP.NET page life cycle?****

- Page request
- Starting of page life cycle
- Page initialization
- Page Load
- Validation
- Postback event handling
- Page rendering
- Unload

### ****44. What is tracing in .NET?****

ASP.NET includes an easy-to-use functionality that helps to debug Web applications. Tracing functionality allows debugging print statements to be inserted into the code to output variables or structures, assert whether a condition is met, or trace through the execution path of the application. Trace feature is used to track particular types of actions in a deployed application as they occur (for example, database connections), and can thus monitor the application’s efficiency. The new tracing features of ASP.NET allow simulating ****Response.Write()**** statements. The users need not worry about removing the statements before deploying the applications. Instead of using Response.Write(), Trace.Write() is used. The Trace object is an intrinsic page object, similar to Request, Response, Server, etc. It is accessible directly with the page code.

****Trace class:**** A Trace class is used to get information about Trace. When the Trace property is used, an instance of the TraceContext class is defined in the System.Web namespace. Trace class provides a set of methods and properties that help to trace the execution of code. Instrumentation allows monitoring the health of the application running in real-life settings. Tracing helps to isolate problems and fix them without disturbing a running system.

__There are two different ways to enable tracing:__

- In C# or Managed Extensions for C++, the /d: TRACE flag can be added to the compiler command line. In Visual Basic, the /d: TRACE=True flag can be added to the compiler command line
- The #define TRACE can be added to the top of the file. This syntax is compiler-specific. If the user is using a compiler other than the ones specified above, the compiler’s documentation has to be referred to enable conditional compilation

### ****45. Write down different Trace Methods provided in ASP.NET?****

- ****Assert()**** – Checks for a condition, and displays a message if the condition is false.
- ****Close()**** – Cleanup the output buffer, and then closes the Listeners so that they no longer receive debugging output.
- ****Fail()**** – This method emits an error message.
- ****GetType()**** – It is used for “Gets the Type of the Object”.
- ****ToString()**** – Returns a String that represents the current Object
- ****GetHashCode()**** – This method works like a hash function for a particular type. It is suitable for use in hashing algorithms and data structures like a hash table.
- ****Equals()**** – Determines whether the specified Object is the same instance as the current Object
- ****Warn()**** – Writes trace information, along with optional exception data, to the trace log. All warnings appear as red text. It has two forms. The first form writes trace information to the trace log including any user-defined categories.
- ****Write()**** – Writes trace information to the trace log. It has two forms. The first form writes trace information to the trace log, including any user-defined categories and traces messages.

### ****46. Explain Local Resources and Global Resources?****

A local resource is explicit to a specific page, which is the one in particular who can get to it, while global resources can be accessed from any place. Local resources are kept in the App_LocalResources organizer, while global are kept in the App_GlobalResources folder. Local and global resources records will appear to be identical, so the only distinction is the folder they reside in. But they are utilized in different.

### ****47. Write down various page events in ASP.NET?****

- PreInit
- Init
- InitComplete
- LoadViewState
- LoadPostData
- PreLoad
- Load
- LoadComplete
- PreRender
- PreRenderComplete
- SaveStageComplete
- UnLoad

### ****48. What is Navigation control in ASP.NET?****

Navigation Control is defined as a menu that can be stored in a file to make it easier to maintain. This file is normally called web.Sitemap, and is stored in the root directory of the web. An ASP.NET has three different types of Navigation control:

- Dynamic Menus
- TreeView
- Site Map path

### ****49. Describe TreeView control?****

The  TreeView control is made up of nodes. Each entry in the tree is called a node and is represented by a TreeNode object. A node that contains other nodes is called a parent node. A node that is contained by another node is called a child node. A node that has no child nodes is called a leaf node. A node that is not contained by any other node but is the ancestor to all the other nodes in the root node. A node can be both a parent and a child, but root, parent, and leaf nodes are mutually exclusive. Several visual and behavioural properties of nodes are determined by whether a node is a root, parent, or leaf node.

### ****50. Explain ADO.net?****

ASP.NET has introduced the next generation of ADO known as ADO.NET with respect to data access. ADO.NET places more emphasis on disconnected recordsets by employing XML as a medium of communication between these record sets and the DataStore.ADO.NET is the latest of the database access technologies that began with the Open Database Connectivity (ODBC) application programming interface (API). Microsoft introduced open database connectivity with the promise of creating a singular common access methodology for databases. ODBC has come a long way since those early days. Almost every major database in use today supports ODBC drivers, and third-party developers provide optimized driver versions. The primary focus of the ODBC is to provide a consistent interface to database data sources.

## Conclusion

The article “ASP.NET Interview Questions and Answers” serves as an invaluable guide, offering comprehensive insights into this powerful platform. By exploring these latest questions and their concise answers, you can enhance your knowledge and enhance your chances of acing your ASP.NET interview. Stay prepared, stay confident, and embark on your journey to success in the ever-evolving realm of ASP.NET development.

****Here are some valuable sources and references for your ease:****

- ****Official Website****: [https://dotnet.microsoft.com/apps/aspnet](https://dotnet.microsoft.com/en-us/apps/aspnet)
- ****ASP.NET Documentation****: [https://learn.microsoft.com/en-us/aspnet/core/](https://learn.microsoft.com/en-us/aspnet/core/)

## ASP.NET Interview Questions – FAQs

### 1. What are the benefits of ASP.NET Core over the classic ASP.NET?

> Benefits of ASP.NET Core over classic ASP.NET:
> 
> - Improved performance and scalability.
> - Cross-platform support, running on Windows, Linux, and macOS.

### 2. When do you choose classic ASP.NET over ASP.NET Core?

> Choose classic ASP.NET when you have an existing application built on the .NET Framework and need to maintain compatibility with legacy code and libraries.

### 3. What are some of the most common ASP.NET interview questions?

> Some of the most common ASP.NET interview questions include:
> 
> - What is ASP.NET?
> - What are the benefits of ASP.NET?
> - What are the different types of ASP.NET applications?
> - What is the MVC pattern?
> - How do you create a web application in ASP.NET?
> - How do you handle user input in ASP.NET?
> - How do you secure a web application in ASP.NET?
> - How can I prepare for an ASP.NET interview?