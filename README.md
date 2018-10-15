# .NET Core 2.1 Buildpack for Heroku
## by Softtrends LLC

This Buidpack can be used to compile and deploy .Net Core application, ASP.Net Application, ASP.Net MVC Application to Heroku.

# Programming Note

We've made some big updates in this release, so it’s **important** that you spend a few minutes to learn what’s new.

You've created a new ASP.NET Core MVC project. [Learn what's new](https://go.microsoft.com/fwlink/?LinkId=518016)

You need to make the following changes in your Program.cs to deploy on Heroku
<br/>
In **Program.cs**

*   Add UseUrls method and pass args[0] as parameter to start your app. Because Heroku web dyno will start with dynamic port after sucessful deployment. We need to use the same port in code behind also then only your app will start and listen on that port else dotnet runtime will set default port 5000. Thereby we pass port number as parameter with url in Procfile
<br/>
public static void Main(string[] args
{<br/>
            {
            BuildWebHost(args).Run();
        }
                public static IWebHost BuildWebHost(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>()
                .Build();
}<br/>
<br/>
            
# Example
In order to see the buildpack in action, you can click on the button below which will deploy a sample ASP.Net MVC application to heroku and you can see the build and deployment logs as the application gets deployed for you. This application was developed using Visual Studio 2017. 
<br/>
<br/>
<a href="https://heroku.com/deploy?template=https://github.com/heroku-softtrends/dotnetcore2.main.sample/tree/master">
  <img src="https://www.herokucdn.com/deploy/button.svg" alt="Deploy">
</a>

You can also download the source code for the Sample Application by [Clicking here](https://github.com/heroku-softtrends/dotnetcore2.main.sample/tree/master)

