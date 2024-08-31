#  Run a Java application 

 Convert a desktop app to a webapp 

CheerpJ can run a Java application in the browser with little to no  modifications. This page will help you getting started with CheerpJ and  running your first Java application in the browser.

Java source code is not needed to use CheerpJ. If you are building your own application you should already have its `.jar` file(s).

**To get started you will need:**

- Your Java application file(s). You can also use this [TextDemo.jar![img](https://cheerpj.com/docs/icons/external-link.svg)](https://docs.oracle.com/javase/tutorialJWS/samples/uiswing/TextDemoProject/TextDemo.jar) sample.
- An HTML file where your Java app will be wrapped
- A simple HTTP server to test your webpage locally

## 1. Create a project directory[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#1-create-a-project-directory)

Let’s start by creating a project folder where all your files will be. Please copy your java and future HTML files here.

Terminal window

```
mkdir directory_name
```

## 2. Create a basic HTML file[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#2-create-a-basic-html-file)

Let’s create a basic HTML file like the following example. Please  notice the CheerpJ runtime environment has been integrated and  initialized. In this example we are assuming your HTML file and your `.jar` files are under the project directory you just created.

index.html

```
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>CheerpJ test</title>
    <script src="https://cjrtnc.leaningtech.com/3.0/cj3loader.js"></script>
  </head>
  <body>
    <script>
      (async function () {
        await cheerpjInit();
        cheerpjCreateDisplay(800, 600);
        await cheerpjRunJar("/app/my_application_archive.jar");
      })();
    </script>
  </body>
</html>
```

Alternatively, if your application is not designed to be executed with the command `java -jar` you can replace `cheerpjRunJar()` for `cheerpjRunMain()` and pass your qualified class name as an argument. For example:

```
cheerpjRunMain(
  "com.application.MyClassName",
  "/app/my_application_archive.jar:/app/my_dependency_archive.jar",
);
```



> Don’t forget to use the /app/ prefix
>
> It is common for first-time users to forget to add  the prefix “/app/” when passing the application location to  cheerpJRunJar() or cheerpjRunMain().

## 3. Host your page[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#3-host-your-page)

You can now serve this web page on a simple HTTP server, such as the http-server utility.

Terminal window

```
npx http-server -p 8080
```



> Opening the page directly from the disk (for example, by double-clicking on it) is not supported.

## What’s going on?[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#whats-going-on)

- The `<head>` script loads CheerpJ.
- [`cheerpjInit`](https://cheerpj.com/docs/reference/cheerpjInit) initialises the CheerpJ runtime environment.
- [`cheerpjCreateDisplay`](https://cheerpj.com/docs/reference/cheerpjCreateDisplay) creates a graphical environment to contain all Java windows.
- [`cheerpjRunJar`](https://cheerpj.com/docs/reference/cheerpjRunJar) executes your application!
- `/app/` is a [virtual filesystem](https://cheerpj.com/docs/guides/File-System-support) mount point that references the root of the web server this page is loaded from.

## The result[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#the-result)

You will see the CheerpJ display on your browser with some loading  messages before showing your application running. Depending on your  application and the optimizations applied, this could take just a few  seconds.

### Is your application not working?[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#is-your-application-not-working)

Please try these checks:

- The location of your JARs is correct and the prefix `/app/` is added when passing it to [`cheerpjRunJar`](https://cheerpj.com/docs/reference/cheerpjRunJar) or [`cheerpjRunMain`](https://cheerpj.com/docs/reference/cheerpjRunMain). For more information visit the [virtual filesystem](https://cheerpj.com/docs/guides/File-System-support) guide.
- Your Java application works normally on your machine without CheerpJ.
- You are not opening the page by double clicking on it and you are using an http-server instead.

## Further reading[![img](https://cheerpj.com/docs/icons/heading-link.svg)](https://cheerpj.com/docs/getting-started/Java-app#further-reading)

- [Runtime API reference](https://cheerpj.com/docs/reference)