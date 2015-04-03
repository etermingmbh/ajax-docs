---
title: Protecting the Telerik ASP.NET AJAX Assembly
page_title: Protecting the Telerik ASP.NET AJAX Assembly | UI for ASP.NET AJAX Documentation
description: Protecting the Telerik ASP.NET AJAX Assembly
slug: introduction/deployment/protecting-the-telerik-asp.net-ajax-assembly
tags: protecting,the,telerik,asp.net,ajax,assembly
published: True
position: 4
---

# Protecting the Telerik ASP.NET AJAX Assembly



## 

__Technical guidelines for protecting Telerik UI for ASP.NET AJAX binaries when redistributed with other applications__





We are providing the following suggestions to protect our IP (Intellectual Property) when redistribute our assemblies as a part of shrink-wrapped software (packaged products).

__Prerequisites__

Protecting *Telerik UI for ASP.NET Ajax* requires the *Telerik.Web.UI* assembliy to be built from source code (due to modifications applied to the source files). The source code of Telerik UI for ASP.NET AJAX is distributed separately and is bundled with build instructions. Please read the source code building instructions beforehand.

For brevity this document assumes that the source distribution ZIP file is extracted in C:\TelerikControlsAjaxSource.



__Instructions__

1. Open C:\TelerikControlsAjaxSource\Telerik.Web.UI\Common\AssemblyProtection.cs in a text editor (notepad, Visual Studio etc)

1. Uncomment the following line:

````C#
	public static void Validate()
	{
	   //Uncomment the following line
	   //ValidatePassPhrase();
	} 
````



````C#
	public static void Validate()
	{
	   //Uncomment the following line
	   ValidatePassPhrase();
	} 
````



1. Change the value of the *__ApplicationName__* constant to match the name of your application:

````C#
	//Modify to match your application name
	private const string ApplicationName = "MyApp"; 
````



````C#
	//Modify to match your application name
	private const string ApplicationName = "Sample Application Name v2.0 (tm)"; 
````



1. Save *AssemblyProtection.cs* and rebuild Telerik UI for ASP.NET Ajax (described separately in the source code build instructions document).

1. In your application replace the existing reference to Telerik.Web.UI.dll with the one built from source code.

1. If you run your application now you should see the following error message (“Sample Application Name v2.0 (tm)” will be replaced with the name of your application set in step 3):
>caption 

![](images/introduction-applicationisnotlicensed.jpg)

1. Add the following code in the Page_Load method of your page codebehind class.

````C#
	Application["Telerik.Web.UI.Key"] = "Sample Application Name v2.0 (tm)";
````



>note IMPORTANT!!! Instead of “Sample Application Name v2.0 (tm)” use the value of theApplicationName constant from step 3.
>
